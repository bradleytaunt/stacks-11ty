---
title: Handy use of extension method on a bool
date: '2011-05-11T20:41:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 33
category:
    - .net
    - 'c#'
    - tips
tag:
    - idea
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2011/05/handy-use-of-extension-method-on-bool.html
blogger_internal:
    - /feeds/32841709/posts/default/1035053383948661691
dsq_thread_id:
    - '6037834203'
---
I don’t like to overuse if/else statements. I really dislike seeing code like this:

<div class="oembed-gist"><script src="https://gist.github.com/SteveDunn/2bd239bdcdd517efc845022b6ded45e5.js"></script><noscript>View the code on [Gist](https://gist.github.com/SteveDunn/2bd239bdcdd517efc845022b6ded45e5).</noscript></div>I just had an idea about using extension methods so I can write this instead:

<div class="oembed-gist"><script src="https://gist.github.com/SteveDunn/c68d85b681c94ebd2b501bf3e247cb2c.js"></script><noscript>View the code on [Gist](https://gist.github.com/SteveDunn/c68d85b681c94ebd2b501bf3e247cb2c).</noscript></div>and here’s the extension method:

<div class="oembed-gist"><script src="https://gist.github.com/SteveDunn/c7180f57adb98a946dd70e5de9cef5c8.js"></script><noscript>View the code on [Gist](https://gist.github.com/SteveDunn/c7180f57adb98a946dd70e5de9cef5c8).</noscript></div>Nice or not? I think it reads a bit better (for single line expressions anyway).