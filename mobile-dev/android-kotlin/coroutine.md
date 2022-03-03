# Coroutine

## NonBlocking

### GlobalScope

```
GlobalScope.launch {
    // TODO GlobalScope is delicate and should be replaced
}
```

`GlobalScope.launch(Dispatchers.IO) { }` is the same as `CoroutineScope(Dispatchers.IO).launch{}`

{% hint style="info" %}
`Anyway use CoroutineScope`
{% endhint %}

### NonBlocking lifecyclescope

```
activity.lifecycleScope.launch {
    withContext(Dispatchers.IO) { 
        // code
    }
}
```

## RunBlocking

```
fun main() {
    runBlocking {
        launch {
            checkForInternet()
            makeAPIRequest()
        }
        log("This will be printed first.")
    }
    log("This will be printed last.")
}
```

```
runBlocking {
    // blocking context
    withContext(Dispatchers.IO) {
        // detach from main thread
    }
}
```

## Good Sources

* [https://stackoverflow.com/questions/65008486/globalscope-vs-coroutinescope-vs-lifecyclescope](https://stackoverflow.com/questions/65008486/globalscope-vs-coroutinescope-vs-lifecyclescope)
