---
title: Programs that launch (or should launch) Visual Studio
date: '2009-03-03T12:34:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 51
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2009/03/programs-that-launch-or-should-launch.html
blogger_internal:
    - /feeds/32841709/posts/default/3899971527459743981
---
Programs such as [FxCop](http://msdn.microsoft.com/en-us/library/bb429476(VS.80).aspx) provide links to source files that can be clicked and then edited in Visual Studio.

FxCop recently *(probably since I went 64bit, but also possibly a side-effect of running Windows 7)* started failing when clicking these links. It said:

> *Could not start Microsoft Visual Studio. Try specifying an alternate source code editor in Application Settings.*

Maybe it just looks in Program FilesMicrosoft Visual Studio\[whatever version\]. Anyway, I couldn’t see anything in the event log or any local FxCop logs, so I just changed the setting under ToolsSettings to use an explicit path to devenv.exe.

This worked, although it started a new instance of the IDE for every file. To get around that, you need to use the **/Edit** argument. Here’s what it looks like (click to make it bigger):

[![sshot-2](https://lh5.ggpht.com/_bIhihWOyLpw/Sa0VqI_zwYI/AAAAAAAABio/auvddtXA9Oo/sshot-2_thumb%5B4%5D.png?imgmax=800 "sshot-2")](https://lh6.ggpht.com/_bIhihWOyLpw/Sa0VpfS7CrI/AAAAAAAABik/JXo2ssdJd_g/s1600-h/sshot-2%5B6%5D.png)

> 

There’s other handy switches, some of which I knew about, like building a particular project/solution (to get the full list, run devenv.exe /?). It now uses an existing instance of Visual Studio if one’s present, otherwise it starts one up.