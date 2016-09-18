# android-studio-gradle-test
A test project with a structure to stress test and find out issues in Android Studio and Gradle

Also provides an alternative build path using [Buck](https://buckbuild.com/) to compare. For more details on how the buck build path is setup, please see [OkBuck](https://github.com/OkBuilds/OkBuck)

## To build all apps with gradle:
```bash
./gradlew assemble
```

## To build all apps with buck

### Setup
```bash
brew update
brew install watchman ant
```

### Build
```bash
./buckw targets # to make sure buckw will invoke the gradle okbuck task if needed
./buckw query "kind('android_binary', '//...')" | xargs ./buckw build
```

## Incremental build comparision

An example use case would be to uncomment line 7 in `e/build.gradle` to check the effect of a new dependency as part of an incremental build.
