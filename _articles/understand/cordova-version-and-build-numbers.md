---
title: 'Cordova: Version + Build Number for iOS and Android apps'
published: true
date: 2017-08-29 16:00:00 +0000
last_updated: ''
---
# Cordova: Version + Build Number for iOS and Android apps
{:.no_toc}

> A deep Dive into Cordova version numbers for iOS and Android projects

At the latest when your app is ready and should be uploaded to the stores (but better sooner) you have to think about how to version your apps. If you go into it with a naïve understanding of how versioning _should_ work, you might come out a bit confused.

If you come from either iOS or Android, researching how it is done on the other platform can become confusing quickly as well. Same if you only thought about it from aCordova viewpoint for now, seeing how this translates to the native platforms (and properties in Xcode or the store interfaces) definitely will be confusing: build number, version code, version name, version number, short version, bundle version, project version...

So how does versioning work in Cordova iOS and Android projects?

* toc
{:toc}

## Concepts

Let's start with the generalized concepts: There are two numbers connected to each build of an app: A _version_ and a _build_ number. 

### Version

The **Version** is the number that is shown to users and identifies which version of the app they have installed. This usually uses [Semantic Versioning](http://semver.org/) of Major.Minor.Patch. 

### Build

**Build** is an internal counter that increments with each build of the app, so there are usually lots of builds of the same version before one is considered "good" and released to the world. Most of the time it isn't shown to the user at all, so they just know about the version of an app, not the build.

TODO
automated bumping of build number with each build.
manual changes to version number with deliberate choice

## Native Platforms

This general idea gets complicated as soon as we look at the native platforms we are building our apps for and how they apply these concepts:

### iOS

For iOS the _version_ and _build number_ are usually set in the Xcode interface and written to some file of the Xcode project:

#### `CFBundleShortVersionString`

[`CFBundleShortVersionString`](https://developer.apple.com/library/content/documentation/General/Reference/InfoPlistKeyReference/Articles/CoreFoundationKeys.html#//apple_ref/doc/uid/20001431-111349) represents the _release version number_:

> The release version number is a string composed of three period-separated integers. The first integer represents major revision to the app, such as a revision that implements new features or major changes. The second integer denotes a revision that implements less prominent features. The third integer represents a maintenance release revision.
> The value for this key differs from the value for CFBundleVersion, which identifies an iteration (released or unreleased) of the app.

In Xcode access it via Project -> General -> Identity -> Version, saved in `App-Info.plist`.


```
    = Info -> Custom iOS Target Properties -> Bundle versions string, short
    = `xcrun agvtool what-marketing-version`
```

#### `CFBundleVersion`

[`CFBundleVersion`](https://developer.apple.com/library/content/documentation/General/Reference/InfoPlistKeyReference/Articles/CoreFoundationKeys.html#//apple_ref/doc/uid/20001431-102364) is called _build version number_:

> The build version number should be a string comprised of three non-negative, period-separated integers with the first integer being greater than zero—for example, 3.1.2. [...]
> While developing a new version of your app, you can include a suffix after the number that is being updated; for example 3.1.3a1. [...] The final number in the suffix is the build version, which cannot be 0 and cannot exceed 255. When you release the new version of your app, remove the suffix.

In Xcode access it via Project -> General -> Identity -> Build, saved in `App-Info.plist`.

```
    = Info -> Custom iOS Target Properties -> Bundle version
```

TODO Check if this is true
So during development _CFBundleVersion_ contains a suffix that represents an environment and can contain a _build version_. For release this suffix is removed which makes _CFBundleVersion_ identical to _CFBundleShortVersionString_ for release versions.

That could be it for iOS. Unfortunately Apple recently decided to move some stuff around in Xcode TODO:

#### `CURRENT_PROJECT_VERSION`

To accomodate its [tool `agvtool` for "Automating Version and Build Numbers"](https://developer.apple.com/library/content/qa/qa1827/_index.html) Apple moved the _build number_ value from `CFBundleVersion` and links to a new `CURRENT_PROJECT_VERSION`. In Xcode you access it via Project -> Build Settings -> Versioning -> Current Project Version. It is saved directly in `App.xcodeproj`.

Documentation on `agvtool` indicates that this [value also may be a incrementing Integer](https://developer.apple.com/library/content/qa/qa1827/_index.html#//apple_ref/doc/uid/DTS40014500-CH1-COMMAND_LINE-UPDATING_THE_BUILD_NUMBER) :

> Running agvtool next-version -all increments your version number to the next highest integer value. For instance, it will update 2 to 3 and 1.3 to 2. 

```
    = fastlane -> increment_build_number
    = Fastlane "build number"
    = `xcrun agvtool what-version`
```

#### Summary iOS

So for iOS _version number_ (`CFBundleShortVersionString`) should be a MAJOR.MINOR.PATCH string. The _build number_ should either be the same string with an added suffix MAJOR.MINOR.PATCHenvironmentBUILDNR (`CFBundleVersion`) or a simple incrementing Integer (`CURRENT_PROJECT_VERSION`).


### Android

In Android _version_ is known as **Version Name** (`versionName`) and the _build_  as **Version Code** (`versionCode`). They are both defined in the `build.gradle` file:

```gradle
android {
  ...
  defaultConfig {
    ...
    versionCode 2
    versionName "1.1"
  }
  ...
}
```

which is merged into `AndroidManifest.xml` during the build process:

```xml
<manifest android:versionCode="2" android:versionName="1.1" package="org.example.app" xmlns:android="http://schemas.android.com/apk/res/android">
```

Android is quite flexible in [its requirements for version naming](https://developer.android.com/studio/publish/versioning.html#appversioning). 

#### `versionName`

For the version name documentation defines

> The value is a string so that you can describe the app version as a `<major>.<minor>.<point>` string, or as any other type of absolute or relative version identifier. The versionName has no purpose other than to be displayed to users. 

#### `versionCode`

And only for the version code they limit a bit to

> An integer used as an internal version number. [...] The value is an integer so that other apps can programmatically evaluate it, for example to check an upgrade or downgrade relationship. You can set the value to any integer you want, however you should make sure that each successive release of your app uses a greater value. You cannot upload an APK to the Play Store with a versionCode you have already used for a previous version.

#### Summary Android

You can use any String as _version number_ (`versionName`) and a unique Integer for _build number_ (`versionCode`).


## Cordova

As Cordova is used to build both platforms from the same base project, another layer of abstraction is required here. 

### `version`

In the default configuration only a **Version** is set in `config.xml` and the **Build** number is automatically generated.

```xml
<widget id="org.example.app" version="0.0.1" xmlns="http://www.w3.org/ns/widgets" xmlns:cdv="http://cordova.apache.org/ns/1.0">
```

### `android-versionCode` + `ios-CFBundleVersion`

Unfortunately the build number generation is not very transparent and pretty broken[^1].

TODO rewrite: If you want control, you can also handle the build number yourself, but you have to do so separately for the platforms:
Attributes `android-versionCode` and `ios-CFBundleVersion` for the `widget` tag:

```xml
<widget id="org.example.app" version="0.0.1" android-versionCode="17" ios-CFBundleVersion="34" xmlns="http://www.w3.org/ns/widgets" xmlns:cdv="http://cordova.apache.org/ns/1.0">
```

As you see these attributes are named after their "target", not by their functionality. Correspondingly `android-versionCode` has to be an Integer and `ios-CFBundleVersion` could be the complicated iOS build number thingie TODO or an Integer as well.

Of course you are free to synchronize these two numbers and use the same build number for both `ios-CFBundleVersion` and `android-versionCode`.

### Summary Cordova

TODO

## Overview (Table)

Still confused? Have a look at this nice tabular overview:

|           | Version                       | Build
|-----------|:------------------------------|:------
| iOS<br/><br/>             | CFBundleShortVersionString<br/><br/>                                  | -&nbsp;CFBundleVersion<br/>-&nbsp;CURRENT_PROJECT_VERSION 
| Android<br/><br/><br/>    | versionName<br>"A string used as the version number shown to users."  | versionCode<br/>"An integer used as an internal version number." 
| Cordova<br/><br/><br/>    | version<br/><br/><br/>                                                | <br/>-&nbsp;android-versionCode<br/>-&nbsp;ios-CFBundleVersion  
| Others<br/><br/><br/>     | version name<br/><br/><br/>                                           | version number<br>build number<br>build version

## Automated incrementing

One way to automat this for Cordova is to use a hook like for example [`cordova-build-increment`](https://www.npmjs.com/package/cordova-build-increment) that "will increment platform specific version numbers" or [in this gist](https://gist.github.com/hstaudacher/d78b154509e2783cfcc2) that [uses the timestamp as build versoin](https://eclipsesource.com/de/blogs/2015/04/07/an-apache-cordova-hook-to-auto-bump-ios-cfbundleversion-and-android-versioncode/).

Another (way is to use [Fastlane](../fastlane) to automate the whole build process, including [changing and incrementing version and build numbers](TODO).


[^1] It is only really defined for [cordova-android](https://cordova.apache.org/docs/en/latest/guide/platforms/android/index.html#setting-the-version-code) where the `versionCode` is calculated as `MAJOR * 10000 + MINOR * 100 + PATCH`. 




TODO: Post to https://forum.ionicframework.com/t/how-do-you-handle-version-and-build-numbers/102274/10 when published