---
title: 'Ionic + Fastlane: Upload your Cordova apps for testing'
published: true
date: 2017-08-29 16:00:00 +0000
last_updated: ''
parent: ['Ionic + Fastlane', '../fastlane']
---
# Upload your Ionic and Cordova apps for testing with Fastlane
{:.no_toc}

When you are done developing your app and [created the first builds of it](build-your-project-choose-how), it's time to distribute your app to your testers for quality assurance and testing.

* toc
{:toc}

## Recap: Build your app

You already learned about the [multiple options how to create a build of your app](build-your-project-choose-how.md). No matter which variant you chose, for this article we assume you have a `build_debug` lane to create debug and a `build_release` lane to create release builds for each of the two platforms, iOS and Android, in your `Fastfile` - makes 4 in total.

Note that the path where your `build_*` lanes save the app file might be different if you are not using the `ionic` plugin, so make sure the following lanes use the correct path or variable to get the file.
{:.message}

## Introduction: Testing and Beta Distribution

There are two different ways to test an app: With the Debug version, or with the Release version. You can [read a detailed explanation of the differences, advantages and disadvantages of testing debug vs. release builds in this other article](). 

For this article here the following facts are important:

* Only debug builds can be debugged
* For iOS, debug builds can only installed on max. 100 devices that have to be registered
* 



During development you probably did some local testing of your app with e.g. `ionic serve`, the Ionic DevApp or Ionic View. Later you might have switched to actually run your app on an emulator or local connected device with `ionic cordova run android/ios` or `cordova run android/ios`.

For testing via a testing or beta Distribution service to get your app out to testers, you now can also do it this way or you can create a Release build that can be tested:

### Debug Testing

When doing this you created a Debug app of your app

 that your debugger and developer tools could connect to.
App can be debugged (connect from computer to look inside the app)
(e.g. remote debug the app via Safari, test the actual same version that you are developing)

For iOS debug testing happens with `development` certificates, which require devices to be listed in the provisioning profiles. 
You have to worry about provisioning profiles and the devices included in them. Only devices with UDIDs in there can run the app. Have to [make sure your provisioning profiles used to build are up to date](setup-ios-certificate-handling.md#regenerate-provisioning-profiles-with-newly-added-devices).
)

it allows these services to mess with the certificates a bit and also install the app via a simple download. (resign)

Simplest variant: Just send an email with the file.

More luxury:
Downloading from a website
only for authenticated users
managing lists of testers
Added SDK in app: Logging of crashes, in-app feedback, in-app update notifications and updates, event tracking and analytics, binary and version archival, download tracking

