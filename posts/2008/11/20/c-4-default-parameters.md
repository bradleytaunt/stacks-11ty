---
title: C# 4 - Default Parameters
date: '2008-11-20T13:04:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 57
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2008/11/c-4-default-parameters.html
blogger_internal:
    - /feeds/32841709/posts/default/6674564964859119900
dsq_thread_id:
    - '7889947217'
---
Coming from a C++ background, I’m really pleased that there’ll eventually be [default parameters ](http://codebetter.com/blogs/matthew.podwysocki/archive/2008/10/29/c-4-0-named-and-optional-parameters-behind-the-scenes.aspx)built into the next version of C#. But I do think that C++ had a much cleaner way of handling them: it would only allow defaults from right to left, for instance:

```
void foo(int a, int b, int c=3, int d=4)
```

It wouldn’t let you do:

```
void foo(int a=1, int b=2, int c, int d)
```

C# will, so for the example above, you’d end up with method calls that could look like:

```
foo( ,  , 3, 4)
```

One feature that I still really miss from C++ is <span style="font-weight: bold;">const</span>. This keyword could be applied to methods or parameters, so a method declared as:

```
void foo(int a, int b) const
{
}
```

would be guaranteed to not modify the state of the object (except for mutable members)

A method declared as:

```
void foo (const Person person)
{
}
```

would be guaranteed to not modify the person.

Maybe C# 5?