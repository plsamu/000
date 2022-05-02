# Intents

### Print all Intents

```kotlin
val bundle = intent.extras
if (bundle != null) {
    for (key in bundle.keySet()) {
            Log.e(TAG, key + " : " + if (bundle[key] != null) bundle[key] else "NULL")
    }
}
```
