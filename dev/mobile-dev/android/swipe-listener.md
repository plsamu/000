# Swipe Listener

```kotlin
class MainActivity : AppCompatActivity() {

    private val TAG = MainActivity::class.java.simpleName

    private lateinit var swipeListenerDetector : GestureDetectorCompat
    private val swipeListener = object : GestureDetector.SimpleOnGestureListener() {

        private val swipeThreshold = 100
        private val swipeVelocityThreshold = 100

        override fun onFling(
            e1: MotionEvent?,
            e2: MotionEvent?,
            velocityX: Float,
            velocityY: Float
        ): Boolean {
            try {
                val diffY = e2!!.y - e1!!.y
                val diffX = e2.x - e1.x
                if (abs(diffX) > abs(diffY)) {
                    if (abs(diffX) > swipeThreshold && abs(velocityX) > swipeVelocityThreshold) {
                        if (diffX > 0) {
                            Toast.makeText(
                                applicationContext,
                                "Left to Right swipe gesture",
                                Toast.LENGTH_SHORT
                            ).show()
                        } else {
                            Toast.makeText(
                                applicationContext,
                                "Right to Left swipe gesture",
                                Toast.LENGTH_SHORT
                            ).show()
                        }
                    }
                }
            } catch (exception: Exception) {
                exception.printStackTrace()
            }
            return true
        }
    }

    override fun onTouchEvent(event: MotionEvent?): Boolean {
        swipeListenerDetector.onTouchEvent(event)
        return super.onTouchEvent(event)
    }

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        supportFragmentManager
            .beginTransaction()
            .add(R.id.frags_containter, MyFrag1())
            .commit()

        swipeListenerDetector = GestureDetectorCompat(this, swipeListener)
    }

}
```
