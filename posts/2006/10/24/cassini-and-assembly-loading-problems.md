---
title: Cassini and assembly loading problems
date: '2006-10-24T14:36:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 86
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2006/10/cassini-and-assembly-loading-problems.html
blogger_internal:
    - /feeds/32841709/posts/default/3630799249245541494
dsq_thread_id:
    - '6408936052'
---
Cassini is the Visual Studio development web server. Generally, Cassini is great; you give it a port number and a path and off it goes – hosting ASP.NET pages in a similar fashion to ISS but much quicker. Plus, it’s unloaded when you stop debugging.

One issue I came across today was with Cassini and the loading of assemblies. During development of .NET applications, I like to use project references rather than binary references (whether those references are in our out of the GAC).

The problem lies with the fact that Cassini occasinally switches app domains, forcing objects to be serialised across. This serialisation was failing as one of our serialisable objects were in an assembly that wasn’t in the GAC and wasn’t available anywhere for the Cassini process to load. The exact error was:

*Type is not resolved for member ‘Company.Product.Type,Company.Product.dll, Version=1.0.0.0, Culture=neutral, PublicKeyToken=blah’*

Investigation led to the [suggestion to use DEVPATH](http://blogs.msdn.com/junfeng/archive/2005/12/13/503059.aspx). Basically, this means adding the following entry to the ‘runtime’ section of the machine.config file:

<div contenteditable="false" style="padding-right: 0px; display: inline; padding-left: 0px; float: none; padding-bottom: 0px; margin: 0px; width: 282px; padding-top: 0px">```
<pre style="background-color:White;"><div><span style="color: #0000FF; "><</span><span style="color: #800000; ">developmentMode </span><span style="color: #FF0000; ">developerInstallation</span><span style="color: #0000FF; ">="true"</span><span style="color: #0000FF; ">/></span></div>
```

</div>… and setting the **DEVPATH** environment variable to the directory where your private copies of assemblies are located. This is *supposed* to load a matching assembly regardless of version. Unfortunately, this didn’t work and for whatever reason, a ComException was being thrown very early on when Cassini started.

Although this didn’t work, there was a link in the page to another [MSDN article](http://msdn2.microsoft.com/en-US/library/efs781xb.aspx) describing a way to redirect assembly loading. This again used the runtime section of the machine.config file, but this time using:

<div contenteditable="false" style="padding-right: 0px; display: inline; padding-left: 0px; float: none; padding-bottom: 0px; margin: 0px; padding-top: 0px">```
<pre style="background-color:White;white-space:-moz-pre-wrap; white-space: -pre-wrap; white-space: -o-pre-wrap; white-space: pre-wrap; word-wrap: break-word;"><div><span style="color: #000000; "> </span><span style="color: #0000FF; "><</span><span style="color: #800000; ">assemblyBinding </span><span style="color: #FF0000; ">xmlns</span><span style="color: #0000FF; ">="urn:schemas-microsoft-com:asm.v1"</span><span style="color: #0000FF; ">></span><span style="color: #000000; ">
      </span><span style="color: #0000FF; "><</span><span style="color: #800000; ">dependentAssembly</span><span style="color: #0000FF; ">></span><span style="color: #000000; ">
        </span><span style="color: #0000FF; "><</span><span style="color: #800000; ">assemblyIdentity </span><span style="color: #FF0000; ">name</span><span style="color: #0000FF; ">="Company.Product"</span><span style="color: #FF0000; "> publicKeyToken</span><span style="color: #0000FF; ">="blah"</span><span style="color: #FF0000; "> culture</span><span style="color: #0000FF; ">="neutral"</span><span style="color: #FF0000; "> </span><span style="color: #0000FF; ">/></span><span style="color: #000000; ">
        </span><span style="color: #0000FF; "><</span><span style="color: #800000; ">codeBase </span><span style="color: #FF0000; ">version</span><span style="color: #0000FF; ">="1.0.0.0"</span><span style="color: #FF0000; "> href</span><span style="color: #0000FF; ">="file://C:/Blah/Company.Product.dll"</span><span style="color: #0000FF; ">/></span><span style="color: #000000; ">
      </span><span style="color: #0000FF; "></</span><span style="color: #800000; ">dependentAssembly</span><span style="color: #0000FF; ">></span><span style="color: #000000; ">
    </span><span style="color: #0000FF; "></</span><span style="color: #800000; ">assemblyBinding</span><span style="color: #0000FF; ">></span></div>
```

</div>This worked great and saved me having to use IIS or copying my assemblies all over the place so Cassini can load them.

I hope this post proves useful to anyone having a similar problem. It will probably prove useful to me when I come across the problem again in the far future having forgotten how I got around it the first time!