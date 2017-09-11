---
title: 'Ionic + Fastlane: Create local metadata file structure'
published: true
date: 2017-08-29 16:00:00 +0000
last_updated: ''
parent: ['Ionic + Fastlane', '../fastlane']
---
# Create local metadata file structure

After you [installed](install-fastlane) and [initialized `fastlane`](initialize-fastlane-for-your-cordova-ios-and-android-apps) you [created your apps in the stores](create-your-remote-app-with-fastlane) which we can now use to create a local file structure representing the necessary metadata.

## iOS: `fastlane deliver init`

`fastlane deliver` is the tool that "uploads screenshots, metadata and binaries to iTunes Connect.". But it can also be used to download all the exisiting metadata of an app or create an empty file structure to be filled with new metadata.

Run `fastlane deliver init` to download all the (of course non-existing) app metadata for your iOS app. By doing this Fastlane creates the local file structure for you to fill with actual data:

```
fastlane
├── Appfile
├── Deliverfile
├── Fastfile
├── metadata
│   ├── copyright.txt
│   ├── en-US
│   │   ├── description.txt
│   │   ├── keywords.txt
│   │   ├── marketing_url.txt
│   │   ├── name.txt
│   │   ├── privacy_url.txt
│   │   ├── promotional_text.txt
│   │   ├── release_notes.txt
│   │   ├── subtitle.txt
│   │   └── support_url.txt
│   ├── primary_category.txt
│   ├── primary_first_sub_category.txt
│   ├── primary_second_sub_category.txt
│   ├── review_information
│   │   ├── demo_password.txt
│   │   ├── demo_user.txt
│   │   ├── email_address.txt
│   │   ├── first_name.txt
│   │   ├── last_name.txt
│   │   ├── notes.txt
│   │   └── phone_number.txt
│   ├── secondary_category.txt
│   ├── secondary_first_sub_category.txt
│   ├── secondary_second_sub_category.txt
│   └── trade_representative_contact_information
│       ├── address_line1.txt
│       ├── city_name.txt
│       ├── country.txt
│       ├── is_displayed_on_app_store.txt
│       ├── postal_code.txt
│       └── trade_name.txt
└── screenshots
    └── README.txt
```

You can delete the `Deliverfile` created here as it only contains duplicated information from our `Appfile`.

If you just created your app in the previous step, of course most of these files are empty for now. Only `en-US/name.txt` and the files in `trade_representative_contact_information/` contain some already known information.

## Android: `fastlane supply init`

This time an Android equivalent tool exists, it is called `fastlane supply`. 

By running `fastlane supply init` you can do the same for Android. Again it will create some local folders and files. If you just created a new app, `en-US/title.txt` is the only one which already contains data.

```
metadata/android
└── en-US
    ├── full_description.txt
    ├── images
    │   ├── phoneScreenshots
    │   ├── sevenInchScreenshots
    │   ├── tenInchScreenshots
    │   ├── tvScreenshots
    │   └── wearScreenshots
    ├── short_description.txt
    ├── title.txt
    └── video.txt
```

## Done

You now have a local file structure for metadata and screenshots of both apps in your `fastlane` folder. (The combined file and folder structure in `metadata` clearly shows that Fastlane was started as a iOS tool.) 

Now you can [add metadata to this local structure and upload it to the stores](add-metadata-and-upload).
