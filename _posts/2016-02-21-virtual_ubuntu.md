---
layout: post
title:  Setup Jekyll development environment
tags:
- Blog
- Post
---
<p>My old Dell Inspiron 1420 was slowly dying on me. This was a Core 2 duo model from 2007 <i class="fa fa-smile-o"></i> This machine was my development Ubuntu machine and it was working just fine for <a href="https://wordpress.com/"> Wordpress</a>, <a href="http://jekyllrb.com/">Jekyll</a> and <a href="https://www.djangoproject.com/">Django</a> development except lately when the nVidia graphic card started turning off the monitor every now and then. It was time to start thinking of a replacement and retire the Inspiron 1420. Initially I thought about getting myself a Mac OS X laptop. When I go to meetups it appears most developers work on Mac OS X. On the other hand they are pretty pricey and since I am not doing  iPhone/OSX development, I still don't know why would I choose Mac OS X instead of Ubuntu. While pondering this idea I had to find an interim solution. </p>

<p>The fastest interim solution was runing Ubuntu 14.04 on a VMWare Workstation with VMTools on my work Windows 7 Dell Latitute E6530. If this solution works well I will look into getting some new hardware (i7 Processor).</p>

<h3>Here is what I needed to do to setup Jekyll on Ubuntu 14.04: </h3>
<p>The best way to install Jekyll is via RubyGems by simply running the following command:</p>
<pre>
<code>
gem install jekyll
</code>
</pre>
This command returned <code>“Error Installing Jekyll - Native Extension Build
“</code> described <a href="http://stackoverflow.com/questions/10725767/error-installing-jekyll-native-extension-build">here</a>.

I ran the following commands:
<pre>
<code>
sudo apt-get install ruby2.0 ruby2.0-dev
sudo gem2.0 install jekyll-import
</code>
</pre>

which still did not help and returned <code>"Error installing Jekyll, requires Ruby >= 2.0.0"</code> so I tried the solution described <a href=" http://stackoverflow.com/questions/33503796/error-installing-jekyll-requires-ruby-2-0-0">here</a>.

This is what I ran:
<pre>
<code>
sudo rm /usr/bin/ruby
sudo rm /usr/bin/gem
sudo ln -s /usr/bin/ruby2.0 /usr/bin/ruby
sudo ln -s /usr/bin/gem2.0 /usr/bin/gem
</code>
</pre>

This last solution finally worked and Jekyll installed: <code>gem install jekyll</code> finished successfully.

Now I needed to install <https://git-scm.com/">git</a> on Ubuntu.

To setup <b>git</b> on Ubuntu 14.04 I followed this <a href=" https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu-14-04">tutorial</a>.
This is what I ran:
<pre>
<code>
sudo apt-get install git
git config --global user.name "Your Name"
git config --global user.email "My email address"
git clone -b gh-pages-working https://github.com/webcampsi/lj2016.git
</code>
</pre>

The last command cloned the <a href="https://github.com/webcampsi/lj2016.git">Webcamp 2016</a> git repository on my local machine.

And voila, the <a href="http://2016.webcamp.si/">Webcamp 2016 website</a> was rendering on my local machine by running:
<pre>
<code>
jekyll serve
</code>
</pre>

Now the only thing left was to install <b><a href="https://atom.io/">Atom</a></b>, my favorite text editor, on Ubuntu. This was easy by following the video <a href="
https://www.youtube.com%2Fwatch%3Fv%3DdxPm2s34aXs&usg=AFQjCNGZjOfqdrexL9bBXcCbHD2fmNOtHA">here</a>.
