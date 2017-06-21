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
Note: What I call just "Ionic" in the following paragraphs and lists was formerly known as Ionic 2. But Ionic quickly followed up with Ionic 3 and is working hard on the next iterations - so it makes more sense to call is just Ionic. The older iteration of the Framework that was built on AngularJS (instead of Angular for the current Ionic) is now known as "Ionic v1" and referred as such here.
</div>

* [ionic ![Github Stars](https://img.shields.io/github/stars/ionic-team/ionic.svg?style=flat&label=Github%20Stars)](https://github.com/ionic-team/ionic) - This is the main _Ionic Framework_ repository that is published as `ionic-angular` to npm and by this name included in the `package.json` of newly created Ionic projects. It includes... TODO

* [ionic-app-scripts ![Github Stars](https://img.shields.io/github/stars/ionic-team/ionic-app-scripts.svg?style=flat&label=Github%20Stars)](https://github.com/ionic-team/ionic-app-scripts) - Ionic _App Scripts_ are "App Build Scripts for Ionic Projects". They are used by the Ionic CLI to do everything that is required to go from a simple `/src` where you type your code in Typescript files to the processed `/www` where you only have a few optimized `.js` files (meaning these tasks: build, clean, cleancss, copy, lint, minify, sass, watch and more).

* [ionic2-app-base](https://github.com/ionic-team/ionic2-app-base) - Pure base project for Ionic projects. It includes the stuff that when you start a new Ionic apps is identical in all of them, no matter what starter template (see below) is used. This includes the definition which version of `ionic-angular` is actually used in the project, but also all the other dependencies in `package.json`. It adds the default `config.xml` for Cordova projects, the `src/index.html` that loads all the JS, and the `src/app/main.ts` that is the "entry" point of all the code that gets executed. In `/resources` you also get the default app icons and splash screens.

* [ionic-native](https://github.com/ionic-team/ionic-native) - _Ionic Native_ bridges all the Cordova plugins out there into the Ionic and Angular world. It adds a wrapper around the plugin codes that offers Promises and Observables you can use in your code. Additionally it adds Runtime Diagnostics and Browser Usage support, so you can write mocks for the plugins that work during browser testing.

* [ionic-storage](https://github.com/ionic-team/ionic-storage) - _Ionic Storage_ is a simple key value store made for Ionic, solving many of the storage requirements in common projects. In the background it uses IndexedDB, WebSQL, and LocalStorage and also can use SQLite on native environments where the SQLite Cordova plugin is installed. It uses the excellent [localForage](https://github.com/localForage/localForage) in the background.

* [ionic-module-template](https://github.com/ionic-team/ionic-module-template) - This template could be the base if you decide to build and distribute a reusable module for Ionic.

### Ionic Starter Templates

These templates are downloaded and applied on top of the ionic2-app-base by the CLI when you `ionic start` a project. They contain only the code for the pages (`/src/app` and `/src/pages`), sometimes additional things (like assets, a `package.json` with additional dependencies, providers etc.).

* [ionic2-starter-blank](https://github.com/ionic-team/ionic2-starter-blank) - Blank page with some text
* [ionic2-starter-tabs](https://github.com/ionic-team/ionic2-starter-tabs) - 3 tabs with some text
* [ionic2-starter-sidemenu](https://github.com/ionic-team/ionic2-starter-sidemenu) - Sidemenu and some text
* [ionic2-starter-tutorial](https://github.com/ionic-team/ionic2-starter-tutorial) - Template that is used in the [Ionic Tutorial](https://ionicframework.com/docs/intro/tutorial/)
* [ionic-starter-super](https://github.com/ionic-team/ionic-starter-super) - Different kind of pages
* [ionic2-starter-aws](https://github.com/ionic-team/ionic2-starter-aws) - Connects Ionic with AWS Mobile Hub

### Ionic Example Apps

* [ionic-preview-app](https://github.com/ionic-team/ionic-preview-app) - embedded in docs
* [ionic-conference-app](https://github.com/ionic-team/ionic-conference-app) -
* [ionic-unit-testing-example](https://github.com/ionic-team/ionic-unit-testing-example) - You should test your apps.
* [ionic-pwa-demos](https://github.com/ionic-team/ionic-pwa-demos) -
* [ionic-image-gallery-app](https://github.com/ionic-team/ionic-image-gallery-app) -
* [ionic-tinder-app](https://github.com/ionic-team/ionic-tinder-app) -
* [ionic-mailbox-app](https://github.com/ionic-team/ionic-mailbox-app) -
* [ionic-paging-animation-app](https://github.com/ionic-team/ionic-paging-animation-app) -
* [ionic2-deeplinks-demo](https://github.com/ionic-team/ionic2-deeplinks-demo) -
* [ionic-camera-component-demo](https://github.com/ionic-team/ionic-camera-component-demo) -
* [wkwebview-test-app](https://github.com/ionic-team/wkwebview-test-app) - App that includes and tests a Cordova plugin listed below.

### Ionic Other

* [ionic-themer](https://github.com/ionic-team/ionic-themer) - Super simple [Ionic Theme Generator](https://ionic-theme-creator.herokuapp.com/)
* [ionicons](https://github.com/ionic-team/ionicons) - _Ionicons_ are the "premium icon font for Ionic" and define the look of Ionic you know: By default, they are used everywhere where Icons appear in the apps created by Ionic. Tabbars, Buttons with Icons, Navigation use icons built with this icon font.
* [learn-angular2](https://github.com/ionic-team/learn-angular2) - Ionic switched from AngularJS to Angular, back then still known as Angular2. This repo contains the code for the website [http://learnangular2.com](http://learnangular2.com) that can help you get comfortable with Angular and learn all the stuff that changed.

## Ionic v1

* [ionic-v1](https://github.com/ionic-team/ionic-v1) - Here Ionic moved the "old" code of _Ionic v1_ when they released Ionic "2".
* [ionic-app-base](https://github.com/ionic-team/ionic-app-base) - Similar to the ionic2-app-base this is the base project template downloaded by the CLI when you `ionic start` a v1 project.
* [ng-cordova](https://github.com/ionic-team/ng-cordova) - _ngCordova_ is Ionic Native for Ionic v1
* [ionic-code](https://github.com/ionic-team/ionic-code) - Ionic has a CDN for Ionic v1 files at http://code.ionicframework.com
* [ionic-bower](https://github.com/ionic-team/ionic-bower) - Ionic v1 is/was available on [Bower](https://bower.io/)
* [ionic-native-bower](https://github.com/ionic-team/ionic-native-bower) - Makes Ionic Native available via bower for Ionic v1
* [ionic-typescript-example](https://github.com/ionic-team/ionic-typescript-example) - Use TypeScript with Ionic v1 (includes Screencast)

### Ionic v1 Starter Templates

* [ionic-starter-tabs](https://github.com/ionic-team/ionic-starter-tabs) -
* [ionic-hello-world](https://github.com/ionic-team/ionic-hello-world) -
* [ionic-starter-sidemenu](https://github.com/ionic-team/ionic-starter-sidemenu) -
* [ionic-starter-blank](https://github.com/ionic-team/ionic-starter-blank) -
* [ionic-starter-salesforce](https://github.com/ionic-team/ionic-starter-salesforce) -
* [ionic-starter-maps](https://github.com/ionic-team/ionic-starter-maps) -

### Ionic v1 Example Apps

* [ionic-weather](https://github.com/ionic-team/ionic-weather) -
* [ionic1-deeplinks-demo](https://github.com/ionic-team/ionic1-deeplinks-demo) -
* [ionic-push-tutorial-app](https://github.com/ionic-team/ionic-push-tutorial-app) -
* [ionic-third-party-lib-example](https://github.com/ionic-team/ionic-third-party-lib-example) - "An example App showing how to use third party libs in Ionic"

### Migrate Ionic v1 to Ionic

* [ionic-migration-demo-v1](https://github.com/ionic-team/ionic-migration-demo-v1) -
* [ionic-migration-demo-v2](https://github.com/ionic-team/ionic-migration-demo-v2) -

### Ionic v1 Contrib / Ion

* [ionic-ion-drawer](https://github.com/ionic-team/ionic-ion-drawer) -
* [ionic-ion-tinder-cards](https://github.com/ionic-team/ionic-ion-tinder-cards) -
* [ionic-ion-swipe-cards](https://github.com/ionic-team/ionic-ion-swipe-cards) -
* [ionic-ion-frost](https://github.com/ionic-team/ionic-ion-frost) -
* [ionic-ion-header-shrink](https://github.com/ionic-team/ionic-ion-header-shrink) -
* [ionic-contrib-frosted-glass](https://github.com/ionic-team/ionic-contrib-frosted-glass) -

## Ionic Services / Cloud / Platform

* [ionic-cloud-angular](https://github.com/ionic-team/ionic-cloud-angular) - Use _Ionic Services_ in Ionic/Angular
* [ionic-cloud](https://github.com/ionic-team/ionic-cloud) - Use Ionic Services in Ionic v1/AngularJS
* [ionic-plugin-deploy](https://github.com/ionic-team/ionic-plugin-deploy) - Cordova Plugin for Ionic Deploy / Live Updates
* [ionic-package-hooks](https://github.com/ionic-team/ionic-package-hooks) - "Cordova hooks that you can run in Ionic Package"
* [ionic-view-issues](https://github.com/ionic-team/ionic-view-issues) - _Ionic View_ is the app to show and test apps you `ionic upload`ed to apps.ionic.io. That source code is not open source, but here you can create issues for bugs or feature requests.
* [ionic-cloud-issues](https://github.com/ionic-team/ionic-cloud-issues) # deprecated
* [custom-auth-examples](https://github.com/ionic-team/custom-auth-examples) - ['Custom Auth'](http://docs.ionic.io/services/auth/custom-auth.html) Examples for Ionic Auth
* [platform-client-node](https://github.com/ionic-team/platform-client-node) - Node.js library implementing the [Push Endpoints](https://docs.ionic.io/api/endpoints/push.html) of the Ionic Service HTTP API

## Cordova Plugins

Ionic also offers and creates some Cordova plugins for use in all Cordova projects, not only Ionic.

* [ionic-plugin-keyboard](https://github.com/ionic-team/ionic-plugin-keyboard) - Interacting with the keyboards and get events fire on keyboard changes

* [ionic-plugin-deeplinks](https://github.com/ionic-team/ionic-plugin-deeplinks) - "Handle deeplinks into your Ionic/Cordova apps from Universal Links, App Links, and Custom URL schemes."

* [cordova-plugin-ios-keychain](https://github.com/ionic-team/cordova-plugin-ios-keychain) - Access the iOS keychain

* [cordova-camera-roll](https://github.com/ionic-team/cordova-camera-roll) - "The Cordova Camera Roll plugin makes it easy to read from the iOS camera roll."

* [cordova-plugin-localstorage-backup](https://github.com/ionic-team/cordova-plugin-localstorage-backup) - Backup your local storage to the device

* https://github.com/ionic-team/cordova-plugin-wkwebview-engine

## Ionic Creator

Ionic Creator is a nifty WYSIWYG editor for Ionic v1 that you can use to click your interface and then back it with code.

* [creator-weekly-workshops](https://github.com/ionic-team/creator-weekly-workshops) -
* [creator-code-todo-demo](https://github.com/ionic-team/creator-code-todo-demo) -

## Deprecated

### CLI v2

With the release of Ionic CLI v3 these two repositories are not needed any more as a rewrite of them is now part of the CLI itself:

* [ionic-app-lib](https://github.com/ionic-team/ionic-app-lib) -
* [ionic-app-generators](https://github.com/ionic-team/ionic-app-generators) -

## Internal / Unrelated / Abandoned / Not Relevant / Very Old / Unkown

* https://github.com/ionic-team/ionicate = Internal Survey for apps.ionic.io

* https://github.com/ionic-team/ionic2 = Former home of Ionic 2

* https://github.com/ionic-team/ionic-closure = Closure Experiment

* https://github.com/ionic-team/repool

* https://github.com/ionic-team/ionic-box

* https://github.com/ionic-team/ionic-web-analytics

* https://github.com/ionic-team/ionic-precommit-hooks

* https://github.com/ionic-team/cordova-plugin-inapppurchase

* https://github.com/ionic-team/ionic-gulp-tasks

* https://github.com/ionic-team/tslint-ionic-rules

* https://github.com/ionic-team/ionic-heroku-button

* https://github.com/ionic-team/localForage-cordovaSQLiteDriver

* https://github.com/ionic-team/ionic-scripts

* https://github.com/ionic-team/ionic-platform-web-client

* https://github.com/ionic-team/reactionic

* https://github.com/ionic-team/cordova-plugin-statusbar

* https://github.com/ionic-team/ionic-bootstrap-theme-generator

* https://github.com/ionic-team/cordova-plugin-template

* https://github.com/ionic-team/eslint-config-ionic

* https://github.com/ionic-team/ionic-learn

* https://github.com/ionic-team/ionic-present

* https://github.com/ionic-team/cordova-lib

* https://github.com/ionic-team/ionitron-issues

* https://github.com/ionic-team/ionic-service-analytics

* https://github.com/ionic-team/ionic-cz-conventional-changelog

* https://github.com/ionic-team/ionic-issue-submit

* https://github.com/ionic-team/ionic-push-issues

* https://github.com/ionic-team/storm

* https://github.com/ionic-team/heroku-buildpack-sphinx

* https://github.com/ionic-team/heroku-buildpack-python

* https://github.com/ionic-team/jetstrap-docs

* https://github.com/ionic-team/ionitron-lingo

* https://github.com/ionic-team/gulp-angular-seed

* https://github.com/ionic-team/ionic2-starter

* https://github.com/ionic-team/nginx-buildpack

* https://github.com/ionic-team/ionicons-wp

* https://github.com/ionic-team/ionic-starter-cardboard

* https://github.com/ionic-team/ionic-workshop-london

* https://github.com/ionic-team/ionic-service-push-client

* https://github.com/ionic-team/ionic-starter-push

* https://github.com/ionic-team/ionic-service-core

* https://github.com/ionic-team/ionic-service-deploy

* https://github.com/ionic-team/heroku-buildpack-multi

* https://github.com/ionic-team/ionic-workshop

* https://github.com/ionic-team/deploy-tutorial

* https://github.com/ionic-team/appcamp-issues

* https://github.com/ionic-team/electron-builder

* https://github.com/ionic-team/ionic-angular-cordova-seed

* https://github.com/ionic-team/usemin-lib

* https://github.com/ionic-team/node-xcode

* https://github.com/ionic-team/ionic-lab-issues

* https://github.com/ionic-team/heroku-buildpack-nodejs-gulp

* https://github.com/ionic-team/collide

* https://github.com/ionic-team/api-tester

* https://github.com/ionic-team/node-js-getting-started

* https://github.com/ionic-team/gulp-electron

* https://github.com/ionic-team/ionic-starter-analytics

* https://github.com/ionic-team/lazy-loading-poc

*

## Unsorted

https://github.com/ionic-team/bonjour = Internal fork

https://github.com/ionic-team/cordova-plugin-keyboard =

https://github.com/ionic-team/ionic-error-tracking/ = "Internal" error tracking tool

https://github.com/ionic-team/ionic-example-cordova-camera

https://github.com/ionic-team/ionic-starter-io

https://github.com/ionic-team/ionic-starter-deploy

https://github.com/ionic-team/ionic-io-docs

https://github.com/ionic-team/cordova-android

https://github.com/ionic-team/cordova-crosswalk-engine

https://github.com/ionic-team/ionic-io-testers

https://github.com/ionic-team/ionic-default-resources

https://github.com/ionic-team/standard

https://github.com/ionic-team/tiny-lr

https://github.com/ionic-team/InstagramPlugin

https://github.com/ionic-team/ionic-proxy-example

https://github.com/ionic-team/opbeat-node

https://github.com/ionic-team/front-page

https://github.com/ionic-team/ionic-starter-tests

https://github.com/ionic-team/ionic-starter-complex-list

https://github.com/ionic-team/docker-consul

https://github.com/ionic-team/ionic-ion-ios-buttons

https://github.com/ionic-team/ionic-theme-server

https://github.com/ionic-team/gosass

https://github.com/ionic-team/go-utils

https://github.com/ionic-team/cordova-plugin-discovery

https://github.com/ionic-team/ionic-cordova-wrapper

https://github.com/ionic-team/ionic-contrib-firebase-login

https://github.com/ionic-team/ngMad

https://github.com/ionic-team/ionic-todo

https://github.com/ionic-team/ionic-firebase-buses

https://github.com/ionic-team/chatroom-cordova-ionic-angularjs-firebase

https://github.com/ionic-team/django-template

https://github.com/ionic-team/cordova-splash-generator

https://github.com/ionic-team/ionic-intro

https://github.com/ionic-team/ionic-tutorial-status-fade

https://github.com/ionic-team/discourse

https://github.com/ionic-team/jqm-neue

https://github.com/ionic-team/graphite

https://github.com/ionic-team/jquerymobile-tabbar

https://github.com/ionic-team/jqm-plain
