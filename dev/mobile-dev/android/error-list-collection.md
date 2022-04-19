# Error List Collection

## Bad notification for startForeground

```
E/AndroidRuntime: FATAL EXCEPTION: main
    Process: com.example.appname:service, PID: 4179
    android.app.RemoteServiceException: Bad notification for startForeground
        at android.app.ActivityThread$H.handleMessage(ActivityThread.java:2005)
        at android.os.Handler.dispatchMessage(Handler.java:106)
        at android.os.Looper.loop(Looper.java:223)
        at android.app.ActivityThread.main(ActivityThread.java:7656)
        at java.lang.reflect.Method.invoke(Native Method)
        at com.android.internal.os.RuntimeInit$MethodAndArgsCaller.run(RuntimeInit.java:592)
        at com.android.internal.os.ZygoteInit.main(ZygoteInit.java:947)
```

{% hint style="warning" %}
You need to use coroutines, or a thread.\
Do NOT run background services in the main thread!!
{% endhint %}

### Notification context

Talking about notification, if version is over API level 26 you need to create a channel:

```kotlin
class NotificationHelper(private val activity: AppCompatActivity) : CoroutineScope {

    private val job = Job()
    override val coroutineContext = Dispatchers.IO + job
    
    fun start() {
        val notification = createNotification(activity)
        setNotification(notification)
    }
    
    private fun createNotification(context: Context): NotificationCompat.Builder {
       
        val notificationManager =
            context.getSystemService(Context.NOTIFICATION_SERVICE) as NotificationManager

        val channelId = NOTIFICATION_CHANNEL
        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
            notificationManager.createNotificationChannel(
                NotificationChannel(
                    channelId,
                    context.getString(R.string.notification_name),
                    NotificationManager.IMPORTANCE_LOW
                )
            )
        }

        val builder = NotificationCompat.Builder(context, channelId)
            .setSmallIcon(R.drawable.ic_notification)
            .setContentTitle(context.getString(R.string.title))
            .setChannelId(channelId)
        builder.setVisibility(NotificationCompat.VISIBILITY_PUBLIC)
        builder.setWhen(System.currentTimeMillis())
        builder.setShowWhen(true)
        builder.priority = NotificationCompat.PRIORITY_MIN
        builder.setOngoing(true)
        return builder
    }
    
}
```

{% hint style="warning" %}
What is important:

* CoroutineScope
* private val job = Job()
* override val coroutineContext = Dispatchers.IO + job
{% endhint %}
