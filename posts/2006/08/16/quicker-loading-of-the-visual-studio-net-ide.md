---
title: Quicker loading of the Visual Studio .NET IDE
date: '2006-08-16T19:51:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 108
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2006/08/quicker-loading-of-visual-studio-net.html
blogger_internal:
    - /feeds/32841709/posts/default/115575427054276813
dsq_thread_id:
    - '6163755010'
---
###### A handy tip from the [Bug Slayer](http://msdn.microsoft.com/msdnmag/issues/03/11/Bugslayer/) MSDN column: 

Tip 57 – To hasten the startup of the Visual Studio .NET IDE, get rid of the Start Page. Because the Start Page requires all Web-browsing components to be loaded, you can chop off a considerable amount of startup time by skipping it. To turn off the Start Page, select Options from the Tools menu to bring up the Options dialog. In the Environment/General property page, select “Show empty environment” in the “at Startup” combobox.

Of course, with [Resharper](http://www.jetbrains.com/resharper/) installed, this causes the the IDE’s start-up time to become terribly slow. But it’s worth it!