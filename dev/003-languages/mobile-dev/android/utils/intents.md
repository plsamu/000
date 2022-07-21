# Intents

### Print all Intents

```kotlin
// print intent
Log.e(TAG, intent.toString())

// print intent extras
val bundle = intent.extras
if (bundle != null) {
    for (key in bundle.keySet()) {
            Log.e(TAG, key + " : " + if (bundle[key] != null) bundle[key] else "NULL")
    }
}
```
