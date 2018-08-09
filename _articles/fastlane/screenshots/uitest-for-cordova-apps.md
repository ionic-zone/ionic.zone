---
title: 
published: true
date: 2017-08-29 16:00:00 +0000
last_updated: ''
parent: ['Ionic + Fastlane', '../fastlane']
---
# Build UI Tests for your Cordova iOS app (to use with Fastlane's `snapshot`)

General:
https://stackoverflow.com/a/35455671/252627
http://masilotti.com/ui-testing-cheat-sheet/
http://samwize.com/2016/02/28/everything-about-xcode-ui-testing-snapshot/
http://averagepro.com/2015/11/06/xctest-ui-testing-hints-and-tips/
https://blog.metova.com/guide-xcode-ui-test/

https://stackoverflow.com/a/33534187/252627
best friend!

https://tisunov.github.io/2015/11/06/automating-app-store-screenshots-generation-with-fastlane-snapshot-and-sketch.html

Fastlane:
http://samwize.com/2015/12/09/automate-screenshots-capture-using-snapshot-via-xcode-ui-testing/


## Common Erros

### Computed invalid hit point 

```
testSnapshots, UI Testing Failure - Computed invalid hit point (-1.3, -1.0) for Button 0x608000364bc0: traits: 8590065921, &#123;&#123;0.0, 639.0&#125;, &#123;1024.0, 61.3&#125;&#125;, label: 'trash Delete all data (Caution!)
```
https://stackoverflow.com/questions/40571744/xcode-ui-testing-failure-computed-invalid-hit-point

### Failed to scroll to visible

```
testSnapshots, UI Testing Failure - Failed to scroll to visible (by AX action) Button 0x7c379850: traits: 8590065665, &#123;&#123;282.0, 26.0&#125;, &#123;33.0, 32.0&#125;&#125;, label: 'information circle', error: Error -25204 performing AXAction 2003
```