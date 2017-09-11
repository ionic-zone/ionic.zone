---
title: Possible problems using Fastlane for Ionic Cordova projects
published: true
date: 2017-08-29 16:00:00 +0000
last_updated: ''
parent: ['Ionic + Fastlane', '../fastlane']
---
# Possible problems using Fastlane for Ionic Cordova projects

You now know [what Fastlane offers](introduction-to-fastlane). So how about Ionic support with its hybrid apps based on Cordova? 

## Fastlane + Ionic? (and Cordova?)

Well, it won't work out of the box. Here are some of the reasons:

* Fastlane expects projects to be iOS _or_ Android. Ionic/Cordova projects can be both, which makes the first difficulty. Fortunately, fastlane uses different file and folder structures for iOS and Android so the same setup can actually be used for both platforms at the same time.

* It also normally wants to be installed into the native projects, and as these are generated with Ionic/Cordova projects (`/platforms/ios` and `/platforms/android`), handled as build artifacts and not checked into `git`, the `fastlane` installation and configuration would get lost with each new checkout of the project. Fortunately we can work around this by supplying explicit paths to our native projects in `/platforms` and install Fastlane in our normal project folder that contains our `www` folder and `config.xml`.

* The commands you execute via the `ionic` CLI are also unique for Ionic (`ionic cordova build`, `ionic cordova prepare` etc.) [same if you are using the `cordova` CLI directly for `cordova build`, `cordova prepare` etc], and so are of course not taken into consideration in all documentation of Fastlane (where everything is done with Xcode for iOS or Gradle for Android) and the published tutorials around the web.

{::comment}
(In the process you will also discover several other stumbling blocks.)
{:/comment}

This requires some creative handling of things and also usage of some plugins. But: It is perfectly doable!

Start by [preparing your Ionic/Cordova project for Fastlane](prepare-your-ionic-project-for-fastlane).