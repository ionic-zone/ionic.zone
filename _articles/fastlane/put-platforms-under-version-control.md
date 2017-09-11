---
title: Put your Cordova /platforms directory under version control
published: true
date: 2017-08-29 16:00:00 +0000
last_updated: ''
parent: ['Ionic + Fastlane', '../fastlane']
---
# Put your Cordova `/platforms` directory under version control

{::comment}TODO Refactor to general article and not in fastlane context!{:/comment}

Normally `/platforms` and similar folders are in the `.gitignore` file of Cordova projects. This means the whole generated iOS and Android projects don't take up space in your repository - they can be recreated by running the `(ionic) cordova build` command.

But when we work with `fastlane`, it can be beneficial to know what our code changed in the native projects (and being able to simply revert all the things we messed up...).

There are two way to achieve this:

## a) Remove `/platforms` from the default `.gitignore` file

If you have no problem with all the `platforms` files and folders being in the main git repository of your project, you can just remove `/platforms` from the `.gitignore` file.

Open the `.gitignore` file in your favorite editor. Remove or uncomment (`#`) this line:

```
platforms/
```

Commit and push the edited `.gitignore` file, which should also add all the files and folders inside `/platforms` to git automatically. The folder is now under the same version control as the rest of your project.

### How to handle a versioned `platforms` directory

I suggest you commit changes to the normal project seperate from the changes in `platforms`. Only then commit the changes in there and use the command (e.g. `(ionic) cordova build` and `(ionic) cordova prepare`) as the commit message. This makes it easy to follow the changes.

## b) Create a local git repository in `/platforms`

If you prefer to keep the project repository lean and without `/platforms`, you can just create a git repository in `/platforms` itself to track (and undo, if necessary) any changes:

```
cd platforms
git init
git add .
git commit -m "Initial commit"
```

Caution: This might at times cause problems with `cordova` commands that read the list of platforms from the folders in `/platforms` like `(ionic) cordova plugin add ...`. They will complain that the `.git` platform is missing an `Api.js` file. If you need to run one of these commands, temporarily move or delete the `/platforms/.git` folder, run the command, and then move it back / restore it. Git should take note of the added files just then.
{:.message}

Now you have a local git repository for `platforms` that of course can also pushed to your favorite repository host.

### How to handle a independent `platforms` repository

I suggest you check for changes in the `platforms` repository after every command that might have changed the native project files. `(ionic) cordova build` and `(ionic) cordova prepare` are the most obvious ones, but also several `fastlane` commands we will use might change things there. 

When changes are detected, commit them and note the command you ran in the commit log. That way you get a neat history of changes to your native projects as you have it for your main project. This not only makes following the changes much easier, but will also help you identify if something goes wrong.

{::comment}
## Track even more in `platforms`

Now you just have to make sure to look at the changes with `git status` (or your favorite GUI) from time to time and commit the changes and maybe add the commands you just ran in the commit message.

If you want to really see all the changes, you will have to edit the `.gitignore` files in `platforms/ios` and `platforms/android` though:

TODO
{:/comment}