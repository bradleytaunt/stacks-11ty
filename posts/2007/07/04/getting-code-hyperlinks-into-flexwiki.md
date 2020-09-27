---
title: "Getting 'code://' hyperlinks into FlexWiki"
date: '2007-07-04T18:02:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 67
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2007/07/getting-hyperlinks-into-flexwiki.html
blogger_internal:
    - /feeds/32841709/posts/default/3224027422899205273
---
[Reflector](http://www.aisto.com/roeder/dotnet/), when installed, adds a “*code://*” protocol handler, enabling hyperlinks to specified types in assemblies. This handler is similar to http:// or ftp://, but instead of taking you to a web site, it takes you to a type in an assembly!

For example, *code://System.Web/System.Web.UI.WebControls.WebControl* will launch Reflector and navigate to the WebControl type in the System.Web.UI.WebControls namespace.

Custom types can also be navigated to, although the associated assembly must be loaded first.

By default, FlexWiki does not handle all protocol handlers. To get it to handle the code:// protocol, a recompile is needed. I’m working with version [2.0.0.41](http://builds.flexwiki.com/download/FlexWikiCore-20/2.0.0.41/). [Later versions](http://builds.flexwiki.com/download/FlexWikiCore-20/) are now available, but the code should be in a similar place. So, for version 2.0.0.41, changes are needed to the file:  *FlexWikiCore-2.0.0.41-srcEngineSourceFormatter.cs*.

Change lines **1706** and **1707** – adding the ‘**code|**‘ segment next to the *https?|* text:

<div contenteditable="false" style="padding-right: 0px; display: inline; padding-left: 0px; float: none; padding-bottom: 0px; margin: 0px; padding-top: 0px">```
<pre style="background-color:White;"><div><span style="color: #0000FF; ">static</span><span style="color: #000000; "> </span><span style="color: #0000FF; ">string</span><span style="color: #000000; "> urlPattern </span><span style="color: #000000; ">=</span><span style="color: #000000; "> 
  </span><span style="color: #000000; ">@"</span><span style="color: #000000; ">((https?|code|ftp|gopher...</span><span style="color: #000000; ">"</span><span style="color: #000000; "> ) ;

</span><span style="color: #0000FF; ">static</span><span style="color: #000000; "> </span><span style="color: #0000FF; ">string</span><span style="color: #000000; "> urlPatternInBrackets </span><span style="color: #000000; ">=</span><span style="color: #000000; "> 
  </span><span style="color: #000000; ">@"</span><span style="color: #000000; ">((https?|code|ftp|gopher...</span><span style="color: #000000; ">"</span><span style="color: #000000; "> ) ;
</span></div>
```

</div>I must say, it’s very handy for your team to be able to navigate directly to code from a Wiki entry.