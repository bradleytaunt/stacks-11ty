---
title: Code Formatter Plugin for Windows Live Writer
date: '2006-08-20T23:01:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 103
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2006/08/code-formatter-plugin-for-windows-live.html
blogger_internal:
    - /feeds/32841709/posts/default/115611127632181467
---
I’m quite new to blogging and have recently discovered Windows Live Writer. I’ve downloaded various plugins for code formatting but none provided me with what I wanted:

- The ability to format the code ‘live’
- The ability to wrap lines
- The ability to change the background color
- The ability to just quickly paste what’s in the clipboard as code

The plugin I implemented formats and highlights code and also does all the above. Here’s a screen shot of it in use:

[![](https://1.bp.blogspot.com/_bIhihWOyLpw/RkYMJf97lWI/AAAAAAAAAAk/hCF-Iu8bOhA/s400/codeFormatterPlugin.png)](https://1.bp.blogspot.com/_bIhihWOyLpw/RkYMJf97lWI/AAAAAAAAAAk/hCF-Iu8bOhA/s1600-h/codeFormatterPlugin.png)

[](http://homepage.ntlworld.com/steve_dunn/blogpics/CodeFormatterPluginforWindowsLiveWriter_14207/image04.png)

Here you can see that the content editor on the right can change the tab width, background color, language, and line numbers.

Below are some sample of code used with the plugin.

**Here’s some C# code:**

<div contenteditable="false" style="PADDING-RIGHT: 0px; DISPLAY: inline; PADDING-LEFT: 0px; FLOAT: none; PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-TOP: 0px">```
<pre style="BACKGROUND-COLOR: white; WORD-WRAP: break-word"><span style="color:#000000;"></span><span style="color:#0000ff;">public</span><span style="color:#000000;"> </span><span style="color:#0000ff;">int</span><span style="color:#000000;"> TabWidth<br></br><br></br>{<br></br><br></br></span><span style="color:#0000ff;">get</span><span style="color:#000000;"><br></br><br></br>{<br></br><br></br></span><span style="color:#0000ff;">return</span><span style="color:#000000;"> _content.Properties.GetInt( </span><span style="color:#000000;">@"</span><span style="color:#000000;">TabWidth</span><span style="color:#000000;">"</span><span style="color:#000000;">, </span><span style="color:#000000;">4</span><span style="color:#000000;"> );<br></br><br></br>}<br></br><br></br></span><span style="color:#0000ff;">set</span><span style="color:#000000;"><br></br><br></br>{<br></br><br></br>_content.Properties.SetInt( </span><span style="color:#000000;">@"</span><span style="color:#000000;">TabWidth</span><span style="color:#000000;">"</span><span style="color:#000000;">, value );<br></br><br></br>}<br></br><br></br>}<br></br><br></br></span><br></br>
```

</div>**and some XML markup…**

<div contenteditable="false" style="PADDING-RIGHT: 0px; DISPLAY: inline; PADDING-LEFT: 0px; FLOAT: none; PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-TOP: 0px">```
<pre style="BACKGROUND-COLOR: white"><span style="color:#000000;"></span><span style="color:#0000ff;"><</span><span style="color:#800000;">Triggers</span><span style="color:#0000ff;">></span><span style="color:#000000;"><br></br><br></br></span><span style="color:#0000ff;"><</span><span style="color:#800000;">KeyPressTrigger </span><span style="color:#ff0000;">Key</span><span style="color:#0000ff;">="PropertyListTrigger"</span><span style="color:#ff0000;"> Character</span><span style="color:#0000ff;">=" "</span><span style="color:#0000ff;">></span><span style="color:#000000;"><br></br><br></br></span><span style="color:#0000ff;"><</span><span style="color:#800000;">KeyPressTriggerValidStates</span><span style="color:#0000ff;">></span><span style="color:#000000;"><br></br><br></br></span><span style="color:#0000ff;"><</span><span style="color:#800000;">KeyPressTriggerValidState </span><span style="color:#ff0000;">State</span><span style="color:#0000ff;">="PropertyState"</span><span style="color:#ff0000;"> </span><span style="color:#0000ff;">/></span><span style="color:#000000;"><br></br><br></br></span><span style="color:#0000ff;"></</span><span style="color:#800000;">KeyPressTriggerValidStates</span><span style="color:#0000ff;">></span><span style="color:#000000;"><br></br><br></br></span><span style="color:#0000ff;"></</span><span style="color:#800000;">KeyPressTrigger</span><span style="color:#0000ff;">></span><span style="color:#000000;"><br></br><br></br></span><span style="color:#0000ff;"><</span><span style="color:#800000;">KeyPressTrigger </span><span style="color:#ff0000;">Key</span><span style="color:#0000ff;">="ValueListTrigger"</span><span style="color:#ff0000;"> Character</span><span style="color:#0000ff;">=" "</span><span style="color:#0000ff;">></span><span style="color:#000000;"><br></br><br></br></span><span style="color:#0000ff;"><</span><span style="color:#800000;">KeyPressTriggerValidStates</span><span style="color:#0000ff;">></span><span style="color:#000000;"><br></br><br></br></span><span style="color:#0000ff;"><</span><span style="color:#800000;">KeyPressTriggerValidState </span><span style="color:#ff0000;">State</span><span style="color:#0000ff;">="ValueState"</span><span style="color:#ff0000;"> </span><span style="color:#0000ff;">/></span><span style="color:#000000;"><br></br><br></br></span><span style="color:#0000ff;"></</span><span style="color:#800000;">KeyPressTriggerValidStates</span><span style="color:#0000ff;">></span><span style="color:#000000;"><br></br><br></br></span><span style="color:#0000ff;"></</span><span style="color:#800000;">KeyPressTrigger</span><span style="color:#0000ff;">></span><span style="color:#000000;"><br></br><br></br></span><span style="color:#0000ff;"></</span><span style="color:#800000;">Triggers</span><span style="color:#0000ff;">></span><span style="color:#000000;"><br></br><br></br></span><br></br>
```

</div>I’ve made available the [source](http://files.dunnhq.com/CodeFormatterPluginSource.zip) and the [binaries](http://files.dunnhq.com/CodeFormatterPluginBinaries.zip) for this plugin.

To use it, extract the binaries to Windows Live WriterPlugins and run WLW. The source is in C# 2.0 and comes with a Visual Studio 2005 solution.

Note that the [.NET 2.0 Framework](http://www.microsoft.com/downloads/details.aspx?FamilyID=0856eacb-4362-4b0d-8edd-aab15c5e04f5&displaylang=en) must be installed before this plugin will work.

Going forward
-------------

I plan to put this plugin onto [CodePlex](http://codeplex.com/) (if they let me!). I also plan on making a few additions to the defaults via the Options screen. New languages can easily be added too thanks to the great [ActiPro Code Highlighter](http://www.actiprosoftware.com/Products/DotNet/Default.aspx). I’d also like to thank Christophe De Baene for his syntax highlighting tool. It’s a great plugin and also helped me understand how to use the ActiPro control.

Please let me know if you’d like to contribute on CodePlex or if there are any features you’d like to see at steve at dunnhq d.o.t. com