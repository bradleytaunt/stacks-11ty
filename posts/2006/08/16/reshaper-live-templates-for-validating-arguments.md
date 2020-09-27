---
title: Reshaper Live Templates for validating arguments
date: '2006-08-16T20:15:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 105
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2006/08/reshaper-live-templates-for-validating.html
blogger_internal:
    - /feeds/32841709/posts/default/115575572596927769
dsq_thread_id:
    - '7567313955'
---
I strongly agree with the [‘contract](http://www.regdeveloper.co.uk/2005/12/29/first_among_equals/)‘ mataphor in API design, hence my interest in [Spec#](http://research.microsoft.com/specsharp/) (that I’ve [blogged about before](http://stevedunns.blogspot.com/2006/08/spec.html)).

To assist in this and to eliminate the tedium of writing argument checks, I’ve created 3 Resharper Live Templates. These check for

- null parameters for any object passed
- invalid parameters for any object passed
- null or empty check for any String passed.

These templates are called **‘arg’**, **‘argnull’** and **‘argempty’** respectivly.

Resharper 1.5 doesn’t allow importing or exporting of Live Templates from the GUI. They are however stored in an XML file at %userprofile%Application DataJetBrainsReSharperUserSettings.xml. Below is a chunk of XML that must be placed under the TemplateManagerTemplates node. If you have any others, please let me know!

> &lt;Template text=”if( $TYPE$$EXPRESSION$ )&amp;#xA; throw new ArgumentException( @&amp;quot;Cannot $ACTION$ as the value passed was invalid. Please provide a valid value.&amp;quot;, @&amp;quot;$TYPE$&amp;quot; ) ;&amp;#xA;” shortcut=”arg” description=”Throws an ArgumentException” kind=”livetemplate” reformat=”false” fileMask=”” context=”Everywhere” fileContext=”CSharp” enabled=”False” id=”1723695683″&gt;
> 
> &lt;Variables&gt;
> 
> &lt;Variable name=”TYPE” expression=”variableOfType(&amp;quot;System.Object&amp;quot;)” initialRange=”0″ /&gt;
> 
> &lt;Variable name=”EXPRESSION” expression=”constant(&amp;quot; != 1&amp;quot;)” initialRange=”0″ /&gt;
> 
> &lt;Variable name=”ACTION” expression=”constant(&amp;quot;PERFORM AN ACTION&amp;quot;)” initialRange=”0″ /&gt;
> 
> &lt;/Variables&gt;
> 
> &lt;/Template&gt;
> 
> &lt;Template text=”if( $TYPE$ == null || $TYPE$.Length == 0 )&amp;#xA;throw new ArgumentNullException( @&amp;quot;$TYPE$&amp;quot;, @&amp;quot;Cannot $ACTION$ as the value passed was null or empty. Please provide a valid non null value.&amp;quot; ) ;&amp;#xA;” shortcut=”argempty” description=”Throws an ArgumentNullException when a string is null or empty” kind=”livetemplate” reformat=”true” fileMask=”” context=”Everywhere” fileContext=”CSharp” enabled=”False” id=”1705884294″&gt;
> 
> &lt;Variables&gt;
> 
> &lt;Variable name=”TYPE” expression=”variableOfType(&amp;quot;System.String&amp;quot;)” initialRange=”0″ /&gt;
> 
> &lt;Variable name=”ACTION” expression=”constant(&amp;quot;PERFORM AN ACTION&amp;quot;)” initialRange=”0″ /&gt;
> 
> &lt;/Variables&gt;
> 
> &lt;/Template&gt;
> 
> &lt;Template text=”if( $TYPE$ == null )&amp;#xA;throw new ArgumentNullException( @&amp;quot;$TYPE$&amp;quot;, @&amp;quot;Cannot $ACTION$ as the value passed was null. Please provide a valid non-null value.&amp;quot; ) ;&amp;#xA;” shortcut=”argnull” description=”Throws an ArgumentNullException” kind=”livetemplate” reformat=”true” fileMask=”” context=”Everywhere” fileContext=”CSharp” enabled=”False” id=”1497171628″&gt;
> 
> &lt;Variables&gt;
> 
> &lt;Variable name=”TYPE” expression=”variableOfType(&amp;quot;System.Object&amp;quot;)” initialRange=”0″ /&gt;
> 
> &lt;Variable name=”ACTION” expression=”constant(&amp;quot;PERFORM AN ACTION&amp;quot;)” initialRange=”0″ /&gt;
> 
> &lt;/Variables&gt;
> 
> &lt;/Template&gt;