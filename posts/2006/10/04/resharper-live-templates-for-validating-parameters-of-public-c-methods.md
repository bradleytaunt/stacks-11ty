---
title: ReSharper Live Templates for validating parameters of public C# methods.
date: '2006-10-04T07:21:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 93
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2006/10/resharper-live-templates-for-validating.html
blogger_internal:
    - /feeds/32841709/posts/default/3052416656173580755
---
ReSharper Live Templates are smart shortcuts you can type and have filled in automatically. For instance, typing ‘foreach’ and pressing tab produces:

```
      foreach ( object o in something )
      {
      }
```

I’ve created 3 Live Templates for validating arguments in public methods (C#). Here’s a short [video demonstration](http://files.dunnhq.com/ReSharperLiveTemplateDemo.avi "Video demonstration of what I'm talking about"). I’ve [blogged about these before](http://stevedunns.blogspot.com/2006/08/reshaper-live-templates-for-validating.html) for ReSharper 1.5 and said that there’s no way to export/import the templates. But in ReSharper 2.0, there is! You can get them [here](http://files.dunnhq.com/ArgCheckLiveTemplatesForResharper.xml). Go to ReSharper/Options/Templates/LiveTemplates and click the ‘Import templates from file’ button.