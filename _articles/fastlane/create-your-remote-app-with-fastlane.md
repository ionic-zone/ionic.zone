---
title: 'Ionic + Fastlane: Create your apps on the stores with `produce`'
published: true
date: 2017-08-30 18:00:00 +0000
last_updated: ''
parent: ['Ionic + Fastlane', '../fastlane']
---
# Create your remote app

Before you [installed `fastlane`](install-fastlane.md) and [created a local `Appfile` and `Fastfile`](initialize-fastlane-for-your-cordova-ios-and-android-apps.md). The next step is to create the remote apps that will be used to upload metadata and app binaries into later:

## iOS

We can use `fastlane produce` to create our app in [iTunes Connect](https://itunesconnect.apple.com/WebObjects/iTunesConnect.woa/ra/ng/app) and the [Apple Developer Center](https://developer.apple.com/account/ios/identifier/bundle). It asks for the `app_name` and then just goes ahead and uses the information it gets from the `Appfile` (and the saved credentials) to create the app remotely:

![`fastlane produce`](/assets/fastlane/fastlane-produce.png)

If this is the very first app you create on this account, you will get an error containing "You must provide a company name to use on the App Store." now. To work aroudn this, add `-c "YourCompanyName Ltd"` to the `ionic produce` call. `-c` is short for `--company_name` which [Apple asks for with the first app you create](https://developer.apple.com/library/content/documentation/LanguagesUtilities/Conceptual/iTunesConnect_Guide/Chapters/FirstSteps.html#//apple_ref/doc/uid/TP40011225-CH19-SW4).
{:.message}

Check "My Apps" in [iTunes Connect](https://itunesconnect.apple.com/WebObjects/iTunesConnect.woa/ra/ng/app) and "Identifiers" => "App IDs" in the [Developer Center](https://developer.apple.com/account/ios/identifier/bundle) to confirm.

![New app in Apple Developer Center](/assets/fastlane/fastlane-produce-dev.png) ![New App in iTunes Connect](/assets/fastlane/fastlane-produce-connect.png)

That was easy, wasn't it?

## Android

Unfortunately an Android equivalent of `produce` doesn't exist. The Google Play API doesn't support creation of apps, so we have to get manual for Android.

### Create app in Play Console

Open [Google Play Console](https://play.google.com/apps/publish/) and hit "Create Application" and use the `app_name` from before.

[TODO]: <> (animated gif)

![Google Play Console, name only](/assets/fastlane/google-play-console-name-only.png)

(You don't have to add any other data yet - we will do that later with Fastlane.)

### Upload initial APK

To connect this new app (that for now only has a name) to your `package_name` (which Fastlane will use to identify it) you have to upload an initial APK file to the Play Console manually. It will not actually be published (and you can do that in the "alpha" distribution group), so no harm done. 

Go to "App Releases" -> "Manage Alpha" -> "Create Release" and "Upload APK". You will have to upload a proper `--release` build of your app [that you build the normal Ionic way once, manually](TODO). (It is enough to upload, you don't have to click "Review".)

Going back to the initial list of applications in the [Google Play Console](https://play.google.com/apps/publish/) it should now list the `package_name` under your app's name:

![Google Play Console, with package name](/assets/fastlane/google-play-console-package-name.png)

## Done

Now your app is created in both remote administration interfaces. Your local setup has credentials to connect to both APIs. On to [create a local file structure that represents the metadata.](create-local-file-structure.md)

