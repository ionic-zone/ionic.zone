---
title: 
published: true
date: 2017-08-29 16:00:00 +0000
last_updated: ''
parent: ['Ionic + Fastlane', '../fastlane']
---
# Fastlane: Bump version numbers

For now we handled version numbers manually in config.xml and let Fastlane only take care of the build numbers (See: ... for the difference between version and build numbers). But of course you can also create lanes that enable you do automate the changing of versions with Fastlane:

lanes for:
major
minor
patch

both for iOS and Android

bump_major
bump_minor
bump_patch

Read value from config.xml, modify value, write value back, commit changed config.xml to Git.

Can be integrated into you release lanes or just be used individually.



iOS example (for build number, not version!)
```
  desc "Bump build number, commit & push to remote"
  lane :incrementBuild do

    # Bump build number
    increment_build_number

    # Commit and push to remote
    commit_version_bump(
      message: 'Build number bump by fastlane - buildnumber lane',
      force: true
    )
    push_to_git_remote
  end
```