---
layout: post
title:  Setup a site on Github Pages
tags:
- Blog
- Post
---
<p>This post actually started when <a href="https://twitter.com/gandalfar">@gandalfar</a> was looking for voluneers to create new <b><a href="http://2016.webcamp.si/">Webcamp 2016 website</a></b> . Webcamp is the largest local Web Developer Conference.</p>

<p>Without much hesitation I decided to join the ranks. The local coding group <a href="http://codecatz.org/">CodeCatz</a> was not meeting anyomore so this was a good way to continue contributing and have a good mentor (<a href="https://twitter.com/gandalfar">@gandalfar</a>).</p>

<p>My role was to create and setup the site using <a href="https://jekyllrb.com/">Jekyll</a> that will be hosted on <a href="https://pages.github.com/">GitHub Pages</a>. The design for the site was created.</p>

<p>Jekyll is a great tool for building static webpages. To get me started on Jekyll I followed a  <a href="http://codecatz.org/codecatz-tutorial/">tutorial</a> that I found on the <a href="http://codecatz.org/">CodeCatz</a> site. The hardest part was installing ruby gems on my system. I am running Ubuntu 14.04 LTS. I was able to find a solution on <a href="http://stackexchange.com/">StackExchange</a>. The tutorial uses <a href="http://getbootstrap.com/Bootstrap">Bootstrap</a> and Sass for styling. I played further with <a href="https://fortawesome.github.io/Font-Awesome/">Font-Awesome</a> for styling icons and buttons. </p>

<p>Publishing the site on Github Pages was straightforward following the tutorial. I also found a great video that covers that.<p>

<div class="divider"></div>

<iframe width="420" height="315" src="https://www.youtube.com/embed/nN6QuNqmAwk" frameborder="0" allowfullscreen></iframe>

<p>To understand the Jekyll file structure I did some reading and experimenting using the excellent  <a href="http://jekyllrb.com/docs/home/">Jekyll documentation</a>.

<p>At this point I was able to turn the Webcamp design documentation into Jekyll files. The biggest challenge was responsievenes which turned out to be really easy to solve using <a href="https://getbootstrap.com/examples/grid/">Bootstrap 12 columns system</a>.</p>


<p>Here we make use of the Bootstrap classes to display the header area:</p>

{% highlight css %}
<div class="row">

  <div class="col-md-8 col-md-offset-2 logo-wrapper">
    <a href="/">
      <img src="../assets/images/WC_logo.png" class="logo">
    </a>
  </div>
  <div class="btn-group tbl-op col-sm-12 col-md-2 hidden-xs" role="social icons">
    <ul class="fa-ul">

    {% if site.twitter_username %}
    <li>
      <a href="https://twitter.com/{{ site.twitter_username }}" class="twitter">
        <i class='fa fa-twitter fa-2x'>
        </i>
      </a>
    </li>
    {% endif %}

    {% if site.facebook_username %}
    <li>
      <a href="https://github.com/{{ site.facebook_username }}" class="facebook">
        <i class='fa fa-facebook fa-2x'>
        </i>
      </a>
    </li>
    {% endif %}

  </ul>
  </div>
</div>
{% endhighlight %}

<p>The site is hosted on  <a href="https://getbootstrap.com/examples/grid/">Github Pages</a> using CNAME to point to its domain name. What I like the most about GitHub Pages is that several people can work on the site taking advantage of github version control system. It is also publicly available for other people to clone and peruse.</p>
