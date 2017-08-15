# Initialize and prepare Fastlane for your Cordova iOS and Android apps


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