# Creating-Splash-Screen-Using-Kotlin

Here are the steps for creating splash screen in android studio using kotlin.

1. Add logo image to the drawable folder.
   Image= png form + has less size than 200kb + name should be in small letters and must have no space(no special characters except underscore).
   
2. Create a new Empty Activity "in the package folder" by name SplashScreenActivity. 
   Both SplashScreenActivity.xml (layout file) and SplashScreenActivity.kt (.kt file) is created automatically.
 
3. Add the logo image and text views to the splash screen layout file i.e. in SplashScreenActivity.xml file.
   Also set the background colour of the constraint/linear layout/relative layout.
   
4. In the themes folder, in the theme.xml file , add the following code:
 
   <style name="splashBackground" parent="Theme.MaterialComponents.DayNight.NoActionBar">
        <item name="android:windowBackground">"@drawable/activity_splash" </item>
    </style>     
    
    -> We can use any style and item name.
    -> In the parent theme, we will assingn the value as "No Action Bar" becoz, usually the action bar is hidden in splash screen.
    => Add the same code to theme.xml(night) file, so that the style will be applied on the dark theme of the app too.
    
5. Add the following code in the SplashScreenActivity.kt file : 
   
   val time:Long=2000
   (If we want the time of appearance of splash screen to be 1 sec..use 1000
                                                             2 sec..use 2000
                                                             3 sec..use 3000
                                                             and so on.....)

   Handler().postDelayed ( Runnable {
   val intent= Intent (SplashScreenActivity@this,MainActivity::class.java)
   startActivity (intent)
   finish () },time)
   
   -> Don't forget to import Handler and Intent.
   
6. Make the following changes in the AndroidManifest.xml file : 
   
   -> Make the SplashScreenActivity activity the launcher activity.
   (launcher activity is the activity which run first when the app is lauched.)
   
   -> Add the theme style which we have defined in the themes.xml file.
   
      Add the following code:
      
    // existing code of manifest file 
      
      <?xml version="1.0" encoding="utf-8"?>
      <manifest xmlns:android="http://schemas.android.com/apk/res/android"
      package="com.anandini.package">

        <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.FoodRunnerApp"> -->
          
      // existing code of manifest file 
          
   --------------------------------------------------------------------------------------------------
          
      //code for adding theme file and making the splash screen activity the launcher activity.
      
         <activity
            android:name=".SplashScreenActivity" android:theme="@style/splashBackground"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
         </activity>
        
      //code for adding theme file and making the splash screen activity the launcher activity.
      
   --------------------------------------------------------------------------------------------------      
          
          
      // existing code of manifest file 
          
        <activity
            android:name=".MainActivity"
            android:exported="true">
        </activity>
      </application> -->
     </manifest>
     
   // existing code of manifest file 

HURRAY..!! YOUR APP IS READY TO DISPLAY SPLASH SCREEN.
