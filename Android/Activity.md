# Activity

 provides the window in which the app draws its UI

To use activities in your app, you must register information about them in the app’s manifest

the only required attribute is name

```XML
<manifest ... >
  <application ... >
      <activity android:name=".ExampleActivity" />
      ...
  </application ... >
  ...
</manifest >
```

### Intent Filter

provide the ability to launch an activity based not only on an *explicit* request, but also an *implicit* one

action to specify the action that launch the activity

category of the action (optional)

date the type of data that activity expect as extra (optional)

```xml
<activity android:name=".ExampleActivity" android:icon="@drawable/app_icon">
    <intent-filter>
        <action android:name="android.intent.action.SEND" />
        <category android:name="android.intent.category.DEFAULT" />
        <data android:mimeType="text/plain" />
    </intent-filter>
</activity>
```

## Life-cycle callbacks

### onCreate()

You must implement this callback, which fires when the system first creates the activity

form basic application startup logic that should happen only once for the entire life of the activity

bind data to lists, associate the activity with a ViewModel and instantiate some class-scope variable

get savedInstanceState

**onStart()**

makes the activity visible to the user, as the app prepares for the activity to enter the foreground and become interactive

**onResume()**

This is the state in which the app interacts with the user

The app stays in this state until something happens to take focus away from the app

### onPause()

 indication that the user is leaving your activity

In Android 7.0 (API level 24) or higher, multiple apps run in multi-window mode

A new, semi-transparent activity (such as a dialog) opens.

release system resources, handles to sensors (like GPS),

 execution is very brief

you should **not** use to save application or user data, make network calls, or execute database transactions

### onStop()

When your activity is no longer visible to the user

should release or adjust resources that are not needed while the app is not visible to the user

save application or user data, make network calls, or execute database transactions

### onDestroy()

the activity is finishing

the system is temporarily destroying the activity due to a configuration change

## Configuration change 

change between portrait and landscape

changes to language or input device

When a configuration change occurs, the activity is destroyed and recreated

## Tasks and Back Stack

A task is a collection of activities that users interact with when performing a certain job

The activities are arranged in a stack—the *back stack*)—in the order in which each activity is opened

![](/home/mhalim/Downloads/diagram_backstack.png)

### Launch Mode

#### Stranded

This is the default launch mode of activity 

A →B→ C→D 

launch B

A → B → C→D→ B

launch B again

A → B → C→D→ B → B

#### Single Mode

If an instance of activity already exists at the top of the current task, a new instance will not be created

**A →B →C →D**

launch C 
**A →B →C →D →C**

launch C again

 **A →B →C →D →C** 

#### Single Task

An activity declared with launch mode as **single Task** can have **only one instance in the system**

**A →B →C**

launch B

**A →B** 

c destroyed

#### Single Instance

**A →B →C**

launch D

**A →B →C **

**D** launch in anew task

launch E

**A →B →C →E**

#### change launch mode

- manifest activity attributes
- on start activity intent





