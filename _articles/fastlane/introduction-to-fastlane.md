---
title: Introduction to Fastlane
published: true
date: 2017-08-29 16:00:00 +0000
last_updated: ''
parent: ['Ionic + Fastlane', '../fastlane']
---
# Introduction to Fastlane

[Fastlane](https://fastlane.tools/) describes itself as 

> [...] the tool to release your iOS and Android app 🚀 It handles all tedious tasks, like generating screenshots, dealing with code signing, and releasing your application. 

or 

> The easiest way to automate building and releasing your iOS and Android apps 

Many people probably come into contact with Fastlane because it also promises to get rid of the certification and signing chaos often created when developing for iOS. I know that alone was enough to sell me on the tool.

## Fastlane Tools

But Fastlane also offers much more: creating screenshots, managing and uploading metadata to the stores, creating apps entries, even building and (beta) distribution. With all the tools in its toolchain, the whole "deploy + release" process can be covered:

- `produce` = Create apps on Apple Developer Center and iTunes Connect
- `precheck` = Check if your app and its data will pass the app review
- `deliver` = Upload metadata for iOS apps
- `supply` = Upload metadata for Android apps
- `match` = Manage iOS certificates and provisioning profiles
- `snapshot` = Screenshots for iOS apps
- `screengrab` = Screengrabs for Android apps
- `gym` = Build your iOS apps

You can also manually manage your certificates with `sigh`, `cert` and `pem`, handle your testing with `scan`, `pilot` and `boarding`, use `frameit` to put your iOS screenshots into a template or manually interface with Apple Dev center and iTunes Connect with `spaceship`.

{::comment}
## Fastlane Bascis

### Background
Felix Krause
Fabric
first Twitter
now Google

### Architecture
TODO lane?
Ruby?
*file?

### Functionality
...

### Documentation
...
{:/comment}

Now you know what Fastlane offers. But [can it be used with Ionic Cordova projects?](problems-with-using-fastlane-for-ionic)