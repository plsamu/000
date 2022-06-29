# Toolbar

## Method 1

### 0) Import & dependencies

```xml
implementation 'androidx.appcompat:appcompat:1.4.1'
```

```kotlin
import androidx.appcompat.app.AppCompatActivity
import androidx.appcompat.widget.Toolbar
```

### 1) Set the Theme

themes.xml

```xml
<resources xmlns:tools="http://schemas.android.com/tools">
    <style name="Theme.AppTheme" parent="Theme.MaterialComponents.DayNight.NoActionBar">
```

"NoActionBar" is the important part.

### 2) Create the layout

m\_toolbar.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.appcompat.widget.Toolbar
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/m_toolbar"
    android:layout_width="match_parent"
    android:background="?attr/colorPrimary"
    android:layout_height="?attr/actionBarSize">

</androidx.appcompat.widget.Toolbar>
```

### 3) Include in activity or fragment

```xml
<include
        android:id="@+id/m2_toolbar"
        layout="@layout/m_toolbar" />
```

### 4) Reference the Toolbar

```kotlin
 override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_permissions)
        val toolbar = findViewById<Toolbar>(R.id.m2_toolbar)
        setSupportActionBar(toolbar)
        toolbar.title = "Simple Sample"
        toolbar.setNavigationIcon(R.drawable.back_arrow)
        toolbar.setNavigationOnClickListener {
            onBackPressed()
        }
```
