# Create native package

## Create and install local package

```
npx create-react-native-library my_package
cd ./my_package
npm pack
cp my_package.tgz ../path/to/react_native_proj
cd ../path/to/react_native_proj
npm install --save .\my_package.tgz 
```

```javascript
import * as MyModule from 'my_package'
MyModule.multiply(3, 4).then((result) => {
    console.log(result)
})
```

## Other things

{% embed url="https://stackoverflow.com/questions/44061155/react-native-npm-link-local-dependency-unable-to-resolve-module" %}
CHECK THIS
{% endembed %}

The `npm link` command doesn't work because React Native packager [doesn't support symlinks](https://github.com/facebook/metro-bundler/issues/1).

1. Use [haul packager](https://github.com/callstack/haul) in the example app. Haul supports symlinks, so you can use `npm link` as usual.
2. Use local dependency via `file:../` and then edit files in `node_modules` folder or reinstall every time you make changes.

I found [Haul](https://github.com/callstack/haul) to work great for this use-case and even set-up a [little starter project](https://github.com/pavloko/react-native-library-starter) that also includes [storybook](https://github.com/storybooks/storybook), which is really helpful if you have many components to switch between.

{% embed url="https://reactnative.dev/docs/native-modules-setup" %}

{% embed url="https://medium.com/wix-engineering/creating-a-native-module-in-react-native-93bab0123e46" %}

{% embed url="https://medium.com/@AidThompsin/how-to-npm-link-to-a-local-version-of-your-dependency-84e82126667a" %}

```
npm link --save <native-package>
npm unlink --no-save <native-package>
```
