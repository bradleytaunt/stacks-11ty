---
title: A tool to switch project files between using Visual Studio 2008 and 2010
date: 2010-02-25
status: publish

author: stevedunn
excerpt: ''
type: post
id: 36
thumbnail: /static/images/imported_from_wp/2010/02/toolbox_thumb6.jpg
tags:
    - tool
    - 'visual studio'
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2010/02/tool-to-switch-project-files-between.html
blogger_internal:
    - /feeds/32841709/posts/default/4437544393809635168
dsq_thread_id:
    - '5950316269'
---
***Update: the source is now on [GitHub](https://github.com/SteveDunn/SwitchVsVersion)***

Visual Studio 2010 is almost here. Visual Studio 2010 (the release candidate) **is here**.

I’ll describe the problem before I describe the tool: You want to use the <span style="font-size: 1rem;">latest version of Visual Studio but you don’t want it to modify all of your projects and solutions because you’ve got other team members who don’t want to (or can’t) switch to 2010.</span>

A serious problem indeed. If only you could you run a tool to update all of you project files to 2010, do your changes in Visual Studio 2010, then switch all projects back to 2008 format before checking in.

Well, here’s a command line tool to do just that!

It’s very easy to use: run it from the command line, give it a folder name, and tell it whether you want all your projects and solutions under that folder to be either 2008 or 2010 format. For example:

`SwitchVsVersion c:\temp\MySolution 2010`  
`SwitchVsVersion c:\temp\MySolution 2008`

As a bonus, you can also tell it to change all your target frameworks to either .NET 4 or .NET 3.5. For example:

`SwitchVsVersion c:temp\MySolution 3.5Framework`  
`SwitchVsVersion c:temp\MySolution 4.0Framework`

[Binary](http://sites.google.com/a/dunnhq.com/steve/SwitchVsVersion-Binary.zip?attredirects=0&d=1) here. [Source code](http://sites.google.com/a/dunnhq.com/steve/SwitchVsVersion-source.zip?attredirects=0&d=1) here. Here’s a [test solution](http://sites.google.com/a/dunnhq.com/steve/TestSolutionWithLotsOfDifferentTypeOfBlankProjects.7z?attredirects=0&d=1) with lots of different empty projects to try it out on too.

**Disclaimer: this is a noddy little tool that may not work properly on your projects and solutions. I’ve tested it on quite a large WinForms solution and it worked fine. I’ve also tested it on quite a variety of projects including C# and VB WinForms, Web Apps, Libraries, WPF Projects, and WPF Libraries. The only one it doesn’t do is C++ projects (which is a coincidence, because I no longer do C++ projects either). Be sure to back up your stuff before you use this tool! Terms and conditions apply.**

**Update: Thanks for the feedback. As requested, the source is covered under the WTFPL. Do what you want with it:**

DO WHAT THE FUCK YOU WANT TO PUBLIC LICENSE  
 **This program is free software. It comes without any warranty, to the extent permitted by applicable law. You can redistribute it and/or modify it under the terms of the Do What The Fuck You Want To Public License, Version 2, as published by Sam Hocevar. See <http://sam.zoy.org/wtfpl/COPYING> for more details.**