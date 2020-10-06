---
title: Running unit tests in Visual Studio Express
date: 2007-03-19
status: publish

author: stevedunn
excerpt: ''
type: post
id: 74
tags:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2007/03/running-unit-tests-in-visual-studio.html
blogger_internal:
    - /feeds/32841709/posts/default/194124793454938226
dsq_thread_id:
    - '6929723235'
---
The brilliant [TestDriven.net](http://testdriven.net/) can’t run in Visual Studio Express (well, from what I’ve heard, it **can**, but [Microsoft asked for it to be removed](http://weblogs.asp.net/nunitaddin/archive/2006/10/16/What-happened-to-TestDriven.NET-1.0_3F00_.aspx)).

Therefore, to run unit tests in Visual Studio Express, you must set your debugger application to point to NUnit.exe (or the brilliant [MBUnit](http://www.mbunit.com/)). This isn’t straightforward in Express and means editing the .csproj file by hand and telling it to run the NUnit exe.

Today, I wanted to run and debug some unit tests I’d written in the [XNA](http://msdn2.microsoft.com/en-us/xna/default.aspx) [Game Studio Express](http://msdn2.microsoft.com/en-us/xna/aa937795.aspx) (Visual Studio Express with some XNA bits bolted on). I couldn’t have the excellent right click/run unit test feature and I thought there’s got to be a better way than editing the .csproj file manually.

So I changed the unit test project to be a console application and added this to the Main method.

```
public static void Main( )
{
    AppDomain.CurrentDomain.ExecuteAssembly(
        @"C:Program FilesNUnit-Net-2.0 2.2.9binNUnit-console.exe",
        null,
        new string[ ] { Assembly.GetExecutingAssembly( ).Location } );
}
```

And it worked. Which was nice.

Update:
=======

Jamie recently left a message saying that the new Beta version DOES support Express editions! Read his post [here](http://weblogs.asp.net/nunitaddin/archive/2007/04/02/express-sku-support.aspx) and get [downloading](http://www.testdriven.net/download.aspx) straight away!