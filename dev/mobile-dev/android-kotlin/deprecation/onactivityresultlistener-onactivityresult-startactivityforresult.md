# OnActivityResultListener - onActivityResult - startActivityForResult

```kotlin
var resultLauncher = 
    (currentActivity as AppCompatActivity).registerForActivityResult(
        ActivityResultContracts.StartActivityForResult()
    )        
    { result ->            
        if (result.resultCode == Activity.RESULT_OK) {                
            val data: Intent? = result.data            
        }        
    }
```

```kotlin
if (!Settings.canDrawOverlays(reactContext)) {    
    val intent = Intent(        
        Settings.ACTION_MANAGE_OVERLAY_PERMISSION,        
        Uri.parse("package:" + reactContext.packageName)    
    )      
    // currentActivity?.startActivityForResult(intent, 7001) OLD WAY    
    resultLauncher.launch(intent)
} 
```
