---
title: An Overview of Ionic's Github Repositories
date: '2017-05-12T17:15:00.000+00:00'
last_updated: '2017-06-17T17:24:41.317Z'
published: true
---
# An Overview of Ionic's Github Repositories
{:.no_toc}

If you develop applications using Ionic Framework you will - sooner or later - come into contact with one of its Github repositories. When looking for how to do something, it is sometimes easier to look into and search the code directly on Github where it is versioned and easily searchable, than to limit yourself to what you have available locally. Fortunately, all components of Ionic are developed in the open. At the latest when something doesn't work as expected and it really isn't user error, you end up at the issue's of the project or even submitting a Pull Request fixing the bug you encountered.

But Ionic (or better [ionic-team](https://github.com/ionic-team), the Github organization that hosts and collects all the repositories) has a loooot of Github repositories. More than 150 in fact. What is which and needed why?

This post gives you an overview of all these repositories. For that, I went through all of them, grouped them and added some description and explanation:

* toc
{:toc}


Let's start with the most important ones:

## General

* [ionic-cli](https://github.com/ionic-team/ionic-cli) - The _Ionic Command Line Interface `ionic` (CLI)_ is what everybody that works with Ionic installs as one of the first steps with `npm install -g ionic`. It is what enables you to `ionic start` projects, `ionic serve` them in the local browser to test them and `ionic cordova build` them into Cordova wrapped native apps for mobile - and so much more.

* [ionic-site](https://github.com/ionic-team/ionic-site) - You most probably visited _[ionicframework.com](https://ionicframework.com)_ when you learned about Ionic Framework. Here is all the information you need, including the [complete documentation](https://ionicframework.com/docs/). The site is built from this repository, which in turn gets its content from many of the child repositories.

## Ionic

<div class="message">
Note: What I call just "Ionic" in the following paragraphs and lists was formerly known as Ionic 2. But Ionic quickly followed up with Ionic 3 and is working hard on the next iterations - so it makes more sense to call is just Ionic. The older iteration of the Framework that was built on AngularJS (instead of Angular for the current Ionic) is now known as "[Ionic v1](#ionic-v1)" and referred as such here.
</div>

* [ionic](https://github.com/ionic-team/ionic) - This is the main _Ionic Framework_ repository that is published as `ionic-angular` to npm and by this name included in the `package.json` of newly created Ionic projects. It includes... TODO

* [ionic-app-scripts](https://github.com/ionic-team/ionic-app-scripts) - Ionic _App Scripts_ are "App Build Scripts for Ionic Projects". They are used by the Ionic CLI to do everything that is required to go from a simple `/src` where you type your code in Typescript files to the processed `/www` where you only have a few optimized `.js` files (meaning these tasks: build, clean, cleancss, copy, lint, minify, sass, watch and more).

* <a name="ionic2-app-base"></a> [ionic2-app-base](https://github.com/ionic-team/ionic2-app-base) - Base project for Ionic projects. It includes the stuff that when you start a new Ionic apps is identical in all of them, no matter what [starter template](#ionic-starter-templates) is used. This includes the definition which version of `ionic-angular` is actually used in the project, but also all the other dependencies in `package.json`. It adds the default `config.xml` for Cordova projects, the `src/index.html` that loads all the JS, and the `src/app/main.ts` that is the "entry" point of all the code that gets executed. In `/resources` you also get the default app icons and splash screens.

* [ionic-native](https://github.com/ionic-team/ionic-native) - _Ionic Native_ bridges all the Cordova plugins out there into the Ionic and Angular world. It adds a wrapper around the plugin codes that offers Promises and Observables you can use in your code. Additionally it adds Runtime Diagnostics and Browser Usage support, so you can write mocks for the plugins that work during browser testing.

* [ionic-storage](https://github.com/ionic-team/ionic-storage) - _Ionic Storage_ is a simple key value store made for Ionic, solving many of the storage requirements in common projects. In the background it uses IndexedDB, WebSQL, and LocalStorage and also can use SQLite on native environments where the SQLite Cordova plugin is installed. It uses the excellent [localForage](https://github.com/localForage/localForage) in the background.

* [ionic-module-template](https://github.com/ionic-team/ionic-module-template) - This template could be the base if you decide to build and distribute a reusable module for Ionic.

### Ionic Starter Templates

These templates are downloaded and applied on top of the [ionic2-app-base](#ionic2-app-base) by the CLI when you `ionic start` a project. They contain mainly the code for the pages (`/src/app` and `/src/pages`), sometimes additional things (like assets, a `package.json` with additional dependencies, providers etc.).

* [ionic2-starter-blank](https://github.com/ionic-team/ionic2-starter-blank) - Blank page with some text
* [ionic2-starter-tabs](https://github.com/ionic-team/ionic2-starter-tabs) - 3 tabs with some text
* [ionic2-starter-sidemenu](https://github.com/ionic-team/ionic2-starter-sidemenu) - Sidemenu and some text
* [ionic2-starter-tutorial](https://github.com/ionic-team/ionic2-starter-tutorial) - Template that is used in the [Ionic Tutorial](https://ionicframework.com/docs/intro/tutorial/)
* [ionic-starter-super](https://github.com/ionic-team/ionic-starter-super) - Different kind of pages
* [ionic2-starter-aws](https://github.com/ionic-team/ionic2-starter-aws) - Connects Ionic with AWS Mobile Hub

### Ionic Example Apps

* [ionic-preview-app](https://github.com/ionic-team/ionic-preview-app) - This app is embedded in the [documentation at ionicframework.com](http://ionicframework.com/docs/components/) and shows the usage of components and APIs
* [ionic-conference-app](https://github.com/ionic-team/ionic-conference-app) - "A conference app built with Ionic to demonstrate Ionic" that includes lotfs of real live examples of how to use components and solve specific problems.
* [ionic-unit-testing-example](https://github.com/ionic-team/ionic-unit-testing-example) - You should test your apps. This repository "gives guidance on setting up your Ionic application for unit testing and end-to-end (E2E) testing".
* [ionic-pwa-demos](https://github.com/ionic-team/ionic-pwa-demos) - "A collection of cool Ionic Progressive Web App demos"
* [ionic-image-gallery-app](https://github.com/ionic-team/ionic-image-gallery-app) - "A simple image gallery app built with Ionic and filled with Unsplash photos."
* [ionic-tinder-app](https://github.com/ionic-team/ionic-tinder-app) - "An app showing a UX similar to Tinder implemented in Ionic"
* [ionic-mailbox-app](https://github.com/ionic-team/ionic-mailbox-app) - "A sample app that mimics the user experience of the beloved email client MailBox."
* [ionic-paging-animation-app](https://github.com/ionic-team/ionic-paging-animation-app) - "An Ionic app that shows off a cool pagination effect"
* [ionic2-deeplinks-demo](https://github.com/ionic-team/ionic2-deeplinks-demo) - "A test repo for deep linking in Ionic"
* [ionic-camera-component-demo](https://github.com/ionic-team/ionic-camera-component-demo) - Example projectfr a custom component `<ion-camera>`
* [wkwebview-test-app](https://github.com/ionic-team/wkwebview-test-app) - App that includes and tests a Cordova plugin for WKWebView.

### Ionic Other

* [ionic-themer](https://github.com/ionic-team/ionic-themer) - Super simple [Ionic Theme Generator](https://ionic-theme-creator.herokuapp.com/)
* [ionicons](https://github.com/ionic-team/ionicons) - _Ionicons_ are the "premium icon font for Ionic" and define the look of Ionic you know: By default, they are used everywhere where Icons appear in the apps created by Ionic. Tabbars, Buttons with Icons, Navigation use icons built with this icon font.
* [learn-angular2](https://github.com/ionic-team/learn-angular2) - Ionic switched from AngularJS to Angular, back then still known as Angular2. This repo contains the code for the website [http://learnangular2.com](http://learnangular2.com) that can help you get comfortable with Angular and learn all the stuff that changed.
* [tslint-ionic-rules](https://github.com/ionic-team/tslint-ionic-rules) - "Common TypeScript lint rules/preferences for Ionic."

**Migrate to Ionic from Ionic v1**

Ionic provides a [33 page Migration Guide to Ionic 2 from Ionic v1 (PDF)](http://ionicframework.com/files/Ionic2Migration.pdf) for people with v1 projects. 
* [ionic-migration-demo-v1](https://github.com/ionic-team/ionic-migration-demo-v1) - Ionic v1 project
* [ionic-migration-demo-v2](https://github.com/ionic-team/ionic-migration-demo-v2) - Migrated Ionic project

## Ionic v1

<div class="message">
Note: Ionic v1 is the "old" version of Ionic Framework that is builts on AngularJS.
</div>

* [ionic-v1](https://github.com/ionic-team/ionic-v1) - Here Ionic moved the "old" code of _Ionic v1_ when they released Ionic "2".
* [ionic-app-base](https://github.com/ionic-team/ionic-app-base) - Similar to the ionic2-app-base this is the base project template downloaded by the CLI when you `ionic start` a v1 project.
* [ng-cordova](https://github.com/ionic-team/ng-cordova) - _ngCordova_ is Ionic Native for Ionic v1
* [ionic-code](https://github.com/ionic-team/ionic-code) - Ionic has a CDN for Ionic v1 files at http://code.ionicframework.com
* [ionic-bower](https://github.com/ionic-team/ionic-bower) - Ionic v1 is/was available on [Bower](https://bower.io/)
* [ionic-native-bower](https://github.com/ionic-team/ionic-native-bower) - Makes Ionic Native available via bower for Ionic v1
* [ionic-typescript-example](https://github.com/ionic-team/ionic-typescript-example) - Use TypeScript with Ionic v1 (includes Screencast)

### Ionic v1 Starter Templates

* [ionic-starter-tabs](https://github.com/ionic-team/ionic-starter-tabs)
* [ionic-hello-world](https://github.com/ionic-team/ionic-hello-world)
* [ionic-starter-sidemenu](https://github.com/ionic-team/ionic-starter-sidemenu)
* [ionic-starter-blank](https://github.com/ionic-team/ionic-starter-blank)
* [ionic-starter-salesforce](https://github.com/ionic-team/ionic-starter-salesforce)
* [ionic-starter-maps](https://github.com/ionic-team/ionic-starter-maps)
* [ionic-starter-io](https://github.com/ionic-team/ionic-starter-io) - "An ionic starter project containing the ionic.io services."
* [ionic-starter-deploy](https://github.com/ionic-team/ionic-starter-deploy) - "A starter project with Ionic Deploy"


### Ionic v1 Example Apps

* [ionic-weather](https://github.com/ionic-team/ionic-weather) - "A simple Ionic Weather app"
* [ionic1-deeplinks-demo](https://github.com/ionic-team/ionic1-deeplinks-demo) - Deeplinks demo
* [ionic-third-party-lib-example](https://github.com/ionic-team/ionic-third-party-lib-example) - "how to use third party libs in Ionic"
* [ionic-example-cordova-camera](https://github.com/ionic-team/ionic-example-cordova-camera) - "An example of how to use the Cordova Camera API"
* [front-page](https://github.com/ionic-team/front-page) - "An example Hacker News app showcasing what's possible with Ionic"
* [ionic-firebase-buses](https://github.com/ionic-team/ionic-firebase-buses) - "A bus tracking app for various cities using Ionic and Firebase"
* [chatroom-cordova-ionic-angularjs-firebase](https://github.com/ionic-team/chatroom-cordova-ionic-angularjs-firebase) - "Chat room app built with Cordova, Ionic and Angularjs"
* [ionic-intro](https://github.com/ionic-team/ionic-intro) - "A demo app for showing an intro tutorial for your apps"



### Ionic v1 Other

* [ionic-present](https://github.com/ionic-team/ionic-present) - Source of http://ionicframework.com/present-ionic/, a presentation about Ionic v1

**Contrib / Ion**

* [ionic-ion-drawer](https://github.com/ionic-team/ionic-ion-drawer) - "A side menu drawer for Ionic v1 apps"
* [ionic-ion-tinder-cards](https://github.com/ionic-team/ionic-ion-tinder-cards) - "Add Tinder-style card swiping to any app with this simple Ionic Ion."
* [ionic-ion-swipe-cards](https://github.com/ionic-team/ionic-ion-swipe-cards) - "Swipeable card based layout for Ionic v1"
* [ionic-ion-frost](https://github.com/ionic-team/ionic-ion-frost) - "A reusable frosted-glass effect for adding this cool iOS effect to your Ionic v1 apps."
* [ionic-ion-header-shrink](https://github.com/ionic-team/ionic-ion-header-shrink) - "A demo of making a header that shrinks based on the user scrolling (like Facebook's iOS app)."
* [ionic-contrib-frosted-glass](https://github.com/ionic-team/ionic-contrib-frosted-glass) - "An optional frosted-glass effect for iOS 7 styled Ionic v1 apps."
* [ionic-ion-ios-buttons](https://github.com/ionic-team/ionic-ion-ios-buttons) - "Simple iOS 7 style rounded buttons with CSS"
* [ionic-contrib-firebase-login](https://github.com/ionic-team/ionic-contrib-firebase-login) - "Using Firebase's angularFire and simple login with Ionic"


## Ionic Services / Cloud / Platform

* [ionic-cloud-angular](https://github.com/ionic-team/ionic-cloud-angular) - Use _Ionic Services_ in Ionic/Angular
* [ionic-cloud](https://github.com/ionic-team/ionic-cloud) - Use Ionic Services in Ionic v1/AngularJS
* [ionic-plugin-deploy](https://github.com/ionic-team/ionic-plugin-deploy) - Cordova Plugin for Ionic Deploy / Live Updates
* [ionic-package-hooks](https://github.com/ionic-team/ionic-package-hooks) - "Cordova hooks that you can run in Ionic Package"
* [ionic-view-issues](https://github.com/ionic-team/ionic-view-issues) - _Ionic View_ is the app to show and test apps you `ionic upload`ed to apps.ionic.io. That source code is not open source, but here you can create issues for bugs or feature requests.
* [ionic-cloud-issues](https://github.com/ionic-team/ionic-cloud-issues) # deprecated
* [custom-auth-examples](https://github.com/ionic-team/custom-auth-examples) - ['Custom Auth'](http://docs.ionic.io/services/auth/custom-auth.html) Examples for Ionic Auth
* [platform-client-node](https://github.com/ionic-team/platform-client-node) - Node.js library implementing the [Push Endpoints](https://docs.ionic.io/api/endpoints/push.html) of the Ionic Service HTTP API
* [ionic-error-tracking](https://github.com/ionic-team/ionic-error-tracking) - Future error tracking tool?

## Cordova Plugins

Ionic also offers and creates some Cordova plugins for use in all Cordova projects, not only Ionic.

* [ionic-plugin-keyboard](https://github.com/ionic-team/ionic-plugin-keyboard) - Interacting with the keyboards and get events fired on keyboard changes
* [ionic-plugin-deeplinks](https://github.com/ionic-team/ionic-plugin-deeplinks) - "Handle deeplinks into your Ionic/Cordova apps from Universal Links, App Links, and Custom URL schemes."
* [cordova-plugin-ios-keychain](https://github.com/ionic-team/cordova-plugin-ios-keychain) - Access the iOS keychain
* [cordova-camera-roll](https://github.com/ionic-team/cordova-camera-roll) - "The Cordova Camera Roll plugin makes it easy to read from the iOS camera roll."
* [cordova-plugin-localstorage-backup](https://github.com/ionic-team/cordova-plugin-localstorage-backup) - Backup your local storage to the device
* [cordova-plugin-wkwebview-engine](https://github.com/ionic-team/cordova-plugin-wkwebview-engine) - "This plugin makes Cordova use the `WKWebView` component instead of the default `UIWebView` component"
* [cordova-plugin-template](https://github.com/ionic-team/cordova-plugin-template) - "simple starting point for building a Cordova plugin on iOS and Android"

## Ionic Creator

[Ionic Creator](https://creator.ionic.io/) is a nifty WYSIWYG editor for [Ionic v1](#ionic-v1) that you can use to click your interface and then back it with code.

* [creator-weekly-workshops](https://github.com/ionic-team/creator-weekly-workshops) -
* [creator-code-todo-demo](https://github.com/ionic-team/creator-code-todo-demo) -

## Deprecated

* [ionic2](https://github.com/ionic-team/ionic2) - Former home of Ionic 2
* [ionic-box](https://github.com/ionic-team/ionic-box) - "A Vagrant install for Android, Cordova, and Ionic v1"
* [ionic-gulp-tasks](https://github.com/ionic-team/ionic-gulp-tasks) - "Collection of gulp tasks for building Ionic apps"
* [ionic-learn](https://github.com/ionic-team/ionic-learn) - once was learn.ionicframework.com
* [ionitron-issues](https://github.com/ionic-team/ionitron-issues) - "A custom issue tracker for GitHub with issue ranking/scoring, and bot templated responses"
* [ionic-push-issues](https://github.com/ionic-team/ionic-push-issues) - "A repo for filing and getting push notification help."
* [ionic2-starter](https://github.com/ionic-team/ionic2-starter) - "An Ionic2 starter project"
* [ionic-starter-cardboard](https://github.com/ionic-team/ionic-starter-cardboard) - "A google cardboard template for Ionic"
* [ionic-angular-cordova-seed](https://github.com/ionic-team/ionic-angular-cordova-seed) - "The perfect starting point for an Ionic v1 project"
* [ionic-lab-issues](https://github.com/ionic-team/ionic-lab-issues) - "Issues to track for the Ionic Lab project."

**Old Ionic Services**

* [ionic-platform-web-client](https://github.com/ionic-team/ionic-platform-web-client) - Precursor to `@ionic/cloud`
* [ionic-service-analytics](https://github.com/ionic-team/ionic-service-analytics) - Precursor of `ionic-platform-web-client`
* [ionic-push-tutorial-app](https://github.com/ionic-team/ionic-push-tutorial-app) - "
Companion app to the Ionic Push startup guide."
* [ionic-service-push-client](https://github.com/ionic-team/ionic-service-push-client) - "Client-side code for the ionic push service"
* [ionic-starter-push](https://github.com/ionic-team/ionic-starter-push) - Start for Ionic Push
* [ionic-service-core](https://github.com/ionic-team/ionic-service-core) - "Common required service tools and addons"
* [ionic-service-deploy](https://github.com/ionic-team/ionic-service-deploy) - "Update service for Ionic"
* [deploy-tutorial](https://github.com/ionic-team/deploy-tutorial) - "Companion app to the Ionic Deploy tutorial"
* [ionic-starter-analytics](https://github.com/ionic-team/ionic-starter-analytics) - "Your basic Ionic starter app, plus analytics"
* [ionic-default-resources](https://github.com/ionic-team/ionic-default-resources) - "Default resources for icons and splash screens"

**CLI v2**

With the release of Ionic CLI v3 these two repositories are not needed any more as a rewrite of them is now part of the CLI itself:

* [ionic-app-lib](https://github.com/ionic-team/ionic-app-lib)
* [ionic-app-generators](https://github.com/ionic-team/ionic-app-generators)


## Other

### Internal

* [ionicate](https://github.com/ionic-team/ionicate) - Internal Survey for apps.ionic.io
* [ionic-precommit-hooks](https://github.com/ionic-team/ionic-precommit-hooks) - "Runs the test for Ionic 2."
* [ionic-cz-conventional-changelog](https://github.com/ionic-team/ionic-cz-conventional-changelog) - "A commitizen adapter"
* [ionic-issue-submit](https://github.com/ionic-team/ionic-issue-submit) - [Submit issue form](http://ionicframework.com/submit-issue/), see: [http://blog.ionic.io/how-ionic-uses-github-better/](http://blog.ionic.io/how-ionic-uses-github-better/)
* [ionitron-lingo](https://github.com/ionic-team/ionitron-lingo) - "teaching Ionitron to speak"
* [gulp-angular-seed](https://github.com/ionic-team/gulp-angular-seed) - "A simple starting project for JS utilities that use Angular and want to build with Gulp"
* [ionic-workshop-london](https://github.com/ionic-team/ionic-workshop-london) - "Workshop for AngularConnect"
* [api-tester](https://github.com/ionic-team/api-tester) - "Simple node.js server that mirrors responses back"


### Abandoned, Unkown

* [ionic-closure](https://github.com/ionic-team/ionic-closure) - Closure Experiment
* [ionic-web-analytics](https://github.com/ionic-team/ionic-web-analytics) - "Express middleware for sending web analytics to BigQuery"
* [ionic-heroku-button](https://github.com/ionic-team/ionic-heroku-button) - "A one-click Ionic v1 app template for Heroku"
* [ionic-scripts](https://github.com/ionic-team/ionic-scripts) - "ionic-scripts is a set of scripts/utilities to help ionic 2 app development"
* [ionic-bootstrap-theme-generator](https://github.com/ionic-team/ionic-bootstrap-theme-generator) - "[Generate an Ionic theme from a bootstrap theme](https://ionic-bootstrap-theme.herokuapp.com/)"
* [eslint-config-ionic](https://github.com/ionic-team/eslint-config-ionic) - "Common eslint rules/preferences for Ionic."
* [jetstrap-docs](https://github.com/ionic-team/jetstrap-docs)
* [ionicons-wp](https://github.com/ionic-team/ionicons-wp) - "Official Ionicons WordPress Plugin"
* [ionic-workshop](https://github.com/ionic-team/ionic-workshop) - "Ionic Workshop"
* [appcamp-issues](https://github.com/ionic-team/appcamp-issues) - "Issues for the Appcamp project"
* [collide](https://github.com/ionic-team/collide) - "A powerful javascript animation engine for web and hybrid mobile apps, inspired by Facebook Pop"
* [lazy-loading-poc](https://github.com/ionic-team/lazy-loading-poc) - "Lazy loading POC"
* [ionic-io-docs](https://github.com/ionic-team/ionic-io-docs) - "Ionic.io Docs Site"
* [ionic-io-testers](https://github.com/ionic-team/ionic-io-testers)
* [ionic-proxy-example](https://github.com/ionic-team/ionic-proxy-example) - "A quick Ionic project showing how to use the proxy server"
* [ionic-starter-tests](https://github.com/ionic-team/ionic-starter-tests) - "A test of different kinds of page navigation"
* [ionic-starter-complex-list](https://github.com/ionic-team/ionic-starter-complex-list) - "A complex list starter template"
* [ionic-theme-server](https://github.com/ionic-team/ionic-theme-server) - "A theme server for building and serving Ionic SASS themes with set variables"
* [go-utils](https://github.com/ionic-team/go-utils) - "Common Go Utils for go programs"
* [cordova-plugin-discovery](https://github.com/ionic-team/cordova-plugin-discovery) - "Network discovery plugin for iOS and Android Cordova apps"
* [ionic-cordova-wrapper](https://github.com/ionic-team/ionic-cordova-wrapper) - "A empty wrapping project for an Ionic app that uses Cordova"
* [ngMad](https://github.com/ionic-team/ngMad) - "Homepage for the Madison Angular Meetup Group"
* [ionic-todo](https://github.com/ionic-team/ionic-todo)
* [django-template](https://github.com/ionic-team/django-template) - "Generates cordova/phonegap splash screen images for multiple platforms given a logo and background color/image."
* [cordova-splash-generator](https://github.com/ionic-team/cordova-splash-generator)
* [ionic-tutorial-status-fade](https://github.com/ionic-team/ionic-tutorial-status-fade) - "A simple fading statusbar as seen on the Facebook app on iOS 7"
* [jqm-neue](https://github.com/ionic-team/jqm-neue) - "A slightly tweaked default jQuery Mobile theme."
* [graphite](https://github.com/ionic-team/graphite) - "Clean jQuery Mobile theme-pack and theme generator"
* [jquerymobile-tabbar](https://github.com/ionic-team/jquerymobile-tabbar) - "An easier to use NavBar control for jQuery Mobile apps"
* [jqm-plain](https://github.com/ionic-team/jqm-plain) - "A fork of jQuery Mobile with one swatch and a simple, default theme."


### Forks
* [repool](https://github.com/ionic-team/repool) - "RethinkDB connection pool"
* [cordova-plugin-inapppurchase](https://github.com/ionic-team/cordova-plugin-inapppurchase) - "A lightweight cordova plugin for in app purchases on iOS/Android"
* [localForage-cordovaSQLiteDriver](https://github.com/ionic-team/localForage-cordovaSQLiteDriver) - "SQLite driver for Cordova apps using localForage"
* [reactionic](https://github.com/ionic-team/reactionic) - "React Ionic"
* [cordova-plugin-statusbar](https://github.com/ionic-team/cordova-plugin-statusbar) - "The StatusBar object provides some functions to customize the iOS and Android StatusBar."
* [cordova-lib](https://github.com/ionic-team/cordova-lib) - `cordova-lib`
* [storm](https://github.com/ionic-team/storm) - "Apache Storm"
* [heroku-buildpack-sphinx](https://github.com/ionic-team/heroku-buildpack-sphinx)
* [heroku-buildpack-python](https://github.com/ionic-team/heroku-buildpack-python)
* [nginx-buildpack](https://github.com/ionic-team/nginx-buildpack) - "Run NGINX (with SSL) in front of your app server on Heroku"
* [heroku-buildpack-multi](https://github.com/ionic-team/heroku-buildpack-multi) - "Composable buildpacks"
* [electron-builder](https://github.com/ionic-team/electron-builder) - "Build installers for Electron apps the easy way"
* [usemin-lib](https://github.com/ionic-team/usemin-lib) - "Replaces references to non-optimized scripts or stylesheets into a set of HTML files (or any templates/views)"
* [node-xcode](https://github.com/ionic-team/node-xcode) - "tools and utilities for working with xcode/ios projects"
* [heroku-buildpack-nodejs-gulp](https://github.com/ionic-team/heroku-buildpack-nodejs-gulp) - "A slightly modified version of Heroku's official Node.js buildpack with added gulp.js support"
* [gulp-electron](https://github.com/ionic-team/node-js-getting-started) - "Getting Started with Node on Heroku"
* [gulp-electron](https://github.com/ionic-team/gulp-electron) - "A gulp plugin for atom-shell distribute applications"
* [bonjour](https://github.com/ionic-team/bonjour) - "A Bonjour/Zeroconf protocol implementation in JavaScript"
* [cordova-plugin-keyboard](https://github.com/ionic-team/cordova-plugin-keyboard) - "Keyboard Plugin for Cordova"
* [cordova-android](https://github.com/ionic-team/cordova-android) - `cordova-android`
* [cordova-crosswalk-engine](https://github.com/ionic-team/cordova-crosswalk-engine) - "Proof of Concept Third Party Web Engine using Crosswalk"
* [standard](https://github.com/ionic-team/standard) - "JavaScript Standard Style — One Style to Rule Them All"
* [tiny-lr](https://github.com/ionic-team/tiny-lr) - "tiny livereload"
* [InstagramPlugin](https://github.com/ionic-team/InstagramPlugin) - "Instagram plugin for PhoneGap/Cordova"
* [opbeat-node](https://github.com/ionic-team/opbeat-node) - "A Node.js client for Opbeat"
* [docker-consul](https://github.com/ionic-team/docker-consul) - "Dockerized Consul Agent"
* [gosass](https://github.com/ionic-team/gosass) - "Go language wrapper for LibSass"
* [discourse](https://github.com/ionic-team/discourse) - "A platform for community discussion."
