# Send and receive JSON

## Method 1

```kotlin
class WgRequestConf(
    @SerializedName("device_id")
    var deviceId: String = "",
    var pubkey: String = ""
)

class WgResponseConf(
     @SerializedName("client_ipv4")
     var clientIpv4: String = "",
     @SerializedName("client_ipv6")
     var clientIpv6: String = "",
     @SerializedName("dns_ipv4")
     var dnsIpv4: Array<String>? = null,
     @SerializedName("dns_ipv6")
     var dnsIpv6: Array<String>? = null,
     var pubkey: String = "",
     var server: String = "",
     var port: Int? = null,
     @SerializedName("handshake_ttl")
     var handshakeTtl: String = ""
)

@Headers("Content-Type: application/json")
@POST("wg/auth")
fun getWireguardConnConf(
    @Header("Authorization") password: String,
    @Body body: WgRequestConf
): Call<WgResponseConf>
```

## Method 2

```kotlin
import com.google.gson.JsonArray
import okhttp3.ResponseBody

@Headers("Content-Type: application/json")
@POST("/default/LogCollector")
fun sendAllLogs(@Body body: JsonArray): Call<ResponseBody>
```
