---
title: 
published: true
date: 2017-08-29 16:00:00 +0000
last_updated: ''
parent: ['Ionic + Fastlane', '../fastlane']
---
# Fastlane: Create CHANGELOG from commit messages

Good practice to offer testers some information on what actually changes. Depending on who is testing, you of course want to write this manually. But if you are just creating automatic builds of the developers changes for e.g. CI or testing by those same developers, you can get away by just taking the Git commit messages (of course presuming these are useful) to build a changelog that is attached to the build on Testflight, HockeyApp or similar


## Android in general

https://github.com/fastlane/fastlane/tree/master/supply#changelogs-whats-new


## Use git commit messages

https://docs.fastlane.tools/getting-started/ios/beta-deployment/#release-notes


## Alternative: From CHANGELOG.md

```
desc "Deploy a new build via HockeyApp"
  lane :hockey do

    # Bump build number
    increment_build_number

    # Download and install the latest AdHoc profile
    sigh(adhoc: true, force: true, output_path: "./fastlane/provisioning")

    # Set version number to the one at the top of the CHANGELOG
    readme = File.read("../CHANGELOG.md")
    latest_version = readme.split("\n## ").first
    first_line = latest_version.split("\n").first
    version_number = first_line.split(" ")[1]

    increment_version_number(version_number: version_number)

    # Generate release notes from CHANGELOG
    release_notes = latest_version.split("\n")[1..-1].join("\n")
    puts release_notes

    # Create the IPA file - save in Temp folder
    profileUDID = lane_context[SharedValues::SIGH_UDID]
    puts "Profile UUID: #{profileUDID}"
    gym(
      xcargs: "PROVISIONING_PROFILE=#{profileUDID}",
      scheme: "xxxxxxx",
      silent: true
    )

    # Deploy via HockeyApp
    markdown_type = '1'
    hockey(
      api_token: 'xxxxxxxxxxxxxxxxxxxxxxxxxxx',
      notes_type: markdown_type,
      notes: release_notes
    )

    # Make sure our directory is clean, except for changes Fastlane has made
    clean_build_artifacts

    # Commit and push to remote
    commit_version_bump(
      message: 'Build number bump by fastlane - hockey lane',
      force: true
    )
    push_to_git_remote
  end
```