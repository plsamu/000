# Current Time

## In Millis

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

## [From Instant to TimeStamp](https://stackoverflow.com/questions/49862357/how-do-i-get-the-current-time-as-a-timestamp-in-kotlin)

```kotlin
if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
    println(DateTimeFormatter.ISO_INSTANT.format(Instant.now()))
}

// I/System.out: 2022-03-23T11:39:46.370Z
```
