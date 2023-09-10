# Hiya!  
Today I'm going to Implement Fragment Theory  
Here's what I did:  
### 1.  Creating new project with the following criteria:  
``
Project Name: Fraction     
TargetSDK: 24  
Empty Views Activity: MainActivity
Kotlin
``  
### 2.  Create a new fragment file  
make a new blank fragment
### 3.  Creating a the fragment xml  
we will be making a simple fragment page with 1 TextView and 1 Button  
> Xml file: Fragment_home.xml  
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".HomeFragment"
    android:orientation="vertical">

    <!-- TODO: Update blank fragment layout -->
    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:padding="40dp"
        android:text="@string/Title"
        android:textSize="60dp" />

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="@string/sub1"
        android:padding="40dp"

        />
    <Button
        android:id="@+id/gateFragment"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Fragment"
        android:layout_gravity="center"
        android:backgroundTint="@color/black"/>

</LinearLayout>
```

### 4.  Adjusting the Fragment file  
Go to the HomeFragment.kt and delete the unnecessary lines, and add these code lines:  
```kotlin
    override fun onViewCreated(view: View, savedInstanceState: Bundle?) {
        super.onViewCreated(view, savedInstanceState)
        val btnCategory:Button = view.findViewById(R.id.gateFragment)
        btnCategory.setOnClickListener(this)
    }

```  
Your whole HomeFragment.kt file will look like this  
```kotlin
class HomeFragment : Fragment(), View.OnClickListener {

    override fun onCreateView(
        inflater: LayoutInflater, container: ViewGroup?,
        savedInstanceState: Bundle?
    ): View? {
        // Inflate the layout for this fragment
        return inflater.inflate(R.layout.fragment_home, container, false)
    }


    override fun onViewCreated(view: View, savedInstanceState: Bundle?) {
        super.onViewCreated(view, savedInstanceState)
        val btnCategory:Button = view.findViewById(R.id.gateFragment)
        btnCategory.setOnClickListener(this)
    }

    override fun onClick(v: View?) {
        TODO("Not yet implemented")
    }


}
```  
And for the final touch, add these lines to MainActivity.kt  
```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val fragmentManager = supportFragmentManager
        val homeFragment = HomeFragment()
        val fragment = fragmentManager.findFragmentByTag(HomeFragment::class.java.simpleName)

        if (fragment !is HomeFragment){
            Log.d("MyFlexibleFragment", "Fragment Name:"+ HomeFragment::class.java.simpleName)
            fragmentManager
                .beginTransaction()
                .add(R.id.home, homeFragment, HomeFragment::class.java.simpleName)
                .commit()

        }


    }
}
```  

| Code                                 | Description                                                                                                        |
|--------------------------------------|--------------------------------------------------------------------------------------------------------------------|
| OnCreateView                         | this method will be working first when the whole code running                                                      |
| inflate                              | this method transforms xml layout to object view                                                                   |
| OnViewCreated                        | this methold will be executed after OnCreateView method, here we can declare  <br/> new view and set it's listener |
| view.findViewById(R.id.gateFragment) | casting in the OnViewCreated method slighty different from normal casting,                                         |



















