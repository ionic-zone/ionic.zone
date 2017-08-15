# Fastlane + Ionic

* initialize-fastlane-for-your-cordova-ios-and-android-apps.md
* [Take screenshots of your Ionic app (iOS and Android) with Fastlane](take-screenshots-of-your-ionic-app-ios-ad-android-with-fastlane)
  * [android-screenshots-with-screengrab.md](android-screenshots-with-screengrab)
  * [ios-screenshots-with-snapshot.md](ios-screenshots-with-snapshot)
  * Writing native Tests for Cordova apps
    * [instrumented-espresso-or-ui-automator-tests-for-android-cordova-apps.md](instrumented-espresso-or-ui-automator-tests-for-android-cordova-app)
    * [uitest-for-cordova-apps.md](uitest-for-cordova-apps)
* bla

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



## Preparation

First install Homebrew
Then run the `brew cask install fastlane`
After adding something to your .bash_profile you have to restart your terminal

We will start with iOS because fastlane does more here

(Make sure you ran `cordova prepare` before you continue that so that the `platforms` folder is there and the iOS project files exist locally.)

## Initiate iOS

### `fastlane init`

Now you can run `fastlane init` in your project. Choose ios so fastlane starts with the iOS part first.

This will create the app ID if it doesn't exist yet (ask for iTunes email and pass and two factor auth if needed)
You might have to input the package id manually
Then it goes and create that in your developer account!

Create fastlane/Appfile and fastlane/Fastfile

Appfile connects to your apple_id, the app_identified and team_id
Fastfile is a template of "lanes" you can create to actually do automated stuff later

(this ran `fastlane produce` partially in the background)

### `fastlane produce`

This creates your app on iTunes Connect
Check "my Apps" in iTunes Connect to confirm.

### `fastlane deliver init`

Downloads all the (of course non-existing) app metadata for the app it just created
By doing this it creates the local file structure for you to fill with actual data!
Creates fastlane/Deliverfile

All set up for uploading stuff to iTunes Connect.

## Initiate Android

no automatic app creation here unfortunately - the Google Play API doesn't that support yet - you have to do that manually
you have to add the app and then upload an initial apk manually (you can do that in the ' alpha'  distirbution group, so no harm done) so it registers your package id - if the list of applications shows teh package id you are good to go

then you follow the setup instructions:
https://docs.fastlane.tools/getting-started/android/setup/#collect-your-google-credentials
with this file fastlane then can access your Google Play account

when you have the .json file you can continue with

### `fastlane supply init`

this will download the initial data as `fastlane deliver init` did for ios
and create additional folders locally

(with the folder structure you can see that iOS was first and Android was added later to fastlane)


## iOS Certificates 

On to the nasty stuff: Certificates and Provisioning Profiles

### `fastlane match init`

This wants a private (!) git repo you have access to where it can save the created stuff. When this is correctly added, it creates a `Matchfile` in your project that contains that git URL.

### `fastlane match nuke development` and `fastlane match nuke distribution`

gets rid of all the certificates and profiles already present in your account from earlier endevours. You want to do that so `match` can start with a clean slate. Check before and after in your Apple Developer console to see how it worked.

### `fastlane match development` and `fastlane match appstore`

then creates brand new certificates and provisioning profiles in your account and commits them to the Git repo you provided earlier. No more changes on your local project for now, but these certificates are also adding to your Mac's keychain so fastlane can use them.

From now on you can just run `fastlane match` to just install the certificates and profiles on the machine you are developing on.


## Build and upload for testing

Now that we have both iOS and Android correctly configured and connected it is a good time to actually do something with our Ionic project: build a development version and upload it for testing.

To build we will leverage the Fastfile for the first time.

For iOS our goal is to build the app and then upload it to Testflight.
For Android we will..

### iOS to Testflight

With normal Xcode projects uploading to Testflight via `fastlane` is so easy, that it is one of the templates generated in the Fastfile:

```
  desc "Submit a new Beta Build to Apple TestFlight"
  desc "This will also make sure the profile is up to date"
  lane :beta do
    # match(type: "appstore") # more information: https://codesigning.guide
    gym # Build your app - more options available
    pilot

    # sh "your_script.sh"
    # You can also use other beta testing services here (run `fastlane actions`)
  end
```

This defines a `beta` lane, that uses `match` to take care of certificates (commented out right by default because not all people want to use that, we do!), then `gym` to build the app and finally `pilot` to upload to Testflight.

Unfortunately the default Xcode project file generated by Cordova is not ready for this. If you built an iOS app manually before, you know that by default the codesigning is not set and has to be edited manually in Xcode. Same for build numbering. This of course won't work for this automated process, so we have to do additional things in our lane to fix this. 

When we try to do this however we will see that the xcodeproj file generated by Cordova is too old for the current tools. To fix this you can either open the project once in Xcode which will upgrade it to a more recent version. Or you can install a fastlane plugin and use this lane:

```
desc "Upgrade the Cordova project to Xcode 8"
	lane :upgrade_xcode do
        ... bla upgrade xcode to 8
end
```

Then run `fastlane ios upgrade_xcode` and confirm the prompt.

Now we can continue to fix the signing and versioning stuff:

```
code signing stuff
```

Now on to the real lane:

first certificates, then get, increase and write a build number, then build the project and finally upload it to testflight.

### Android to ?? (Hockey? Play Store?)

TODO

---

## Add meta data and publish

Now you have to do some manual work and fill these files created by `deliver`and `supply` with real data. 

### iOS

Go through the `fastlane/metadata` folder and add your description etc. (possible categories are listed [here](https://github.com/fastlane/fastlane/blob/master/deliver/Reference.md)).

When you are done you can run `fastlane deliver` to generate a html file as overview of the data (and press `n` to not continue with the upload for now).

### Android

After that you can do the same for Android in `fastlane/metadata/android`. (There is no "generate preview" functionality in `supply` yet unfortunately)

### Upload both

Note that both tools don't remove translations or set the default language of your app. You will have to do that manually for both the Play Store and the App Store.

Note also that `supply` doesn't yet support all fields, e.g. "category" is not downloaded and can not be set for Android apps. You have to do that manually as well.

Run `fastlane supply` and `fastlane deliver` to update your apps. Check both stores if the upload worked.


## Create Screenshots and add to metadata

INCLUDE iOS

INCLUDE Android

### Upload screenshots

Again, run `fastlane supply` and `fastlane deliver` to update your apps with the updated metadata that now includes screenshots. Check both stores if the upload worked.


## Build and upload for release

Again Fastfile:

Build with Ionic
Upload with Fastlane


### iOS

TODO

### Android

TODO







TODO: Create fastlane Ionic plugin



