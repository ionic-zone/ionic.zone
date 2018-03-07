---
layout: article
title: 'Capacitor CLI: @capacitor/cli'
date: 2018-03-07 00:00:00 +0000
last_updated: ''
---
# Overview of the Capacitor CLI, @capacitor/cli

Most of the interactions you will have with [Capacitor](what-is-capacitor.md), the recently alpha-release Cordova successor by Ionic, will be through its Command Line Interface or CLI: `npx cap`.

## npx?

The `cap` in `npx cap` obviously stands for "Capacitor", which would have been a bit too long to type regularly. 

But did you notice the `npx` in front of it? `npx` is a [relatively new "package runner"](http://blog.npmjs.org/post/162869356040/introducing-npx-an-npm-package-runner) from the team behind `npm` that allows you to run npm packages as CLI tools without globally installing them.

If you used Cordova or Ionic before, you know that the first step before being able to create a project with them is always to create a global installation of their CLI tool by running `npm install -g cordova` or `npm i -g ionic`. Then `cordova` or `ionic` becomes available globally in your command line.

`npx` on the other hand enables you to a) run a _local package_ from the project you are working on or b) run a _package that is not (yet) installed in your project_ or even _outside of a project context_ alltogether.

The first two Capacitor commands use these options:

## 1. Create a Capacitor project

To [create your Capacitor project](https://capacitor.ionicframework.com/docs/getting-started/) you have two options:

### a) `npx cap init [appName] [appId]`

> Initializes a new Capacitor project in the current directory

If you already have a web app with a `package.json` file, for example one built with Ionic, you start by installing the CLI and the Core library via `npm` as usual:

```
npm install @capacitor/cli @capacitor/core
```

Then you can use the `init` command from above to create the initial Capacitor configuration file, `capacitor.config.json`, in your existing project.

### b) `npx @capacitor/cli create [appDir] [appName] [appId]`

> Creates a new Capacitor project

If you start without an existing web app project, you can use `npx` to temporarily download and install `@capacitor/cli` and use its `create` command to generate a whole Capacitor project with a rudimentary web app included (that has `@capacitor/core` installed).  

## 2. Add native platforms

The next step is then to add the native platforms you want to support in your app:

### `npx cap add ios`  
### `npx cap add android`

> Add a native platform project

To actually start development of a native app you now have to add the platforms of your choice to the project. Running the above commands will create a `ios` or `android` folder that contains a normal native project. 

It sets up the project for you and also copies over your `www` to the correct path and creates the native bridge file that will be injected into the webview showing your web app that enables the communication between native code and Javascript code.

## 3. Develop your app

Yeah, there is not really a CLI command for that - you have to do that manually. 

But there are 2 commands that might make it easier:

### `npx cap open`

Opens the project in the native IDE for the chosen platform: Xcode for iOS, Android Studio for Android.

### `npx cap serve`

> Serves a Capacitor Progressive Web App in the browser

If your web app doesn't have its own `serve` or `watch` workflow, Capacitor provides a minimal implementation that runs the current content of `www` in your default browser.

## 4. Update your Capacitor project(s)

Now that you have your native projects (via `npx cap add`) there are two tasks that you have to run from time to time:

### `npx cap copy`

> copies the web app build into the native app

Each time you create a new build of your web app in `www`, it has to be copied over to the native platforms to be included in the next native build of the app. `cap copy` takes care of that. 

If you run your build via e.g. `npm run build`, it probably makes to add the `npx cap copy` command to the end automatically. For an Ionic project this might look like this:

```
# package.json
{
  "scripts": {
    "build": "ionic-app-scripts build && npx cap copy",
  },
}

```

### `npx cap update`

> updates the native plugins and dependencies based in package.json

If you also changed something with the native plugins 



https://capacitor.ionicframework.com/docs/getting-started/with-ionic#using-ionic-native
https://capacitor.ionicframework.com/docs/basics/workflow#4-periodic-maintenance
https://capacitor.ionicframework.com/docs/ios/updating#updating-capacitor-library

And when you change something about the plugins your app should use (both Capacitor or Cordova) you have to make sure the plugins get updated in the native projects.


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