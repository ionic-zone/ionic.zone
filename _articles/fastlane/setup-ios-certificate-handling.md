---
title: 'Fastlane: Setup iOS certificate handling for your Cordova app'
date: 2017-09-27 16:00:00 +0000
published: true
last_updated: ''
parent: ['Ionic + Fastlane', '../fastlane']
---
# Setup iOS certificate handling for your Cordova app with Fastlane
{:.no_toc}

On to the (usually) nasty stuff: Certificates and Provisioning Profiles for iOS.

* toc
{:toc}

## The problem: certificates and provisioning profiles

If you already dabbled with Xcode manually you know there are a million ways certificates and provisioning profiles can go wrong.

They are cumbersome to create in the web UI that Apple offers, they are problematic to install, the configuration needed to make them work was changed 3 times already (pre Xcode 8, Xcode 8, since Xcode 9) and the error messages you get when something goes wrong often point to the wrong place. If you work in a team where test devices get added or removed frequently, you also have to redo and redownload the provisioning profiles quite often.

If you follow [Apple's documentation on Code-Signing](https://developer.apple.com/support/code-signing/) exactly this tends to work - until it doesn't.

When running a Fastlane lane this could look like this:

![`ionic cordova build error 1`](images/build/ionic-cordova-build-error-1.png)

Or this:

![`ionic cordova build error 2`](images/build/ionic-cordova-build-error-2.png)

You really don't want to spend time to debug and solve these.

Lucky for us Fastlane offers a nice solution that fully manages all the complexity and replaces it with one call in a lane: `match`.

## The solution: `match`

From the beginning a big part of Fastlane was to help with the codesigning mess. The tools `sigh`  and `cert` are a semi automated way to do that:

> `cert` will make sure you have a valid certificate and its private key installed on the local machine
> `sigh` will make sure you have a valid provisioning profile installed locally, that matches the installed certificate

Later this was expanded into `match`, whose founding idea is described in the [codesigning guide](https://codesigning.guide/).

> With match you store your private keys and certificates in a git repo to sync them across machines.

Unless you absolutely you can't revoke your existing certificates and profiles (which is necessary to use `match`) you should definitely use `match` to solve this once and for all:

### `fastlane match init`

Initialize `match` by running `fastlane match init` manually on the command line. This wants a private (!) git repo you have access to where it can save the created things:

![`fastlane match init` output](images/match/fastlane-match-init.png)

When this command was successful, it also creates a `Matchfile` in your project's `/fastlane` folder that contains this git URL:

```ruby
git_url "https://username@example.org/username/reponame.git"
type "development" # The default type, can be: appstore, adhoc, enterprise or development
```

### Clean up with `fastlane match nuke development/distribution`

If you used your Apple developer account before to develop apps, `fastlane match nuke development/distribution` can get rid of all the certificates and profiles already present in your account. You want to do that so `match` can start with a clean slate.

Run `fastlane match nuke development` and `fastlane match nuke distribution` separately to get rid of the different types of certificates:

![`fastlane match nuke development` output](images/match/fastlane-match-nuke.png)

Check before and after in your Apple Developer console to see if it worked. (You will also get a scary sounding "Your Certificate Has Been Revoked" email(s) from Apple.)

Don't worry, apps signed with the old certificates won't stop working and the next builds with these certificates will update just fine. (Note that if your colleagues are using the same certificates, definitely talk to them then before running any command like this or they might be very unhappy.)
{:.message}

### Create and download certificates with `fastlane match` or the `match` action in a lane

`match` itself then can create brand new certificates and provisioning profiles in your account and commit them to the Git repo you provided earlier.

You can do this by explicitly running `fastlane match development` or `fastlane match appstore` in the command line, or by just adding `match` to one for your existing lanes or a new lane:

```ruby
match(type: 'appstore')
```

```ruby
match(type: 'development')
```

or just

```ruby
match
```

This will output something like this:

![`fastlane match` output](images/match/fastlane-match-in-lane-1.png)

It will first clone your certificates repo specified in `Matchfile`, decrypt its content (if present) with your passphrase and check if the certificates are still valid by logging into your Developer Portal account (might require two factor authentication!).

![`fastlane match` output](images/match/fastlane-match-in-lane-2.png)

If there are no certificates for the project you are currently working on it will **create** them in the Developer Portal, then **download and install** them locally in your Mac's keychain. After encrypting them (and asking for your new passphrase if this is a new repository!) it will push them to your _certificates git repository_ for future usage:

![`fastlane match` output](images/match/fastlane-match-in-lane-3.png)

If the certificates already exist in the repo, they are downloaded and installed locally before the lane continues.
{:.message}

### Use certificates in normal lanes with `match`

Now you can use these certificates [in your normal build processes](build-your-project.md).

Most fastlane iOS "build" actions and plugins will automatically pick up the correct certificate values (paths, IDs, signature) if you run a simple `match` first (`fastlane-plugin-ionic` and `gym` definitely do!). This makes sure the certificates are definitely there and installed properly.

## Daily life with `match`

There are several tasks that can become necessary in your daily life with certificates and provisioning profiles:

### Regenerate provisioning profiles with newly added devices

When you add a new device's UDID in the ["All Devices" list in Apple's Developer Portal](https://developer.apple.com/account/ios/device/), you have to invalidate your old and create new development or ad-hoc provisioning profiles that include this device.

You can do so with `fastlane match` on the command line by simply calling:

```
fastlane match development --force_for_new_devices
fastlane match adhoc --force_for_new_devices
```

### Change encryption password of your your in Git repository

You might want to change the password used to secure your profiles and certificates in your Git repository.

```
fastlane match change_password
```
