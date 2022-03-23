# Current Time in Milliseconds

```kotlin
import java.util.*

// method 1
val calendar = Calendar.getInstance()
println(calendar.timeInMillis)

// method 2
println(System.currentTimeMillis())
```

### Mind the Date, isn't in millis

```
Log.d(TAG, System.currentTimeMillis().toString())
Log.d(TAG, Date().toString())
```

Output

```
1645630448874
Wed Feb 23 16:34:08 GMT+01:00 2022
```
