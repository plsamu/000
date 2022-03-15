# Create Expo Package

A **module** is a single JavaScript file that has some reasonable functionality.

A **package** is a directory with one or more modules inside of it and a package.json file which has metadata about the package.

## What worked for me

```
expo init demo1
# you can choose managed workflow
cd ./demo1
yarn
expo install /path/to/react-native-mypkg-0.1.0.tgz
# eject the project
expo run:android
```

### [how to create react-native-mypkg-0.1.0.tgz](../../react-native/create-native-package.md)

## Info

{% embed url="https://www.farhansayshi.com/post/build-an-npm-package-with-expo-dependencies-for-expo-and-plain-react-native-projects" %}

{% embed url="https://github.com/expo/expo/tree/main/packages/create-expo-module" %}

{% embed url="https://blog.expo.dev/whats-new-in-expo-modules-infrastructure-7a7cdda81ebc#0ff9" %}
From unimodules to Expo package
{% endembed %}

## How

{% hint style="warning" %}
Use [EAS ](https://docs.expo.dev/eas/)if you are going to use native package\
\
$ expo init app-demo1\
$ cd ./app-demo1\
$ npm install\
&#x20;   \# it's a pure react native module \
$ npm install --save --legacy-peer-deps react-native-blurhash\
\
$ npm install -g eas-cli\
&#x20;   \# in eas.json add\
&#x20;   "preview": { "distribution": "internal", "android": { "buildType": "apk" } },\
$ eas build --profile preview -p android\
&#x20;   \# install apk on device
{% endhint %}

### step 1

```bash
npx create-react-native-library my_package
yarn add react react-native react-native-builder-bob pod-install
yarn add expo
yarn add typescript
```

#### android

Expo needs 'maven' as plugin, but this was removed in gradle 7.x.\
So keep gradle to version 4.1.0:

```
dependencies {
    classpath 'com.android.tools.build:gradle:4.1.0'
}
```

### step 2

Follow the installation guide here:

{% embed url="https://www.npmjs.com/package/expo-modules-core" %}



1. get a sample project
2. expo install
3. change modules code
4. pack
5. try to install&#x20;
