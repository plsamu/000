# Fragments System

1. add `FragmentContainerView` to Activity
2. create fragment
3. add fragment&#x20;

```kotlin
class HomeFragment: Fragment() {
    companion object {
        fun newInstance() = HomeFragment()
    }
    
     override fun onCreateView(
        inflater: LayoutInflater,
        container: ViewGroup?,
        savedInstanceState: Bundle?
    ): View {
        val view = inflater.inflate(R.layout.fragment_home, container, false)
        return view
    }
}
```

```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        if (savedInstanceState == null) {
            supportFragmentManager
                .beginTransaction()
                .add(R.id.fragment_container_view_tag, HomeFragment.newInstance())
                .commit()
        }
    }
}
```
