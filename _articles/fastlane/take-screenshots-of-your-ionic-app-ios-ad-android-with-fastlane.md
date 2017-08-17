# Take screenshots of your Ionic app (iOS and Android) with Fastlane

* screenshots of different screens
* languages: EN, ES, DE, CN, ...
* device types: Smartphone, Tablet, Watch, TV
* devices sizes: iPhone 5, iPhone 6, iPhone 6 Pro, ...

Makes: Loooots of screenshots to take
Often this is the task of a developer. **Very** expensive.
If you have an underemployed intern that might not be a problem.
But it still takes a lot of time and is prone to mistakes and errors.

Solution: Automation.

## Create Screenshots and add to metadata

* [iOS Screenshots with `snapshot`](ios-screenshots-with-snapshot.md)
* [Android Screenshots with `screengrab`](android-screenshots-with-screengrab.md)

### Upload screenshots

Run `fastlane supply` and `fastlane deliver` to update your apps with the screenshots which are now included in the metadata folders. Check both stores if the upload worked.