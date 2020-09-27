---
title: Quicky StringBuilder Tip
date: '2006-08-16T19:53:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 107
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2006/08/quicky-stringbuilder-tip.html
blogger_internal:
    - /feeds/32841709/posts/default/115575441960442137
---
StringBuilder has an Append method that returns a reference to itself. This is useful for when you want to append several items in one go. The following code is an example. Obviously, you’ll get more benefit the more items you add:

 StringBuilder sb = new StringBuilder( ) ;  
 string s = sb.Append( @”Hello ” )  
 .Append( @”World” )  
 .ToString( ) ;

If you’ve been forced into programming in VB, then check out the original text of this tip at devx.com:

<http://www.devx.com/tips/Tip/28152>