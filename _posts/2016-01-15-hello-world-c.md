---
layout:     post
title:      Easy, Breezy Intro to C
date:       2016-01-15 11:00:19
summary:  How to write, compile and execute a basic Hello World program in C.
categories: C basics
published: true
---

One of my goals for 2016 is to learn more about the lower levels of Android: how the OS source code is structured, how messages are passed down through the application framework to make things happen on the hardware, and at the bottom of it all, how the Linux kernel works.

I've found some great resources

Here's a guide to writing your first C program using Terminal on OS X:

First, open a Terminal window and navigate to the directory you'd like to work in. Create and open a new file using nano or vim:

{% highlight bash %}

$ nano helloworld.c

{% endhighlight %}

Now here comes the program:

{% highlight c %}
#include<stdio.h>

int main(void) {

printf("Hello, world!\n");

return 0;

}
{% endhighlight %}

Going over it line by line:

Now use ^O to save and ^X to exit nano. Back on the command line, compile your program:

{% highlight bash %}

$ cc helloworld.c

{% endhighlight %}

Now use ls -l to print out the contents of your directory. You'll see that a new file has been created, a.out. This is the compiled version of your program. Open it:

{% highlight bash %}

$ ./a.out
Hello, world!

{% endhighlight %}
