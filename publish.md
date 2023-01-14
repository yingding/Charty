# Publish to JitPack.io from github
Guide
* https://dev.to/vtsen/how-to-publish-android-library-on-jitpackio-with-github-50n1


## Add plugin in lib module charty
```kotlin
plugins {
    
    id("maven-publish")
}
```

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

# Gradle Setup
```
repositories {
    maven { url 'https://jitpack.io' }
}

dependencies {
    implementation 'com.github.yingding:MPAndroidChart:v3.1.0'
}
```