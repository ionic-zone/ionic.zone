# Put your Cordova `/platforms` directory under version control

Normally `/platforms` and similar folders are on the `.gitignore` of Cordova. This means the whole generated iOS and Android projects don't take up space in your repository - they can be recreated by running the `cordova build` command.

But when we work with `fastlane`, it can be beneficial to know what our code changed in the native projects. So let's just create a git repository in there so we can track (and undo, if necessary) changes:

```
git init
git add .
git commit -m "Initial commit"
git push master # TODO Is this necessary?
```

Caution: This will cause problems with `cordova` commands that read the list of platforms from the folders in `/platforms` like `cordova plugin add ...`. They will complain that the `.git` platform is missing an `Api.js` file. If you need to run one of these commands, temporarily move or delete the `/platforms/.git` folder, run the command, and then move it back / restore it. Git should take note of the added files just then.

TODO Remove stuff from .gitignore in /ios and /android to track more?

Now you just have to make sure to look at the changes with `git status` (or your favorite GUI) from time to time and commit the changes and maybe add the commands you just ran in the commit message.