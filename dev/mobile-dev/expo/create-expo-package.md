# Create Expo Package

A **module** is a single JavaScript file that has some reasonable functionality.

A **package** is a directory with one or more modules inside of it and a package.json file which has metadata about the package.

{% embed url="https://www.farhansayshi.com/post/build-an-npm-package-with-expo-dependencies-for-expo-and-plain-react-native-projects" %}

{% embed url="https://github.com/expo/expo/tree/main/packages/create-expo-module" %}

## How

{% hint style="warning" %}
**UNIX** is needed
{% endhint %}

### step 1

```
npx create-react-native-library my_package
npm install --save react-native-unimodules
npm install --save expo-updates
```

### step 2

Follow the installation guide here:

{% embed url="https://www.npmjs.com/package/expo-modules-core" %}



1. get a sample project
2. expo install
3. change modules code
4. pack
5. try to install&#x20;
