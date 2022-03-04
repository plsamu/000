# \[NOT WORKING] Start

## Examples

* [https://github.com/ios122/kotlin-module-sample-for-reactnative/tree/master/MyReactNativeApp](https://github.com/ios122/kotlin-module-sample-for-reactnative/tree/master/MyReactNativeApp)
* [https://bitfrit.com/writing-a-native-module-for-react-native-using-kotlin/](https://bitfrit.com/writing-a-native-module-for-react-native-using-kotlin/)

## Dependencies

Add dependency:

```
implementation "com.facebook.react:react-native:0.20.1"
```

## Create  a test module

```kotlin
class NativeModule1 internal constructor(context: ReactApplicationContext?) :
    ReactContextBaseJavaModule(context) {
    
    private val TAG = NativeModule1::class.simpleName
    
    override fun getName() = TAG!!
    
    @ReactMethod
    fun logSomething(name: String, location: String) {
        Log.d(TAG, "Create event called with name: $name and location: $location")
    }
}
```

## Create Packager

```kotlin
import android.view.View
import com.facebook.react.ReactPackage
import com.facebook.react.bridge.JavaScriptModule
import com.facebook.react.bridge.NativeModule
import com.facebook.react.bridge.ReactApplicationContext
import com.facebook.react.uimanager.ReactShadowNode
import com.facebook.react.uimanager.ViewManager
import java.util.*
import kotlin.collections.ArrayList

class MyAppPackage : ReactPackage {

    override fun createViewManagers(reactContext: ReactApplicationContext?): MutableList<ViewManager<View, ReactShadowNode>> {
        return Collections.emptyList()
    }

    override fun createNativeModules(
        reactContext: ReactApplicationContext
    ): List<NativeModule> {
        val modules: MutableList<NativeModule> = ArrayList()
        modules.add(NativeModule1(reactContext))
        return modules
    }

    override fun createJSModules(): MutableList<Class<out JavaScriptModule>> {
        return Collections.emptyList()
    }

}
```

{% hint style="danger" %}
This way of registering native modules eagerly initializes all native modules when the application starts, which adds to the startup time of an application.
{% endhint %}

## Add package to the queue

`MyAppPackage` has to be added to the list of packages returned in ReactNativeHost's `getPackages()` method.

Go to: `android/app/src/main/java/com/your-app-name/MainApplication.java and add:`

```
packages.add(new MyAppPackage());
```

## Optional

```java
npx react-native link
```

## Errors

### cannot find symbol&#x20;

{% hint style="success" %}
I was calling a kotlin class from a Java class.\
Do everything in kotlin or do everything in java.\
Do not mix.
{% endhint %}

```bash
# 1. delete .gradle folder
# 2. run this command
.\gradlew.bat clean
# 3. delete node_modules file
# 4. reinstall
npm install
```

* [https://stackoverflow.com/questions/49542654/react-native-error-cannot-find-symbol-after-upgrade](https://stackoverflow.com/questions/49542654/react-native-error-cannot-find-symbol-after-upgrade)

## raw

// ---- method 1 ---- // import { NativeModules } from 'react-native'; // const { NativeModule1 } = NativeModules; // NativeModule1.logsomething('1', '2')

// ---- method 2 ---- // import { requireNativeComponent } from 'react-native' // const NM1 = requireNativeComponent('NativeModule1',)
