# Project

### Modules

A *module* is a collection of source files and build settings that allow you to divide your project into discrete units of functionality

* **Android app module**
* **Dynamic feature module** : used in instant apps
* **Library module** : Provides a container for your reusable code
  * Android Library
  * Java Library
* **Google Cloud module** : Google Cloud backend code

### Project

- mainfest
- java
- res

### Manifest

every mainfest has :

- The app's package name
- the components of the app
- The permissions
- The hardware and software features the app requires



```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:versionCode="1"
    android:versionName="1.0"
    package="com.example.myapp">
            android:theme="@style/AppTheme">
		<uses-permission android:name="android.permission.SEND_SMS"/>
 		<uses-feature android:name="android.hardware.sensor.compass"
                  android:required="true" />
    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:label="@string/app_name"
        android:supportsRtl="true"

        <!-- This name is resolved to com.example.myapp.MainActivity based upon the package attribute -->
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

        <activity
            android:name=".DisplayMessageActivity"
            android:parentActivityName=".MainActivity" />
    </application>
</manifest>
```





