# Fastlane + Ionic: How to write instrumented (Espresso or UI Automator) tests for Android 
(to e.g. use in `screengrab`)

As usual navigating the WebView is a bit more difficult as the test frameworks are written to navigate native elements. Lucky for us the Android people were aware of this and created `espresso-web`.

TODO Imports

## Navigate the app by clicking/tapping on things

TODO Navigate the page by finding an element and clicking on it

## Select element by ID

You might want to add `id` attributes to all your elements that should be clicked on.

TODO example

## Select element with XPath

XPath is your friend. Right click the thing you want to find and inspect it. There you can right click on the underlying code any Copy -> Copy Xpath. This selector can directly be used in:

TODO example

## Wait

Now if you do stuff that requires a screen to be in a specific state (like create screenshots, fill a form or similar) you might need to "wait" a bit for the Ionic app to catch up. Here you can just add a short `sleep`:

```
Thread.sleep(1500);
```

This sleeps for 1.5 seconds and then continues with the execution of the test.