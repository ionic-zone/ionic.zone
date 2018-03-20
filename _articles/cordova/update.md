---
layout: article
title: 'How to update Cordova CLI, Platforms and Plugins'
date: 2018-03-20 00:00:00 +0000
last_updated: ''
parent: ['Cordova', '../cordova']
---
# How to update Cordova?

This article explains how to update Cordova CLI, Cordova Platforms and Cordova Platforms in your project.

## Why should I update Cordova?

If your project is not on the newest version of Cordova CLI, platforms or plugins there is a pretty good chance your setup will not work with current mobile platform tools like Xcode for iOS or Android Studio, Gradle or Android SDK for Android.

Any errors or problem you are getting might be from your app - or just because you are using an outdated Cordova setup. Updating everything to the most recent stable versions excludes this as a source for errors and makes debugging much easier.

If you don't have any problems right now, you can still invest the time now to update Cordova to make sure it doesn't break when you are under pressure to get an update rolled out.

---

What we refer to as "Cordova" are actually 3 different parts that can be updated independently:

- [Update Cordova CLI, `cordova`](#update-cordova-cli-cordova)
- [Update Cordova Platforms](#update-cordova-platforms)
- [Update Cordova Plugins](#update-cordova-plugins)

---

## Update Cordova CLI, `cordova`

To find the locally installed version of Cordova CLI run `cordova -v` (If you are using Ionic, this version is also included in the `ionic info` output). Then compare the returned version number to the output of `npm info cordova version` (You can also check manually for the newest available version on [npm](https://www.npmjs.com/package/cordova) or [GitHub](https://github.com/apache/cordova-cli/releases)).

If these two versions don't match, there is a newer version of the CLI available and should be installed:

```
npm update -g cordova
```

Run `cordova -v` again after the update to make sure the update worked and it now returns the current version.

## Update Cordova Platforms

To find out which platform (`cordova-ios`, `cordova-android`, `cordova-windows`, ...) versions are currently installed, run `cordova platform list` (If you are using Ionic, this information is also included in the `ionic info` output). This will return a list of "Installed platforms" with their version number:

```
λ cordova platform list
Installed platforms:
  android 5.0.0
Available platforms:
  browser ~5.0.1
  ...
```

One way to find out which platform version is currently available, is to run e.g. `npm info cordova-android version` (or check manually on [npm](https://www.npmjs.com/package/cordova-android)):

```
λ npm info cordova-android version
7.1.0
```

Another way to find outdated platforms is to run `npm outdated`. As platforms are installed as npm packages, this will also give you the installed and available version:

```
λ npm outdated
Package                   Current  Wanted  Latest  Location
cordova-android             5.0.0   5.2.2   7.1.0  helloworld
```

If the installed and available versions don't match, there is a newer version of the Cordova platform available and should be updated. The safest way to achieve this is to first remove, and then re-add the newest platform version explicitly:

```
cordova platform rm android
cordova platform add android@7.1.0
```

Rerun `cordova platform list` to check that the new version was successfully installed.

## Update Cordova Plugins

Run `cordova plugin list` to get a list of the currently installed plugins in your project:

```
λ cordova plugin list
cordova-plugin-device 1.1.4 "Device"
cordova-plugin-ionic-webview 1.1.16 "cordova-plugin-ionic-webview"
cordova-plugin-splashscreen 4.0.3 "Splashscreen"
cordova-plugin-whitelist 1.3.1 "Whitelist"
ionic-plugin-keyboard 2.2.1 "Keyboard"
```

Again you can use `npm outdated` to check for updates automatically:

```
λ npm outdated
Package                            Current  Wanted  Latest  Location
cordova-plugin-device                1.1.4   1.1.7   2.0.1  ionicBlank
cordova-plugin-splashscreen          4.0.3   4.1.0   5.0.2  ionicBlank
cordova-plugin-whitelist             1.3.1   1.3.3   1.3.3  ionicBlank
```

or do it manually for each plugin

```
λ npm info cordova-plugin-device version
2.0.1
```

(or check manually on [npm](https://www.npmjs.com/package/cordova-plugin-device)).

Then first remove and re-install the plugin:

```
cordova plugin remove cordova-plugin-device
cordova plugin add cordova-plugin-device
```

Run `npm outdated` and `cordova plugin list` again to check if this worked.

If this manual process is too cumbersome, you might want to try the [`cordova-check-plugins`](https://www.npmjs.com/package/cordova-check-plugins) command line tool that automates and helps with this process.
