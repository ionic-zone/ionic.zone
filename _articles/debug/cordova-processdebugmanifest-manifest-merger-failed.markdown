---
title: 'Cordova: Execution failed for task '':processDebugManifest''. Manifest merger
  failed : Attribute X is also present at Y'
date: 2017-06-17 16:13:38.402000000 Z
published: false
position: 4
---

# Cordova: Execution failed for task ':processDebugManifest'. Manifest merger failed : Attribute X is also present at Y

Text

### Examples

```
Execution failed for task ':processDebugManifest'.
Manifest merger failed : Attribute meta-data#android.support.VERSION@value value=(26.0.0-alpha1) from [com.android.support:support-v4:26.0.0-alpha1] AndroidManifest.xml:27:9-38 is also present at [com.android.support:appcompat-v7:25.3.1] AndroidManifest.xml:27:9-31 value=(25.3.1)
```

See: 
https://forum.ionicframework.com/search?q=%2226.0.0-alpha1%22
https://stackoverflow.com/questions/42949974/android-support-repo-46-0-0-with-android-studio-2-3
https://docs.gradle.org/current/userguide/dependency_management.html#sec:blacklisting_version
