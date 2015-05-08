---
layout:     post
title:      Activities, Contexts, and Views
date:       2015-05-08 12:00:19
summary:  An overview of three fundamental Android objects.
categories: android
published: true
---


####Context

####Activity

When an activity is created, one of the first things it does (during its onCreate() method) is setup the initial View.

####View

The View class is fundamental to your app's user interface. A View object can be thought of as rectangular portion of the device screen. It can take up the whole screen or just a part of it. Its properties define how that screen portion will appear to the user. ViewGroup, which is the base class for layouts, is a subclass of View. So are TextView, ImageView, and the other widgets. Views can be associated with an integer ID, typically assigned in XML:

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
