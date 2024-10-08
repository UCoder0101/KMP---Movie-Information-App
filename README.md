# KMP Movie (Compose Multiplatform)  
[![Compose Multiplatform](https://img.shields.io/badge/Compose%20Multiplatform-v1.6.11-green)](https://developer.android.com/jetpack/compose)
[![Kotlin](https://img.shields.io/badge/Kotlin-2.0.20-blue.svg?style=flat&logo=kotlin)](https://kotlinlang.org)
![badge-Android](https://img.shields.io/badge/Platform-Android-brightgreen)
![badge-iOS](https://img.shields.io/badge/Platform-iOS-lightgray)
![badge-desktop](http://img.shields.io/badge/Platform-Desktop-4D76CD.svg?style=flat)
![badge-web](https://img.shields.io/badge/Platform-Web-blueviolet.svg?style=flat)
[![GitHub license](https://img.shields.io/badge/license-Apache%20License%202.0-blue.svg?style=flat)](https://www.apache.org/licenses/LICENSE-2.0)
<a href="https://github.com/piashcse"><img alt="License" src="https://img.shields.io/static/v1?label=GitHub&message=piashcse&color=C51162"/></a>

KMP Movie app built with Compose Multiplatform, supporting Android, iOS, Desktop, and Web. The app follows the MVVM architecture to ensure clean, maintainable code and delivers a responsive, modern UI experience across all platforms, leveraging [The Movie DB API](https://www.themoviedb.org). </br>

# Platform
- iOS
- Android
- Desktop
- Web
<p float="left">
  <img width="100%" height="100%" src="https://github.com/piashcse/kmp-movie/blob/master/screenshots/Screen Recording 2024-08-24 at 7.31.48 PM.gif" />
 </p> 
<p float="left">
  <img width="100%" height="60%" src="https://github.com/piashcse/kmm-movie/blob/master/screenshots/Screenshot 2024-08-24 at 7.24.41 PM.PNG" />
</p>
<p float="left" style="padding-top: 200px;">
  <img width="100%" height="60%" src="https://github.com/piashcse/kmm-movie/blob/master/screenshots/Screenshot 2024-08-24 at 7.27.23 PM.PNG" />
</p>
<p float="left" style="padding-top: 200px;">
  <img width="100%" height="60%" src="https://github.com/piashcse/kmm-movie/blob/master/screenshots/Screenshot 2024-08-24 at 7.30.34 PM.PNG" />
</p>


# Main Features
- Movie
  - Movie List  
  - Movie Search
  - Movie Detail
  - Recommended Movie
- TV Series
  - TV Series List
  - TV Series Search
  - TV Series Detail
  - Recommended TV Series 
- Artist Detail
- Bottom Navigation
- Navigation Rail

## Architecture
  - MVVM Architecture (Model - ComposableView - ViewModel)

<p float="left">
  <img width="100%" height="60%" src="https://github.com/piashcse/kmm-movie/blob/master/screenshots/mvvm_architecture.png" />
</p>

## API Key 🔑
You will need to provide a developer key to fetch the data from TMDB API.
* Generate a new key (v3 auth) from [here](https://www.themoviedb.org/settings/api). Copy the key and go back to the project.
* Add the key to build config in `./composeApp/build.gradle.kts`:

```kotlin
defaultConfig {
    ...
    buildConfigField("API_KEY", TMDB_API_KEY)
    ...
}
```

## Built With 🛠
- [Compose Multiplatform](https://github.com/JetBrains/compose-multiplatform) - Compose Multiplatform, a modern UI framework for Kotlin that makes building performant and beautiful user interfaces.
- [PreCompose](https://github.com/Tlaster/PreCompose) - Compose Multiplatform Navigation && State Management
- [Ktor Client](https://ktor.io/docs/welcome.html) - Ktor includes a multiplatform asynchronous HTTP client, which allows you to make requests and handle responses.
- [kotlinx.serialization](https://github.com/Kotlin/kotlinx.serialization) - Kotlin multiplatform / multi-format reflectionless serialization
- [View Model](https://developer.android.com/topic/libraries/architecture/viewmodel) - The ViewModel class is a business logic or screen level state holder. It exposes state to the UI and encapsulates related business logic
- [Coroutines](https://kotlinlang.org/docs/reference/coroutines-overview.html) - For asynchronous and more.
- [Flow](https://kotlin.github.io/kotlinx.coroutines/kotlinx-coroutines-core/kotlinx.coroutines.flow/-flow/) - A cold asynchronous data stream that sequentially emits values and completes normally or with an exception.
- [Landscapist](https://github.com/skydoves/landscapist) - 🌻 A pluggable, highly optimized Jetpack Compose and Kotlin Multiplatform image loading library that fetches and displays network images with Glide, Coil, and Fresco.
- [Android Studio](https://developer.android.com/studio/intro) - Android Studio is the official Integrated Development Environment (IDE) for Android app development.
- [XCode](https://developer.apple.com/xcode/) - Xcode 14 includes everything you need to develop, test, and distribute apps across all Apple platforms.

## Before running!
 - check your system with [KDoctor](https://github.com/Kotlin/kdoctor)
 - install JDK 11 or higher on your machine
 - add `local.properties` file to the project root and set a path to Android SDK there

### Android
To run the application on Android device/emulator:  
 - open the project in Android Studio and run the imported android run configuration

To build the application bundle:
 - run `./gradlew :composeApp:assembleDebug`
 - find `.apk` file in `composeApp/build/outputs/apk/debug/composeApp-debug.apk`
Run android simulator UI tests: `./gradlew :composeApp:pixel5Check`

### Desktop
Run the desktop application: `./gradlew :composeApp:run`
Run desktop UI tests: `./gradlew :composeApp:jvmTest`

### Web
- Before running make sure you have yarn 1.22.22
- Run the web application: `./gradlew wasmJsBrowserRun`

### iOS
To run the application on an iPhone device/simulator:
 - Open `iosApp/iosApp.xcproject` in Xcode and run standard configuration
 - Or use [Kotlin Multiplatform Mobile plugin](https://plugins.jetbrains.com/plugin/14936-kotlin-multiplatform-mobile) for Android Studio
Run iOS simulator UI tests: `./gradlew :composeApp:iosSimulatorArm64Test`
## Project structure 

This Compose Multiplatform project includes three modules:

### [`composeApp`](/composeApp)
This is a Kotlin module that contains the logic common for both Android and iOS applications, the code you share between platforms.
This shared module is also where you write your Compose Multiplatform code. In `composeApp/src/commonMain/kotlin/App.kt`, you can find the shared root `@Composable` function for your app.
It uses Gradle as the build system. You can add dependencies and change settings in `shared/build.gradle.kts`. The shared module builds into an Android library and an iOS framework.

### [`androidApp`](/composeApp/src/androidMain/)
This is a Kotlin module that builds into an Android application. It uses Gradle as the build system. The `androidApp` module depends on and uses the shared module as a regular Android library.

### [`iosApp`](/iosApp)
This is an Xcode project that builds into an iOS application. It depends on and uses the shared module as a CocoaPods dependency.
