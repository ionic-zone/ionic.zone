# Setup iOS certificate handling for your Cordova app

## iOS Certificates

On to the (normally) nasty stuff: Certificates and Provisioning Profiles

### `fastlane match init`

This wants a private (!) git repo you have access to where it can save the created stuff. When this is correctly added, it creates a `Matchfile` in your project that contains that git URL.

```
TODO
```

### `fastlane match nuke development` and `fastlane match nuke distribution`

gets rid of all the certificates and profiles already present in your account from earlier endevours. You want to do that so `match` can start with a clean slate. Check before and after in your Apple Developer console to see how it worked.

### `fastlane match development` and `fastlane match appstore`

then creates brand new certificates and provisioning profiles in your account and commits them to the Git repo you provided earlier. No more changes on your local project for now, but these certificates are also adding to your Mac's keychain so fastlane can use them.

From now on you can just run `fastlane match` to just install the certificates and profiles on the machine you are developing on.


TODO Changes on Cordova project signing stuff that it actually works out of the box