---
title: Ionic and Fastlane
date: 2017-08-15 16:00:00 +0000
published: true
last_updated: ''
---
# Ionic and Fastlane

![Ionic + Fastlane](fastlane/images/ionic_fastlane.png)

This series of articles investigates and explains how to use Fastlane with your Ionic or Cordova projects for automating common tasks that normally are done manually and take tons of time.

## Introduction, Preparation

What is this all about?

- [Introduction to Fastlane](fastlane/introduction-to-fastlane.md)
- [Problems using Fastlane for Ionic Cordova projects](fastlane/problems-with-using-fastlane-for-ionic.md)
- [Prepare your Ionic/Cordova project for Fastlane](fastlane/prepare-your-ionic-project-for-fastlane.md)
  - [Optional: Put `/platforms` under version control](fastlane/put-platforms-under-version-control.md)

## Installation, Initialization

Before we get to the _really_ fun part...

- [Install `fastlane`](fastlane/install-fastlane.md)
- [Initialize Fastlane with `fastlane init`](fastlane/initialize-fastlane-for-your-cordova-ios-and-android-apps.md)

## Upload App Metadata to App Store and Google Play

Have all app data for both stores in (versioned) local files and upload with one command.

- [Create your apps on the stores with `produce`](fastlane/create-your-remote-app-with-fastlane.md)
- [Create local store metadata file structure with `deliver` and `supply`](fastlane/create-local-file-structure.md)
- [Add metadata to local structure and upload to stores](fastlane/add-metadata-and-upload.md)

<div id="future-content">

## Upload your app

### Upload your _Debug_ app for testing

- [Build and upload your app for testing (with Testflight, Play Store Alpha and HockeyApp)](fastlane/build-and-upload-for-testing)
   * [Setup iOS certificate handling with `match`](fastlane/setup-ios-certificate-handling)
   * [Modify your Cordova iOS project to work with Fastlane](fastlane/modify-cordova-ios-project-for-fastlane)
   * ~~[Manage Testflight testers with Fastlane's `pilot` and `boarding`](fastlane/manage-testflight-testers-with-fastlane)~~
   * ~~[Handle version numbers automatically with Fastlane](fastlane/handle-version-numbers-automatically-with-fastlane)~~
   * ~~[Automatically create changelog from Git commit messages](fastlane/automatically-create-changelogs-from-git-commit-messages)~~
</div>

- [Upload your app for testing (with HockeyApp or Testflight and Play Store Alpha)](fastlane/upload-for-testing.md)

### Publish your _Release_ app

- [Take screenshots of your Ionic app (iOS and Android) with Fastlane](fastlane/take-screenshots-of-your-ionic-app-ios-ad-android-with-fastlane)
   * [iOS Screenshots with `snapshot`](fastlane/ios-screenshots-with-snapshot)
     * [UI Tests for your Cordova iOS app ](fastlane/uitest-for-cordova-apps)
   * [Android Screenshots with `screengrab`](fastlane/android-screenshots-with-screengrab)
     * [Instrumented (Espresso or UI Automator) tests for your Cordova Android app](fastlane/instrumented-espresso-or-ui-automator-tests-for-android-cordova-apps)

<div id="future-content">

   * [Upload your generated screenshots to the stores](fastlane/upload-generated-screenshots)
   * ~~[Improve your Fastlane app screenshots by cleaning the status bar](fastlane/improve-generated-screenshots-by-cleaning-status-bar)~~
   * ~~[Improve your Fastlane app screenshots by framing them with `frameit`](fastlane/improve-screenshots-by-framing-them)~~

- [Publish your app for production release (to App Store and Google Play Store)](fastlane/publish-your-app.md)

## Additional functionality for building and testing:

- ~~[Automatically increment build number of your Cordova project](fastlane/increment-build-number.md)~~
- ~~[Handle version numbers automatically with Fastlane](fastlane/handle-version-numbers-automatically-with-fastlane.md)~~
- ~~[Manage Testflight testers with Fastlane's `pilot` and `boarding`](fastlane/manage-testflight-testers-with-fastlane.md)~~
- ~~[Automatically create changelog from Git commit messages](fastlane/automatically-create-changelogs-from-git-commit-messages.md)~~

## Take Screenshots of your App and upload to App Store and Google Play

Automated screenshot creation in all required formats and languages.

- [Take screenshots of your Ionic app (iOS and Android) with Fastlane](fastlane/take-screenshots-of-your-ionic-app-ios-ad-android-with-fastlane.md)
  - [iOS Screenshots with `snapshot`](fastlane/ios-screenshots-with-snapshot.md)
    - [UI Tests for your Cordova iOS app](fastlane/uitest-for-cordova-apps.md)
  - [Android Screenshots with `screengrab`](fastlane/android-screenshots-with-screengrab.md)
    - [Instrumented (Espresso or UI Automator) tests for your Cordova Android app](fastlane/instrumented-espresso-or-ui-automator-tests-for-android-cordova-apps.md)
  - [Upload your generated screenshots to the stores](fastlane/upload-generated-screenshots.md)
  - ~~[Improve your Fastlane app screenshots by cleaning the status bar](fastlane/improve-generated-screenshots-by-cleaning-status-bar.md)~~
  - ~~[Improve your Fastlane app screenshots by framing them with `frameit`](fastlane/improve-screenshots-by-framing-them.md)~~

## ~~Advanced Topics~~

- ~~[Advanced handling of version numbers of your Cordova project with Fastlane](fastlane/advanced-handling-of-version-numbers-with-fastlane.md)~~
- ~~[Using Fastlane as a safe way to mess with your native Cordova projects](fastlane/mess-with-your-native-cordova-projects-with-fastlane.md)~~
- [Fastlane and Windows](fastlane/fastlane-and-windows.md)

### ~~iOS only~~

- ~~[Run all your iOS tests with `scan`](fastlane/run-all-your-tests-with-scan.md)~~
- ~~[Handle iOS push certificates with `pem`](fastlane/handle-ios-push-certificates-with-fastlane.md)~~
- ~~[Make sure your iOS app will not be rejected with `precheck`](fastlane/check-your-ios-metadata-with-precheck.md)~~

</div>

## TL;DR

If you don't have time for all the explanation and nice prose I wrote, here is a [TL;DR version](fastlane/TLDR.md) that only lists the commands, necessary inputs and steps for everything.

{::comment}
<div id="future-content">
## Guides

- [How to manage your Ionic app store meta data with Fastlane](TODO)
- ~~[How to build and upload your Ionic app for testing](TODO)~~
- ~~[How to create Ionic app screenshots with Fastlane](TODO)~~
- ~~[How to build and upload your Ionic app for release](TODO)~~
- ...

</div>
{:/comment}

## Example project on GitHub

You can also cheat a bit and take a look at this example project on GitHub. It includes all the things generated by following the above steps:

- [https://github.com/ionic-zone/ionic-fastlane](https://github.com/ionic-zone/ionic-fastlane)

The README also explains what to do to get it working locally, and links to the (automatically generated) `fastlane` README that lists all the functionality available.
