---
title: I Hate ClearCase Part II - When a text file isn't a text file!
date: '2006-11-21T11:53:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 84
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2006/11/i-hate-clearcase-part-ii-when-text-file.html
blogger_internal:
    - /feeds/32841709/posts/default/863661899858205259
dsq_thread_id:
    - '6401298727'
---
Here’s a question: If you have a text file that contains a very long line of text (&gt;8000 characters), is it still a text file?

I’d say Yes. But <strike>Computer</strike>ClearCase says No. Or at least hinted it meant No via several obscure error messages.

The file in question is a whole bunch of JavaScript code (part of the Microsoft AJAX release) that is not intended to be read by anyone viewing a web page, and hence is sensibly put on one line (albeit 69168 bytes in length).

Firstly, I was getting a strange error when adding them to ClearCase. Apparently, despite of the error, they were being added – I found them in a checked-out state. Upon trying to check them in, I got:

> Error checking in ‘…MicrosoftAjax.js’. Type manager “text\_file\_delta” failed create\_version operation.  
> Unable to check in ‘…MicrosoftAjax.js’

…followed by OK and Cancel buttons (quite how one can Cancel an operation that can’t be done anyway is beyond me!)

I then thought I’d take a look at the file and did a ‘diff’ with the previous version. I got this:

> Error encountered doing compare operation.  
> “c:tempccdm02327” is not a ‘text file’: it contains a line exceeding 8000 bytes.  
> Use a different type manager (such as a compressed file).

So, according to ClearCase, a text file is not a text file if it has lines of over 8000 characters!

Anyway, the solution was to use the cleartool command line tool to add the file using a different ‘type’ – a compressed text file type. Note that this doesn’t actually change the contents of the file, nor the way it’s handled (thankfully!). Of course, once the solution was presented to me…

***C:folderScriptLibraryRelease&gt;*cleartool mkelem -nc -eltype compressed\_text\_file MicrosoftAjax.js**

…everything became perfectly clear!