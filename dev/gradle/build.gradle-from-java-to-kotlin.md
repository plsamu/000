# build.gradle from java to kotlin

```
buildscript {
  def kotlin_version = "1.6.10"

  repositories {
    maven {
      url 'https://maven.google.com/'
      name 'Google'
    }
    ...
  }

  dependencies {
    classpath 'com.android.tools.build:gradle:7.1.2'
    
    // ADD THIS
    classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
  }
}

// ADD THIS
apply plugin: 'kotlin-android'

...

def kotlin_version = "1.6.10"

dependencies {
  // ADD THIS
  implementation "org.jetbrains.kotlin:kotlin-stdlib:$kotlin_version"
  // implementation "com.android.support:appcompat-v7:28.0.0"
}
```
