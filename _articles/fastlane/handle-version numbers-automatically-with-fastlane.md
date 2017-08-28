# Handle version numbers automatically with Fastlane



First: What are we talking about?
Version and Build:
* Version is the thing users see. It can be of many forms, most often it is `MAJOR.MINOR.PATCH`, e.g. `1.4.2`
* Build is internal for the stores to differentiate different builds. For Android this is most often just an incrementing integer, for iOS it can be whatever it wants (and is also only unique per Version, so it can repeat with each version)

Cordova problem: 
"Version" comes from `config.xml` as "version" of `<widget>` and is put into `CFBundleShortVersionString` for iOS (In Xcode: Project -> General -> Identity -> Version) and `versionName` for Android (AndroidManifest.xml: versionCode).
But "Build" is automatically and -magically generated when the project is built (`ionic start`, `cordova create`, `cordova prepare`). This makes controlling it from the outside a bit of work.

Lucky for us, Cordova people also recognized this and we can set it for each platform in `config.xml` explicitly: 
* `android-versionCode` overwrites the value for Android's `versionCode`
* `ios-CFBundleVersion` overwrites the value for iOS's `CFBundleVersion`

So to set the Version and Build for both platforms, we can use:
```
<widget version='...' android-versionCode='...' ios-CFBundleVersion='...'>
```

This is the way we can manipulate our `config.xml` from fastlane to affect both Version and Build on both platforms.


## iOS



## Android