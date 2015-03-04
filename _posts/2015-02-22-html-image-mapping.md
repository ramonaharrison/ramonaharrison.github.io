---
layout:     post
title:      Building HTML Image Maps
date:       2015-02-22 11:21:29
summary:    I attended the Access Code application workshop and figured out how to divide a single image into many clickable regions using images maps.
categories: accesscode html tutorial
---
<p>I learned a number of neat HTML/CSS tricks at this weekend's Access Code application workshop. During the presentation, we were encouraged to advance our knowledge by checking out the source code behind some of the interesting HTML elements that we encounter across the web. With that goal in mind, I was intrigued into figuring out the inner workings of <a href="http://www.w3schools.com/">w3schools.com's</a> cool, interactive hexagonal hexadecimal <a href="http://www.w3schools.com/tags/ref_colorpicker.asp">HTML Color Picker</a>:
   </p>


   <center>
     <a href="http://www.w3schools.com/tags/ref_colorpicker.asp"><img id="colormap" src="http://www.w3schools.com/tags/colormap.gif"></a>
   </center>

   <p>On <a href="http://www.w3schools.com/tags/ref_colorpicker.asp">w3schools.com's site</a>, this colorful image serves as an interactive map to help web designers identify a color's corresponding hex code. As you mouse-over each individual colored 'cell', a box below the hexagon displays the color along with its code. When you click on a cell, the hex code appears in a text box where it can be easily selected and copied. When I inspected the page's source with Chrome, I was surprised to find that the entire Color Picker hexagon is a single <span>.gif</span> image.
   </p>

   <p>I knew that images could be used as links, but I had no idea that a single image could be broken up into several seemingly-independent clickable regions using just HTML. This unfamiliar snippet of code gave me a clue into how it's done:
   </p>

   {% highlight html %}
     <map id="colormap" name="colormap" onmouseout="mouseOutMap()">
         <area style="cursor:pointer" shape="poly" coords="63,0,72,4,72,15,63,19,54,15,54,4"  ...
   {% endhighlight %}

   <p>I had never seen <span><map></span> or <span><area></span> tags before, so I googled them to get more info. It turns out that these tags are the key to creating HTML "image-maps". Image-maps are <a href="http://www.w3schools.com/tags/tag_map.asp">just images with clickable areas</a>.
   </p>

   <p>To create an image-map, the first step is to include a picture on your webpage using the <span><img></span> tag. Along with a <span>src=</span> attribute, also include a <span>usemap=</span> attribute, and begin its corresponding value name with a hash (<span>#</span>). Your complete tag should look something like this:
   </p>

   {% highlight html %}
     <img src="image.jpg" usemap="#mapofthings">
   {% endhighlight %}

   <p>Below your <span><img></span> tag, create a <span><map></span> tag. You should include the attribute <span>name=</span>, and set it equal to the value of <span>usemap</span> (no need to include the <span>#</span>). Also, remember to follow it with a closing tag. For example: <span><map name="mapofthings"></map></span>. Nested inside the <span><map></span> tag you'll put <span><area></span> tags (one for every clickable region of the image):
   </p>

   {% highlight html %}
       <img src="image.jpg" usemap="#mapofthings">
       <map name="mapofthings">
         <area>
         <area>
         <area>
       </map>
       {% endhighlight %}

   <p>Now, to define our clickable regions, we’ll add these magical attributes to each <span><area&gt</span> tag:
   </p>
     <ul>
       <li><span>shape=</span>
       <li><span>coords=</span>
       <li><span>href=</span>
     </ul>

   <p>The <span>shape=</span> attribute specifies the shape of an <span>area</span>’s clickable region: <span>”rect"</span>, <span>”circle"</span>, or <span>”poly"</span>. The positions of these shapes are defined by <span>coords=</span>: for a rectangle as <span>”x1, y1, x2, y2"</span>, where the top-left corner of the rectangle is <span>(x1,y1)</span> and the bottom-left corner is <span>(x2,y2)</span>, or a circle as <span>”center-x, center-y, radius"</span>. The value <span>”poly"</span> can be used to create many-sided or irregular shapes by specifying as many corner coordinate-pairs as you'd like. The <span>href=</span> attribute, as we know, specifies the targeted link.
   </p>

   <p>With a picture of some objects from around my room, I used a photo editing program to measure the rough pixel coordinates of each object and plugged those numbers into our image-map code. So here it is, all together now:
   </p><br>

   <center>
      <img src="http://i62.tinypic.com/10p7n2x.jpg" usemap="#roomthings" id="roomthings" style="outline:none" hidefocus="true">
   </center>

 <map name="roomthings">
   <area shape="rect" coords="0,0,300,150" href="http://jsbin.com/dufogo/">
   <area shape="rect" coords="0,150,300,448" href="http://jsbin.com/locuwu/">
   <area shape="rect" coords="300,250,600,448" href="http://jsbin.com/letuyu/">
   <area shape="rect" coords="300,0,450,125" href="http://jsbin.com/yajovo/">
   <area shape="rect" coords="450,0,600,125" href="http://jsbin.com/kedoxa/">
   <area shape="rect" coords="300,125,450,250" href="http://jsbin.com/fepero/">
   <area shape="rect" coords="450,125,600,250" href="http://jsbin.com/lekoja/">
 </map>

 <center>
 <p id="italic">(Click on the objects in the picture to learn more about them!)
 </p>
 </center><br>

 <p>And the code:
 </p>

 {% highlight html %}
  <img src="http://i59.tinypic.com/1zgvr5h.jpg" usemap="#roomthings">
 <map name="roomthings">
    <area shape="rect" coords="0,0,300,150" href="motorcycle.html">
    <area shape="rect" coords="0,150,300,448" href="pineapple.html">
    <area shape="rect" coords="300,250,600,448" href="spoon.html">
    <area shape="rect" coords="300,0,450,125" href="samsung.html">
    <area shape="rect" coords="450,0,600,125" href="token.html">
    <area shape="rect" coords="300,125,450,250" href="key.html">
    <area shape="rect" coords="450,125,600,250" href="balm.html">
  </map>
   {% endhighlight %}
   <br>

   <p>Of course, <a href="http://www.w3schools.com/tags/ref_colorpicker.asp">w3schools.com’s Color Picker</a> uses JavaScript to fancy things up a bit, allowing events to happen seamlessly on the page rather than linking out. I'm especially curious to figure out how the "Darker/light shades:" selection area is generated. Still, even the basic HTML image-map is pretty cool. I’m looking forward to experimenting with what I've learned for some fun and unusual web designs.
   </p>
