## Android Development Resources


### The concept you need to know for Android beginners

* AVD(Android Virtual Device)

* SDK Manager

* Context


### Core Android Application Components

* Activity: The "C" of MVC, interact with layout

* BroadcastReceiver

* Service

* ContentProvider


### UI Components

* View: UI Widgets

* Layout Manager(ViewGroup): container of View

* Fragment


### Android Manifest

* AndroidManifest.xml

* Permissions

Andorid default does not allow network access, you need to add these lines to manifest:
<pre><code>
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
</code></pre>    


### Resources

* Resource IDs and R.java


### Intent

Intent is a powerful concept within the Android universe. An intent is a message that can be thought of as a request that is given to either an

activity within your own app, an external application, or a built-in Android service.

Think of an intent as a way for an Activity to communicate with the outside Android world. A few key tasks that an intent might be used for within

your apps:

* Take the user to another screen (activity) within your application

* Take the user to a particular URL within the Android web browser

* Take the user to the camera to have them take a picture

* Initiate a call for the user to a given number


### Action Bar

The ActionBar is a consistent navigation element that is standard throughout modern Android applications. The ActionBar can consist of:


* An application icon

* An application or activity-specific title

* Primary action buttons for an activity

* Consistent navigation (including tabbed UI)

You need to define action buttons in /res/menu XML.


### ToolBar

ToolBar was introduced in Android Lollipop, API 21 release and is a complete replacement to ActionBar.It's a ViewGroup so you can place it

anywhere in your layout. ToolBar also provides greater control to customize its appearance for the same reason.


### The things you cannot do in UI thread

* Opening a Socket connection (i.e. new Socket()).

* HTTP requests (i.e. HTTPClient and HTTPUrlConnection).

* Attempting to connect to a remote MySQL database.

* Downloading a file (i.e. Downloader.downloadFile()).



When you debug Android APP on real device, you need first enable "USB Debug" on device. Then install USB driver on PC.

* For Mi 3C, install [小米手机助手](http://zhushou.xiaomi.com/) or manually install USB driver as [Mi 3C USB Driver](http://www.xiaomi.cn/content-19-6735-1.html)

* For Sumsung phone, install [Kies](http://www.samsung.com/cn/support/usefulsoftware/KIES/)

* [Install USB Driver on Windows](http://developer.android.com/tools/extras/oem-usb.html)

When you run APP directly on Mi 3C, you need first make sure your device turn on USB debug mode. 

You just need to "Run" in Android Studio, and select the real device.


### Reference

[Android Official Toturial Chinese](http://hukai.me/android-training-course-in-chinese/index.html)

[Android Toturil](http://www.vogella.com/tutorials/android.html)

[Coursera Android](https://github.com/aporter/coursera-android)

[CodePath](http://guides.codepath.com/android)

[Android Open Project](https://github.com/Trinea/android-open-project)

[Android UI](https://github.com/wasabeef/awesome-android-ui)

[Android Bootstrap](https://github.com/Bearded-Hen/Android-Bootstrap)

[Awesome Android](https://github.com/snowdream/awesome-android)

[MPAndroidChart](https://github.com/PhilJay/MPAndroidChart)

[Gradle](http://gradle.org/)

[Android Best Practice](https://github.com/futurice/android-best-practices)

[NetworkOnMainThreadException](http://www.androiddesignpatterns.com/2012/06/app-force-close-honeycomb-ics.html)

[Retrofit](http://square.github.io/retrofit/)


