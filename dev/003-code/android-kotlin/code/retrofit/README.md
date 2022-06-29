# Retrofit

## Client + API + Raw response

```kotlin
interface mRetrofitClientApi {

    companion object {
        fun getInstance(): mRetrofitClientApi {
            val interceptor = HttpLoggingInterceptor()
            interceptor.level = HttpLoggingInterceptor.Level.BODY
            val client: OkHttpClient = OkHttpClient.Builder().addInterceptor(interceptor).build()

            val retrofit = Retrofit.Builder()
                .baseUrl(BuildConfig.ENDPOINT_BASE_URL)
                .client(client)
                .addConverterFactory(GsonConverterFactory.create())
                .build()

            return retrofit.create(mRetrofitClientApi ::class.java)
        }
    }

    @GET("regions")
    fun getServers(
        @Query("type") type: String,
        @Query("lang") lang: String,
    ): Call<ResponseBody> // raw body response

}
```

### How to read the response

```kotlin
val call = mRetrofitClientApi .getInstance()
    .getServers("type1", "en_EN")

call.enqueue(object : retrofit2.Callback<ResponseBody> {
    override fun onResponse(call: Call<ResponseBody>, response: Response<ResponseBody>) {
        Log.d(TAG, response.message())
    }

    override fun onFailure(call: Call<ResponseBody>, t: Throwable) {
        Log.e(TAG, "", t)
    }

})
```
