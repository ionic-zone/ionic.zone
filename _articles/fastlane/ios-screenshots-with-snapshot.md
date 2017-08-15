# Fastlane + Ionic: iOS Screenshots with `snapshot`

## iOS

As before, using `fastlane snapshot`, the fastlane tool to create iOS screenshots, is a bit more complicated for Ionic apps than for normal iOS apps. Normally you "Add the ./SnapshotHelper.swift to your UI Test target" and then write **UITests** which of course would mean that this file, the adding of it and also the UITests itself would get lost on each new checkout or project regeneration of the Cordova iOS project.

Lucky for us someone wrote a [nice fastlane plugin called `ionic_integration`](https://github.com/knocknarea/fastlane-plugin-ionic_integration) that takes care of that. It places these files and the tests inside the `fastlane` folder and offers a fastlane action to "retrofit" these into the Xcode project.

* Start with `fastlane snapshot init` which creates a `Snapfile` in `/fastlane`.
* Uncomment some devices and add your supported languages. Also uncomment the `clear_previous_screenshots` line
* Run `fastlane add_plugin ionic_integration`to install the plugin.
* Call `fastlane run ionic_ios_config_snapshot ionic_scheme_name:"ionic-screen-shots"` to trigger the file generation of the plugin at `fastlane/ionic/config/ios/ui-tests/ionic-screen-shots`. (This automatically retrofitted the files to your current Cordova Xcode project)
* Open your Xcode project and open the file `ionic-screen-shots/ui-snapshots.swift` (which is a generated file from the folder before, linked into your Xcode project)
* Go into the `testSnapshots` method and write your UI tests (Writing stable UITest tests for your Cordova/Ionic app is a whole another topic and out of scope here. For now it should be enough to capture a screenshot of the app after it started - which the file does in its current state.)
* Create a new lane in your `Fastfile` which contains the following call:
```
snapshot(
      output_simulator_logs: true,
      reinstall_app: false,
      erase_simulator: true,
      scheme: "ionic-screen-shots" # The name of a scheme to use, one that you generated with ionic_ios_config_snapshot
    )
​````
This executes the UITest on all devices in all languages defined in `Snapfile` and then saves these screenshots in the `fastlane/screenshots` folder. Another upload of metadata with `fastlane deliver` will use and upload these screenshots.
```