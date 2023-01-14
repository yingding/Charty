# Publish to JitPack.io from github
https://docs.jitpack.io/android/

## Test with
```
#     buildTypes is `release`
./gradlew publishReleasePublicationToMavenLocal

```

Guide
* https://dev.to/vtsen/how-to-publish-android-library-on-jitpackio-with-github-50n1

# build release with github workflow
* merge feature-branch to main
* tag the release "1.0.2-alpha02"
* with label "1.0.2-alpha02"
* check the pre-release
* by great the release, artifacts will be generated on github workflow

# build with jitpack.io
## Add plugin in lib module charty
```kotlin
plugins {
    
    id("maven-publish")
}
```

## Make jitpack.yml file in project root
jitpack.yml

## Create publish block in `charty` lib model `build.gradle.kts`
```add publishing
publishing {
    publications {
        register<MavenPublication>("release") {
            groupId = "com.github.yingding"
            artifactId = "Charty"
            version = "1.0.2-alpha01"

            afterEvaluate {
                from(components["release"])
            }
        }
    }
}
```

## or just build the release
* search project repository
* Login to the jitpack.io and publish it by click on the release


# Gradle Setup
build.gradle
```
repositories {
    maven { url 'https://jitpack.io' }
}

dependencies {
    implementation 'com.github.yingding:charty:v1.0.2-alpha01'
}
```

project root build.gradle.kts
```
buildscript {
    repositories {
        google()
        mavenCentral()
        maven { setUrl("https://jitpack.io") } // for charty v1.0.1-alpha01
    }

```