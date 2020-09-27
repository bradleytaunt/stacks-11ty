---
title: Challenging Conventions with Test First Development
date: '2007-07-19T11:13:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 65
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2007/07/challenging-conventions-with-test-first.html
blogger_internal:
    - /feeds/32841709/posts/default/4104996582307314106
dsq_thread_id:
    - '6382222383'
---
I’ve just read a [great post](http://blog.objectmentor.com/articles/2007/07/17/testing-will-challenge-your-conventions) over at Tim Ottinger’s blog. In it he discusses how test first development challenges conventional development. He makes several interesting points, some of which include:

> **Point 3: *Private makes less sense than it used to. You can’t test anything that’s private.***

This is something I often [ponder over](http://stevedunns.blogspot.com/2007/05/object-oriented-vs-test-oriented.html). Making things private makes your *intent* very clear, which I think is very important. But private implementation is still a unit of code that needs testing. Then again, as described in [Test Driven Development: A Practical Guide](http://www.amazon.co.uk/Test-Driven-Development-Practical-Guide/dp/0131016490), unit tests should test the facets of *behavior.* As [Dave Astels](http://daveastels.com/) puts it in this [blog post](http://daveastels.com/2005/07/05/a-new-look-at-test-driven-development/):

*“… the idea of “unit” is a major problem. First of all it’s a vague term, and second it implies a structural division of the code (i.e. people think that they have to test methods or classes). We shouldn’t be thinking about units… we should be thinking about facets of behaviour.”*

To me, the term ‘facets of behaviour’ reads that ‘behaviour’ has ‘facets’, and that private implementation makes up each facet. So by testing the facets of behaviour, you are really testing units of private implementation (i.e. private methods). This point may be worthy of a new post…

> **Point 4: *The fat constructor argument list is a concession to the need for isolation and testing with mocks…***

Good comment. I always refactor any code I see with a fat parameter list so it takes a ‘property bag’ instead. In ReSharper, this refactoring is called ‘ExtractClassFromParameters’. The benefit of this is cleaner, more separate code, and also overcomes C#’s limitation of not having default parameters (i.e. you leave it null/default in the property bag).

> **Point 7:  *Hard to use class interfaces are now hard for you to use…***

Exactly. Which is why I find TDD a great way to figure out ‘how to design an API/Framework’ rather than ‘how to implement the API/Framework to achieve something’. Something that made a lot of sense when reading the [Framework Design Guidelines](http://stevedunns.blogspot.com/2007/04/framework-design-guidelines-is.html) is to forget OO when designing the public interface to an API – i.e. design it so it’s easy to use for the most common scenario. Exactly what is achieved by practicing TDD.