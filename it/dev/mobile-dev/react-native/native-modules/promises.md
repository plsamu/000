# Promises

## [com.facebook.react.bridge.Promise](https://github.com/facebook/react-native/blob/main/ReactAndroid/src/main/java/com/facebook/react/bridge/Promise.java)

```kotlin
 promise.resolve(true)
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
