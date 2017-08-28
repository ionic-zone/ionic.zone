
Afterwards you will have a file structure of the data of your app's (empty) meta data.

## iOS: `fastlane deliver init`

Run `fastlane deliver init` to download all the (of course non-existing) app metadata for the app it just created. By doing this it creates the local file structure for you to fill with actual data!

```
TODO tree
```
Also creates `fastlane/Deliverfile`:
```
TODO
```

All set up for uploading stuff to iTunes Connect later: It know about your app, can access your accounts, and has a local representation of the data needed in the local file system.



## Android: `fastlane supply init`

this will download the initial data as `deliver init` did for iOS
and create additional folders locally

```
TODO tree
```

And easy as that, again it added some folders and file that represent the data available in the Google Play console and have to be filled.

(with the folder structure you can see that iOS was first and Android was added later to fastlane)