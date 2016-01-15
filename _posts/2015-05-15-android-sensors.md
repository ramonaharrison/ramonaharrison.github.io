---
layout:     post
title:      Android Sensors
date:       2015-05-15 12:00:19
summary:  An overview of the hardware Android devices use to measure acceleration, rotation, and position.
categories: android sensors
published: true
---

One of the things I find most exciting about beginning to develop for mobile is how many ways there are for people to interact with their devices: touch, movement, rotation, illumination, camera view, sound, and of course, network connectivity...

This week I started playing around with some of my phone's sensors to see what the data coming in from the hardware looks like and what sorts of things can be done with it. In this post I'll talk about the principle sensors the phone uses to calculate movement: the gyroscope, the accelerometer, and the compass.

To read

{% highlight java %}

TextView helloWorld = (TextView) findViewById(R.id.hello_world);
{% endhighlight %}

#### Gyroscope

A gyroscope, in principle, is a spinning wheel or disc that is free to move to any orientation without interference from the fixed body around it. Gyroscopes are used to measure changes in orientation.

![Gyroscope](http://upload.wikimedia.org/wikipedia/commons/d/d5/Gyroscope_operation.gif)

Most mobile phones use MEMS gyroscopes, which are inexpensive electronic circuit boards that use vibration rather than rotating discs to measure rotational movement. An Android device's gyroscope can measure the device's rate of rotation in radians per second around each of the three axes (x,y,z).

#### Accelerometer

An accelerometer is a device that measures acceleration -- a good way to imagine it is like a ball suspended by springs fixed to the walls of a box. As the box moves through space, the ball tugs at the springs, lengthening or shortening them in response to the box's movement. The relative movement of the springs can be translated to describe the acceleration of the box.

An Android device's accelerometer is electromechanical. It measures the force of acceleration in meters per second per second (m/s^2)  applied to it on the three axes (x,y,z). It's important to note that accelerometers are constantly experiencing the force of gravity, which means that a device at rest will read +9.81 m/s^2 on the z-axis (while a device in free fall will read 0 m/s^2 on the z-axis since it is accelerating at the same rate as gravity).

#### Compass

A compass reports direction with respect to magnetic north. Traditionally compasses have used magnets to make the reading. Android devices typically use very small solid-state compasses with two or three [magnetometers](http://en.wikipedia.org/wiki/Magnetometer) that a microprocessor reads to calculate magnetic north.

#### Sensor Fusion

#### More info

 * [developer.android.com](http://developer.android.com/guide/topics/sensors/sensors_overview.html) - Sensors Overview
 * [Google Tech Talk](https://www.youtube.com/watch?v=C7JQ7Rpwn2k) - Sensor Fusion on Android Devices (great overview of sensor hardware and the math google engineers are using to improve data quality and clean up the noise)
