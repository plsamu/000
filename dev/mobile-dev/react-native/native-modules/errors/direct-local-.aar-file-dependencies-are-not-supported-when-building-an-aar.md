# Direct local .aar file dependencies are not supported when building an AAR

## bOn Windows

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

{% embed url="https://stackoverflow.com/questions/16682847/how-to-manually-include-external-aar-package-using-gradle-for-android" %}

## On Linux - Set up a local Maven repository and reference the .aar from there

{% embed url="https://www.flexlabs.org/2013/06/using-local-aar-android-library-packages-in-gradle-builds" %}

```bash
wget https://dlcdn.apache.org/maven/maven-3/3.8.5/binaries/apache-maven-3.8.5-bin.tar.gz
tar -xvf apache-maven-3.8.5-bin.tar.gz

nano ~/.bashrc
# export MAVEN_HOME=/path/to/apache-maven-3.8.5
# export PATH="/path/to/apache-maven-3.8.5/bin:$PATH"
source ~/.bashrc

mvn -v
```

```bash
mvn install:install-file -Dfile=/path/to/my.aar -DgroupId=com.example -DartifactId=mylibrary -Dversion={version} -Dpackaging=aar

# {version}=1.0.0
```

```
buildscript {
  repositories {
    mavenLocal()
  }
}

allprojects {
  repositories {
    mavenLocal()
  }
}

dependencies {
  // Direct local .aar file dependencies are not supported when building an AAR.
  // implementation files("libs/mylibrary.aar")
  // implementation fileTree(include: ['*.aar'], dir: 'libs')
  // implementation (files("libs/mylibrary.aar"))

  // works for project but not for "npm pack"
  // implementation(name:'mylibrary', ext:'aar')

  implementation 'com.example:mylibrary:1.0.0'
}  
```
