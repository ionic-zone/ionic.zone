---
title: An Overview of Ionic's Github Repositories
date: 2017-05-12 17:15:00 Z
---

# An Overview of Ionic's Github Repositories

If you develop applications using Ionic Framework you will - sooner or later - come into contact with one of its Github repositories. When looking for how to do something, it is sometimes easier to look into and search the code directly on Github where it is versioned and easily searchable, than to limit yourself to what you have available locally. Fortunately, all components of Ionic are developed in the open. At the latest when something doesn't work as expected and it really isn't user error, you end up at the issue's of the project or even submitting a Pull Request fixing the bug you encountered.

But [Ionic, or better Driftyco](https://github.com/driftyco), the Github organization (and also [the company behind Ionic development](https://ionicframework.com/about)) that hosts and collects all the repositories, has a loooot of Github repositories, more than 150 in fact. What is which and needed why?

This post gives you an overview of all these repositories. For that, I went through all of them, grouped them and added some description and explanation of their use - on non-use for older and obsolete ones.

## General Ionic

* [https://github.com/driftyco/ionic-cli](https://github.com/driftyco/ionic-cli) - The Ionic Command Line Interface (CLI) is what everybody that works with Ionic installs as one of the first steps with `npm install -g ionic`. It is the base that enables you to `ionic start` projects, `ionic serve` them in the local browser to test them and `ionic cordova build` to build them into Cordova wrapped native apps for mobile - and so much more.

* [https://github.com/driftyco/ionic-site](https://github.com/driftyco/ionic-site) - If you visit [ionicframework.com](https://ionicframework.com) you see the contents and results of this repository. It's a Jekyll site that grew out of the humble beginnings when the Ionic website was still hosted on Github Pages. The content is pulled in from the different repositories (ionic, ionicv1, ionic-native and others) to create this one big documentation.

  * [https://github.com/driftyco/ionic-preview-app](https://github.com/driftyco/ionic-preview-app) - One other repository pulled in is the `ionic-preview-app` that is used to create the live previews of how different UI components actually look on [http://ionicframework.com/docs/components/](http://ionicframework.com/docs/components/)

* [https://github.com/driftyco/ionicons](https://github.com/driftyco/ionicons) - Ionicons are the "premium icon font for Ionic" and define the look of Ionic you know: By default, they are used everywhere where Icons appear in the apps created by Ionic. Tabbars, Buttons with Icons, Navigation use icons built with this icon font.

Note: What I call just "Ionic" in the following paragraphs and lists was formerly known as Ionic 2. But Ionic quickly followed up with Ionic 3 and is working hard on the next iterations - so it makes more sense to call is just Ionic. The older iteration of the Framework that was built on AngularJS (instead of Angular for the current Ionic) is now known as "Ionic v1" and referred as such here.

## Ionic

* [https://github.com/driftyco/ionic](https://github.com/driftyco/ionic) - This is the main Ionic Framework repository that is published as `ionic-angular` to npm and by this name included in the `package.json` of newly created Ionic projects. It includes... TODO

* [https://github.com/driftyco/ionic-app-scripts](https://github.com/driftyco/ionic-app-scripts) - Ionic App Scripts are "App Build Scripts for Ionic Projects". They are used by the Ionic CLI to do everything that is required to go from a simple `/src` where you type your code in Typescript files to the processed `/www` where you only have a few optimized `.js` files (meaning these tasks: build, clean, cleancss, copy, lint, minify, sass, watch and more).

* [https://github.com/driftyco/ionic2-app-base](https://github.com/driftyco/ionic2-app-base) - Pure base project for Ionic projects. It includes the stuff that when you start a new Ionic apps is identical in all of them, no matter what starter template (see below) is used. This includes the definition which version of `ionic-angular` is actually used in the project, but also all the other dependencies in `package.json`. It adds the default `config.xml` for Cordova projects, the `src/index.html` that loads all the JS, and the `src/app/main.ts` that is the "entry" point of all the code that gets executed. In `/resources` you also get the default app icons and splash screens.

* [https://github.com/driftyco/ionic-native](https://github.com/driftyco/ionic-native) - Ionic Native bridges all the Cordova plugins out there into the Ionic and Angular world. It adds a wrapper around the plugin codes that offers Promises and Observables you can use in your code. Additionally it adds Runtime Diagnostics and Browser Usage support, so you can write mocks for the plugins that work during browser testing.

* [https://github.com/driftyco/ionic-storage](https://github.com/driftyco/ionic-storage) - Ionic Storage is a simple key value store made for Ionic, solving many of the storage requirements in common projects. In the background it uses IndexedDB, WebSQL, and LocalStorage and also can use SQLite on native environments where the SQLite Cordova plugin is installed. It uses the excellent [localForage](https://github.com/localForage/localForage) in the background.

* [https://github.com/driftyco/ionic-module-template](https://github.com/driftyco/ionic-module-template) - This template could be the base if you decide to build and distribute a reusable module for Ionic.

### Ionic Starter Templates

These templates are downloaded and applied on top of the app-base by the CLI when you `ionic start` a project. They only contain the code for the pages (`/src/app` and `/src/pages`), sometimes additional things (like assets, a `package.json` with additional dependencies, providers etc.).

* [https://github.com/driftyco/ionic2-starter-blank](https://github.com/driftyco/ionic2-starter-blank) - Blank page with some text

* [https://github.com/driftyco/ionic2-starter-tabs](https://github.com/driftyco/ionic2-starter-tabs) - 3 Tabs with some text

* [https://github.com/driftyco/ionic2-starter-sidemenu](https://github.com/driftyco/ionic2-starter-sidemenu) - Sidemenu and some text

* [https://github.com/driftyco/ionic2-starter-tutorial](https://github.com/driftyco/ionic2-starter-tutorial) - Template that is used in the [Ionic Tutorial in the docs](https://ionicframework.com/docs/intro/tutorial/)

* [https://github.com/driftyco/ionic-starter-super](https://github.com/driftyco/ionic-starter-super) - Different kind of pages

* [https://github.com/driftyco/ionic2-starter-aws](https://github.com/driftyco/ionic2-starter-aws) - Connects Ionic with AWS Mobile Hub

### Ionic Example Apps

* [https://github.com/driftyco/ionic-conference-app](https://github.com/driftyco/ionic-conference-app) - 

* [https://github.com/driftyco/ionic-unit-testing-example](https://github.com/driftyco/ionic-unit-testing-example) - You should test your apps. 

* [https://github.com/driftyco/ionic-pwa-demos](https://github.com/driftyco/ionic-pwa-demos) - 

* [https://github.com/driftyco/ionic-image-gallery-app](https://github.com/driftyco/ionic-image-gallery-app) - 

* [https://github.com/driftyco/ionic-tinder-app](https://github.com/driftyco/ionic-tinder-app) - 

* [https://github.com/driftyco/ionic-mailbox-app](https://github.com/driftyco/ionic-mailbox-app) - 

* [https://github.com/driftyco/ionic-paging-animation-app](https://github.com/driftyco/ionic-paging-animation-app) - 

* [https://github.com/driftyco/ionic2-deeplinks-demo](https://github.com/driftyco/ionic2-deeplinks-demo) - 

* [https://github.com/driftyco/ionic-camera-component-demo](https://github.com/driftyco/ionic-camera-component-demo) - 

### Ionic Other

* [https://github.com/driftyco/ionic-themer](https://github.com/driftyco/ionic-themer) - Super simple [Ionic Theme Generator](https://ionic-theme-creator.herokuapp.com/)

## Ionic v1

* [https://github.com/driftyco/ionic-v1](https://github.com/driftyco/ionic-v1) - Here Ionic moved the "old" code of Ionic v1 when they released Ionic "2".

* [https://github.com/driftyco/ionic-app-base](https://github.com/driftyco/ionic-app-base) - Similar to the ionic2-app-base this is the base project template downloaded by the CLI when you `ionic start` a v1 project.

* [https://github.com/driftyco/ng-cordova](https://github.com/driftyco/ng-cordova) - ng-cordova is Ionic Native for Ionic v1

* [https://github.com/driftyco/ionic-code](https://github.com/driftyco/ionic-code) - Ionic has a CDN for Ionic v1 files at http://code.ionicframework.com

* [https://github.com/driftyco/ionic-bower](https://github.com/driftyco/ionic-bower) - Ionic v1 is/was available on [Bower](https://bower.io/)

* [https://github.com/driftyco/ionic-native-bower](https://github.com/driftyco/ionic-native-bower) - Makes Ionic Native available via bower for Ionic v1

* [https://github.com/driftyco/ionic-typescript-example](https://github.com/driftyco/ionic-typescript-example) - Use TypeScript with Ionic v1 (includes Screencast)

### Ionic v1 Starter Templates

* [https://github.com/driftyco/ionic-starter-tabs](https://github.com/driftyco/ionic-starter-tabs) - 

* [https://github.com/driftyco/ionic-hello-world](https://github.com/driftyco/ionic-hello-world) - 

* [https://github.com/driftyco/ionic-starter-sidemenu](https://github.com/driftyco/ionic-starter-sidemenu) - 

* [https://github.com/driftyco/ionic-starter-blank](https://github.com/driftyco/ionic-starter-blank) - 

* [https://github.com/driftyco/ionic-starter-salesforce](https://github.com/driftyco/ionic-starter-salesforce) - 

* [https://github.com/driftyco/ionic-starter-maps](https://github.com/driftyco/ionic-starter-maps) - 

### Ionic v1 Example Apps

* [https://github.com/driftyco/ionic-weather](https://github.com/driftyco/ionic-weather) - 

* [https://github.com/driftyco/ionic1-deeplinks-demo](https://github.com/driftyco/ionic1-deeplinks-demo) - 

* [https://github.com/driftyco/ionic-push-tutorial-app](https://github.com/driftyco/ionic-push-tutorial-app) - 

* [https://github.com/driftyco/ionic-third-party-lib-example](https://github.com/driftyco/ionic-third-party-lib-example) - "An example App showing how to use third party libs in Ionic"

### Migrate Ionic v1 to Ionic

* [https://github.com/driftyco/ionic-migration-demo-v1](https://github.com/driftyco/ionic-migration-demo-v1) - 

* [https://github.com/driftyco/ionic-migration-demo-v2](https://github.com/driftyco/ionic-migration-demo-v2) - 

### Ionic v1 Contrib / Ion

* [https://github.com/driftyco/ionic-ion-drawer](https://github.com/driftyco/ionic-ion-drawer) - 

* [https://github.com/driftyco/ionic-ion-tinder-cards](https://github.com/driftyco/ionic-ion-tinder-cards) - 

* [https://github.com/driftyco/ionic-ion-swipe-cards](https://github.com/driftyco/ionic-ion-swipe-cards) - 

* [https://github.com/driftyco/ionic-ion-frost](https://github.com/driftyco/ionic-ion-frost) - 

* [https://github.com/driftyco/ionic-ion-header-shrink](https://github.com/driftyco/ionic-ion-header-shrink) - 

* [https://github.com/driftyco/ionic-contrib-frosted-glass](https://github.com/driftyco/ionic-contrib-frosted-glass) - 

## Ionic Services / Cloud / Platform

* [https://github.com/driftyco/ionic-cloud-angular](https://github.com/driftyco/ionic-cloud-angular) - Use Ionic Services in Ionic/Angular

* [https://github.com/driftyco/ionic-cloud](https://github.com/driftyco/ionic-cloud) - Use Ionic Services in Ionic v1/AngularJS

* [https://github.com/driftyco/ionic-plugin-deploy](https://github.com/driftyco/ionic-plugin-deploy) - Cordova Plugin for Ionic Deploy / Live Updates

* [https://github.com/driftyco/ionic-package-hooks](https://github.com/driftyco/ionic-package-hooks) - "Cordova hooks that you can run in Ionic Package"

* [https://github.com/driftyco/ionic-view-issues](https://github.com/driftyco/ionic-view-issues) - Ionic View is the app to show and test apps you `ionic upload`ed to apps.ionic.io. That source code is not open source, but here you can create issues for bugs or feature requests.

* [https://github.com/driftyco/ionic-cloud-issues](https://github.com/driftyco/ionic-cloud-issues) # deprecated

* [https://github.com/driftyco/custom-auth-examples](https://github.com/driftyco/custom-auth-examples) - ['Custom Auth'](http://docs.ionic.io/services/auth/custom-auth.html) Examples for Ionic Auth

* [https://github.com/driftyco/platform-client-node](https://github.com/driftyco/platform-client-node) - Node.js library implementing the [Push Endpoints](https://docs.ionic.io/api/endpoints/push.html) of the Ionic Service HTTP API

## Cordova Plugins

Ionic also offers and creates some Cordova plugins for use in all Cordova projects, not only Ionic.

* [https://github.com/driftyco/ionic-plugin-keyboard](https://github.com/driftyco/ionic-plugin-keyboard) - Interacting with the keyboards and get events fire on keyboard changes

* [https://github.com/driftyco/ionic-plugin-deeplinks](https://github.com/driftyco/ionic-plugin-deeplinks) - "Handle deeplinks into your Ionic/Cordova apps from Universal Links, App Links, and Custom URL schemes."

* [https://github.com/driftyco/cordova-plugin-wkwebview-engine](https://github.com/driftyco/cordova-plugin-wkwebview-engine) - "This plugin makes Cordova use the `WKWebView` component instead of the default `UIWebView` component"

  * [https://github.com/driftyco/wkwebview-test-app](https://github.com/driftyco/wkwebview-test-app) - ... and a Ionic app testing this

* [https://github.com/driftyco/cordova-plugin-ios-keychain](https://github.com/driftyco/cordova-plugin-ios-keychain) - Access the iOS keychain

* [https://github.com/driftyco/cordova-camera-roll](https://github.com/driftyco/cordova-camera-roll) - "The Cordova Camera Roll plugin makes it easy to read from the iOS camera roll."

* [https://github.com/driftyco/cordova-plugin-localstorage-backup](https://github.com/driftyco/cordova-plugin-localstorage-backup) - Backup your local storage to the device

## Ionic Creator

Ionic Creator is a nifty WYSIWYG editor for Ionic v1 that you can use to click your interface and then back it with code.

* [https://github.com/driftyco/creator-weekly-workshops](https://github.com/driftyco/creator-weekly-workshops) - 

* [https://github.com/driftyco/creator-code-todo-demo](https://github.com/driftyco/creator-code-todo-demo) - 

## Other

* [https://github.com/driftyco/learn-angular2](https://github.com/driftyco/learn-angular2) - Ionic 2 switched from AngularJS to Angular, back then still known as Angular2. This repo contains the code for the website [http://learnangular2.com](http://learnangular2.com/) that can help you get comfortable with Angular and learn all the stuff that changed.

## Deprecated

### CLI v2

With the release of Ionic CLI v3 these two repositories are not needed any more as a rewrite of them is now part of the CLI itself:

* [https://github.com/driftyco/ionic-app-lib](https://github.com/driftyco/ionic-app-lib) - 

* [https://github.com/driftyco/ionic-app-generators](https://github.com/driftyco/ionic-app-generators) - 

## Internal / Unrelated / Abandoned / Not Relevant / Very Old

* https://github.com/driftyco/ionicate = Internal Survey for apps.ionic.io

* https://github.com/driftyco/ionic2 = Former home of Ionic 2

* https://github.com/driftyco/ionic-closure = Closure Experiment

* https://github.com/driftyco/repool

* https://github.com/driftyco/ionic-box

* https://github.com/driftyco/ionic-web-analytics

* https://github.com/driftyco/ionic-precommit-hooks

* https://github.com/driftyco/cordova-plugin-inapppurchase

* https://github.com/driftyco/ionic-gulp-tasks

* https://github.com/driftyco/tslint-ionic-rules

* https://github.com/driftyco/ionic-heroku-button

* https://github.com/driftyco/localForage-cordovaSQLiteDriver

* https://github.com/driftyco/ionic-scripts

* https://github.com/driftyco/ionic-platform-web-client

* https://github.com/driftyco/reactionic

* https://github.com/driftyco/cordova-plugin-statusbar

* https://github.com/driftyco/ionic-bootstrap-theme-generator

* https://github.com/driftyco/cordova-plugin-template

* https://github.com/driftyco/eslint-config-ionic

* https://github.com/driftyco/ionic-learn

* https://github.com/driftyco/ionic-present

* https://github.com/driftyco/cordova-lib

* https://github.com/driftyco/ionitron-issues

* https://github.com/driftyco/ionic-service-analytics

* https://github.com/driftyco/ionic-cz-conventional-changelog

* https://github.com/driftyco/ionic-issue-submit

* https://github.com/driftyco/ionic-push-issues

* https://github.com/driftyco/storm

* https://github.com/driftyco/heroku-buildpack-sphinx

* https://github.com/driftyco/heroku-buildpack-python

* https://github.com/driftyco/jetstrap-docs

* https://github.com/driftyco/ionitron-lingo

* https://github.com/driftyco/gulp-angular-seed

* https://github.com/driftyco/ionic2-starter

* https://github.com/driftyco/nginx-buildpack

* https://github.com/driftyco/ionicons-wp

* https://github.com/driftyco/ionic-starter-cardboard

* https://github.com/driftyco/ionic-workshop-london

* https://github.com/driftyco/ionic-service-push-client

* https://github.com/driftyco/ionic-starter-push

* https://github.com/driftyco/ionic-service-core

* https://github.com/driftyco/ionic-service-deploy

* https://github.com/driftyco/heroku-buildpack-multi

* https://github.com/driftyco/ionic-workshop

* https://github.com/driftyco/deploy-tutorial

* https://github.com/driftyco/appcamp-issues

* https://github.com/driftyco/electron-builder

* https://github.com/driftyco/ionic-angular-cordova-seed

* https://github.com/driftyco/usemin-lib

* https://github.com/driftyco/node-xcode

* https://github.com/driftyco/ionic-lab-issues

* https://github.com/driftyco/heroku-buildpack-nodejs-gulp

* https://github.com/driftyco/collide

* https://github.com/driftyco/api-tester

* https://github.com/driftyco/node-js-getting-started

* https://github.com/driftyco/gulp-electron

* https://github.com/driftyco/ionic-starter-analytics

## Unsorted

https://github.com/driftyco/ionic-example-cordova-camera
https://github.com/driftyco/ionic-starter-io
https://github.com/driftyco/ionic-starter-deploy
https://github.com/driftyco/ionic-io-docs
https://github.com/driftyco/cordova-android
https://github.com/driftyco/cordova-crosswalk-engine
https://github.com/driftyco/ionic-io-testers
https://github.com/driftyco/ionic-default-resources
https://github.com/driftyco/standard
https://github.com/driftyco/tiny-lr
https://github.com/driftyco/InstagramPlugin
https://github.com/driftyco/ionic-proxy-example
https://github.com/driftyco/opbeat-node
https://github.com/driftyco/front-page
https://github.com/driftyco/ionic-starter-tests
https://github.com/driftyco/ionic-starter-complex-list
https://github.com/driftyco/docker-consul
https://github.com/driftyco/ionic-ion-ios-buttons
https://github.com/driftyco/ionic-theme-server
https://github.com/driftyco/gosass
https://github.com/driftyco/go-utils
https://github.com/driftyco/cordova-plugin-discovery
https://github.com/driftyco/ionic-cordova-wrapper
https://github.com/driftyco/ionic-contrib-firebase-login
https://github.com/driftyco/ngMad
https://github.com/driftyco/ionic-todo
https://github.com/driftyco/ionic-firebase-buses
https://github.com/driftyco/chatroom-cordova-ionic-angularjs-firebase
https://github.com/driftyco/django-template
https://github.com/driftyco/cordova-splash-generator
https://github.com/driftyco/ionic-intro
https://github.com/driftyco/ionic-tutorial-status-fade
https://github.com/driftyco/discourse
https://github.com/driftyco/jqm-neue
https://github.com/driftyco/graphite
https://github.com/driftyco/jquerymobile-tabbar
https://github.com/driftyco/jqm-plain