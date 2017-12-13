---
title: 'Ionic + Fastlane: Add metadata and upload to stores'
published: true
date: 2017-08-29 16:00:00 +0000
last_updated: ''
parent: ['Ionic + Fastlane', '../fastlane']
---
# Add metadata and upload to stores

You currently have lots of empty files in your `fastlane/metadata` folder from when you [created the local metadata file structure](create-local-file-structure.md) (after you previously [installed](install-fastlane.md) and [initialized `fastlane`](initialize-fastlane-for-your-cordova-ios-and-android-apps.md) and [created your apps in the stores](create-your-remote-app-with-fastlane.md)).

Now you have to do some manual work and fill these files with real data.

## iOS

### Add metadata to files

Go through the `fastlane/metadata` folder and add your own metadata:

* `metadata/copyright.txt` contains ["The name of the person or entity that owns the exclusive rights to the app, preceded by the year the rights were obtained (for example, 2014 Example, Inc.). The copyright symbol is added automatically."](https://developer.apple.com/library/content/documentation/LanguagesUtilities/Conceptual/iTunesConnect_Guide/Chapters/Properties.html#//apple_ref/doc/uid/TP40011225-CH26-SW3)
* The files in `metadata/en-US` are the so called ["Platform Version Information"](https://developer.apple.com/library/content/documentation/LanguagesUtilities/Conceptual/iTunesConnect_Guide/Chapters/Properties.html#//apple_ref/doc/uid/TP40011225-CH26-SW3) that "appear for the app in stores for each territory in which the app is available for sale or download". A general overview about these values is also on this ["App Store Product Page"](https://developer.apple.com/app-store/product-page/) information.
* [App Store Categories](https://developer.apple.com/app-store/categories/) and the keys, to be used in the following files, are [listed on this helpful document from Fastlane](https://github.com/fastlane/fastlane/blob/master/deliver/Reference.md#available-categories)
  * `metadata/primary_category.txt`, `primary_first_sub_category.txt` and `primary_second_sub_category.txt` contain information about the primary category (only first file **has** to be filled)
  * `metadata/secondary_category.txt`, `secondary_first_sub_category.txt` and `secondary_second_sub_category.txt`concern the secondary category (and are all optional)
* `metadata/review_information/` contains ["information [...] to support the app review process"](https://developer.apple.com/library/content/documentation/LanguagesUtilities/Conceptual/iTunesConnect_Guide/Chapters/Properties.html#//apple_ref/doc/uid/TP40011225-CH26-SW8). You should definitely fill it if your apps requires a login, or your app might be declined by Apple app review.
* `metadata/trade_representative_contact_information/` is technically only for ["Trade Representative Contact Information" for publishing your app in Korea](https://developer.apple.com/library/content/documentation/LanguagesUtilities/Conceptual/iTunesConnect_Guide/Chapters/Properties.html#//apple_ref/doc/uid/TP40011225-CH26-SW9), but it doesn't hurt to fill it in even when you don't plan to publish there. It is already mostly filled out anyway.

{::comment}
TODO what is NOT available on the first upload? (what's changed)
TODO what can be changed all the time? what will only change with the next release?
{:/comment}

If you want your app to contain localized app information for additional languages, just create a copy of the `en-US` folder and rename it to the [respective language code (e.g. `de-DE` for German)](https://github.com/fastlane/fastlane/blob/master/deliver/Reference.md#available-languages).

When you are done you can run `fastlane deliver` to generate a html file as overview of the data:

![`fastlane deliver` html preview](/assets/fastlane/fastlane-deliver-preview.png)

### Upload to iTunes Connect

If you press <kbd>n</kbd> it won't continue with the upload and you can fix things further.  
If you are ready, press <kbd>y</kbd> to upload the data:

![`fastlane deliver` upload success](/assets/fastlane/fastlane-deliver-upload-success.png)

Check iTunes Connect for success:

![`fastlane deliver` metadata in iTunes Connect](/assets/fastlane/fastlane-deliver-metadata-in-itunes-connect.png)

### Optional: Advanced language structure

If you want to to use the same strings in several languages and only differentiate some special languages you can also [use the `default` language](https://github.com/fastlane/fastlane/tree/master/deliver#default-values) to avoid duplicating the string to all languages: [Create the common string in a `default` folder, and the special version for example only in the `de-DE` folder that should be different from all the other languages that don't include the string at all.](https://github.com/fastlane/fastlane/tree/master/deliver#default-values)

## Android

### Add metadata to files

Of course you also have to do the same for the Android metadata in `fastlane/metadata/android`:

* `metadata/android/en-US/full_description.txt` contains your full app description.
* `metadata/android/en-US/short_description.txt` should also describe your app but [is limited to 80 characters](https://support.google.com/googleplay/android-developer/answer/113469#store_listing) and is "the first text users see when looking at your app's detail page on the Play Store app."
* `metadata/android/en-US/title.txt` should already be prefilled with your initial app name
* `metadata/android/en-US/video.txt` can be a YouTube URL of a [video that previews your app and will be shown in the Play Store](https://support.google.com/googleplay/android-developer/answer/1078870)

Additionally to the files that get created by default you also should create these [required graphic files](https://support.google.com/googleplay/android-developer/answer/1078870):

* `metadata/android/en-US/featureGraphic.png` is a promotional banner that can be shown in the Play Store to advertise your app (Size: 1024x500px)
* `metadata/android/en-US/icon.png` is the app icon shown in the Play Store (Size: 512x512px)

All files are localized, and identical to iOS you can create additional languages by duplicating the `en-US` folder and giving it the intended countries' language code as new name.

{::comment}
TODO

#### Changelogs

Android's changelogs for apps [live in another folder `metadata/android/en-US/changelogs` and have the "version code" as their filename with a `.txt` file extension](https://github.com/fastlane/fastlane/tree/master/supply#changelogs-whats-new):

```
metadata
    └── android
        └── en-US
            └── changelogs
                ├── 100000.txt

```
TODO Already needed here or only confusing? Where would we add this then?

#### Screenshots

```
    ├── images
    │   ├── phoneScreenshots
    │   ├── sevenInchScreenshots
    │   ├── tenInchScreenshots
    │   ├── tvScreenshots
    │   └── wearScreenshots

```
TODO App Screenshots hier schon erwähnen?
{:/comment}

There is no "generate preview" functionality in `supply` [yet](https://github.com/fastlane/fastlane/issues/9960) unfortunately, so check your files twice to make sure you didn't miss anything.

### Upload to Google Play Console

Execute `fastlane supply` to upload the data to Google Play Console:

![`fastlane supply` upload success](/assets/fastlane/fastlane-supply-upload-success.png)

Check the Play Console for confirmation it worked:

![`fastlane supply` metadata in Play Console](/assets/fastlane/fastlane-supply-metadata-in-play-console.png)

Note that `supply` doesn't yet support all fields that the Google Play console requires, e.g. "category" is not downloaded and can not be set for Android apps. You have to do that manually before publishing your app later.
{:.message}

Note that both tools don't update the default language of your app or remove translations that are not part of your file structure. You will have to do that manually for both the Play Store and the App Store.
{:.message}

## Next

With your [apps created in the stores](create-your-remote-app-with-fastlane.md) and them being [filled with metadata](add-metadata-and-upload.md), you "only" have to [build your app](build-your-project.md) for testing and later release.
