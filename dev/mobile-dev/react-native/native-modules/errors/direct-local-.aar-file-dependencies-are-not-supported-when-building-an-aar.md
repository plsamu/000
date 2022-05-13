# Direct local .aar file dependencies are not supported when building an AAR

## On Windows

```
react-native-pkg
    libs
        my.aar
    src
    build.gradle
```

### build.gradle

```
allprojects {
    repositories {
        flatDir {
            dirs 'libs'
        }
    }
}

dependencies {
  implementation fileTree(include: ['*.aar'], dir: 'libs')
}
```
