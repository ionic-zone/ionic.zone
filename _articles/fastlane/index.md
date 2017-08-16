---
title: Ionic and Fastlane (iOS and Android)
date: 2017-08-15 16:00:00 +0000
published: true
last_updated: ''
---
# Ionic and Fastlane (iOS and Android)

Fastlane promises to get rid of the cert foo with iOS. Sold. 
And it also offers more: screenshots, metadata, beta distribution.
So much wow

- produce = create apps on itunes and dev account
- deliver = metadata ios
- supply = metadata android
- match = iOS certificates and provisioning profiles
- snapshot = Screenshots with iOS
- screengrab = Screengrabs with Android

The goal: Don't do anything manually for build your app, releasing it to testers, no manual screenshot creation, no fighting with Xcode and Apple about certificates, updating everything in the stores (app and metadata like text or screenshots) - this can all be automated.

Android and iOS.
Mac only unfortunately
Ionic support not perfect, but absolutely fine.

Problems: 
Fastlane more or less expects projects to be iOS _or_ Android
Wants to be installed into the native project - in Ionic/Cordova these are generated and not checked into git
Different build process than native apps via `ionic`
But: All solvable!

## Content

* [initialize-fastlane-for-your-cordova-ios-and-android-apps.md](initialize-fastlane-for-your-cordova-ios-and-android-apps)
* [Build and upload for testing](build-and-upload-for-testing)
* [add-metadata-and-publish.md](add-metadata-and-publish)
* [Take screenshots of your Ionic app (iOS and Android) with Fastlane](take-screenshots-of-your-ionic-app-ios-ad-android-with-fastlane)
  * [ios-screenshots-with-snapshot.md](ios-screenshots-with-snapshot)
    * [uitest-for-cordova-apps.md](uitest-for-cordova-apps)
  * [android-screenshots-with-screengrab.md](android-screenshots-with-screengrab)
    * [instrumented-espresso-or-ui-automator-tests-for-android-cordova-apps.md](instrumented-espresso-or-ui-automator-tests-for-android-cordova-app)
* [Build and upload for release](build-and-upload-for-release)








---
TODO: Create fastlane Ionic plugin
TODO: Create fastlane cordova_screenshots plugin



