---
title: Cassini and assembly loading problems
date: 2006-10-24
status: publish

author: stevedunn
excerpt: ''
type: post
id: 86
tags:
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

```
<developmentMode developerInstallation="true"/>
```

… and setting the **DEVPATH** environment variable to the directory where your private copies of assemblies are located. This is *supposed* to load a matching assembly regardless of version. Unfortunately, this didn’t work and for whatever reason, a ComException was being thrown very early on when Cassini started.

Although this didn’t work, there was a link in the page to another [MSDN article](http://msdn2.microsoft.com/en-US/library/efs781xb.aspx) describing a way to redirect assembly loading. This again used the runtime section of the machine.config file, but this time using:

```
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
      <dependentAssembly>
        <assemblyIdentity name="Company.Product" publicKeyToken="blah" culture="neutral" />
        <codeBase version="1.0.0.0" href="file://C:/Blah/Company.Product.dll"/>
      </dependentAssembly>
    </assemblyBinding>
```

This worked great and saved me having to use IIS or copying my assemblies all over the place so Cassini can load them.

I hope this post proves useful to anyone having a similar problem. It will probably prove useful to me when I come across the problem again in the far future having forgotten how I got around it the first time!