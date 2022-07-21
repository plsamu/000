# Send file to an app

```xml
<application>	
	<activity
      android:name=".FileReceiver"
      android:enabled="true"
      android:exported="true">
      <intent-filter>
          <action android:name="android.intent.action.SEND" />
          <category android:name="android.intent.category.DEFAULT" />
          <data android:mimeType="*/*" />
      </intent-filter>
  </activity>

</application>
```

```kotlin
class FileReceiver : AppCompatActivity() {
    private val TAG = FileReceiver::class.java.simpleName
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        val dataStr = intent?.dataString
        Log.d(TAG, dataStr!!)
    }
}
```
