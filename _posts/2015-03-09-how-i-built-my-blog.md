---
layout:     post
title:      How I Built My Blog with Jekyll and GitHub Pages
date:       2015-03-09 12:31:19
summary:    A overview of the Jekyll framework and walkthrough of how I created my blog on GitHub pages.
categories: jekyll pixyll technical git github
published: true
---

This site is built with [Jekyll](http://jekyllrb.com/) and [GitHub Pages](https://help.github.com/articles/using-jekyll-with-pages/). In this post, I'll talk about what that means and how you can create your own free, customizable blog using these tools.

[Jekyll](https://github.com/jekyll/jekyll) is an open-source generator for creating simple websites and blogs. You write content in [Markdown](https://help.github.com/articles/markdown-basics/). Jekyll takes that content, runs it through a [template](http://jekyllrb.com/docs/templates/), and produces a static HTML/CSS website. Don't worry if that seems confusing. Once you start playing around with Jekyll things become clearer. Jekyll is the engine behind GitHub Pages.

[GitHub Pages](https://help.github.com/articles/what-are-github-pages/) is a free service that allows GitHub users to create their own website located at the URL <i>http://yourusername.github.io</i>. To activate GitHub Pages, all you need to do is create a repository in your account named <i>yourusername.github.io</i>. GitHub will recognize that you're creating a website and serve files in this repository automatically.

### I chose Jekyll because...

  * Jekyll and GitHub Pages are free. No need to pay for hosting.
  * Jekyll is simple. All of my posts live as .md files in a folder on my computer. When I want to create a new post, I just open a text editor. When I'm ready to put that post online, I just use git to push it.
  * Jekyll is customizable. There are a ton of [nice themes](https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&es_th=1&ie=UTF-8#safe=off&q=jekyll+themes) out there. You can modify them. You can create your own theme from scratch.
  * [Disqus](https://disqus.com/) for commenting.
  * Supports lots of [plugins](http://jekyllrb.com/docs/plugins/).
  * Your content belongs to you.
  * No ads.

### How to Create a Blog

Jekyll is written in [Ruby](https://www.ruby-lang.org/en/). If you know some Ruby, that's awesome, but it's absolutely not a prerequisite to get your blog up and running. These are the steps I followed on my MacBook running OS X Yosemite. I was doing research at the same time, so it took me about 2 hours from start to finish. It may take more or less time depending on the theme you choose and if you run into any unexpected errors.

#### 1) Get the tools
We'll be doing a lot of work in the terminal. Let's make sure we have all the tools we need:

  * [<b>Ruby</b>](https://www.ruby-lang.org/en/). OS X Yosemite comes preinstalled with Ruby. In terminal, type <span style="font-family:Courier" class="bg-dark-gray white">ruby -v</span> . If you have Ruby you should see a version number, like <span style="font-family:Courier" class="bg-dark-gray white">ruby 2.2.0p0 (2014-12-25 revision 49005) [x86_64-darwin14]</span> . If not, follow the [link to install](https://www.ruby-lang.org/en/documentation/installation/).
  * [<b>RubyGems</b>](http://guides.rubygems.org/). Type <span style="font-family:Courier" class="bg-dark-gray white">gem -v</span> . You should get back a version number, like <span style="font-family:Courier" class="bg-dark-gray white">2.4.6</span> . Otherwise, [follow the link to install RubyGems](https://rubygems.org/pages/download).
  * [<b>NodeJS</b>](https://nodejs.org/). Type  <span style="font-family:Courier" class="bg-dark-gray white">node -v</span> . If you don't see a version number, install [NodeJS](https://nodejs.org/download/).


#### 2) Install Jekyll using RubyGems
RubyGems is a package manager that makes it easy to download and install Ruby programs. We're going to use RubyGems to install Jekyll.

  * In terminal, run the command <span style="font-family:Courier" class="bg-dark-gray white">gem install jekyll</span>
  * You now have Jekyll installed on your local system!

#### 3) Choose a theme and fork it to your own repository
Here comes the fun part. It's time to choose a theme and fork it to your own repository on GitHub. <i>(At this point, if you don't have a GitHub account, you'll want to [create one](https://github.com/))</i>

  * Search for a theme online. I found my theme at [jekyllthemes.org](jekyllthemes.org), which I would recommend, but you can find others by googling 'jekyll themes'. Don't worry, you can always change your theme down the road.
  * Once you've found a theme you like, go to its GitHub repository.
  * In the upper left corner, click on the 'Fork' button. This will create your own forked copy of the repository.
  * After forking, click on the 'Settings' button midway down the page on the right side. You'll see a box to rename your new repository. Change the name to <i>yourusername.github.io</i> (for example, <i>ramonaharrison.github.io</i>) and click the 'Rename' button.

#### 4) Clone the forked copy to your local computer

  * Decide where on your computer you want the blog files to live. I keep mine in the directory <span style="font-family:Courier" class="bg-dark-gray white">~/Documents/coding/</span>, but it's totally up to you to decide where you want the files to be.
  * Use the terminal to <span style="font-family:Courier" class="bg-dark-gray white">cd</span> to your chosen directory.
  * Clone the forked repository: <span style="font-family:Courier" class="bg-dark-gray white">git clone git@github.com:<i>yourusername</i>/<i>yourusername</i>.github.io.git</span>

#### 5) Edit your _config.yml file

  * Now, in terminal, <span style="font-family:Courier" class="bg-dark-gray white">cd</span> into the cloned directory.
  * Type <span style="font-family:Courier" class="bg-dark-gray white">ls</span> . These files are the framework of your Jekyll blog.
  * For now, we're going to focus on <span style="font-family:Courier" class="bg-dark-gray white">_config.yml</span>. This file contains some basic information about your blog, such as title, author (you), URL, your email, twitter and GitHub links.
  * Open the file in nano: <span style="font-family:Courier" class="bg-dark-gray white">nano _config.yml</span>
  * Update the header at the top of the file with your information. Save with <i>control+o</i> and exit nano with <i>control+x</i>.

#### 6) Create and preview your first post

  * At this point, it may be easier to use a text editor like [Atom](https://atom.io/) to manage your posts. You can use TextEdit as well, just make sure that your settings are on 'plain-text'.
  * Your blog posts live in the <span style="font-family:Courier" class="bg-dark-gray white">_posts</span> folder. Navigate into it.
  * You should see some sample posts that came with your theme. Notice the naming convention. Jekyll posts are always named <span style="font-family:Courier" class="bg-dark-gray white">yyyy-mm-dd-title-of-the-post.md</span>. Pick one and open it up in a text editor.
  * At the top of the file is a header with some information about the post. For example, the header on the post I'm writing now looks like:


{% highlight html %}
---
layout:     post
title:      How I Built My Blog with Jekyll and GitHub Pages
date:       2015-03-09 12:31:19
summary:    A overview of the Jekyll framework and walkthrough of how I created my blog on GitHub pages.
categories: jekyll pixyll technical git github
published: true
---
{% endhighlight %}

  * Every Jekyll post you create will include a similar header.
  * Let's create a test post together: in the <span style="font-family:Courier" class="bg-dark-gray white">_posts</span> directory create a new file called <span style="font-family:Courier" class="bg-dark-gray white">2015-03-09-my-first-jekyll-post.md</span> and open it with your text editor.
  * Create a header:

{% highlight html %}
---
layout:     post
title:      My First Jekyll Post
date:       2015-03-09 12:00:00
summary:    This is a test post.
categories: jekyll testing
published: true
---
{% endhighlight %}

  * As you might have guessed, <span style="font-family:Courier" class="bg-dark-gray white">published:</span> sets whether or not the post is listed on your blog. If you are working on a new entry that you don't want to share yet, or trying to hide but not delete an old entry, you can set <span style="font-family:Courier" class="bg-dark-gray white">published: false</span>. Keep in mind that the content of a 'false' post is still stored in your public GitHub repository, so this may not be the best method for storing something you really want to keep secret.
  * Below your header, add a short body to your post. You can use [Markdown](https://help.github.com/articles/markdown-basics/) to format it (for example create headers, lists, links, or code blocks). Here's my complete sample post:

{% highlight html %}
---
layout:     post
title:      My First Jekyll Post
date:       2015-03-09 12:00:00
summary:    This is a test post.
categories: jekyll testing
published: true
---

### Check it out!

This is my sample Jekyll post. My next steps will be:
 * Save it
 * Push it to GitHub
 * Check it out in my browser

{% endhighlight %}


#### 7) Push your test post and view it online!
  * After you've saved your file, you can preview it on your own computer before pushing to GitHub. To do this, use the terminal to navigate to the blog's main directory and type <span style="font-family:Courier" class="bg-dark-gray white">jekyll serve</span>.
  * Leave the process running and open a web browser. Go to [localhost:4000](localhost:4000). If everything's gone well, you should see a preview of the blog in your browser. You can click on your test post to preview it.
  * Go back to the terminal and kill jekyll with <i>control+c</i>.
  * Now it's time to push everything to GitHub and make it live:

  {% highlight html %}
$ git add .
$ git commit -m "Added test post"
$ git push origin master

  {% endhighlight %}

  * Visit <i>yourusername.github.io</i> to see your blog in action!

When you're ready, you can delete the sample posts and start pushing your own content. Follow the process in steps 6-7 anytime to create a new post. When I write a post, I like to keep open my text editor, a browser at localhost:4000, and a terminal window running <span style="font-family:Courier" class="bg-dark-gray white">jekyll serve</span>. That way, as I'm editing, I can see my progress simply by saving the file and refreshing the browser.


### More Resources

  * GitHub Help: [Using Jekyll with Pages](https://help.github.com/articles/using-jekyll-with-pages/)
  * Find a [Jekyll Theme](http://jekyllthemes.org/)
  * From Tom Preston-Werner, creator of Jekyll: [Blogging Like a Hacker](http://tom.preston-werner.com/2008/11/17/blogging-like-a-hacker.html)
  * GitHub Guide to [Markdown](https://help.github.com/articles/markdown-basics/)

<br>
