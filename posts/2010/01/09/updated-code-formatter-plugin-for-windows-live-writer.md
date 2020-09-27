---
title: 'Updated (again!): Code Formatter Plugin for Windows Live Writer'
date: '2010-01-09T21:07:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 37
thumbnail: /static/images/imported_from_wp/2010/01/image_thumb-5B15-5D.png
category:
    - open-source
    - tool
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2010/01/updated-code-formatter-plugin-for.html
blogger_internal:
    - /feeds/32841709/posts/default/163635037699929970
dsq_thread_id:
    - '6238615289'
---
This plug-in formats and highlights code. Version 2.0.0.3 can be [downloaded here](http://sites.google.com/a/dunnhq.com/steve/CodeFormatterPlugin2.0.0.3.zip?attredirects=0). Keep reading for more info.

As well as a few bug fixes, this release includes the following features:

· Use different formatting engines such as [**ActiPro** ](http://www.actiprosoftware.com/Products/DotNet/WindowsForms/SyntaxEditor/Default.aspx)(Insert formatted code), and [SyntaxHighlighter](http://alexgorbatchev.com/wiki/SyntaxHighlighter:Demo) (Insert highlighted code)  
· Dozens of languages, including PowerShell, MSIL, Pascal and XAML  
· Live formatting of code using the superb ActiPro code editor. ActiPro very kindly donated the license.  
· The ability to output either **highlighted text** (html) or an **image** · WordPress support for the SyntaxHighlighter Evolved plugin

This plugin adds **four tools** in WLW’s tool window:

[![image](https://lh6.ggpht.com/_bIhihWOyLpw/S0jh3HeF5bI/AAAAAAAABmE/OW94DbGPMW8/image_thumb%5B15%5D.png?imgmax=800 "image")](https://lh4.ggpht.com/_bIhihWOyLpw/S0jh2R2qIwI/AAAAAAAABmA/_XcKx99thbk/s1600-h/image%5B27%5D.png)

**Tool 1) Code as bitmap**

This uses the ActiPro formatting engine to take a snapshot of the code.

You’ll see this screen when clicked – if there’s text in the clipboard, it’ll be shown here, or you can copy and paste when the window appears:

[![image](https://lh5.ggpht.com/_bIhihWOyLpw/S0jh5XL7F7I/AAAAAAAABm4/dh3N0HtWhKc/image_thumb%5B16%5D.png?imgmax=800 "image")](https://lh5.ggpht.com/_bIhihWOyLpw/S0jh4DeQhxI/AAAAAAAABmw/8myBHxtVfGY/s1600-h/image%5B28%5D.png)

This srceen allows you to set the size of the editor window. You can either select common widths from the drop-down or put in your own width – for instance, 465 is the ideal width for my template on Blogger. The buttons on the bottom right allow you to then:

*a)* insert the image straight into the blog post or  
*b)* have the plugin copy the image or  
c) discard it.

The advantage of the option A is that the code is still editable in WLW; the disadvantage – you cannot \[yet\] apply bitmap effects, such as reflection or drop shadow.

The advantage of option B is that you can apply bitmap effects, but the disadvantage is that code will no longer be editable.

**Tool 2) Formatted code**

This also uses uses the ActiPro formatting engine.

When inserting code, the plugin window will allow various properties of the code to be changed:

[![image](https://lh5.ggpht.com/_bIhihWOyLpw/S0jh7GLsatI/AAAAAAAABnI/QxGapuPzoss/image_thumb%5B17%5D.png?imgmax=800 "image")](https://lh4.ggpht.com/_bIhihWOyLpw/S0jh6K_HyZI/AAAAAAAABnA/yEdtq8v7dfI/s1600-h/image%5B29%5D.png)

When clicking edit code, you’ll see the edit source code screen:

[![image](https://lh3.ggpht.com/_bIhihWOyLpw/S0jh89B3KqI/AAAAAAAABnY/qw26NOYDziM/image_thumb%5B18%5D.png?imgmax=800 "image")](https://lh6.ggpht.com/_bIhihWOyLpw/S0jh7_ku-SI/AAAAAAAABnM/jXZX2r-__io/s1600-h/image%5B30%5D.png)

**Tool 3) Highlighted code**

This uses the Syntax Highlighter formatting engine. When inserting code, the edit screen will appear in the same way as when you insert formatted code (see above). The only difference is a ‘show preview’ button, which displays this preview window:  
[![image](https://lh3.ggpht.com/_bIhihWOyLpw/S0jh-mAsSdI/AAAAAAAABno/S9v-5czRCxs/image_thumb%5B19%5D.png?imgmax=800 "image")](https://lh3.ggpht.com/_bIhihWOyLpw/S0jh98LDvoI/AAAAAAAABng/bEGSH3JLB3U/s1600-h/image%5B31%5D.png)

To use the SyntaxHighlighter engine, ensure your blog is correctly set-up. For the preview window to correctly display your code, ensure the Settings are correct. Here’s the Settings window:  
[![image](https://lh4.ggpht.com/_bIhihWOyLpw/S0jiAlLtuPI/AAAAAAAABn4/tLG6HLaj7aA/image_thumb%5B20%5D.png?imgmax=800 "image")](https://lh4.ggpht.com/_bIhihWOyLpw/S0jh_nC5lVI/AAAAAAAABnw/6G2mf8mVyLs/s1600-h/image%5B32%5D.png)

**Tool 4) WordPress Formatted**

This changes the HTML output to that expected by theSyntaxHighlighter Evolved plugin for WordPress. It’s very similar to using the SyntaxHighlighter engine, but you don’t need to worry about setting up your blog with the correct scripts. *Do be aware though, that for the Preview window to work correctly, you still need to set-up this plugin so that it knows where the SyntaxHighlighter brushes and scripts are (the default settings work right now, but if Alex changes the location in the future, you’ll need to update the settings).*

To see examples of the output, please [see this blog post](https://blog.dunnhq.com/posts/2009/03/06/new-version-of-the-code-formatter-plugin/).

Version 2.0.0.3 can be [downloaded here](http://sites.google.com/a/dunnhq.com/steve/CodeFormatterPlugin2.0.0.3.zip?attredirects=0). To use it, extract the binaries to **Program FilesWindows LiveWriterPlugins** and run WLW. If you’re using a version of WLW prior to Beta 3, then you need to remove it and update! (Alternatively, change the directory to Program FilesWindows Live WriterPlugins)

Thanks again to all those that left feedback. Please keep it coming. Hopefully, the bugs that have been reported have now been fixed.