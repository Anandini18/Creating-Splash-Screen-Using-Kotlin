# Creating Splash Screen Using Kotlin

Here are the steps for creating splash screen in android studio using kotlin.

1. Add logo image to the drawable folder. <br/>
   Image= png form + has size less than 200kb + name should be in small letters and must have no space(no special characters except underscore).
   
2. Create a new Empty Activity "in the package folder" by name SplashScreenActivity. <br/>
   Both SplashScreenActivity.xml (layout file) and SplashScreenActivity.kt (.kt file) is created automatically.
 
3. Add the logo image and text views to the splash screen layout file i.e. in SplashScreenActivity.xml file.<br/>
   Also set the background colour of the constraint/linear layout/relative layout.
   
4. In the themes folder, in the theme.xml file , add the following code:<br/>
 
   <style name="splashBackground" parent="Theme.MaterialComponents.DayNight.NoActionBar"> <br/>
    </style> <br/>    
    
    -> We can use any style name.<br/>
    -> In the parent theme, we will assingn the value as "No Action Bar" becoz, usually the action bar is hidden in splash screen.<br/>
    => Add the same code to theme.xml(night) file, so that the style will be applied on the dark theme of the app too.<br/>
    
5. Add the following code in the SplashScreenActivity.kt file : <br/>
   
   val time:Long=2000<br/>
   (If we want the time of appearance of splash screen to be 1 sec..use 1000<br/>
                                                             2 sec..use 2000<br/>
                                                             3 sec..use 3000<br/>
                                                             and so on.....)<br/>

   Handler().postDelayed ( Runnable {<br/>
   val intent= Intent (SplashScreenActivity@this,MainActivity::class.java)<br/>
   startActivity (intent)<br/>
   finish () },time)<br/>
   
   -> Don't forget to import Handler and Intent.<br/>
   
6. Make the following changes in the AndroidManifest.xml file : <br/>
   
   -> Make the SplashScreenActivity activity the launcher activity.<br/>
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
      
   --------------------------------------------------------------------------------------------------      
          
      // existing code of manifest file 
          
        <activity
            android:name=".MainActivity"
            android:exported="true">
        </activity>
      </application> 
     </manifest>
     

                     ---------------|||||   HURRAY..!! YOUR APP IS READY TO DISPLAY SPLASH SCREEN.   |||||---------------
