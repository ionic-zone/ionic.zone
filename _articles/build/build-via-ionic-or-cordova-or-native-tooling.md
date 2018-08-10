---
title: Should I build my project via Ionic, Cordova or native tooling (Android Studio,
  Xcode)?
date: 2017-10-09 18:00:00 Z
position: 8
last_updated: ''
---

# Should I build my project via Ionic CLI, Cordova CLI or native tooling like Android Studio or Xcode?

When you are done developing locally and testing and debugging your app via `ionic serve` it is time to build your app as a native app that can be deployed to simulators, emulators or devices.

You can do this in a number of different ways that all have slightly different results with advantages and disadvantages. You should know these differences:

1. Build via native tooling

   If you open the native project (`platforms/ios` or `platforms/android`) directly in Android Studio or Xcode you can simply build the native platform project. This skips _both_ Ionic CLI and Cordova CLI builds and just builds the current state of the native platform project. Skipping these means that there is no update of what is in `www` (because no Ionic build) and also copy of `www` over to the native platform directory and no evaluation of `config.xml` that defines your app name, version, configuration etc. (For the first build of an app this won't work at all as no `www` has ever been copied over before and you have to use 2) or 3)).

1. Build via Cordova

   Alternatively you can `cordova build ios/android --release` which skips the Ionic build, but then builds the Cordova project and finally the native platform project. This build takes whatever is already built inside `www` of your project folder - so you have to make sure it is the correct version.

1. Build via Ionic

   If you run `ionic cordova build ios/android [--prod](TODO) --release` this builds the Ionic project first (`src` gets compiled into `www`), then the Cordova project (`www` and finally the native platform project that packages the result into an app file.    This is the only option that allows you to choose the [`--prod` parameter to indicate an Ionic production build](TODO).

These build methods get "slower" from 1) to 2) to 3) as they have to do more things. But they also get more "current": 1) only refreshes the native part with each build, 2) additionally the Cordova part but only 1) also creates a new build of the Ionic project.

> If you have a Cordova project not using Ionic, 3) gets replaced with whatever process is used to build your HTML/JS app. If it doesn't have a build step, you can just ignore 3) and look at the differences between 2) and 1).

Safest option is to always build with 3) Ionic CLI. That way you can be sure you get exactly the result you want to get.  
If you only have to test something in different devices or simulators, feel free to use 1) with Xcode or Android Studio.
