---
layout:     post
title:      Generating a Starry Sky with java.util.Random
date:       2015-03-20 8:00:19
summary:
categories: accesscode java random ascii
---
My earliest memories of interacting with a computer are of . It was a 'sideways tower' style PC, beige and boxy, with an enormous, bright-orange switch on the back that you'd toggle to power the computer on and off. It would boot to a white MS-DOS prompt on a black screen.

We lived in the country in a pretty rural area. We didn't have TV. My experience of the world was pretty small. The computer was mesmerizing to me, like an alien artifact plunked down into my life.

My dad was in the merchant marine. He'd 'swap' software with other computer hobbyists on the ships, and every few months would come home from sea with a collection of 5-1/4" floppy disks loaded with new games.


I played (Commander Keen)[https://archive.org/details/msdos_Commander_Keen_1_-_Marooned_on_Mars_1990], (Cosmo's Cosmic Adventure)[http://en.wikipedia.org/wiki/Cosmo%27s_Cosmic_Adventure] and (Crystal Caves)[http://www.classicdosgames.com/online/1cc10a.html] obsessively. I also

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

            if (i == (length - 20)) {            // determines position of scene in scroll
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

mfd.smf,.dmsf,ds
