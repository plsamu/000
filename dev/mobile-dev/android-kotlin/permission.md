# Permission

{% embed url="https://stackoverflow.com/questions/38480671/android-m-onrequestpermissionsresult-in-non-activity" %}

You cannot also create the activity first then call it...

```kotlin
val mActivity = MyActivity().apply {    
    this.callback = callback
}

val intent = Intent(context, activityPermission)
context.startActivity(intent)
```

### Can be useful

```
implementation "org.jetbrains.kotlin:kotlin-serialization:$kotlin_version"
```

```
import java.io.Serializableclass ParcellableUnit() : Serializable { 
    private var callback: ((MyCallback<Boolean>) -> Unit)? = null
}
```
