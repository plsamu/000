# Notifications

## Sources

* [https://medium.com/fueled-engineering/testing-fcm-notifications-like-a-pro-e3db32d87e84](https://medium.com/fueled-engineering/testing-fcm-notifications-like-a-pro-e3db32d87e84)
* [https://stackoverflow.com/questions/56901253/is-there-a-tool-to-test-mobile-push-notifications-without-having-actual-mobile](https://stackoverflow.com/questions/56901253/is-there-a-tool-to-test-mobile-push-notifications-without-having-actual-mobile)
  * [https://medium.com/android-school/test-fcm-notification-with-postman-f91ba08aacc3](https://medium.com/android-school/test-fcm-notification-with-postman-f91ba08aacc3)

## Notification channel

```kotlin
if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O)    
    notificationManager.createNotificationChannel(        
        NotificationChannel(            
            channelId,            
            context.getString(R.string.notification_recognition),            
            NotificationManager.IMPORTANCE_LOW        
        )    
    )
```
