# Singleton

## Lazy initialization with thread safe

### Lazy init

{% hint style="info" %}
Lazy initialization avoids initializing a value until the first time it is accessed.
{% endhint %}

### Thread safe

{% hint style="info" %}
If the static method might be called from multiple threads simultaneously, measures may need to be taken to prevent [race conditions](https://en.wikipedia.org/wiki/Race\_condition) that could result in the creation of multiple instances.


{% endhint %}

```java
public class Singleton {

    private static volatile Singleton INSTANCE = null;

    private Singleton() {}  // hide constructor (private constructor)

    public static Singleton getInstance() {
        // removing the 1° IF will result in forcing all threads to check
        // the (INSTANCE == null) one by one in the 2° IF because of 
        // the synchronized.
        if (INSTANCE == null) {  
            synchronized(Singleton.class) {
                if (INSTANCE == null)
                    INSTANCE = new Singleton();
            }
        }
        return instance;
    }
}
```
