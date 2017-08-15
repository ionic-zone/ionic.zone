## Add metadata and publish

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