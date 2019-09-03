---
title: 'Fastlane: Automatically increment build number of your Cordova project'
published: true
date: 2017-09-28 16:00:00 +0000
last_updated: ''
parent: ['Ionic + Fastlane', '../fastlane']
---
# Automatically increment build number of your Cordova project with Fastlane

## iOS

Automatically increment the build number in the iOS project.

Here with latest build number +1 from Testflight:

```ruby
  increment_build_number({
    build_number: latest_testflight_build_number + 1, # TODO magically available?
    xcodeproj: xcodeprojpath
  })
  # TODO Save new value to config.xml
```

## Android

Automatically increment the build number in the iOS project.

If you are uploading to Google Play alpha track:

```ruby
  play_version_codes = google_play_track_version_codes(track: 'alpha')
  version_code = play_version_codes.first + 1
  gradle(
    task: 'assemble',
    build_type: 'Release',
    project_dir: 'platforms/android',
    properties: { 
      'cdvVersionCode' => version_code # TODO check if this is the correct way to do this
    }
  )
  ```

