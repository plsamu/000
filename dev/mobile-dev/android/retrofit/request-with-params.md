# Request with params

```
www.url.net/api/films?director=<director_name>&year=<year>
```

```kotlin
class Film(
    @SerializedName("film_id")
    var filmId: Int? = null,
    var title: String? = null, 
)

@GET("/films")
fun getFilms(
    @Query("director") director: String,
    @Query("year") year: String,
): Call<List<Film>>
```
