---
title: Ionic and Fastlane
date: 2017-08-15 16:00:00 Z
position: 0
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

## Build your app

Automatically build your app (Includes fully automated handling of iOS certificates).

- [Build your Ionic app with Fastlane](fastlane/build-your-project.md)
  1. [Build your Ionic app with the `ionic` Fastlane plugin](fastlane/build-your-project-with-ionic-plugin.md)
  1. [Build your Ionic or Cordova app with the `cordova` Fastlane plugin](fastlane/build-your-project-with-cordova-plugin.md)
  1. [Build your Ionic or Cordova app with native tooling in Fastlane](fastlane/build-your-project-with-native-tooling.md)
- [Setup iOS certificate handling with `match`](fastlane/setup-ios-certificate-handling.md)

{::nomarkdown}
<div id="update-box">

  <strong>Get notified about new <em>Ionic + Fastlane</em> articles</strong><br>
  The articles below are not ready yet and are actively worked on right now. Enter your email address to automatically be notified when they are published:<br>
  <br>

<!-- Begin MailChimp Signup Form -->
<link href="//cdn-images.mailchimp.com/embedcode/horizontal-slim-10_7.css" rel="stylesheet" type="text/css">
<style type="text/css">
  #mc_embed_signup{ clear:left; font:14px Helvetica,Arial,sans-serif; width:100%;}
</style>
<div id="mc_embed_signup">
  <form action="//zone.us16.list-manage.com/subscribe/post?u=343ee35d12246a68f6310af0c&amp;id=b0d2853531" method="post" id="mc-embedded-subscribe-form" name="mc-embedded-subscribe-form" class="validate" target="_blank" novalidate>
    <div id="mc_embed_signup_scroll">
      <input type="email" value="" name="EMAIL" class="email" id="mce-EMAIL" placeholder="email address" required>
        <!-- real people should not fill this in and expect good things - do not remove this or risk form bot signups-->
      <div style="position: absolute; left: -5000px;" aria-hidden="true"><input type="text" name="b_343ee35d12246a68f6310af0c_b0d2853531" tabindex="-1" value=""></div>
      <div class="clear"><input type="submit" value="Subscribe" name="subscribe" id="mc-embedded-subscribe" class="button"></div>
    </div>
  </form>
</div>
<!--End mc_embed_signup-->

</div>
{:/nomarkdown}

<div id="future-content">

## Upload your app

### Upload your _Debug_ app for testing

Upload your app for testing via different beta distribution services.

- [Upload your app for testing (with HockeyApp or Testflight and Play Store Alpha)](fastlane/upload-for-testing.md)

### Publish your _Release_ app

Upload your app to the app stores for release.

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
