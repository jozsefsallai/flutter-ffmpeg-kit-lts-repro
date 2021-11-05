# flutter-ffmpeg-kit-lts-repro

Steps to reproduce:

```
git clone git@github.com:jozsefsallai/flutter-ffmpeg-kit-lts-repro.git
cd flutter-ffmpeg-kit-lts-repro
flutter pub get
flutter dev
```

Output on Android:

```
Launching lib/main.dart on M2002J9G in debug mode...
/Users/joe/Projects/flutter-ffmpeg-kit-lts-repro/android/app/src/debug/AndroidManifest.xml Error:
	uses-sdk:minSdkVersion 16 cannot be smaller than version 24 declared in library [:ffmpeg_kit_flutter] /Users/joe/Projects/flutter-ffmpeg-kit-lts-repro/build/ffmpeg_kit_flutter/intermediates/library_manifest/debug/AndroidManifest.xml as the library might be using APIs not available in 16
	Suggestion: use a compatible library with a minSdk of at most 16,
		or increase this project's minSdk version to at least 24,
		or use tools:overrideLibrary="com.arthenica.ffmpegkit.flutter" to force usage (may lead to runtime failures)

FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':app:processDebugMainManifest'.
> Manifest merger failed : uses-sdk:minSdkVersion 16 cannot be smaller than version 24 declared in library [:ffmpeg_kit_flutter] /Users/joe/Projects/flutter-ffmpeg-kit-lts-repro/build/ffmpeg_kit_flutter/intermediates/library_manifest/debug/AndroidManifest.xml as the library might be using APIs not available in 16
  	Suggestion: use a compatible library with a minSdk of at most 16,
  		or increase this project's minSdk version to at least 24,
  		or use tools:overrideLibrary="com.arthenica.ffmpegkit.flutter" to force usage (may lead to runtime failures)

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output. Run with --scan to get full insights.

* Get more help at https://help.gradle.org

BUILD FAILED in 9s
Running Gradle task 'assembleDebug'...                             10.8s

The plugin ffmpeg_kit_flutter requires a higher Android SDK version.
Fix this issue by adding the following to the file
/Users/joe/Projects/flutter-ffmpeg-kit-lts-repro/android/app/build.gradle:
android {
  defaultConfig {
    minSdkVersion 24
  }
}


Note that your app won't be available to users running Android SDKs below 24.
Alternatively, try to find a version of this plugin that supports these lower
versions of the Android SDK.
Exception: Gradle task assembleDebug failed with exit code 1
```

Output on iOS:

```
Launching lib/main.dart on iPhone 13 in debug mode...
Running pod install...                                             574ms
CocoaPods' output:
↳
      Preparing

    Analyzing dependencies

    Inspecting targets to integrate
      Using `ARCHS` setting to build architectures of target `Pods-Runner`: (``)

    Fetching external sources
    -> Fetching podspec for `Flutter` from `Flutter`
    -> Fetching podspec for `ffmpeg_kit_flutter` from
    `.symlinks/plugins/ffmpeg_kit_flutter/ios`

    Resolving dependencies of `Podfile`
      CDN: trunk Relative path: CocoaPods-version.yml exists! Returning local
      because checking is only performed in repo update
    [!] CocoaPods could not find compatible versions for pod
    "ffmpeg_kit_flutter/https-lts":
      In Podfile:
        ffmpeg_kit_flutter (from `.symlinks/plugins/ffmpeg_kit_flutter/ios`) was
        resolved to 4.5.0, which depends on
          ffmpeg_kit_flutter/https-lts (= 4.5.0)

    Specs satisfying the `ffmpeg_kit_flutter/https-lts (= 4.5.0)` dependency
    were found, but they required a higher minimum deployment target.

    [ ... ]

Error output from CocoaPods:
↳

    [!] Automatically assigning platform `iOS` with version `9.0` on target
    `Runner` because no platform was specified. Please specify a platform for
    this target in your Podfile. See
    `https://guides.cocoapods.org/syntax/podfile.html#platform`.

Error running pod install
Error launching application on iPhone 13.
```
