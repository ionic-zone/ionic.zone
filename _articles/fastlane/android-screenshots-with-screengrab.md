# Fastlane + Ionic: Android Screenshots with `screengrab`

## Android

For Android, you can use `fastlane screengrab` to create the screenshots. It uses "UI Automator" and "Espresso" tests (or only "Espresso" for older versions) to drive the interactions in your app.

### Installation and preparation

- `fastlane screengrab init` - this creates a "Screengrabfile" you should customize (check `locales`)
- Add a lane to Fastfile which calls `screengrab` to the `android` platform:

```
  lane :screenshots do
    screengrab()
  end
```

- Run that lane:
  `bundle exec fastlane android screenshots`
- Error messages:

a)

> There are no connected and authorized devices or emulators

You need an active "device" (real or emulator) connected to your computer

```
- Just connect your Android device via USB
- You might have to install emulators in Android Studio (AVD Manager), activate them by running a native Android demo project (create one in Studio) in them
- Or you can use [Genymotion](TODO)
```

b)

> The `adb` command could not be found on your PATH
> Please ensure that the Android SDK is installed and the platform-tools directory is present and on your PATH

You have to add Android SDK platform-tools to PATH: Add `export PATH="$PATH:/Users/sujan/Library/Android/sdk/platform-tools/"` to your `.bash_profile` and restart the terminal

c)

> The `aapt` command could not be found on your system, so your app APK could not be validated

Fix by adding to your path `export PATH="$PATH:/Users/sujan/Library/Android/sdk/build-tools/26.0.1/"`

- Choose the one any only selectable APK as app and test
  - If you have the app installed already, you might have to uninstall it first to get rid of another error


- Add permissions to `src/debug/AndroidManifest.xml` (create the folder): https://docs.fastlane.tools/getting-started/android/screenshots/#configuring-your-manifest-permissions

```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="de.janpiotrowski.zaehlerstand"
    xmlns:tools="http://schemas.android.com/tools">

    <uses-permission android:name="android.permission.WAKE_LOCK" />
    <uses-permission android:name="android.permission.DISABLE_KEYGUARD" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.CHANGE_CONFIGURATION" />

</manifest>
```

This will be merged with your default `AndroidManifest.xml` created by Cordova from your `config.xml` file during the build.

- Before we continue, lets get rid of the "Choose APK" step each time. Add this to your `Screengrabfile`:

```
app_apk_path 'platforms/android/build/outputs/apk/android-debug.apk'
tests_apk_path 'platforms/android/build/outputs/apk/android-debug-androidTest.apk'
```

- Now only one error is left:

> Make sure you've used Screengrab.screenshot() in your tests and that your expected tests are being run.

That means we are now actually going to create some tests as the environment is ready.

### Create the test that takes screenshots

- Run -> "Record Espresso Test". This creates a [basic JUnit 4 test class](https://developer.android.com/training/testing/start/index.html#junit), adds in some Espresso (UI Test) stuff and takes care of the imports (via messing with your build.gradle)
  - Manually add assertion for Webview that won't work, but adds a nice delay thingie
- Diamond Operator: https://stackoverflow.com/a/29432474/252627 Fix by making it explicit.
- Add `Screengrab.screenshot("0_app-launch");` to test to trigger screenshot generation
- Add `build-extras.gradle` with content

```
dependencies {
	compile 'tools.fastlane:screengrab:1.0.0'
}
```

- Add import `import tools.fastlane.screengrab.Screengrab;` to test file
- Run the lane again to see if everything works and this one screenshot is successfully created!

// TODO Find a way to fix compile/androidTestCompile foo: https://stackoverflow.com/questions/29687897/why-is-library-module-android-support-test-not-visible-in-add-dependency/33259738#33259738

- Done.

// TODO Link to Article about clean status bar