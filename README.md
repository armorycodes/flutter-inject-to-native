## Flutter Inject To Native
- This Project is Flutter App
- Main Goals : Implement to Existing Android Project

## How To Use This Project

### Convert Flutter App to Flutter Module
- Adding some code in pubspec.yaml

```kotlin
 flutter:
 module:
    androidX: true
    androidPackage: [Package.Name] Example : com.example.fluttermodule
    iosBundleIdentifier: [Package.Name] Example : com.example.fluttermodule
```

- Run Flutter Pub Get

```kotlin
flutter pub get
```

### Setup to Existing Android Native Project (Inside Folder Android Native Project)

- Add Flutter Project

  - Manual Integration
  
    - Copy / Move Inside Folder Android Native
  
  - Submodule Integration
  
    - Code

    ```kotin
    git submodule add <link-repo-github>
    ```

    - Sample

    ```kotin
    git submodule add https://github.com/amirisback/flutter-inject-to-native
    ```

- Add some code in settings.gradle

```groovy
import org.gradle.api.initialization.resolve.RepositoriesMode

pluginManagement {
    repositories {
        gradlePluginPortal()
        google()
        mavenCentral()
        // Add these two maven entries.
        maven {
            url '../flutter-inject-to-native/build/host/outputs/repo'
        }
        maven {
            url 'https://storage.googleapis.com/download.flutter.io'
        }

    }
}
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.PREFER_PROJECT) // Change to PREFER_PROJECT
    repositories {
        google()
        mavenCentral()
        // Add these two maven entries.
        maven {
            url '../flutter-inject-to-native/build/host/outputs/repo'
        }
        maven {
            url 'https://storage.googleapis.com/download.flutter.io'
        }
    }
}

include ':app'

setBinding(new Binding([gradle: this]))

// Using SettingsDir, because flutter project not siblings but inside the existing project
evaluate(new File(settingsDir, 'flutter-inject-to-native/.android/include_flutter.groovy')) 

```

- Add some code in build.gradle (root project)

```kotlin
allprojects {
    repositories {
        google()
        mavenCentral()
        // Add these two maven entries.
        maven {
            url '../../flutter-inject-to-native/build/host/outputs/repo'
        }
        maven {
            url 'https://storage.googleapis.com/download.flutter.io'
        }
    }
}
```

- Add some code in build.gradle (app)
  
  - In Default Config
  
  ```kotlin
  ndk {
      // Filter for architectures supported by Flutter.
      abiFilters 'armeabi-v7a', 'arm64-v8a', 'x86_64'
  }
  ```
  
  - Above dependencies area
  
  ```kotlin
  repositories {
    google()
    mavenCentral()
    // Add these two maven entries.
    maven {
        url '../flutter-inject-to-native/build/host/outputs/repo'
    }
    maven {
        url 'https://storage.googleapis.com/download.flutter.io'
    }
  }
  ```
  
  - In Dependencies area

  ```groovy
  dependencies {
    implementation project(':flutter')
  }
  ```
  
## Link Docs Setup
### Docs
- https://docs.flutter.dev/development/add-to-app/android/project-setup
- https://github.com/flutter/samples/tree/main/add_to_app
- https://medium.com/flutter/put-flutter-to-work-95f5fdcc592e
- https://github.com/flutter/put-flutter-to-work
- https://levelup.gitconnected.com/how-to-add-flutter-to-android-app-4d80d9820686
- https://flatteredwithflutter.com/how-to-add-flutter-to-android-app/
- https://pahlevikun.medium.com/bridging-between-dart-and-native-code-with-flutter-channel-for-communicate-each-other-7c736929ee42

### Video
- https://www.youtube.com/watch?v=-_k8R1X_oz0
- https://www.youtube.com/watch?v=7gCILw0HLw4&t=446s


## Getting Started Flutter Docs

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.

## Colaborator
Very open to anyone, I'll write your name under this, please contribute by sending an email to me

- Mail To faisalamircs@gmail.com
- Subject : Github _ [Github-Username-Account] _ [Language] _ [Repository-Name]
- Example : Github_amirisback_kotlin_admob-helper-implementation

Name Of Contribute
- Muhammad Faisal Amir
- Waiting List
- Waiting List

Waiting for your contribute

## Attention !!!
- Please enjoy and don't forget fork and give a star
- Don't Forget Follow My Github Account
