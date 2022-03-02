# Headers

```kotlin
@Headers("Content-Type: application/json")
@POST("auth")
fun getWireguardConnConf(
    @Header("Authorization") token: String,
    @Body body: MyRequestObject
): Call<MyResponseObject>
```
