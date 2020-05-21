## Building Android

### Environment Setup

Install Android Studio
- https://developer.android.com/studio
- From Jetbrains Toolbar

Fire up Android Studio.

Open Tools > SDK Manager. Install an SDK (like 10.0). Click SDK Tools tab and install NDK and cmake.

Set your $ANDROID_HOME and $ANDROID_NDK_HOME in `~/.bash_profile`. Change `<user>` to your username.
Double check the NDK path on your system since the version number will change.

```
export ANDROID_HOME="/Users/<user>/Library/Android/sdk"
export PATH=$PATH:$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools

export ANDROID_NDK_HOME=$ANDROID_HOME/ndk/21.1.6352462
```

### App Setup

`cd android/app`
`keytool -genkey -v -keystore my-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000`
Set the password to be "password"

### Simulator

Run the app in the simulator with `GO111MODULE=off yarn run android`. You must be in the same folder
as `package.json`.

### Create APKs

> Note: I had to set my Java to use version 1.8. It might just be a quirk of my machine.
> Use `export JAVA_HOME=`/usr/libexec/java_home -v 1.8` to do that.

To build APKs use `./gradlew assembleRelease`

The APKs will be in `android/app/build/outputs/apk/release`