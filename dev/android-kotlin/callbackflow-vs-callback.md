# CallbackFlow vs Callback

IDK, did this:

```kotlin
class MyCallback<T : Any>(var result: T, val error: Exception? = null)
```
