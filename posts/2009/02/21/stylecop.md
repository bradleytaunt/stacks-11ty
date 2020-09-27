---
title: StyleCop
date: '2009-02-21T14:44:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 55
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2009/02/stylecop.html
blogger_internal:
    - /feeds/32841709/posts/default/2543969566487017326
dsq_thread_id:
    - '6361246653'
---
[StyleCop](http://code.msdn.microsoft.com/sourceanalysis) is a tool that looks at your source code and recommends ways to improve readability and consistency. For instance, it tells you to:

1. Put things in a consistent order in the file – Constructors first, followed by public methods, followed by private methods etc.
2. Put a blank line after a closing brace. I thought this was a bit anal, but for some reason it makes code much more readable. *On a related note, some people swear by having no blank lines in their source. Their reasoning: they can see more on screen without having to scroll and can see more of the method on screen at once. To me, this was like reading a book with no paragraphs. Also, If you’ve got methods that take up a whole screen, they’re probably* [*doing too much*](http://en.wikipedia.org/wiki/Single_responsibility_principle) *and are* [*too complex*](http://www.onjava.com/pub/a/onjava/2004/06/16/ccunittest.html)*. I was invited to try it with the reassurance that I’d eventually see the benefit. I declined, but then realised that I had been ‘trying it’ all along – every time I read the code!*
3. Remove unnecessary parenthesis. Reminds of a quote: *“Parenthesis (however relevant) are unnecessary.”*
4. Add XML comments to methods, properties, and events.

There’s hundreds of suggestions, mostly good, although there are some issues – here’s mine:

1. I generally don’t like to comment private methods, but there doesn’t seem a way to tell it to only warn me if I have public methods that are undocumented. I hope this’ll be added to the next version. I don’t like commenting private methods as, if I feel it needs a comment, then the code isn’t self describing and is either a) poorly named, or b) too complex, or c) doing too much.
2. StyleCop says don’t precede field names with notation. I follow the almost ubiquitous practice of preceding private fields with an underscore. For no other reason than to be able to type *underscore* + *ctrl+space* and have intellisense pop-up my private fields.

The good news is that it’s possible to turn off warnings. It’s also very well thought out in how these settings are managed: If you think a certain warning is so ridiculous you never want to see it again, you can put it in the StyleCop.Settings file and put this file at the top of your source tree. If you’ve got a project where it would make sense to turn off a warning just for that project, you can put another StyleCop.Settings file at the project level. More [here](http://blogs.msdn.com/sourceanalysis/pages/sharing-source-analysis-settings-across-projects.aspx).

I’m wondering if anybody would be brave enough to integrate this in their CI process! Breaking the build because there’s not a blank line under a brace seems a tad extreme!