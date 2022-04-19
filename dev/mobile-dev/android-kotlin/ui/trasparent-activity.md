# Trasparent Activity



```typescript
@Override
public void onCreate(Bundle savedInstanceState) {
    // Set a Translucent NoTitleBar theme before calling super.onCreate()
    setTheme(android.R.style.Theme_Translucent_NoTitleBar);

    super.onCreate(savedInstanceState);
}
```

```kotlin
if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.R) {
    setTranslucent(true)
    window.setBackgroundDrawable(ColorDrawable(Color.TRANSPARENT))
}
```

### method 3

In res/values/style.xml:

```
<style name="Theme.Transparent" parent=""Theme.AppCompat.NoActionBar">  
    <item name="android:windowIsTranslucent">true</item>  
    <item name="android:windowBackground">@android:color/transparent</item>  
    <item name="android:windowContentOverlay">@null</item>  
    <item name="android:windowNoTitle">true</item>  
    <item name="android:windowIsFloating">true</item>  
    <item name="android:backgroundDimEnabled">false</item>
</style>
```

and in manifest in activity tag:

```csharp
 android:theme="@style/Theme.Transparent"
```
