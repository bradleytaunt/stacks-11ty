---
title: What to expose in a framework
date: '2006-10-23T16:27:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 87
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2006/10/what-to-expose-in-framework.html
blogger_internal:
    - /feeds/32841709/posts/default/7128654571628577152
dsq_thread_id:
    - '6323280051'
---
[Scott Hanselman](http://www.hanselman.com/) [blogged](http://www.hanselman.com/blog/IsThereAGoodReasonToMarkAClassPublic.aspx) recently on reasons to make a class public in a framework. One reason was that a developer may want the functionality offered by a particular class, either to be used as-is or to be extended.

Normally, frameworks are quite specific in what they do and what they provide. If a whole ‘chunk’ (class) is required to be made public, then it may be the case that this functionality isn’t in the realm of what the Framework was designed to offer. For example, should a class that lists the zipped files in a directory be exposed from a compression framework? Or, should a regular expression helper class be exposed from a logging/tracing framework?

Opening up large chunks of code because someone wants the functionality can dilute the Framework and make the API harder to understand because it offers so much functionality. With this in mind, if the framework you’ve given them doesn’t do what they want, then maybe rethink ways of incorporating the functionality into the Framework rather than opening up a chunk of code.

You might be thinking that it’d be difficult incorporating all the functionality of a particular class into other parts of the framework; classes, whether internal or exposed, should be succint (following the [Single Responsibility Principle](http://en.wikipedia.org/wiki/Single_responsibility_principle)) – so there shouldn’t be too much to move around to give them the features they require.

When we start talking about frameworks and OO concepts such as SRP, it brings to mind a very valid point raised in the excellent [Framework Design Guidelines](http://www.amazon.com/Framework-Design-Guidelines-Conventions-Development/dp/0321246756) book – something along the lines that OO should play a part in the implementation of a framework but not in the API of the framework (I think the example of Streams/TextReaders was used as a very good example). The .NET Framework now seems to have more and more utility classes that help to flatten the heirarchy and (in my opinion) increase usability/memorability.

Some examples would be a good way of testing our arguments. Perhaps examples based on the .NET Framework wouldn’t be the best to use as this is a lot more generic than say, frameworks for logging/tracing or compression.