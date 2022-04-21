# NotificationBuilder

### minimal

```kotlin
notificationBuilder = NotificationCompat.Builder(this, CHANNEL_ID)
```

### example 1

```kotlin
notificationBuilder = NotificationCompat.Builder(this, CHANNEL_ID)
    .setContentTitle("Foreground Service")
    .setContentText("Content Text")
    .setSmallIcon(R.drawable.ic_shield_img)
    // .setContentIntent(pendingIntent)
    // .setCustomContentView(remoteViews)
    .setStyle(NotificationCompat.DecoratedCustomViewStyle())
    .setColor(
        ContextCompat.getColor(
            this,
            androidx.appcompat.R.color.primary_material_dark
        )
    )
    .addAction(startAction)
    .addAction(stopAction)
    .addAction(stopServiceAction)
```
