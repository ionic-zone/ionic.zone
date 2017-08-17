# Ionic + Fastlane: Build and upload your Cordova apps for testing

Now that we have both iOS and Android correctly configured and connected it is a good time to actually do something with our Ionic project: build a development version and upload it for testing.

To build we will leverage the Fastfile for the first time.

## iOS to ???

For iOS our goal is to build the app and then upload it to Testflight. It is the official tool Apple offers.

### iOS to Testflight

With normal Xcode projects uploading to Testflight via `fastlane` is so easy, that it is one of the templates generated in the Fastfile:

```
  desc "Submit a new Beta Build to Apple TestFlight"
  desc "This will also make sure the profile is up to date"
  lane :beta do
    # match(type: "appstore") # more information: https://codesigning.guide
    gym # Build your app - more options available
    pilot

    # sh "your_script.sh"
    # You can also use other beta testing services here (run `fastlane actions`)
  end
```

This defines a `beta` lane, that uses `match` to take care of certificates (commented out right by default because not all people want to use that, we do!), then `gym` to build the app and finally `pilot` to upload to Testflight.

Unfortunately the default Xcode project file generated by Cordova is not ready for this. If you built an iOS app manually before, you know that by default the codesigning is not set and has to be edited manually in Xcode. Same for build numbering. This of course won't work for this automated process, so we have to do additional things in our lane to fix this. 

When we try to do this however we will see that the xcodeproj file generated by Cordova is too old for the current tools. To fix this you can either open the project once in Xcode which will upgrade it to a more recent version. Or you can install a fastlane plugin and use this lane:

```
desc "Upgrade the Cordova project to Xcode 8"
	lane :upgrade_xcode do
        TODO ... bla upgrade xcode to 8
end
```

Then run `fastlane ios upgrade_xcode` and confirm the prompt.

Now we can continue to fix the signing and versioning stuff:

```
TODO code signing stuff
```

Now on to the real lane:

* first certificates with `match`
* then get a build number with `latest_testflight_build_number`, increase it and set the build number again with `increment_build_number`
* then build the project
* and finally upload it to testflight with `pilot`

```
  desc "Submit a new Beta Build to Apple TestFlight"
  lane :beta do
    name = "Zählerstand"
    xcodeprojpath = "platforms/ios/" + name + ".xcodeproj"

    match
    increment_build_number({
      build_number: latest_testflight_build_number + 1,
      xcodeproj: xcodeprojpath
    })
    gym(
      project: xcodeprojpath
    )
    pilot(
       skip_waiting_for_build_processing: true,
       ipa: "./build/" + name + ".ipa"
    )
  end
```

Check the testflight interface to see if the upload worked.


## Android to ???

For Android the choice of a beta distribution platform is not as clear cut as it is for iOS.

### Android to Play Store Alpha chanel

```
platform :android do
  desc "Deploy a new version to the Google Play Store"
  lane :alpha do
    gradle(
      task: "assemble",
      build_type: "Release",
      project_dir: "android/"
    )
    supply(
      track: "alpha",
      apk: "#{lane_context[SharedValues::GRADLE_APK_OUTPUT_PATH]}"
    )
  end
end
```

### Android to HockeyApp

TODO