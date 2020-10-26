---
title: Readonly parameters in C# - a step closer to immutability
date: 2017-12-15
status: publish

author: stevedunn
excerpt: ''
type: post
id: 210
thumbnail: /static/images/imported_from_wp/2017/12/notouch.jpg
tags:
    - .net
    - 'c#'
    - immutabillity
tag: []
post_format: []
dsq_thread_id:
    - '6351699275'
---
![](/static/images/imported_from_wp/2017/12/notouch.jpg)

I’ve been working with C# for many years now and the new additions to the language are very exciting. They’re focused on immutability. Well, actually, the [Microsoft documentation](https://docs.microsoft.com/en-us/dotnet/csharp/reference-semantics-with-value-types) seem to suggest they’re more focused on Performance, but they go hand-in-hand; the less you can modify, the faster things are.

The benefits of immutability are often overlooked especially by those who have only experienced programming in C#. But coming from a C++ background, I long for the immutability that C++ has. For example, In C++, you can:

- Declare a **method** as `const`, meaning the **method cannot modify any fields** of the class (or call any other non-`const` method)
- Declare a **parameter** as `const`, meaning the **parameter can’t be modified in that method**, and if you passed that parameter around to other methods, those methods would also have to declare that parameter as `const `and follow by the same rules
- Declare a **return type** as `const`, meaning **that you can’t change what you’re given**
- Declare a **field** as `const`, meaning that **only the constructor can set the field**

*(these bullet points are generalisation*s)

`const` is great. There’s even been 80’s pop songs written on the virtues of `const`:

![](/static/images/imported_from_wp/2017/12/img_5a3447c6abf31.png)

 The new features in C# 7.2 are losely related to the above. This post describes one of them; `in` parameters

`in` parameters
---------------

Here’s a method that takes an `in` parameter:

<div class="oembed-gist"><script src="https://gist.github.com/anonymous/8fc7c6769e76e4edd0f1aaf8ac70bb37.js"></script><noscript>View the code on [Gist](https://gist.github.com/anonymous/8fc7c6769e76e4edd0f1aaf8ac70bb37).</noscript></div>It says that the `DoStuffTo `method takes a `Thing `and **cannot modify it**. If you try, you’ll get:

![](/static/images/imported_from_wp/2017/12/img_5a3197d6498aa.png)

This is fantastic! Immutable parameters; I know that my method is immutable and I know that I don’t want to mutate any parameter.s And now, when I accidentally do, I get a compiler error.

The example above clearly violates the *intent* that you wanted a readonly variable, but what about situations where it **isn’t clear** that doing something mutates the object? What about this?

<div class="oembed-gist"><script src="https://gist.github.com/anonymous/a61012dd12882d3672ce27d92b7d1167.js"></script><noscript>View the code on [Gist](https://gist.github.com/anonymous/a61012dd12882d3672ce27d92b7d1167).</noscript></div>This is fine. **No complaints from the compiler.** You might naturally think that `Conculate` **doesn’t mutate the instance…**

Let’s look at the implementation:

<div class="oembed-gist"><script src="https://gist.github.com/anonymous/45b8c7cda12eabe884460fbf9d0913a8.js"></script><noscript>View the code on [Gist](https://gist.github.com/anonymous/45b8c7cda12eabe884460fbf9d0913a8).</noscript></div>Wait! `Conculate` does mutate state?! How could it, our parameter is `readonly`! No compiler errors like when we set the property… This is because the compiler **doesn’t know** that the method mutates state.

But all is not what it seems. Let’s run the following and see what the output is:

<div class="oembed-gist"><script src="https://gist.github.com/anonymous/9cb909a469d5530af058490a87d3405b.js"></script><noscript>View the code on [Gist](https://gist.github.com/anonymous/9cb909a469d5530af058490a87d3405b).</noscript></div>… here’s the output…

![](/static/images/imported_from_wp/2017/12/img_5a343a2d072d8.png)

We called `Conculate`, which we know mutates the state (by setting `Id `to `42`), but it turns out that a **copy was made** and the `ID `was set **on that copy**.

Here’s an excerpt from the [Microsoft page](https://docs.microsoft.com/en-us/dotnet/csharp/reference-semantics-with-value-types) on reference semantics with value types:![](/static/images/imported_from_wp/2017/12/img_5a3199e3f373f.png)

So, it turns out that `readonly` parameters **aren’t as powerful as C++ `const` parameters.** They are, technically, read-only (you can’t mutate them), but they’re not `const` as in C++ `const`.

I also don’t like the fact that you can legally call methods that mutate the instance, but don’t know about it. If `const `methods existed in C#, the compiler would’ve disallowed the call to `Conculate` because it couldn’t be declared as `const` (as it mutates a field).

Perhaps in a future version of C#, we’ll get **`const `**methods…

![](/static/images/imported_from_wp/2017/12/img_5a34415973c7f.png)

But there’s more…
-----------------

Even though `readonly` parameters are a step in the right direction, I was disappointed. I was dissapointed because when I read about `readonly` parameters, I w**anted to immediately jump into every single method I’ve ever written and splash `in` keywords on every parameter**. But the majority of things passed around are **classes** and not **structs.** Notice in the earlier example that `Thing` was a `struct`. In time, with the performance benefits of [reference semantics with value types](https://docs.microsoft.com/en-us/dotnet/csharp/reference-semantics-with-value-types), I’m sure `struct` will be the go-to type instead of `class.`

Anyway, `in parameters` can be either `struct` or `class`. Here’s what happens when you change `Thing` to be a class rather than a struct; remember the earlier example where the compiler stopped you setting a property? Well, now it lets you do whatever you want:

![](/static/images/imported_from_wp/2017/12/img_5a319bb28deb0.png)

**Oh the disappointment!**

Here’s another excerpt from the documentation**:**![](/static/images/imported_from_wp/2017/12/img_5a319bd891a2e.png)

‘*The benefits are minimal*‘. I personally think *minimal* is being generous. I would’ve use the word **Dangerous.** If `Thing` is a `class` rather than a `struct`, then what is passed is a *reference to a reference*. This means that the value that the method is dealing with **can be changed to point to something else at any time**! (*even from outside of that method*)

Here’s a (contrived) example:

<div class="oembed-gist"><script src="https://gist.github.com/anonymous/05dc32470bc1dc7a88073754ed0b507e.js"></script><noscript>View the code on [Gist](https://gist.github.com/anonymous/05dc32470bc1dc7a88073754ed0b507e).</noscript></div>Here, we start off a task to do something with a `Thing`. We wait 1 second and set the reference to `null`. Assuming the user hasn’t pressed Enter yet, a `NullReferenceException` will happen when they do. This is because we’re passing a *reference to a reference* and then setting the reference to `null`.

I can only imagine all the subtle bugs that this will cause if spread throughout a codebase.

ReSharper to the rescue?
------------------------

I don’t even know if it’s possible, but I’d have liked the compiler to disallow `in` parameters that **aren’t value types**. I’m sure the ReSharper team are working on a new code-inspection to warn when passing `in` _references_.