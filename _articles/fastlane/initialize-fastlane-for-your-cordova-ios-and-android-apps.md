---
title: Initialize Fastlane and prepare your Cordova iOS and Android apps
date: 2017-08-15 21:00:00 +0000
published: true
last_updated: ''
---
# Prepare and nitialize Fastlane for your (Cordova) iOS and Android apps

The first step is to get `fastlane` working locally. Afterwards you will have an app at both stores and a file structure of the data of their (empty) meta data.

## Preparation

First install Homebrew
Then run the `brew cask install fastlane`
After adding something to your .bash_profile you have to restart your terminal

We will start with iOS because fastlane does more here:

## Initiate iOS

(Make sure you ran `cordova prepare` before you continue that so that the `platforms` folder is there and the iOS project files exist locally.)

### `fastlane init`

Now you can run `fastlane init` in your project. Choose iOS so fastlane starts with the iOS part first.

This will create the app ID if it doesn't exist yet (asks for iTunes email and pass and two factor auth if needed)
You might have to input the package id manually
Then it goes and create that in your developer account!

> Note: this ran `fastlane produce` partially in the background)
This creates your app on iTunes Connect
Check "my Apps" in iTunes Connect to confirm.

When it is done it creates `fastlane/Appfile` and `fastlane/Fastfile`

`Appfile` connects to your `apple_id`, the `app_id` and `team_id`:
```
TODO
```
`Fastfile` is collection "lanes" you can create to actually do automated stuff later on. For now this shows somes examples:
```
TODO
```

### `fastlane deliver init`

Run `fastlane deliver init`to downloads all the (of course non-existing) app metadata for the app it just created
By doing this it creates the local file structure for you to fill with actual data!

```
TODO tree
```
Also creates `fastlane/Deliverfile`:
```
TODO
```

All set up for uploading stuff to iTunes Connect later: It know about your app, can access your accounts, and has a local representation of the data needed in the local file system.

## Initiate Android

no automatic app creation here unfortunately - the Google Play API doesn't that support yet - you have to do that manually
you have to add the app and then upload an initial apk manually (you can do that in the ' alpha'  distribution group, so no harm done) so it registers your package id - if the list of applications shows the package id you are good to go

TODO screenshot

then you follow the setup instructions:
https://docs.fastlane.tools/getting-started/android/setup/#collect-your-google-credentials which are unfortunately 
with this file fastlane then can access your Google Play account

when you have the .json file you can continue with

### `fastlane supply init`

this will download the initial data as `deliver init` did for iOS
and create additional folders locally

```
TODO tree
```

And easy as that, again it added some folders and file that represent the data available in the Google Play console and have to be filled.

(with the folder structure you can see that iOS was first and Android was added later to fastlane)

## iOS Certificates

On to the (normally) nasty stuff: Certificates and Provisioning Profiles

### `fastlane match init`

This wants a private (!) git repo you have access to where it can save the created stuff. When this is correctly added, it creates a `Matchfile` in your project that contains that git URL.

```
TODO
```

### `fastlane match nuke development` and `fastlane match nuke distribution`

gets rid of all the certificates and profiles already present in your account from earlier endevours. You want to do that so `match` can start with a clean slate. Check before and after in your Apple Developer console to see how it worked.

### `fastlane match development` and `fastlane match appstore`

then creates brand new certificates and provisioning profiles in your account and commits them to the Git repo you provided earlier. No more changes on your local project for now, but these certificates are also adding to your Mac's keychain so fastlane can use them.

From now on you can just run `fastlane match` to just install the certificates and profiles on the machine you are developing on.

## Done

And that is all the work needed to prepare your local `Fastlane` structure to represent your app on both iTunes Connect and Google Play console, and give it access to your iOS certificates that will be needed later when you build your app.