# Basics

## If != null else === let with [Elvis operator](https://kotlinlang.org/docs/reference/null-safety.html#elvis-operator)

```kotlin
mutableProperty?.let {
    doSomething(it)
} ?: run {
    doOtherThing()
    doOtherThing()
}
```
