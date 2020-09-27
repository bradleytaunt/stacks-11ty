---
title: Retrieve your Windows OS Product Keys
date: '2006-10-22T09:50:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 88
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2006/10/retrieving-windows-product-keys.html
blogger_internal:
    - /feeds/32841709/posts/default/5481022870983252552
---
Today I needed to get the Windows XP Product Key but didn’t have the neccessary information to hand. I did a search and found the [MagicJellyBean](http://www.magicaljellybean.com/) utility.

This worked but I was curious how it worked. I read around a little bit and discovered a snippet of [C# code](http://geekswithblogs.net/willemf/archive/2006/04/23/76125.aspx) from [Willem’s blog](http://geekswithblogs.net/willemf/).

I then modified it a bit and created my own C# WinForm application.

[![](https://2.bp.blogspot.com/_bIhihWOyLpw/RkX7c_97lUI/AAAAAAAAAAU/g_hQBEnxBsI/s400/prodkey2.jpg)](https://2.bp.blogspot.com/_bIhihWOyLpw/RkX7c_97lUI/AAAAAAAAAAU/g_hQBEnxBsI/s1600-h/prodkey2.jpg)

The application lists the most common product keys (Windows XP and Office) and has a button to search for more keys that look like product ID’s. It searches all keys in HKEY\_LOCAL\_MACHINE.

Here’s the [source code](http://files.dunnhq.com/KeyFinderSource.zip) and here’s the [binary](http://files.dunnhq.com/KeyFinder.exe). Note, the application depends on the .NET Framework 2.0. Also, save the binary before running it otherwise it’ll run with restricted permissions and won’t be able to probe the registry.