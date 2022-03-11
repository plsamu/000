# Create Expo Package

A **module** is a single JavaScript file that has some reasonable functionality.

A **package** is a directory with one or more modules inside of it and a package.json file which has metadata about the package.

{% embed url="https://www.farhansayshi.com/post/build-an-npm-package-with-expo-dependencies-for-expo-and-plain-react-native-projects" %}

{% embed url="https://github.com/expo/expo/tree/main/packages/create-expo-module" %}

{% embed url="https://blog.expo.dev/whats-new-in-expo-modules-infrastructure-7a7cdda81ebc#0ff9" %}
From unimodules to Expo package
{% endembed %}

## How

{% hint style="warning" %}
**UNIX** is needed
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
So keep gradle to version 4.2.2:

```
dependencies {
    classpath 'com.android.tools.build:gradle:4.2.2'
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
