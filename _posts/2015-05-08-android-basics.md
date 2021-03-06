---
layout:     post
title:      Activities, Views, and Context
date:       2015-05-08 12:00:19
summary:  An overview of three fundamental Android objects.
categories: android
published: false
---

####Activity

When an activity is created, one of the first things it does -- during the onCreate() method -- is setup the initial View.

####View

The [View](http://developer.android.com/reference/android/view/View.html) class is fundamental to Android's user interface. A View object can be thought of as a rectangular portion of the device screen. It can take up the whole screen or just part of it. Its properties define how that screen portion will appear to the user. ViewGroup, which is the base class for layouts, is a subclass of View. So are TextView, ImageView, and the other widgets. Views can be associated with an integer ID, typically assigned in XML:

{% highlight xml %}

<TextView
    android:id="@+id/hello_world"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Hello world!"/>

{% endhighlight %}

The View can then be located inside an Activity by its ID:

{% highlight java %}

TextView helloWorld = (TextView) findViewById(R.id.hello_world);

{% endhighlight %}

<br>

####Context

<br>
