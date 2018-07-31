---
layout: article
title: 'Differences between Capacitor and Cordova'
date: 2018-03-22 00:00:00 +0000
last_updated: ''
parent: ['Capacitor', '../capacitor']
---
# How is Capacitor different from Cordova?

Capacitor is a new alternative to Apache Cordova, which filled the role of wrapping web apps into native apps for the last decade. One way to understand what Capacitor is all about and why it exists, is to look at how it is different from Cordova and why. This article tries to do that.

---

...

---

## Not different

Let's start by looking what is _not_ different between the two:

### WebView

Both Cordova and Capacitor wrap the **web app** in a **Webview** that is packaged as a **native application** that can be uploaded to the **app stores** and installed on devices. That way the same web app can be deployed as a native app to different operating systems.

### Access native functionality

Both offer a way for that web application to access native functionality that is normally not available to web apps in a browser. And both offer ways to extend the default functionality, so it is easy for the community to write their own "plugins".

## Different




The differences are not in the basic functionality, but _how_ they achieve these goals:


## Goals






Let's start with the most drastic one, that has quite a lot of consequences:





### Supported Platforms

One of the core features of both tools is that you can deploy the same web app as an app to multiple platforms.

While Cordova mainly supports iOS, Android, macOS, Windows (and back when they were relevant also supported Blackberry, FirefoxOS, Windows Phone, Ubuntu, FireOS, webOS, Tizen, Bada and many more), Capacitor "only" supports iOS, Android and Electron (for desktop OS like Windows or macOS) but adds Web as a first class platform.

Capacitor doesn't support a dynamic platform system like Cordova did - you can not just implement your platform of choice and install it into a project. But as the relevant mobile platforms are pretty much set today, this is not as big a need as it was >10 years ago when Cordova got started.

#### PWA

web/PWA = first class platform
cordova.js is only available when run on the device - failing if just opened in the browser
Capcitor JS runtime is meant to be built into the app and provide a web implementation as well


#### Other platforms

- Electron support (Cross Platform Desktop Apps)
- no dynamic platform system (yet?)


### Smaller CLI

The Capacitor CLI has a much smaller footprint than Cordova CLI, both in how it is used and what it can be used for.

There is no no global CLI installation for Capacitor like Cordova's `npm install -g cordova`, to have a global `cordova` CLI that is accessible everywhere on your machine. The Capacitor CLI is part of each project via normal npm package installation and is executed with `npx`.

The CLI also doesn't cover running and building apps - so common Cordova commands like `cordova build`, `cordova run`, `cordova emulate`, `cordova prepare`, `cordova clean` don't have a counterpart. The native projects are managed and used with the normal platform IDEs (Android Studio, Xcode).

Capacitor also uses NPM to manage the platform bindings and plugin code. There is no equivalent to `cordova plugin` 

Platforms and plugins are managed via no


### Native Code

- platform folders (where the actual native apps are) are not build artifacts, so have to be committed to source control and not touched by Capacitor
- no config.xml and plugin.xml, but manually manage Info.plist and AndroidManifest.xml 
- no re-add (rm, add) workflow to fix problems
- custom native code (instead of only plugins)

#### Plugins vs. internal Core plugin APIs

- Cordova has a list of "Core plugins", some are suggested to be added to all projects. Capacitor has all those (and more) integrated as "APIs"

#### Configuration of Plugins

- Cordova = config.xml
- Capacitor = capacitor.config.json

### Structure and Organization

- Monorepo - one big project instead of repos/projects for each platform and plugin
- no Apache, less process

#### Languages

- iOS: Swift by default, instead of Obj-C only (can be used as well!)
- Typescript vs. Javascript

### Speed optimizations

#### Native Code

// Lazy loading of plugins - not on startup // is this true?
no platform.ready()

#### Installation and CLI

much faster because it is all in one package
`cordova platform add` can take a long time to download and install the individual packages via `cordova-fetch`

#### Bridge

cordova.js vs. @capacitor/core
capacitor.js => https://capacitor.ionicframework.com/docs/web/#without-a-build-system
@capacitor/core => https://capacitor.ionicframework.com/docs/web/#with-a-build-system

### Dependency management

everything is managed via npm - everything you installl (platform, plugin) is written to package.json and managed there.

### Simplified configuration

no duplicated platform and plugin version recording in both package.json and config.xml or even more files like platforms.json and plugins.json











joshmorony:
key things for me: 
focus on being a runtime that supports all platforms, 
no deviceready (plugins available from boot), 
the "hands off" approach in treating the native project as a source artifact, 
the approach to custom plugins... 
and then more into the future, the focus on allowing the mixing of native ui controls with web content
and also the focus on improving existing APIs (like the filesystem) 
and providing premium support for plugins

max [2:46 PM]
I think the deviceready thing is significant and was one of the big reasons we engineered our plugin system the way we did. 
First-class Swift support for iOS plugins, 
different standard plugins available out of the box (such as Haptics), 
No need for complicated, error-prone hooks since you just modify your project
One of the other big reasons we did this:
If you're an ionic developer and you have a native issue, we hopefully can resolve it a lot faster. We're trying to build as good of a native experience as we have with Ionic Framework, and we will be hiring a team around Capacitor as the project grows and usage increases in Ionic





no hooks





it uses WKWebView
Cordova projects still use UIWebView by default





iOS project is better organized: plugins added via CocoaPods (although files loaded via npm) which creates a workspace to put their code, not directly into the project as Cordova does







PWA/web first class => native plugins can also be tested in browser during local development!




## Which is better?

Right now it is hard to say. Capacitor is leaner and more elegant than Cordova, but is still in active development. Right now Ionic seems to build the base for interesting things to come, which might then offer a clear benefit in comparison to Cordova.
