# Time, Instant, Epoch

## Get current time

### In number

#### In millis

```kotlin
import java.util.*

// method 1
Calendar.getInstance().timeInMillis

// method 2
System.currentTimeMillis()
```

#### In seconds

```kotlin
val now = Instant.now().epochSecond
```

### In formatted string

#### general

```kotlin
// method 1
Date().toString() // Wed Feb 23 16:34:08 GMT+01:00 2022

// method 2
if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
    // 2022-04-22T10:14:11.626Z
    Instant.now()
}
```

#### ISO-8601 timestamp

{% embed url="https://stackoverflow.com/questions/49862357/how-do-i-get-the-current-time-as-a-timestamp-in-kotlin" %}

```kotlin
if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
    // 2022-03-23T11:39:46.370Z
    DateTimeFormatter.ISO_INSTANT.format(Instant.now())
}
```

## From string to epoch seconds

```kotlin
val isoInstantStr = DateTimeFormatter.ISO_INSTANT.format(Instant.now())

// {MicroOfSecond=39000, NanoOfSecond=39000000, MilliOfSecond=39, InstantSeconds=1650534855},ISO
DateTimeFormatter.ISO_INSTANT.parse(isoInstantStr)

// 1650534855
DateTimeFormatter.ISO_INSTANT.parse(isoInstantStr).getLong(ChronoField.INSTANT_SECONDS)
```



