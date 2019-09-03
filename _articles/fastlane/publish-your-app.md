---
title: ' Ionic + Fastlane: Publish your app' 
published: true
date: 2017-08-29 16:00:00 +0000
last_updated: ''
parent: ['Ionic + Fastlane', '../fastlane']
---
# Publish your Ionic Cordova app on the app stores

After extensive testing your Debug and Release builds you now have a version that should be uploaded to the stores, for review for iOS and release for Android.

Build with Ionic
Upload with Fastlane
Do last few steps manually

## iOS

TODO

### Upload `.ipa` file

```ruby
lane :publish do
  build_release
  deliver(
    ipa: ENV('CORDOVA_IOS_RELEASE_BUILD_PATH')
  )
end
```

TODO
https://github.com/fastlane/fastlane/blob/master/deliver/Deliverfile.md#submission_information
https://github.com/fastlane/fastlane/blob/master/spaceship/lib/spaceship/tunes/app_submission.rb#L18-L69

### Submit your iOS app for review

Additional steps in the web UI:

* ...

## Android

TODO

### Upload `.apk` file

```ruby
lane :publish do
  build_release
  supply(
    apk: ENV('CORDOVA_ANDROID_RELEASE_BUILD_PATH')
  )
end
```

### Publish your Android app

Additional steps in the web UI:

* ...

## Conclusion
