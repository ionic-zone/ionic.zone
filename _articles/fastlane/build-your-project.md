---
title: 'Ionic + Fastlane: Build your Ionic app with Fastlane'
published: true
date: 2017-08-29 16:00:00 +0000
last_updated: ''
parent: ['Ionic + Fastlane', '../fastlane']
---
# Build your Ionic or Cordova app with Fastlane

Now that you have Fastlane [correctly configured for both iOS and Android](initialize-fastlane-for-your-cordova-ios-and-android-apps.md), [created remote apps](create-your-remote-app-with-fastlane.md) and [added some first metadata](add-metadata-and-upload.md) it is a good time to actually do something with your Ionic or Cordova project: build it. For this you will leverage and edit the `Fastfile` for the first time and create new lanes in it. Exciting!

## Choose your build method

As with manual building, you have [3 options available how to build: 1) Via `ionic`, 2) via `cordova` or 3) native tooling (Android Studio, Xcode?)](../build/build-via-ionic-or-cordova-or-native-tooling.md). Use the linked article to choose which one best matches your requirements (TLDR: `ionic` for Ionic project, `cordova` for pure Cordova projects, native tooling if there is a specific reason) and then continue with the corresponding article:

1. [Build your Ionic app with the Fastlane Ionic plugin](build-your-project-with-ionic-plugin.md)
1. [Build your Ionic or Cordova app with the Fastlane Cordova plugin](build-your-project-with-cordova-plugin.md)
1. [Build your Ionic or Cordova app with native tooling in Fastlane](build-your-project-with-native-tooling.md)

<div id="future-content">
## Next up
When you have a _Debug version_ of your app you can [upload your app for testing (with HockeyApp or Testflight and Play Store Alpha)](upload-for-testing.md). After testing and you succeeded in building a _Release version_ of your app, [publish it on the stores so your users can download it](publish-your-app.md).
</div>
