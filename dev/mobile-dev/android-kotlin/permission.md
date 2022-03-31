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
