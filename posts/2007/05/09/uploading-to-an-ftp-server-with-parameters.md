---
title: Uploading to an FTP server with parameters
date: '2007-05-09T17:26:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 71
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2007/05/uploading-to-ftp-server-with-parameters.html
blogger_internal:
    - /feeds/32841709/posts/default/832502870527983207
dsq_thread_id:
    - '6368373139'
---
This post will have a limited audience (even more limited than my normal posts!), but if you’re searching for a solution to this particular problem, I hope you’ll be glad you found this.

I was recently tasked with uploading a file to an FTP server. I [optimistically estimated](http://www.hanselman.com/blog/SoftwareEstimationRememberThatTargetsAreNotEstimates.aspx) that it shouldn’t take long as we’re using .NET 2.0 and there’s FTP stuff in 2.0.

But, the particular server I had to write to took parameters on the PUT command (something I’d never seen before). The put looked something like this:  
*PUT thefile.txt %destinationFilename.txt%param2%%param4*

The parameters tell the server things like what ‘mailbox’ to use, what account to use to write the file, etc. etc.

A quick bit of info on FTP: you first send the **PUT** *request*, and get a *response*, followed by other *requests* (for things like credentials), followed ultimately by sending a **STOR** *command*.

The .NET 2.0 implementation of FtpWebRequest does not take into account differences between the *‘request* (PUT)’ parameters and the ‘*command* (STOR) parameters’.

To get around this, one must use sockets directly. I found a [Microsoft KB article](http://support.microsoft.com/kb/812409) that contained just that. The sample demonstrated using pluggable protocol handlers. I removed the bits that weren’t relevant and modified it to handle *command* parameters.

I fronted all this with an **FtpTransfer** class that deals with just uploading files. Typical usage looks like this:

<div contenteditable="false" style="padding-right: 0px; display: inline; padding-left: 0px; float: none; padding-bottom: 0px; margin: 0px; padding-top: 0px">```
<pre style="background-color:White;"><div><span style="color: #000000; ">FtpTransfer ftpTransfer </span><span style="color: #000000; ">=</span><span style="color: #000000; "> </span><span style="color: #0000FF; ">new</span><span style="color: #000000; "> FtpTransfer( 
    </span><span style="color: #0000FF; ">new</span><span style="color: #000000; "> Uri( </span><span style="color: #000000; ">@"</span><span style="color: #000000; ">ftp://serverRequiringParameters</span><span style="color: #000000; ">"</span><span style="color: #000000; "> ), 
    </span><span style="color: #000000; ">@"</span><span style="color: #000000; ">yourUsername</span><span style="color: #000000; ">"</span><span style="color: #000000; ">, 
    </span><span style="color: #000000; ">@"</span><span style="color: #000000; ">yourPassword</span><span style="color: #000000; ">"</span><span style="color: #000000; "> );

ftpTransfer.UploadFileWithParameters( 
    </span><span style="color: #000000; ">@"</span><span style="color: #000000; ">c:tempftptest.txt</span><span style="color: #000000; ">"</span><span style="color: #000000; ">, 
    </span><span style="color: #000000; ">@"</span><span style="color: #000000; ">destinationFilename.txt</span><span style="color: #000000; ">"</span><span style="color: #000000; ">, 
    </span><span style="color: #000000; ">@"</span><span style="color: #000000; ">%destinationFilename.txt%PARAM2%PARAM3</span><span style="color: #000000; ">"</span><span style="color: #000000; "> );</span></div>
```

</div>The source (and a Visual Studio 2005 project) can be download [here](http://dunnhq.com/SimpleFtpWithParameterisedPut.zip).