---
title: Object Oriented vs Test Oriented
date: '2007-05-17T15:25:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 70
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2007/05/object-oriented-vs-test-oriented.html
blogger_internal:
    - /feeds/32841709/posts/default/7167082622153137664
---
[Roy](http://weblogs.asp.net/rosherove/default.aspx) is debating [this very topic](http://weblogs.asp.net/rosherove/archive/2007/02/25/fxcop-is-heading-in-the-wrong-direction-no-testability-whatsoever.aspx) – that is – for any API that needs to be unit-tested, do we forego OOD principles, such as hiding irrelevant stuff, in favour of testability?

To summarise Roy’s case: he’s using public bits of the [FxCop](http://www.gotdotnet.com/Team/FxCop/) API to automate (unit-test) his custom rules – but… the FxCop team have realised they’ve got a bunch of types that shouldn’t be exposed and will be making them internal in the next ‘Orcas’ release. This means that Roy’s unit-tests will not compile against the new API.

I think the issue here is Roy using something in the API that wasn’t intended to be exposed but is rather useful; that is, offering an API to automate custom rules. From what I can see, the FxCop team are quite correctly ‘concealing’ types that shouldn’t be exposed; I for one would be glad of this decision if I were looking through their API [‘contracts’](http://www.regdeveloper.co.uk/2005/12/29/first_among_equals/) – I wouldn’t want to spend time creating and trying to use an exposed type if it weren’t mean to be exposed.

I do see the need to automate testing of custom rules, but I think this should be designed as appopriate additions to the API for that particular purpose (rather than relying on accidentally exposed types spread throughout the API to acheive the same thing). This way, the API stays tight, and also enables a more succinct, targeted API for automating tests for custom rules.

Of course, this doesn’t anwser the more general question “**How do I design an API that hides irrelevant stuff but also enables the irrelevant stuff to be tested?**”

In fact, in the paragraph above, I was going to use the term ‘How **do I design an API that is both OO and easily tested**‘, but, as [Framework Design Guidelines](http://msdn2.microsoft.com/en-us/library/czefa0ke(vs.71).aspx) correctly states, API’s are not meant to be Object Oriented (the implementation is OO, not the public API).

So, I suppose the question really becomes **‘How do I hide my OO implementation but make it easily testable?**”

One way is to have the unit tests in with the implementation. I’d prefer not to do this, but I’ve done it in the past. I’ve also taken the other route and made the odd type here and there public instead of internal so I can test externally.

I’ve been toying with the idea of having a *‘Unit Test Facade’* object in my OO code/API. Anyone use the ‘API’ can see my [intent](http://www.jot.fm/issues/issue_2004_06/article2/article2.pdf) from what’s exposed, and anyone running unit tests can exercise the implementation via the facade. Of course, this adds overhead, but does make the distinction between the API and implementation.