## Add metadata and upload to stores

Now you have to do some manual work and fill these files created by `deliver`and `supply` in the previous step with real data. 

### iOS

Go through the `fastlane/metadata` folder and add your description etc. (possible categories are listed [here](https://github.com/fastlane/fastlane/blob/master/deliver/Reference.md)).

```
TODO tree
```

When you are done you can run `fastlane deliver` to generate a html file as overview of the data (and press `n` to not continue with the upload for now).

### Android

After that you can do the same for Android in `fastlane/metadata/android`. 

```
TODO tree
```

(There is no "generate preview" functionality in `supply` yet unfortunately, so check your files twice to make sure you didn't miss anything.)

> Note that `supply` doesn't yet support all fields that the Google Play console requires, e.g. "category" is not downloaded and can not be set for Android apps. You have to do that manually later.

### Upload to stores

Run `fastlane supply` and `fastlane deliver` to update your apps on the stores administration interfaces. Check both stores (iTunes Connect and Google Play console) if the upload worked.

> Note that both tools don't remove translations or set the default language of your app. You will have to do that manually for both the Play Store and the App Store.
