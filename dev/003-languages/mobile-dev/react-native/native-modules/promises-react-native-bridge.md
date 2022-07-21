# Promises - React Native Bridge

## [com.facebook.react.bridge.Promise](https://github.com/facebook/react-native/blob/main/ReactAndroid/src/main/java/com/facebook/react/bridge/Promise.java)

```kotlin
 promise.resolve(true)
```

```
val results: MutableList<Int> = ArrayList()
results.add(AUTHENTICATION_TYPE_FACIAL_RECOGNITION)
promise.resolve(results)
```

## expo.modules.core.Promise

```kotlin
promise.resolve(    
    Bundle().apply {        
        putBoolean("success", false)        
        putString("error", convertErrorCode(errMsgId))        
        putString("warning", errString.toString())    
    }
)
```

## From Kotlin to JS

### WritableNativeMap

```kotlin
@ReactMethod
fun checkArr(arr: ReadableArray, promise: Promise) {
    val map1: Map<String, Boolean> = // something
    val output = WritableNativeMap()
    map1.forEach { entry ->
        output.putBoolean(entry.key, entry.value)
    }
    promise.resolve(output)
}
```

```kotlin
export function checkArr(datarr: string[]): Promise<{ [key: string]: boolean }> {
  return ReputationModule.checkArr(datarr);
}
```
