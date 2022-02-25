# Unique ID

## Noob

```
val deviceId =
    Settings.Secure.getString(activity.getContentResolver(), Settings.Secure.ANDROID_ID)
val currentTimeMillisStr = System.currentTimeMillis().toString()
val uniqueId = deviceId + currentTimeMillisStr
```
