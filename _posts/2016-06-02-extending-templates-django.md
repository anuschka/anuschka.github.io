---
layout: post
title:  Extending templates
tags:
- Blog
- Post
---

During our weekly Skype meeting Maksim and I discussed extending templates in Django. What does this mean? It means that you can use the same parts of your HTML for different pages of your website.

It meant that I could create a new template called <a href="https://github.com/anuschka/QCapp/blob/master/qcapp/templates/internal_page.html"> internal_page.html</a> that contains the navigation and footer section since these appear on every page. Then in my regular template I use `{% extends "internal_page.html" %}`. <i class="fa fa-smile-o"></i>

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

We also briefly discussed about SaaS applications (like Trelo or Github) and what they are. I read about on edX since they were offering an agile Ruby course for writing <a href="https://en.wikipedia.org/wiki/Software_as_a_service">SaaS </a> applictions. This is still a far fetch for me <i class="fa fa-smile-o"></i>.

To speed up frontend development Maksim suggested s bootstrap designer application like <a href="http://pinegrow.com/"> Pinegrow</a>. Later on I tried it and it works really nice on Win10 but not that nice on Ubuntu. A Slovenian application. It is like buy locally <i class="fa fa-smile-o"></i>. I will probably buy the license since it also creates themes for Wordpress and integrates with Atom (not on Ubuntu though).
