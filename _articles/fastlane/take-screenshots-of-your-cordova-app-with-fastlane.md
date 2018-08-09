---
title: 
published: true
date: 2017-08-29 16:00:00 +0000
last_updated: ''
parent: ['Ionic + Fastlane', '../fastlane']
---
# Take screenshots of your Cordova (or Ionic) apps with Fastlane

When you first published an app, you probably just took some screenshots on your test devices or simulators and uploaded them manually to the App Store or Play Store. Taking 3 screenshots on a hand full of devices is not that big a deal. But for a professional app, this number can increase exponentially. You have to take screenshots of:

* many different *screens*
* the app in different *languages*: EN, ES, DE, CN, ...
* multiple *device categories*: Smartphone, Tablet, Watch, TV
* different *devices*: iPhone 5, iPhone 6, iPhone 6 Pro, ...
* multiple *operating systems*: iOS and Android

What took a few minutes before, now can take hours or even days: 5 screens × 20 languages × 5 devices × 2 operating systems = 1000 screenshots!

Add to that the complexity of it all: Switching between devices and simulators or changing the device language is cumbersome and complicated. If the app is not just a number of simple output screens but requires input or extensive usage to reach a specific state that should be screenshotted, you have to do that over and over again. A bug is discovered on one of the captured screens? You have to start from the beginning once more.

It also gets harder to keep track of all the files and manage them. Uploading the finished screenshots takes longer and longer as well and requires using the Store's UI for hours. Maybe you have a poor intern for such work, but usually it's the developer's to take care of this.

The solution of course is to **automate the screenshot creation** and **upload process** with _fastlane_.

## Create Screenshots and add to metadata

For normal iOS and Android apps fastlane offers two actions to create screenshots: [`capture_ios_screenshots`](https://docs.fastlane.tools/actions/capture_ios_screenshots/) and [`capture_android_screenshots`](https://docs.fastlane.tools/actions/capture_android_screenshots/). To a) enable the taking of screenshots and b) the definition of steps to run and screenshots to take both of these actions unfortunately require manual modifications in your native projects - [which is discouraged for Cordova/Ionic projects as those can be regenerated](problems-with-using-fastlane-for-ionic.md#cordova-native-projects-are-generated).

To help with this problem I created the [`cordova_screenshots` fastlane plugin](https://github.com/janpio/fastlane-plugin-cordova_screenshots). This plugins "extracts" the 


* [Create iOS Screenshots with `snapshot`](screenshots/cordova-ios-screenshots-with-snapshot.md)
* [Create Android Screenshots with `screengrab`](screenshots/cordova-android-screenshots-with-screengrab.md)



### Upload screenshots

Run `fastlane supply` and `fastlane deliver` to update your apps with the screenshots which are now included in the metadata folders. Check both stores if the upload worked.
