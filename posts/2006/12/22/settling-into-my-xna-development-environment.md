---
title: Settling into my XNA Development Environment
date: '2006-12-22T12:21:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 80
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2006/12/settling-into-my-xna-development.html
blogger_internal:
    - /feeds/32841709/posts/default/2516789294226008018
dsq_thread_id:
    - '6425712630'
---
Microsoft recently released the [XNA](http://msdn.com/xna "MSDN XNA Site") toolkit for XBox 360 and PC games development. The supported IDE for this is [Visual C# Express](http://msdn.microsoft.com/vstudio/express/visualcsharp/ "Visual C# Express").

I am quite picky about my development environment, for instance: I like the Consolas 12pt font; I like 2 tab spaces instead of 4; I like virtual space in the editor; etc. etc.

Visual Studio Express does not give the option to change tab size and virtual space settings so I immediately jumped into regedit and edited the values. Then I thought that maybe I could export my settings from Visual Studio 2005 Professional and import them into Express.

This worked, with the exception of some command bar stuff that isn’t supported in Express. The added bonus was that the Options screen now displays more settings that before:

### Options screen before import:

[![](https://sites.google.com/site/stevedunns/VsExpressSettingsBefore.jpg)](https://sites.google.com/site/stevedunns/VsExpressSettingsBefore.jpg)

### Options screen after import:

[![](https://sites.google.com/site/stevedunns/VsExpressSettingsAfter.jpg)](https://sites.google.com/site/stevedunns/VsExpressSettingsAfter.jpg)

Very nice. It’s just a shame that Express doesn’t support plug-ins as I really miss [ReSharper](http://stevedunns.blogspot.com/2006/12/resharper-25-released.html "ReSharper 2.5 Released").