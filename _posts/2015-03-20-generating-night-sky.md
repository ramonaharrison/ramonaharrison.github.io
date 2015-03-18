---
layout:     post
title:      Generating a Starry Sky with java.util.Random
date:       2015-03-20 8:00:19
summary:
categories: accesscode java random ascii
published: true
---

The first computer I can remember was the one my dad brought home in the early 90's, when I was four or five. It was a 'sideways tower'-style PC, beige and boxy, with an enormous, bright-orange power toggle on the back. When you flipped that toggle, it would boot to a white MS-DOS prompt on a black screen, awaiting your commands.

We lived in the country in a pretty rural area -- at the time, too far out for cable TV or decent broadcast reception. My experience of the world was small. The computer was mesmerizing to me, and special, like an alien artifact plunked down into my life.

My dad was in the merchant marine. His work would take him out to sea for several months at a time. On the ships, he'd 'swap' software with other computer hobbyists, and every few months would come home with a new collection of DOS games on 5-1/4" floppy disks for me to play.


I spent obsessive hours with [Commander Keen](https://archive.org/details/msdos_Commander_Keen_1_-_Marooned_on_Mars_1990), [Cosmo's Cosmic Adventure](http://en.wikipedia.org/wiki/Cosmo%27s_Cosmic_Adventure) and [Crystal Caves](http://www.classicdosgames.com/online/1cc10a.html). I also loved the minimal text-based adventure games, which felt immersive, like reading a book that let you choose how the story would go.

That's why I was so excited for last week's Access Code assignment, which was to code our own text-based adventure game in Java.

My game, [Stars](https://github.com/ramonaharrison/HW_03-14), is about an interstellar traveller who crash lands on Earth and needs to figure out how to fix her spaceship so she can return home.

Inspired by [this excellent article](http://www.washingtonpost.com/posteverything/wp/2015/03/04/im-a-12-year-old-girl-why-dont-the-characters-in-my-apps-look-like-me/) written by a twelve-year-old girl asking 'Why don't the characters in my apps look like me?', my main character is a girly alien who has a penchant for solo travel and DIY repairs.

<br>

  {% highlight java %}
        ☆                              ˳✧༚                          ☆
✧
                                                           ☆
                 •ི   •ྀ
    ☆          (◕ ‿ ◕ ✿)
                ૮[ ♡   ]ა
                 ~~~~~~
                  ミ ミ
            ☆                                       ☆                        ˳✧༚
✧
                         ☆                 ☆

  {% endhighlight %}

<br>

Although the core of the game is text-based, I wanted to include some Unicode art sequences as a visual backdrop for the story. Key to this was emulating a starry night sky, with Unicode stars  randomly distributed across whitespace in the console.

At first, my sky-building process looked something like this:

  * Call <span style="font-family:Courier" class="bg-dark-gray white">System.out.println("")</span>
  * Fill the string with a bunch of spaces, pasting in some 'random' stars
  * Repeat

When the code you're writing feels repetitious, there's probably a better way to do it, so I started thinking rethinking my process.

I created a method called <span style="font-family:Courier" class="bg-dark-gray white">starScroll</span> that takes three arguments: <span style="font-family:Courier" class="bg-dark-gray white">int length</span>, <span style="font-family:Courier" class="bg-dark-gray white">int width</span>, and <span style="font-family:Courier" class="bg-dark-gray white">String scene</span> (a string to embed near the bottom of the scroll). Inside the method I created a new Random() object and an integer variable called <span style="font-family:Courier" class="bg-dark-gray white">starSpacing</span>, which is initialized at 80.

Next I created two nested for-loops. The inner loop generates a string <span style="font-family:Courier" class="bg-dark-gray white">width</span> characters long. For each character, it calls a random number between 0 and <span style="font-family:Courier" class="bg-dark-gray white">starSpacing</span> (initially 80). If the number is less than 6, it sets the character to one of the Unicode stars, otherwise it sets the character to a whitespace.

The outer loop repeats the inner loop <span style="font-family:Courier" class="bg-dark-gray white">length</span> times, printing each string on a new line then pausing for 10 ms. Each time the loop repeats, it adds 5 to <span style="font-family:Courier" class="bg-dark-gray white">starSpacing</span>, meaning that the range of the random number being called increases, creating a 'thinning' effect as the scroll progresses. The outer loop is also responsible for embedding the <span style="font-family:Courier" class="bg-dark-gray white">scene</span> 20 lines above the end of the scroll.

Here's the effect:

![starScroll](https://ramonaharrison.github.io/images/starscroll.gif)
<br><br>

And the code, all together:


  {% highlight java %}

public static void starScroll(int length, int width, String scene) {

        // generates random star scroll

        Random random = new Random();
        String starLine = "";
        int starSpacing = 80;      // increasing this value decreases the concentration of stars

        for (int i = 0; i < length; i++) {

            for (int j = 0; j < width; j++) {     // widens the scroll

                int number = random.nextInt(starSpacing);

                if (number < 3) {
                    starLine = starLine + "☆";
                } else if (number == 3) {
                    starLine = starLine + "✧";
                } else if (number == 4) {
                    starLine = starLine + "˳";
                } else if (number == 5) {
                    starLine = starLine + "༚";
                } else {
                    starLine = starLine + " ";
                }
            }

            if (i == (length - 20)) {            // embeds scene in scroll
                System.out.println(scene);
            } else {
                System.out.println(starLine);
                starSpacing += 5;                // thins stars as scroll progresses
                starLine = "";
                try {
                    Thread.sleep(10);            // increasing this value slows the scrolling
                } catch (InterruptedException ex) {
                    Thread.currentThread().interrupt();
                }
            }
        }
    }

    {% endhighlight %}
