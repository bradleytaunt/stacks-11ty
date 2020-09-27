---
title: BackgroundWorker - automating this handy class
date: '2006-10-19T07:39:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 91
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2006/10/resharper-live-template-for-creating.html
blogger_internal:
    - /feeds/32841709/posts/default/8032375236534897037
---
[BackgroundWorker](http://msdn2.microsoft.com/en-us/library/system.componentmodel.backgroundworker.aspx) objects are an addition to .NET 2.0 to simplify asynchronous programming and are very useful in (but not restricted to) Windows Forms.

The basic idea is:

- Create a BackgroundWorker object
- Set-up various events on it, like DoWork, RunWorkerCompleted, and ProgressChanged
- Set-up various properties, like WorkerReportsProgress and WorkerSupportCancellation
- Call RunWorkerAysnc

…then, in your form you get notified of progress and can cancel the operation at any time.

I’ve created a [ReSharper](http://www.jetbrains.com/resharper/) Live Template that will help you create and set-up the BackgroundWorker object. You can download it [here](http://files.dunnhq.com/backgroundWorkerLiveTemplate.xml). For instructions on importing the Live Template into ReSharper, see my previous post [here](http://stevedunns.blogspot.com/2006/10/resharper-live-templates-for-validating.html).