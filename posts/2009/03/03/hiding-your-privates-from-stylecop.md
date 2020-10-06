---
title: Hiding your privates from StyleCop
date: 2009-03-03
status: publish

author: stevedunn
excerpt: ''
type: post
id: 50
tags:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2009/03/hiding-your-privates-from-stylecop.html
blogger_internal:
    - /feeds/32841709/posts/default/709299203569553598
dsq_thread_id:
    - '7847230167'
---
[I like StyleCop](https://blog.dunnhq.com/posts/2009/02/21/stylecop/) but I didn’t like the fact it produced warnings on private fields and methods. I was wrong. Not wrong in that I didn’t like warnings on privates, but wrong that I thought there was no way to tell it to stop it.

Apparently there is. [Jason Allor](http://blogs.msdn.com/sourceanalysis/) kindly left a comment saying that it can be configured through the StyleCop settings dialog in Visual Studio.

I took a look and initially didn’t find it. I didn’t find it because I assumed there’d be different rules for public and private entities. But there’s not, you can decide at the *rule type* level:

[![sshot-1](https://lh3.ggpht.com/_bIhihWOyLpw/Sa0axMcd97I/AAAAAAAABiw/VsPPv7fowpo/sshot-1_thumb%5B2%5D.png?imgmax=800 "sshot-1")](https://lh6.ggpht.com/_bIhihWOyLpw/Sa0awff7anI/AAAAAAAABis/YyDDOL41w8c/s1600-h/sshot-1%5B4%5D.png)

It’d be nice to have separate rules for public and private. Currently, I’ve turned off **all** Documentation rules because I don’t like being warned that I haven’t commented private methods. However, I’d still like it to give me all the other great warnings if I do decide to comment a particular private method.