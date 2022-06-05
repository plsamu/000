# Log

## Log Levels

* **TRACE**
* **DEBUG**
* **INFO**
* **WARN**
* **ERROR**
* **FATAL**

### Example

```
[dependencies]
log = { version = "0.4.0", features = ["max_level_trace", "release_max_level_warn"] }
```

**`max_level_trace`**

Will log, **in debug mode**, everything: trace, debug, info, warn, error, fatal.

**`release_max_level_warn`**

Will log, **in release mode:** warn, error, fatal

## Sources

{% embed url="https://www.youtube.com/watch?v=7wQfqNiY-mY" %}
