---
title: Introduction to Fastlane
date: 2017-08-29 16:00:00 Z
last_updated: ''
parent:
- Ionic + Fastlane
- "../fastlane"
---

# Introduction to Fastlane

[Fastlane](https://fastlane.tools/) describes itself as 

> [...] the tool to release your iOS and Android app 🚀 It handles all tedious tasks, like generating screenshots, dealing with code signing, and releasing your application. 

or 

> The easiest way to automate building and releasing your iOS and Android apps 

Many people probably come into contact with Fastlane because it also promises to get rid of the certification and signing chaos often created when developing for iOS. I know that alone was enough to sell me on the tool.

## Fastlane Tools

But Fastlane also offers much more: creating screenshots, managing and uploading metadata to the stores, creating apps entries, even building and (beta) distribution. With all the tools in its toolchain, the whole "deploy + release" process can be covered:

- `produce` = Create apps on Apple Developer Center and iTunes Connect
- `precheck` = Check if your app and its data will pass the app review
- `deliver` = Upload metadata for iOS apps
- `supply` = Upload metadata for Android apps
- `match` = Manage iOS certificates and provisioning profiles
- `snapshot` = Screenshots for iOS apps
- `screengrab` = Screengrabs for Android apps
- `gym` = Build your iOS apps

You can also manually manage your certificates with `sigh`, `cert` and `pem`, handle your testing with `scan`, `pilot` and `boarding`, use `frameit` to put your iOS screenshots into a template or manually interface with Apple Dev center and iTunes Connect with `spaceship`.

{::comment}
## Fastlane Bascis
TODO
### Background
Felix Krause
Fabric
first Twitter
now Google

### Architecture
TODO lane?

```ruby
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

Ruby?
*file?

### Functionality
First class tools: CLI for one set of tasks, can be used standalone
all grouped under `fastlane` as well

Actions: `fastlane` comes with a list of actions that can be used in Fastfiles
All first class CLI tools are also available as actions

Optional plugins that have to be installed can offer additional actions to be used in Fastfiles
These add more obscure stuff only needed by some people
It's easy to write them yourself, so you can extend fastlane functionality without having to edit fastlane itself

### Documentation
https://docs.fastlane.tools/
{:/comment}

Now you know what Fastlane offers. But [can it be used with Ionic Cordova projects?](problems-with-using-fastlane-for-ionic.md)
