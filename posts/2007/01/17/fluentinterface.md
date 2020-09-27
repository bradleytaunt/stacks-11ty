---
title: FluentInterface
date: '2007-01-17T14:03:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 79
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2007/01/ive-posted-before-about-stringbuilder.html
blogger_internal:
    - /feeds/32841709/posts/default/4981670039336400735
dsq_thread_id:
    - '7711956812'
---
I’ve [posted before](http://stevedunns.blogspot.com/2006/08/quicky-stringbuilder-tip.html) about the StringBuilder tip in .NET.

Martin Fowler describes this as an [ExpressionBuilder ](http://www.martinfowler.com/bliki/ExpressionBuilder.html)pattern.

More formal terms are described in his post, for instance, a [FluentInterface](http://www.martinfowler.com/bliki/FluentInterface.html) which allows code like this:

<div style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; float: none; padding-top: 0px">```
customer.newOrder() 
	.with(6, "TAL") 
	.with(5, "HPK").skippable() 
	.with(3, "LGV").priorityRush();
```

</div> I personally like this style but agree that if every object had these strange looking methods it would certainly pollute an API.

Another formal term describing how not to pollute an API is [CommandQuerySeparation](http://www.martinfowler.com/bliki/CommandQuerySeparation.html). Basically, this means that a method that changes the observable state of an object shouldn’t have a return value.

The ExpressionBuilder pattern is the solution to this: it is a seperate object that defines the FluentInterface and yet doesn’t pollute the API.

I’m glad that I now know more than 3 patterns, the [Factory pattern](http://en.wikipedia.org/wiki/Factory_pattern), the [Visitor pattern](http://en.wikipedia.org/wiki/Visitor_pattern), and the [Submarine pattern](http://dunnhq.com/SubmarinePattern).