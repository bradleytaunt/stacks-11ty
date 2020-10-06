---
title: Excluding Items From Code Coverage
date: 2008-06-27
status: publish

author: stevedunn
excerpt: ''
type: post
id: 60
tags:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2008/06/excluding-items-from-code-coverage.html
blogger_internal:
    - /feeds/32841709/posts/default/3919031299791654917
dsq_thread_id:
    - '6359433948'
---

There’s an attribute in nCover that can be applied to your code to exclude it when doing code coverage. This is handy for auto-generated types such as web services etc.

The attribute is in the nCover assembly, but most people wouldn’t want to ship with their assemblies. Fortunately, you can define your own attribute. If you’re using TestDriven.NET, call it ‘CoverageExcludeAttribute’, if not, call it what you want.

When using NCover, pass the name of the attribute in the */ea WhateverYouCalledTheAttribute* command line attribute.

Here’s the code, with comments. Remember, don’t put this in a namespace!

```
/// <summary> 
/// Use this attribute on types that do not need code coverage analysis. 
/// Such types are auto-generated types, such as web services etc. 
/// 
/// This attribute is used by TestDriven.NET to exclude the type/method in the 'test with coverage' functionality. 
/// This attribute can also be passed to NCover proper by using the /ea CoverageExcludeAttribute command line. 
/// </summary> 
/// <remarks> 
/// Note that this should NOT be part of a namespace! 
/// </remarks> 
[CoverageExclude] 
class CoverageExcludeAttribute : Attribute { } 
```
