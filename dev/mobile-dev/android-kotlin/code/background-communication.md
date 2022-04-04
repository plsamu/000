# Background Communication

## Real Background Comunication

### ReceiverApp

#### AndroidManifest

```kotlin
<receiver
    android:name=".MyBroadcastReceiver"
    android:exported="true">
    <intent-filter>
        <action android:name="MY_ACTION" />
    </intent-filter>
</receiver>
```

```kotlin
class MyBroadcastReceiver : BroadcastReceiver() {
    private val TAG = MyBroadcastReceiver::class.simpleName
    
    override fun onReceive(context: Context?, intent: Intent?) {
        Toast.makeText(context, "Intent Detected.", Toast.LENGTH_LONG).show()
    
        intent?.let {
            it.extras?.let { bundle ->
                val key = bundle.getString("key")
                Log.d(TAG, key!!)
            }
        }
    }
}
```

### SenderApp

This code actually sends the broadcast to all the receiver that are registered to the action called “MY\_ACTION”.

`ComponentName` is explicitly defining (recursivly) app name (`receiver.activityInfo.applicationInfo.packageName`) and service name (`receiver.activityInfo.name`): this is called _**explicit broadcast**._

```kotlin
findViewById<Button>(R.id.btn_2).setOnClickListener {
    var outIntent = Intent("MY_ACTION")
    val receivers = this.packageManager.queryBroadcastReceivers(outIntent, 0)
    for (receiver in receivers) {
        Log.d(
            "Sender", String.format(
                "Polling %s\\n%s",
                receiver.activityInfo.applicationInfo.packageName,
                receiver.activityInfo.name
            )
        )
        val cn = ComponentName(
            receiver.activityInfo.applicationInfo.packageName,
            receiver.activityInfo.name
        )
        outIntent = Intent("MY_ACTION")
        outIntent.putExtra("key", "1234")
        outIntent.component = cn
        sendBroadcast(outIntent)
    }
}
```
