---
title: Initialize Fastlane for your Cordova iOS and Android apps  and create remote apps
date: 2017-08-15 21:00:00 +0000
published: true
last_updated: ''
---
# Install and initialize Fastlane for your (Cordova) iOS and Android apps and create remote apps

The first step is to install `fastlane`. Afterwards you will also have an app at both stores. 

## Install

First install Homebrew
Then run the `brew cask install fastlane`
After adding something to your .bash_profile so `fastlane` is available globally you have to restart your terminal

## Initialize with `fastlane init`

(Make sure you ran `cordova prepare` before you continue that so that the `platforms` folder is there and the iOS project files exist locally.)

We will start with iOS because fastlane does more here:

### iOS

Now you can run `fastlane init` in your project. 

TODO Screenshot

Choose `iOS` so fastlane starts with the iOS part first.

This will create the app ID (TODO Where does this come from?) if it doesn't exist in your iTunes Connect yet (asks for iTunes email and pass and two factor auth if needed)
You might have to input the package id manually
Then it goes and create that in your developer account!

> Note: this ran `fastlane produce` partially in the background

This creates your app on iTunes Connect
Check "my Apps" in iTunes Connect to confirm.

When it is done it also creates `fastlane/Appfile` and `fastlane/Fastfile`

`Appfile` connects to your `apple_id`, the `app_id` and `team_id`:
```
TODO
```

`Fastfile` is collection "lanes" you can create to actually do automated stuff later on. For now this shows somes examples:
```
TODO
```

### Android

no automatic app creation here unfortunately - the Google Play API doesn't that support yet - you have to do that manually

you have to add the app and then upload an initial apk manually (you can do that in the 'alpha'  distribution group, so no harm done) so it registers your package id - if the list of applications shows the package id you are good to go

TODO screenshot

then you follow the setup instructions:
https://docs.fastlane.tools/getting-started/android/setup/#collect-your-google-credentials which are unfortunately a bit hard to follow
with the file you get fastlane then can access your Google Play account

when you have the .json file you can continue with




## Done

TODO fix text

And that is all the work needed to prepare your local `Fastlane` structure to represent your app on both iTunes Connect and Google Play console, and give it access to your iOS certificates that will be needed later when you build your app.