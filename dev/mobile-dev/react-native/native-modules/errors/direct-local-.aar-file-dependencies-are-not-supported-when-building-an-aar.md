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

{% embed url="https://stackoverflow.com/questions/16682847/how-to-manually-include-external-aar-package-using-gradle-for-android" %}

## On Linux - Set up a local Maven repository and reference the .aar from there

{% embed url="https://www.flexlabs.org/2013/06/using-local-aar-android-library-packages-in-gradle-builds" %}

```
wget https://dlcdn.apache.org/maven/maven-3/3.8.5/binaries/apache-maven-3.8.5-bin.tar.gz
tar -xvf apache-maven-3.8.5-bin.tar.gz

nano ~/.bashrc
# export MAVEN_HOME=/path/to/apache-maven-3.8.5
# export PATH="/path/to/apache-maven-3.8.5/bin:$PATH"
source ~/.bashrc

mvn -v
```
