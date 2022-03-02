# Database Client

## Logger Simple Sample Database

### Sample Log Object

```kotlin
enum class LogType {
    app, vpn, a2a, mov
}

class LogJSON(
    var datetime: String,
    var event: String,
    var description: String?
)

```

### DB connection

```kotlin
@Database(entities = [AppLog::class], version = 1)
@TypeConverters(Converters::class)
abstract class AppDatabase : RoomDatabase() {
    abstract fun appLog(): AppLogDao
}
```

### Converters

Android Room (SQLite) do not support saving JSON, but you can provide methods to automatically convert them to string and get them as object (see [DAO](database-client.md#dao-applogdao)).

```kotlin
class Converters {

    @TypeConverter
    fun fromLogTypeToString(logType: LogType): String {
        return logType.name
    }

    @TypeConverter
    fun fromStringToLogType(logTypeString: String): LogType {
        return LogType.valueOf(logTypeString)
    }
    
    @TypeConverter
    fun fromLogJSONToString(logJSON: LogJSON): String {
        val strOut = JSONObject()
        try {
            strOut.put("datetime", logJSON.datetime)
            strOut.put("event", logJSON.event)
            logJSON.description?.let {
                strOut.put("description", it)
            }
        } catch (e: JSONException) {
            e.printStackTrace()
        }
        return strOut.toString()
    }

    @TypeConverter
    fun fromStringToLogJSON(logJSONString: String): LogJSON {
        var datetimeStr: String? = null
        var eventStr: String? = null
        var descriptionStr: String? = null
        val obj = JSONObject(logJSONString)
        try {
            datetimeStr = obj.getString("datetime")
            eventStr = obj.getString("event")
        } catch (e: Exception) {
            e.printStackTrace()
        }

        try {
            descriptionStr = obj.getString("description")
        } catch (e: Exception) {
        }

        return LogJSON(
            datetimeStr!!,
            eventStr!!,
            descriptionStr
        )
    }
}
```

### Entity - AppLog

For example, a "type" can be saved thanks to [Converters](database-client.md#converters).

```kotlin
@Entity(tableName = LOG_TABLE_NAME)
data class AppLog(
    @ColumnInfo(name = "datetime")
    var datetime: String,

    @ColumnInfo(name = "user_id")
    var userId: String,

    @ColumnInfo(name = "type")
    var type: LogType,

    @ColumnInfo(name = "payload")
    var payload: LogJSON
) {
    @PrimaryKey(autoGenerate = true)
    var uid: Int = 0
}
```

### DAO - AppLogDao

```kotlin
@Dao
interface AppLogDao {
    @Query("SELECT * FROM $LOG_TABLE_NAME")
    fun getAll(): List<AppLog>

    @Query("SELECT * FROM $LOG_TABLE_NAME WHERE uid IN (:userIds)")
    fun loadAllByIds(userIds: IntArray): List<AppLog>

    @Insert
    fun insert(log: AppLog)

    @Insert
    fun insertAll(vararg logs: AppLog)

    @Delete
    fun delete(log: AppLog)
}
```

### Client - DBClient

```kotlin
class DBClient private constructor(context: Context) {

    // Singleton
    companion object {
        private var mInstance: DBClient? = null
        @Synchronized
        fun getInstance(context: Context): DBClient? {
            if (mInstance == null) {
                mInstance = DBClient(context)
            }
            return mInstance
        }
    }

    private val db = Room
        .databaseBuilder(context, AppDatabase::class.java, DATABASE_NAME)
        .fallbackToDestructiveMigration()
        .build()

    fun getAppDatabaseInstance(): AppDatabase {
        return db
    }

}
```
