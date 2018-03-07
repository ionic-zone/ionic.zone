---
layout: article
title: "@capacitor/cli: Capacitor CLI"
date: 2018-03-07 00:00:00 +0000
last_updated: ''
---
# Overview of the Capacitor CLI, @capacitor/cli

Most of the interaction you will have with [Capacitor](what-is-capacitor.md), the recently alpha-release Cordova successor by Ionic, will be through it Command Line Interface or CLI: `npx cap`.

## npx?

The `cap` in `npx cap` obviously stands for "Capacitor", which would have been a bit too long to type regularly. 

But did you notice the `npx` in front of it? `npx` is a [relatively new tool](http://blog.npmjs.org/post/162869356040/introducing-npx-an-npm-package-runner) from the team behind `npm` that allows you to run npm packages as CLI tools without globally installing them.

If you used Cordova or Ionic before, you know that the first step before being able to create a project with them is always to create a global installation of their CLI tool by running `npm install -g cordova` or `npm i -g ionic`. Then `cordova` or `ionic` becomes available globally in your command line.

`npx` enables you to a) run a local package from the project you are working on or b) run a package that is not (yet) installed in your project or even outside of a project context alltogether.

That is also how the first two important commands differ:

## 1. Create a Capacitor project

To [create your Capacitor project](https://capacitor.ionicframework.com/docs/getting-started/) you have two options:

### a) `npx cap init [appName] [appId]`

> Initializes a new Capacitor project in the current directory

If you already have a web app, you first install the CLI and the Core library via `npm` as usual:
```
npm install @capacitor/cli @capacitor/core
```
Then you can use the `init` command from above to create the initial Capacitor configuration file, `capacitor.config.json`, in your existing project.

### b) `npx @capacitor/cli create [appDir] [appName] [appId]`

> Creates a new Capacitor project

If you start without an existing web app project, you can use `npx` to temporarily download and install `@capacitor/cli` and use its `create` command to generate a whole Capacitor project with a rudimentary web app included (that has `@capacitor/core` installed).  




you can start inside the folder of a web app project, that already includes a `package.json` file. First install Capacitor by running  first before using the above command. This creates the initial Capacitor configuration that is needed to continue. I assumes your web app content currently lives in `www`.

## 2. Add native platforms

### `npx cap add ios`  
### `npx cap add android`

https://capacitor.ionicframework.com/docs/getting-started/with-ionic#add-platforms

> add a native platform project

To actually start development of a native app you now have to add the platforms of your choice to the project. Running the above commands will create a `ios` or `android` folder that contains a normal native project. It sets up the project for you and also copies over your `www` to the correct path and creates the native bridge file that will be injected into the webview showing your web app that enables the communication between native code and Javascript code.

## 3. Develop your app

Yeah, there is not really a CLI command for that - you have to do that manually. 

But there are 2 commands that might make it easier:

### `npx cap open`

https://capacitor.ionicframework.com/docs/basics/workflow#3-open-your-native-ide
https://capacitor.ionicframework.com/docs/basics/opening-native-projects

> opens the native project workspace (xcode for iOS)

Opens the project in the native IDE for the chosen platform.

### `npx cap serv`

https://capacitor.ionicframework.com/docs/basics/running-your-app#progressive-web-app

> Serves a Capacitor Progressive Web App in the browser

## 4. Update your Capacitor project(s)

### `npx cap copy`

https://capacitor.ionicframework.com/docs/getting-started/with-ionic#syncing-your-app-with-capacitor
https://capacitor.ionicframework.com/docs/basics/workflow#2-copy-your-web-assets
https://capacitor.ionicframework.com/docs/basics/building-your-app#2-copying-web-code

When you change your app app, you have to copy it over to the native projects:


> copies the web app build into the native app

> To copy web assets only, which is faster if you know you don't need to update native dependencies.
https://capacitor.ionicframework.com/docs/ios/#creating-ios-app

copies over `www` to the native projects so you can rebuild your app with the updated content.
// also copies over newly installed (cordova) plugins

### `npx cap update`

https://capacitor.ionicframework.com/docs/getting-started/with-ionic#using-ionic-native
https://capacitor.ionicframework.com/docs/basics/workflow#4-periodic-maintenance
https://capacitor.ionicframework.com/docs/ios/updating#updating-capacitor-library

And when you change something about the plugins your app should use (both Capacitor or Cordova) you have to make sure the plugins get updated in the native projects.

> updates the native plugins and dependencies based in package.json

### `npx cap sync`

https://capacitor.ionicframework.com/docs/basics/cordova#installing-cordova-plugins

> The sync command updates dependencies, and copies any web assets to your project.
https://capacitor.ionicframework.com/docs/ios/#creating-ios-app

> updates + copy

## 5. Helpers

There are also 2 more commands that might come in handy:

### `npx cap doctor`

 >checks the current setup for common errors

### `plugin:generate`

> start a new Capacitor plugin

---

And that's it! As Capacitor doesn't abstract building and packaging your apps (read more about the [differences between Cordova and Capacitor](differences-to-cordova.md), these are all the commands that currently exist and are needed.