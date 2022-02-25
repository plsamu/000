# FormUrlEncoded

## Example 1

```kotlin
@FormUrlEncoded
@POST("wg/auth")
fun getConf(
    @Field("device_id") deviceId: String,
    @Field("pubkey") pubkey: String,
): Call<ResponseBody>
```

## Example to test

```kotlin
@Headers({
    "Content-Type: application/x-www-form-urlencoded",
    "accept-encoding: gzip, deflate",
    "access_token: mtlNzTVmXP4IBSba3z4XXXX",
    "Authorization: Basic a2FtaWwua2ljaW5za2lAc3R1ZGVudC53YXQuZXXX"
})
@FormUrlEncoded
@POST("/auth")
fun login(
    @Field("access_token") String authKey
): Call<ResponseBody>
```
