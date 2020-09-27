---
title: Displaying values in the Visual Studio Debugger
date: '2008-10-20T13:51:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 59
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2008/10/displaying-values-in-visual-studio.html
blogger_internal:
    - /feeds/32841709/posts/default/7682041183591784780
dsq_thread_id:
    - '6376326759'
---
Normally, when you display values in the Visual Studio debugger, you get formatting (quotes, tabs etc.) included. For instance, if you’ve got <span style="font-style: italic">string s = "Hello\[tab\]World";</span> then hovering over s in the debugger displays "HellotWorld". If you wanted to copy a value value to the clipboard (maybe because you landed on an exception and you want to send the error to <strike>the idiot that caused it</strike> your fellow colleague), you’d probably right click on the value and select ‘copy value’. This copies the value to the clipboard. Another way is to use the <span style="font-weight: bold">immediate window</span>. Using the example above, typing ‘s’ in the immediate window would produce:

 [![](https://2.bp.blogspot.com/_bIhihWOyLpw/SPyBkOfTnhI/AAAAAAAAARs/ycCmtOKDvtQ/s400/hw1.png)](https://2.bp.blogspot.com/_bIhihWOyLpw/SPyBkOfTnhI/AAAAAAAAARs/ycCmtOKDvtQ/s1600-h/hw1.png)

 To get rid of formatting (the quotes and the control characters), use the <span style="font-style: italic; font-weight: bold">,nq</span> option:

 [![](https://2.bp.blogspot.com/_bIhihWOyLpw/SPyBjzDc4dI/AAAAAAAAARk/QemrhnrSNIU/s400/hw2.png)](https://2.bp.blogspot.com/_bIhihWOyLpw/SPyBjzDc4dI/AAAAAAAAARk/QemrhnrSNIU/s1600-h/hw2.png)

This is useful in itself, but it really becomes invaluable if you want to show some XML. With the magical <span style="font-style: italic; font-weight: bold">,nq</span> switch, the following code: [![](https://2.bp.blogspot.com/_bIhihWOyLpw/SPyDNmmpDSI/AAAAAAAAAR0/Bbide7cMp8E/s400/x1.png)](https://2.bp.blogspot.com/_bIhihWOyLpw/SPyDNmmpDSI/AAAAAAAAAR0/Bbide7cMp8E/s1600-h/x1.png)

produces the following output in the immediate window: [![](https://4.bp.blogspot.com/_bIhihWOyLpw/SPyExCPdxHI/AAAAAAAAASM/Hk0LOH8w1yE/s400/x2.png)](https://4.bp.blogspot.com/_bIhihWOyLpw/SPyExCPdxHI/AAAAAAAAASM/Hk0LOH8w1yE/s1600-h/x2.png)

Pretty useless, but if you add <span style="font-style: italic; font-weight: bold">,nq</span>, you get: [![](https://4.bp.blogspot.com/_bIhihWOyLpw/SPyDvZxIR8I/AAAAAAAAASE/A_QbIwxvBmg/s400/x3.png)](https://4.bp.blogspot.com/_bIhihWOyLpw/SPyDvZxIR8I/AAAAAAAAASE/A_QbIwxvBmg/s1600-h/x3.png)

Much nicer.

<span style="font-style: italic; font-weight: bold">nq</span> stands for <span style="font-style: italic; font-weight: bold">nice’n quick, </span>because it doesn’t waste time writing quotes.

Probably.