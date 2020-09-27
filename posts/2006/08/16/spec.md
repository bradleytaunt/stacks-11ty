---
title: Spec#
date: '2006-08-16T20:07:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 106
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2006/08/spec.html
blogger_internal:
    - /feeds/32841709/posts/default/115575524640482865
---
Spec# is an addition to C# to allow specifications to be explicitly added to methods. Specifications can state that a method takes a string (which must be non-nul), an integer (which must be between 0 and n), or an array (of which all entries must be non null). Previously in C#, this would have meant a fair few lines of code that manually checked parameters and threw the respective exceptions. Furthermore, without specifications, you cannot force any over-ridden method to comply to the same specification.

Spec# is currently a research project and can be downloaded at <http://research.microsoft.com/specsharp/>

It can be installed to run in Visual Studio 2003 and 2005. For both systems, it requires an application called Simplify. This is a java application that can be downloaded at HP Labs Java Programming Toolkit page. The zipped file that contains Simplify.exe can be found at <http://www.hpl.hp.com/downloads/crl/jtk/download-escjava.html>, but don’t forget to first read the licence at <http://www.hpl.hp.com/downloads/crl/jtk/agreement.html> 😉