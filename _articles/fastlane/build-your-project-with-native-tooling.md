---
title: 'Ionic + Fastlane: Build your Ionic or Cordova app with native tooling in Fastlane'
published: true
date: 2017-08-29 16:00:00 +0000
last_updated: ''
parent: ['Ionic + Fastlane', '../fastlane']
---
# Build your Ionic or Cordova app with native tooling in Fastlane
{:.no_toc}

If you [decided to build your project](build-your-project.md) with native tooling in Fastlane follow these instructions:

Though you can execute shell commands directly from Fastlane with the `sh` action and so could theoretically execute some CLI commands that control Xcode and Gradle, Fastlane has built in actions for both: `gym` and `gradle`.

* toc
{:toc}

## Note about versions

The details for building apps greatly depend on the versions of the software and build tools used to build, and in Cordova's case on the version of the libraries used to create the app.

This article was created when the following versions of the tools and Cordova libraries were current:

* iOS
  * Xcode 9.1
  * iOS 11.1
  * `cordova-ios` 4.5.4
* Android
  * Android Studio 2.3.3 + 3
  * API level 26, 27
  * `cordova-android` 6.3.0

If your software and libraries are older than this, it is very much possible that these instructions don't work 100% for you. If your local setup is newer than the listed versions, you should probably be fine. (Please [comment at the end of this article](#comments) if you encounter any problems - make sure to include your local versions!)

## iOS Limitations & Workaround

The native tooling doesn't play as well with the default iOS project produced by Cordova CLI as the [Fastlane Ionic plugin](build-your-project-with-ionic-plugin.md) or [Fastlane Cordova plugin](build-your-project-with-cordova-plugin.md) do. This means your lanes have to execute some additional code.

For the iOS builds to work with `gym` you need to upgrade your Xcode project from the pre-Xcode8 state it is in. A handy [fastlane plugin `upgrade_super_old_xcode_project`](https://github.com/ionic-zone/fastlane-plugin-upgrade_super_old_xcode_project) exists. It has to be installed and called by the build lanes.

Install it by executing `fastlane add_plugin upgrade_super_old_xcode_project` on the command line.

Add this lane to the iOS area of your `Fastfile` for the build lanes to use:

```ruby
  lane :upgrade_xcode_project do
    name = "FastlaneTest"
    xcodeprojpath = "platforms/ios/" + name + ".xcodeproj"
    team_id = CredentialsManager::AppfileConfig.try_fetch_value(:team_id)
    upgrade_super_old_xcode_project(
      path: xcodeprojpath,
      team_id: team_id,
      use_automatic_signing: true
    )
  end
```

Please be aware that this modifies your Xcode project files. These changes have to either be committed to your version control system or be executed each time (which the following lanes do).

## Debug Builds

The first step is to do a "Debug" build that is [debuggable](../understand/difference-between-a-debug-and-release-build.md). It can be used to test the app on a device or emulator, but later also to [distribute it to your testers via a third party distribution service like HockeyApp](upload-for-testing.md).

Just copy the following lanes in the correct `platform` area of your `Fastfile`:

### Android Debug Build

Start with Android, as everything is simpler with Android:

```ruby
desc "Build Debug"
lane :build_debug do
  gradle(
    task: 'assemble',
    build_type: 'Debug',
    project_dir: 'platforms/android',
  )
end
```

You can run this by executing `fastlane android build_debug`.

### iOS Debug Build

When you try to build your iOS project with the expected iOS equivalents to the Android actions you will unfortunately encounter a big red error message: You have to take care of certificates to be able to build for iOS.

Fortunately, Fastlane offers its own tool for this. [Read more about how to setup iOS certificate handling with Fastlane's `match`](setup-ios-certificate-handling.md) before continuing.

When you are done, the certificates are in place and you only have to add a `match` call to your lane:

```ruby
desc "Build Debug"
lane :build_debug do
  upgrade_xcode_project
  match(type: 'development')
  name = "FastlaneTest"
  xcworkspacepath = "platforms/ios/" + name + ".xcworkspace"
  gym(
    configuration: 'Debug',
    workspace: xcworkspacepath,
    scheme: name,
    export_method: 'development'
  )
end
```

You can run this by executing `fastlane ios build_debug`.

<div id="future-content">
### Conclusion: Debug Builds

Now that you can build the _Debug_ version of your app, go and [upload your app for testing with HockeyApp](upload-for-testing.md).
</div>

## Release Builds

When you are done with testing it's time to build a _Release_ version of your app. As with the CLI commands you are used to, only minimal changes are needed here.

### Android Release Build

For Android the Release version of an app has to be [signed (and zipaligned)](https://developer.android.com/studio/publish/app-signing.html). The `gradle` action can of course take care of that, but you need a _key_ and a _keystore_ file that contains it, both secured with a password before you can begin.

You can [create those using Android Studio](https://developer.android.com/studio/publish/app-signing.html#generate-key) (Open Android Studio -> Build -> Generate Signed APK... -> Create New) if you have it installed or do it [manually on the command line using `keytool`](https://developer.android.com/studio/publish/app-signing.html#signing-manually).

Put the generated file one level above your Ionic/Cordova project, and you can use a lane similar to this to build your Android project for production:

```ruby
desc "Build Release"
lane :build_release do
  gradle(
    task: 'assemble',
    build_type: 'Release',
    project_dir: 'platforms/android',

    properties: {
      "android.injected.signing.store.file" => '../FastlaneIonic.keystore',
      "android.injected.signing.store.password" => 'xyz',
      "android.injected.signing.key.alias" => 'FastlaneIonic',
      "android.injected.signing.key.password" => 'xyz',
    }
  )
end
```

If you remove `keystore_password` and `key_password` it will prompt you during the (first) build process.

### iOS Release Build

For iOS you don't have to change that much as you already had to do [additional work for the Debug build by initiating and configuring `match` to handle certificates](setup-ios-certificate-handling.md). Now this pays off, as you only have to change some parameters slightly:

```ruby
desc "Build Release"
lane :build_release do
  upgrade_xcode_project
  match(type: 'appstore')
  name = "FastlaneTest"
  xcodeprojpath = "platforms/ios/" + name + ".xcodeproj"
  gym(
    configuration: 'Release',
    project: xcodeprojpath,
    scheme: name,
    codesigning_identity: 'iPhone Developer'
  )
end
```

<div id="future-content">
### Conclusion: Release Builds

With the Release version of your app also built, you can either [upload this build for testing with Testflight and Play Store Alpha)](upload-for-testing.md) or even [publish your app to the stores](publish-your-app.md).
</div>

{::comment}
## Roundup: Build for iOS and Android, debug and release versions

You can combine the shown snippets into one simple `build` action per platform that gets a param to decide if it should build a Debug or Release build:

```
TODO
```
{:/comment}
