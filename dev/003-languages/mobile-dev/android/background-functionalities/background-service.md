# Background Service

### minimal example

#### start the service from something like an Activity

```kotlin
ContextCompat.startForegroundService(
    context,
    Intent(context, MyService::class.java)
)
```

#### minimal service

{% hint style="warning" %}
Use Thread for async !!
{% endhint %}

{% embed url="https://stackoverflow.com/questions/68696064/android-jobintentservice-is-deprecated" %}

```kotlin
class MyService : Service() {

    override fun onBind(p0: Intent?): IBinder? {
        return null
    }

    val CHANNEL_ID = MyService::class.java.simpleName

    override fun onStartCommand(intent: Intent?, flags: Int, startId: Int): Int {
        getSystemService(NotificationManager::class.java)
            .createNotificationChannel(
                NotificationChannel(
                    CHANNEL_ID,
                    "MyService Channel",
                    NotificationManager.IMPORTANCE_DEFAULT
                )
            )
        val notification = NotificationCompat.Builder(this, CHANNEL_ID).build()
        startForeground(1, notification)
        return START_STICKY
    }

}
```

### IntentService - deprecated

{% embed url="https://stackoverflow.com/questions/18526131/how-to-run-service-not-on-main-thread" %}