Unfortunately no service by Google or Apple for this, but [many third party offerings took that role](http://mobiledraft.com/tools/app-distribution/). They all work the same way: You build your app, upload the binary to the service where testers are notified that a new version is available and can be downloaded.

We will look at two of them: HockeyApp and App Center.

### Release Testing

Instead of testing a Debug build you can also use a Release build for testing.

App can not be debugged

App can be "promoted" to be the distribution version that actual users get

Big disadvantage is that a Release build for iOS can not be installed via a simple download - which means that third party services don't work here. Reason is that Release builds can only installed if they are downloaded from the app store, which replaces some of the certifications and provisioning profiles along the way. This make iOS devices very secure, as **all** software has to come from the AppStore.



Disadvantage iOS: Can not be installed via simple download
Compared to third party services and distributing development builds the beta distribution of release versions has one big advantage: You don't have to worry about device lists.

  Third Party
    limited benefit
    Uploading a Release version to third party beta distribution tools only really makes sense for Android as an iOS release or distribution build can only be installed when it was downloaded via 
    Only makes semi sense as you can't install `release` builds of iOS apps on devices unless it comes from the AppStore or TestFlight (which does some black magic to make this work)
  Stores
    iOS: TestFlight
    Android: Play Store alpha/beta lane

Similar to debug version distribution, there are third party distribution testing services as HockeyApp, explained above. But also additional possibilities offered by the official platforms themselves: TODO

## Debug Version Testing

### HockeyApp

TODO Logo

[HockeyApp](https://www.hockeyapp.net/) is historically one of the most popular beta distribution services. It is mostly free, easy to use, supports both iOS and Android.

#### Setup and Configuration

The `hockey` fastlane action included in fastline normally expects an `api_token` parameter to authenticate the calls to HockeyApp. Although you could hardcode this value in the `Fastfile` (if you are the only one having access to it), it is suggested to be [set via an environment variable](https://docs.fastlane.tools/advanced/#environment-variables). If you use the name `FL_HOCKEY_API_TOKEN` for the environment variable, you can even leave the `api_token` parameter of the action as `hockey` will automatically use it without any additional code when calling the lane:

1. First generate the token in the ["API Tokens" interface of HockeyApp](https://rink.hockeyapp.net/manage/auth_tokens (Login, then click Avatar -> Accounts Settings -> API Tokens)
1. Copy the newly created token
1. Create a file called `.env` in your `fastlane` folder
1. Fill it with `FL_HOCKEY_API_TOKEN=YOURTOKENHERE` (Replace `YOURTOKENHERE` with the copied token of course)

Now the `hockey` action can use this environment variable for its `api_token` value automatically.

#### Lane

The lane below first executes `build_debug` to create a new build of your app. Then it calls `hockey` to upload that build to HockeyApp. If this is the first time HockeyApp sees this app (package name or bundle id), it will automatically create a new app entry in your HockeyApp account where it then stores the app file.

There are many more [parameters for the `hockey` action to customize what happens when it is used](https://docs.fastlane.tools/actions/hockey/#hockey).

{::comment}
TODO When https://github.com/ionic-zone/fastlane-plugin-ionic/issues/17 is implemented (and also merged over to the Cordova plugin), `ipa` and `apk` parameters can also be removed and the lanes for iOS and Android become identical
{:/comment}

TODO Combine when `ionic` automatically sets the correct variables

##### iOS

```ruby
lane :hockey_debug do
  build_debug
  hockey(
    ipa: ENV['CORDOVA_IOS_RELEASE_BUILD_PATH']
  )
end
```

##### Android

```ruby
lane :hockey_debug do
  build_debug
  hockey(
    apk: ENV['CORDOVA_ANDROID_RELEASE_BUILD_PATH']
  )
end
```

### App Center

TODO Logo

[Visual Studio App Center](https://appcenter.ms) is the successor and replacement of HockeyApp (after Microsoft bought them and decided to integrate all their mobile tools into one offering - nice!). It is built on the learnings of HockeyApp, and besides adding lots of new features it also does the same fine job for beta and testing app distribution.

{::comment}
TODO If you need deeper integration with App Center, for example automated update prompts inside the app, take a look at [cordova-plugin-appcenter]().
{:/comment}

#### Setup and Configuration

The `appcenter_upload` action we will be using is not part of fastlane itself, but available as a fastlane plugin: [fastlane-plugin-appcenter](https://github.com/Microsoft/fastlane-plugin-appcenter). You can install it by executing `fastlane add_plugin appcenter` on the command line.

All calls to App Center require [an API token](https://appcenter.ms/settings/apitokens) and the owner name (URL slug of your username or organization name, take a look at the URLs of App Center) as parameters. You can either define them manually for all actions or [set them via an environment variable](https://docs.fastlane.tools/advanced/#environment-variables): `APPCENTER_API_TOKEN` and `APPCENTER_OWNER_NAME`

#### Lane

The lane below first executes `build_debug` to create a new build of your app. Then it calls `appcenter_upload` to upload that build to App Center. It supplies an `app_name` that includes that platform name - apps in App Center have to be unique per `owner_name`.

If this is the first time App Center sees this app, it will automatically create a new app entry in your App Center account where it then stores the app file.

There are many more parameters for the `appcenter_upload` action to customize what happens when it is used, execute `fastlane action appcenter_upload` to get an overview.

TODO Combine when `ionic` automatically sets the correct variables

##### iOS

```ruby
lane :appcenter_debug do
  build_debug
  name = 'FastlaneExample'
  appcenter_upload(
    ipa: ENV['CORDOVA_IOS_RELEASE_BUILD_PATH'],
    app_name: name + '-' + lane_context[SharedValues::PLATFORM_NAME].to_s + ''
  )
end
```

##### Android

```ruby
lane :appcenter_debug do
  build_debug
  name = 'FastlaneExample'
  appcenter_upload(
    apk: ENV['CORDOVA_ANDROID_RELEASE_BUILD_PATH'],
    app_name: name + '-' + lane_context[SharedValues::PLATFORM_NAME].to_s + ''
  )
end
```

## Release Version Testing

### Beta Distribution via Stores

#### iOS: Testflight

TODO Logo

Apple itself offers [TestFlight](https://developer.apple.com/testflight/) which "makes it easy to invite users to test your apps and collect valuable feedback before you release them on the App Store. You can invite up to 10,000 testers using just their email address."

It is important to note that this "test" is done on a normal production build:

> Using TestFlight to beta test iOS apps involves submitting an app to iTunes Connect that is signed with your App Store **distribution provisioning profile**. […] This is the preferred method of beta testing because it does not require you to re-build or re-sign the submission for App Store publication.

Source: [Apple Technical Note TN2407](https://developer.apple.com/library/content/technotes/tn2407/_index.html#//apple_ref/doc/uid/DTS40014991-CH1-FOLLOW_WORKFLOWS_DOCUMENTED_BY_APPLE_TO_RUN_ON_DEVICE__BETA_TEST__OR_SUBMIT_YOUR_APP-BETA_TESTING)

With normal Xcode projects uploading to Testflight via `fastlane` is so simple, that it is [one of the templates in the generated Fastfile](https://github.com/fastlane/fastlane/blob/51c005ab134b396df73e43403616cbe6adce4c27/fastlane/lib/assets/DefaultFastfileTemplate#L30-L39). For Ionic and Cordova projects it luckily is not much more complicated:

```ruby
platform :ios do
  ...
  desc "Submit a new Beta Build to Apple TestFlight"
  lane :testflight do
    build_release
    testflight(
       ipa: 'platforms/ios/build/device/' + "FastlaneTest"+ '.ipa' # TODO dynamic
      skip_waiting_for_build_processing: true,
    )
  end
  ...
end
```

Check the Testflight tab in your app on iTunes Connect to see if the upload worked.

#### Android: Alpha/Beta tracks

TODO Logo

The Google Play Store has "alpha" and "beta" tracks (in addition to "rollout" and of course "production") that [can be used to conduct closed and open alpha and beta tests](https://support.google.com/googleplay/android-developer/answer/3131213). 

Similar to builds on Testflight for iOS, these can be promoted to production, so you can not upload development builds but have to prepare an APK that could - potentially - be released to all users.

```ruby
platform :android do
  ...
  desc "Deploy a new version to the Google Play Store, alpha lane"
  lane :alpha do
    build_release
    supply(
      track: 'alpha',
      apk: 'platforms/android/build/outputs/apk/android-release.apk' # TODO dynamic
    )
  end
  ...
end
```

### Third party

#### HockeyApp

As `hockey` automatically creates an app per app identifier (package name for Android, bundle id for iOS), you can't just upload a release build next to your debug build - or it will upload it into the same app on HockeyApp. To work around this, you can actually [select a "release type"](https://support.hockeyapp.net/kb/app-management-2/how-to-organize-development-and-production-apps-for-distribution) when creating an app. Next to the default `beta` release type there are `alpha`, `enterprise` and `store` to choose from, the last being the obvious choice here. For the `hockey` action that translates to `release_type: '1'`.

##### iOS

Note: The logical choice `store` will disable downloads not only for iOS release apps - where it makes sense as they can't be installed on a device anyway - but also for Android apps. If you  want to be able to download the `.apk` file, you can switch to `enterprise` (`release_type: '3'`) as a workaround.
{:.message}

```ruby
  lane :hockey_release do
    build_release
    hockey(
      ipa: ENV['CORDOVA_IOS_RELEASE_BUILD_PATH'],
      release_type: '1'
    )
  end
```

##### Android

```ruby
  lane :hockey_release do
    build_release
    hockey(
      apk: ENV['CORDOVA_ANDROID_RELEASE_BUILD_PATH'],
      release_type: '3'
    )
  end
```

#### App Center

##### iOS

Note: When uploading an iOS app, App Center analyzes the provisioning profiles to recognize release apps and disables the download option.
{:.message}

```ruby
  lane :appcenter_release do
    build_release
    appcenter_upload(
      ipa: ENV['CORDOVA_IOS_RELEASE_BUILD_PATH'],
      app_name: name + '-' + lane_context[SharedValues::PLATFORM_NAME].to_s + '-release'
    )
  end
```

##### Android

```ruby
  lane :appcenter_release do
    build_release
    appcenter_upload(
      apk: ENV['CORDOVA_ANDROID_RELEASE_BUILD_PATH'],
      app_name: name + '-' + lane_context[SharedValues::PLATFORM_NAME].to_s + '-release'
    )
  end
```

## Roundup: Build and upload, iOS and Android

Now you saw the individual building blocks: Build the app, both debug and release builds. Then upload them to external services like HockeyApp or testing options offered by the stores themselves, Google Play alpha/beta channel and Apple's Testflight.

TODO rewrite

{::comment}
Combine both "upload for testing" actions into one.

We can pull all this into one `Fastfile`, where we only have 2 actions per platform, but which can be configured with parameters: just build, or build and upload to a selectable beta testing service:

```ruby
android
  build
    debug
    release
  beta
    hockey
    alpha
ios
  build
    debug
    release
  beta
    hockey
    testflight
```
{:/comment}
