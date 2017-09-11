---
title: Prepare your Ionic Cordova project for usage with Fastlane
published: true
date: 2017-08-29 16:00:00 +0000
last_updated: ''
parent: ['Ionic + Fastlane', '../fastlane']
---
# Prepare your Ionic Cordova project for usage with Fastlane

Before we jump into installing and initializing Fastlane we have to make sure our Cordova project is in proper shape.

Note: You can better follow the changes done to the native projects if you [add the `platforms` folder to Git before continuing](put-platforms-under-version-control).
{:.message}

The following paragraphs will make sure you have 1) added both `ios` and `android` platforms to the project, 2) use your own unique project name and 3) package id, 4) app versoin and 5) assets.


## 1) Add the `ios` and `android` platforms

Make sure you have both the `ios` and `android` platform added to your project. You can check by running `ionic cordova platform list`. You should get output similar to this:

```
> ionic cordova platform list
√ cordova platform ls - done!
Installed platforms:
  android 6.2.3
  ios 4.4.0
Available platforms:
  [...]
```

If one is missing, just run `ionic cordova platform add ios` or `ionic cordova platform add android` to add it.
If one is outdated, run `ionic cordova platform update ios` or `ionic cordova platform update android` to update it.

## 2) Use your own project name

New Ionic projects by default are generated with the app name `MyApp` - which is what will be displayed on your user's smartphone screen beneath your app icon. You can set that to e.g. `Fastlane Ionic` by changing your `config.xml`: 

```xml
<name>Fastlane Ionic</name>
```

After saving the file, run `ionic cordova prepare` to update the generated Cordova projects.

 (This will probably prompt you to remove and re-add the `ios` platform as changing the project name requires bigger changes here (renaming of files and folders instead of just editing some files as for `android`) which you do by executing the commands shown to you - followed by another `ionic cordova prepare`).

## 3) Set your own Package ID

New Ionic projects also by default are generated with `io.ionic.starter` as package ID. This "backwards domain" string is not visible to your users, but both Apple App Store and Google Play Store use it to identify your app and it has to be globally unique - so change it to something related to your app. Again you can edit `config.xml` to change this:

```xml
<widget id="zone.ionic.example" …>
```

Again, run `ionic cordova prepare` to update the Cordova projects.

## 4) Set your initial app version

Each Ionic project starts as version `0.0.1` by default. If this will be the first version you want to release to your testers or users, you don't have to change anything. If you  want to start with `1.0.0` or `17.35.99` (for whatever reason), you again have to edit `config.xml`:

```xml
<widget … version="1.0.0" …>
```

As before `ionic cordova prepare` makes sure these changes are propagated to the native projects.

## 5) Use your own assets as app icon

New Ionic projects come with a default app icon. Before uploading your app to the stores you will probably want to change that. You can do that by editing the `resources/icon.png` and then running `ionic cordova resources`. 

```
> ionic cordova resources
√ Collecting resource configuration and source images - done!
√ Filtering out image resources that do not need regeneration - done!
√ Uploading source images to prepare for transformations - done!
√ Generating platform resources: 48 / 48 complete - done!
√ Modifying config.xml to add new image resources - done!
```

This will generate all the required assets. `ionic cordova prepare` will copy them over to the native Cordova projects.

## Done

When you Ionic Cordova project is fully prepared, you can [install `fastlane`](install-fastlane).