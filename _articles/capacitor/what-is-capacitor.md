---
layout: article
title: 'What is Capacitor?'
date: 2018-03-09 00:00:00 +0000
last_updated: ''
parent: ['Capacitor', '../capacitor']
---
# Introduction to Capacitor ⚡️

Capacitor is a way to create cross-platform mobile and desktop applications.

It can be used to package **web apps** made with _HTML, CSS and JavaScript_ into **native apps** that work on _Android and iOS_ (and can be uploaded to their respective _app stores_), **desktop applications** via Electron, and also **Progressive Web Apps** that run in _all browsers_ - targeting all relevant platforms with one code base.

Capacitor itself calls apps built with its help "**Native Progressive Web Apps**", meaning that they combine web apps that have characteristics of a Progressive Web App, with native functionality and code.

{::comment}
Drawing: web app UI on the left without frame, arrows to devices and browser on the right showing the same UI, more arrows pointing to App Store Icons or laptop
{:/comment}

It is functionally pretty similar to [Apache Cordova](https://cordova.apache.org) (formerly known as [PhoneGap](https://en.wikipedia.org/wiki/Phonegap)) which can be viewed as a [predecessor to Capacitor but differs in some important areas and technology choices](#consequences-to-apache-cordova).

Capacitor is built in the open [on GitHub as an Open Source project](https://github.com/ionic-team/capacitor) by the team behind [Ionic](https://ionicframework.com), a "top open source framework for building amazing mobile apps", where Capacitor it also intended to be used as a solution to build native applications.

---

- [Technical Overview](#technical-overview)
- [Supported platforms](#supported-platforms)
  * [Platform version support](#platform-version-support)
  * [Platform extensibility](#platform-extensibility)
- [Supported native functionality](#supported-native-functionality)
  * [Custom Native Code](#custom-native-code)
  * [Capacitor Plugins](#capacitor-plugins)
  * [Cordova Plugins](#cordova-plugins)
- [Command Line Interface](#command-line-interface)
- [Coming soon](#coming-soon)
- [Capacitor's Relationship to Ionic](#capacitor-s-relationship-to-ionic)
- [Consequences for Apache Cordova](#consequences-for-apache-cordova)
  * [Comparison between Cordova and Capacitor](#comparison-between-cordova-and-capacitor)
- [Some more details](#some-more-details)
  * [Native projects are artifacts](#native-projects-are-artifacts)
  * [Use whatever language you want](#use-whatever-language-you-want)
  * [Monorepo](#monorepo)

---

## Technical Overview

Capacitor wraps the web app in a so-called "WebView" that can display web apps inside the native app. It injects a "bridge" into the app running in the webview, that connects the code of the web app and the code of the native part so these can interact.

This way, functionality normally only available to native code can be used in the web app, and native code can interact with the web app running in the webview as well.

{::comment}
Drawing:
Left: Web App in browser
Middle: Web App wrapped in Web View, wrapped in native, bridge "connecting" it all, arrows indicate that communication happens in both directions.
Right: Native app
{:/comment}

For Progressive Web Apps Capacitor provides fallback implementations to native functionality not present - like for example the default "Take a Photo" view on iOS and Android. It is rebuilt with web technology and provides a similar experience to browser users. This way the web app can provide functionality even when running in a normal browser, that is normally only available to native applications.

{::comment}
Drawing: Phone with "Take Photo" screen, Browser windows with modal showing similar UI.
{:/comment}

Capacitor achieves true cross-platform and portable functionality with 100% code sharing by providing a consistent API, `@capacitor/core`, to the web app. Any web app can integrate `@capacitor/core` as a normal `import` or even a "bundled web runtime" called `capacitor.js` that is just included via a `<script>` tag.

No matter if the app runs on iOS, Android, in a browser on a mobile device or normal computer - the provider of some functionality is always identical to the web app and all the complexity is taken care of by Capacitor in the background.

A much, much [more comprehensive and deeper look at how Capacitor works from a technical point of view can be found over here](deep-dive-into-capacitor.md).

## Supported platforms

{::comment}
Logos: iOS, Android, Windows, macOS, Linux, Electron, Edge
{:/comment}

_Native Progressive Web Apps_ built with Capacitor can be used on all the relevant platforms:

- iOS
- Android
- Browsers: Progressive Web Apps
- Desktop: Windows, macOS, Linux via Electron (work in progress)

### Platform version support

Capacitor defines which platform versions are supported when creating the native project:

- For iOS, it supports the last two iOS versions, currently iOS 11 and iOS 10. 
- For Android support starts at API level 21 which corresponds to Android 5.0 (Lollipop) or newer.
- And on the browser side, all modern [browsers that support Web Components](https://caniuse.com/#search=components) (and actually many more via polyfills) will be able to display the web implementations.

### Platform extensibility

Capacitor contains a fixed set of platforms that can be added to projects and doesn't provide a system to dynamically load external platforms "definitions". To add an additional platform, Capacitor has to be adapted and changed.

## Supported native functionality

Providing native functionality to the web app is Capacitor's main job. Because of that it includes a [multitude of native functionality](https://capacitor.ionicframework.com/docs/apis/) out of the box:

- [Accessibility](https://capacitor.ionicframework.com/docs/apis/accessibility): Accessibility features
- [App](https://capacitor.ionicframework.com/docs/apis/app): App state and events
- [Background Task](https://capacitor.ionicframework.com/docs/apis/background-task): run and schedule background tasks
- [Camera](https://capacitor.ionicframework.com/docs/apis/camera): Take photos
- [Clipboard](https://capacitor.ionicframework.com/docs/apis/clipboard): Copy and paste things
- [Console](https://capacitor.ionicframework.com/docs/apis/console): Native logging
- [Device](https://capacitor.ionicframework.com/docs/apis/device): information about the device
- [Filesystem](https://capacitor.ionicframework.com/docs/apis/filesystem): local files on the device (NodeJS style)
- [Geolocation](https://capacitor.ionicframework.com/docs/apis/geolocation): tracking position
- [Haptics](https://capacitor.ionicframework.com/docs/apis/haptics): touch and vibration
- [Keyboard](https://capacitor.ionicframework.com/docs/apis/keyboard): control the keyboard
- [Modals](https://capacitor.ionicframework.com/docs/apis/modals): native alerts, confirmations and inputs
- [Motion](https://capacitor.ionicframework.com/docs/apis/motion): accelerometer and device orientation
- [Network](https://capacitor.ionicframework.com/docs/apis/network): network status
- [Share](https://capacitor.ionicframework.com/docs/apis/share): share content to other apps
- [Splash Screen](https://capacitor.ionicframework.com/docs/apis/splash-screen): launch image
- [Status Bar](https://capacitor.ionicframework.com/docs/apis/status-bar): styling, showing, hiding the status bar
- [Storage](https://capacitor.ionicframework.com/docs/apis/storage): persistent key-value storage

{::comment}
Icons for all native APIs?
{:/comment}

This list is currently still highly in flux as new APIs and plugins are added [according to user feedback](https://github.com/ionic-team/capacitor/issues) all the time. Missing anything? Go [create an issue on GitHub](https://github.com/ionic-team/capacitor/issues/new).

There are also multiple ways to extend that functionality yourself: You can add _custom native code_ to the native projects or install reusable _Capacitor plugins_ or even existing _Cordova plugins_ with `npm`.

### Custom Native Code

{::comment}
Icon that shows normal code in app
{:/comment}

The quickest way to add native code to your app is to write "local plugins" that are included in your native project. For both [Android](https://capacitor.ionicframework.com/docs/android/custom-code#webview-accessible-native-code) and [iOS](https://capacitor.ionicframework.com/docs/ios/custom-code/#webview-accessible-native-code) it is as simple as adding 2 files to your project to make native code accessible to the webview, which then can simply be called from the web app.

### Capacitor Plugins

{::comment}
Plugin Icon with Capacitor logo in app
{:/comment}

Capacitor also has a way to package these native modifications into [reusable Capacitor plugins](https://capacitor.ionicframework.com/docs/plugins/). Those can be published as npm packages, so other people can easily download and install them into their own projects. Of course, they can also provide their own "web fallbacks" so the plugins work in the browser in PWAs as well.

### Cordova Plugins

{::comment}
Plugin Icon with Pluggy logo in app
{:/comment}

As Apache Cordova has a [flourishing plugin ecosystem](http://cordova.apache.org/plugins/) (more than 3000 plugins actually!), the developers of Capacitor decided to also [support Cordova plugins](https://capacitor.ionicframework.com/docs/basics/cordova). Installation is a bit different as Capacitor doesn't normally modify the native project files, but many plugins still work and can be used.

## Command Line Interface

Working with Capacitor is mainly done via its Command Line Interface, or CLI, called `@capacitor/cli` and executed via `npx cap`. It is used to `create` or `init` projects, `add` the native platforms and `copy` the web app or `update` plugin code to the native project. It is a local CLI bundled with each project, so different CLI versions in different projects are possible.

I also wrote a much more detailed [Overview of the Capacitor CLI, @capacitor/cli](cli.md).

## Coming soon

While Capacitor already supports many of its planned use cases, in other areas there exist only plans and not much to look at yet:

- **Electron Support**  
  Already present in its infant stages in the repository now, Electron will enable Capacitor to build apps for all major desktop operating systems like Windows, macOS, and Linux.
- **Native UI Shell / Native Shell Add-ons**  
  The next step for even better apps will be to give developers powerful tools and ways to mix more native UI elements into their apps. A navigation bar built with HTML, JS, and CSS can look pretty much 99% like the real deal, but it will never cover all edge cases and most importantly never feel 100% native. Capacitor can and wants to fix this by popularizing new ways to mix native platform code with a web app, showing content. (See [Basecamp's David Heinemeier Hansson's article "The hybrid sweet spot"](https://signalvnoise.com/posts/3743-hybrid-sweet-spot-native-navigation-web-content) for more information about this idea)
- **Ionic Pro support**  
  Ionic is a commercial company and their main offering is a platform to build and manage applications built with Ionic. As Ionic until now uses Cordova under the hood, the whole platform is also built for that. It will take some time to adapt this and the connected code components to Capacitor.

## Capacitor's Relationship to Ionic

While Capacitor was started and is (currently) mainly built by [Ionic](https://ionicframework.com) staff, it is an Open Source project built on the philosophy to work with any web app - not just ones built with Ionic. Any web app that has an `index.html` file as its entry point can be packaged with Capacitor.

Ionic will probably add Capacitor to Ionic's CLI as the default tooling for building native applications when Capacitor is stable enough and can support all the necessary use cases that are currently covered by Apache Cordova.

## Consequences for Apache Cordova

Ionic Framework is one of the, or _the_, most popular "user(s)" of Apache Cordova. Each developer packaging their Ionic app as a native app installs Cordova via `npm install -g cordova` and uses it to build the native iOS and Android apps with `ionic cordova build ios|android`.

But Cordova was started almost 10 years ago, was still called Phonegap back then, and a lot has changed in the meantime:

It became clear which native platforms are here to stay (not Palm webOS, tizen, FireOS, Blackberry, Firefox OS or Windows Phone - which Cordova all supported at their time), what native functionality all the remaining operating systems offer their users and which of these the users actually want to use. It also became apparent which problems the choices made by the early Cordova developers were causing for developers today.

The biggest change only happened in the last few months when mobile and desktop browser got better support for Progressive Web Apps and Web Components got standardized and implemented. This enabled browsers to become their own, proper _platform_ to be considered to roll out apps. And Cordova is just not set up to support this.

That being said, Apache Cordova of course will not go away - in general and also in Ionic CLI. Capacitor might become the "Successor to Cordova", or it might just become an alternative for slightly different use cases.

### Comparison between Cordova and Capacitor

To understand better why Ionic decided to build Capacitor instead of building further on Cordova, it makes sense to take a deeper look at: [The differences between Capacitor and Cordova](differences-between-capacitor-and-cordova.md). (To summarize: No global CLI, built-in PWA and web support, but also technical details like the non-existence of a `deviceready` event the app has to wait for.)

## Some more details

While not the most important developing facing features, there are some more very interesting details worth to know about Capacitor:

### Native projects are artifacts

In Capacitor the native projects it creates and you customize are treated as so-called "source artifacts". That means that once a project is created, you keep it an check it into source control. Capacitor will not (or as little as possible) mess with it anymore, so it is a fully independent piece of code.

### Use whatever language you want

Capacitor is built with Swift on iOS by default, but Obj-C can still be used for plugins and custom native code if you want to. Android is all written in Java, but Kotlin is also supported if that is more your style.

### Monorepo

Capacitor is structured as one big "monorepo" which contains all the parts (`@capacitor/cli`, `@capacitor/core`, the native libraries for iOS and Android, a development project, the plugin and platform templates, even the website and docs) versus one repository for each component or part of the whole solution, as many other highly complex libraries like Cordova are organized.

---

Did I miss anything? Let me know below in the comments and I will update as fast as possible. Thank you.
