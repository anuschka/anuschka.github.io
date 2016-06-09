---
layout: post
title:  Extending templates in django
tags:
- Blog
- Post
---

During our weekly Skype meeting Maksim and I discussed extending templates in Django. What does this mean? It means that you can use the same parts of your HTML for different pages of your website.

It meant that I could create a new template called <a href="https://github.com/anuschka/QCapp/blob/master/qcapp/templates/internal_page.html"> internal_page.html</a> that contains the navigation and footer section since these appear on every page. Then in my regular template I use `{% extends "internal_page.html" %}`.

We also talked about <a href="https://docs.djangoproject.com/en/1.9/ref/templates/language/#id1">
template inheritance </a>. All the block tag does is to tell the template engine that a child template may override those portions of the template.

Maksim also showed me how to statically supply context for a specific view:
<pre>
<code>
context = {
    #'reagents': reagents,
    'reagents': [
        {
            'type': 'anti-Fya',
            'manufacturer': 'BIO-RAD',
            'lot': '19210.64.10',
            'expiry': '2016-06-06',
            'requiresIDCard': True,
            'created_at': '2016-06-01'
        },
        {
            'type': 'anti-Fya',
            'manufacturer': 'BIO-RAD',
            'lot': '19210.64.10',
            'expiry': '2016-06-06',
            'requiresIDCard': True,
            'created_at': '2016-06-01'
        },
        {
            'type': 'anti-Fya',
            'manufacturer': 'BIO-RAD',
            'lot': '19210.64.10',
            'expiry': '2016-06-06',
            'requiresIDCard': True,
            'created_at': '2016-06-01'
        },
        {
            'type': 'anti-Fya',
            'manufacturer': 'BIO-RAD',
            'lot': '19210.64.10',
            'expiry': '2016-06-06',
            'requiresIDCard': True,
            'created_at': '2016-06-01'
        }
    ],
    'active_page': 'reagent'
}
</code>
</pre>

The `active_page` variable is used in the navigation.


We decided to leave the breadcrumb section in each individual template since. It is not the most elegant solution but it works.

We also briefly discussed about SaaS applications (like Trelo or Github) and what they are. I read about on EdX since they were offering an  EdX:  BerkeleyX: CS169.1x Agile Development Using Ruby on Rails course using <a href="https://en.wikipedia.org/wiki/Software_as_a_service">SaaS </a>. This appears to far fetched for me.

To speed up frontend development Maksim suggested s bootstrap designer application like <a href="http://pinegrow.com/"> Pinegrow</a>. Later on I tried it and it works really nice on Win10 but not that nice on Ubuntu. This is an application written by a <a href="https://medium.com/@mattront/pinegrow-year-in-review-2014-from-0-to-100k-fed4e7a05689#.a3cqdjtjr.">Slovenian developer</a>. It is like buying locally. I will probably buy the license since it also creates themes for Wordpress and integrates with Atom (not on Ubuntu though).
