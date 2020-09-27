---
title: A fast way of converting C# enums to strings–and back again.
date: '2011-08-17T22:45:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 32
category:
    - 'c#'
    - open-source
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2011/08/fast-way-of-converting-c-enums-to.html
blogger_internal:
    - /feeds/32841709/posts/default/2313438609525475397
dsq_thread_id:
    - '5987273061'
---
I recently needed a fast way of converting lots of enums to strings (and back again). I needed to do it very quickly. ‘Enum.Parse’ just wasn’t fast enough.

I discovered there was no ‘enum mapper’ in C#, so I knocked up [this little class](https://gist.github.com/1152680). It uses reflection just once when it comes across a new enum.

It’s compatible with .NET 3.5 too.