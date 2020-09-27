---
title: MbUnit and null parameters
date: '2006-09-29T12:21:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 94
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2006/09/mbunit-and-null-parameters.html
blogger_internal:
    - /feeds/32841709/posts/default/115952886100266203
---
I’ve recently moved from NUnit to MbUnit. I like the extra features it offers, in particular, the RowTest feature. This allows a single test to take different parameters – the parameters of which are specified in the attributes. Here’s an example:

<div contenteditable="false" style="padding-right: 0px; display: inline; padding-left: 0px; float: none; padding-bottom: 0px; margin: 0px; padding-top: 0px">```
<pre style="background-color:White;"><div><span style="color: #0000FF; ">class</span><span style="color: #000000; "> Test
{
    </span><span style="color: #0000FF; ">internal</span><span style="color: #000000; "> Test( </span><span style="color: #0000FF; ">string</span><span style="color: #000000; "> s )
    {
        </span><span style="color: #0000FF; ">if</span><span style="color: #000000; ">( </span><span style="color: #0000FF; ">string</span><span style="color: #000000; ">.IsNullOrEmpty( s ) )
            </span><span style="color: #0000FF; ">throw</span><span style="color: #000000; "> </span><span style="color: #0000FF; ">new</span><span style="color: #000000; "> ArgumentNullException( ) ;
    }
}

[ RowTest ]
[ Row( </span><span style="color: #000000; ">@"</span><span style="color: #000000; ">Hello World!</span><span style="color: #000000; ">"</span><span style="color: #000000; "> )]
[ Row( </span><span style="color: #000000; ">@"</span><span style="color: #000000; ">Another string</span><span style="color: #000000; ">"</span><span style="color: #000000; "> )]
</span><span style="color: #0000FF; ">public</span><span style="color: #000000; "> </span><span style="color: #0000FF; ">void</span><span style="color: #000000; "> Test1( </span><span style="color: #0000FF; ">string</span><span style="color: #000000; "> val )
{
    Test t </span><span style="color: #000000; ">=</span><span style="color: #000000; "> </span><span style="color: #0000FF; ">new</span><span style="color: #000000; "> Test( val );
}
</span></div>
```

</div>Here, Test1 is being given the parameters from the attributes on the test. Previously, say, in NUnit, I’d have written a couple of unit tests that create this Test object and give it different values. Normally, I’d also write a couple that would try and create one with a null string and an empty string and assert that it throws an ArgumentNullException.

Now, in MbUnit, I went to write the test like so:

<div contenteditable="false" style="padding-right: 0px; display: inline; padding-left: 0px; float: none; padding-bottom: 0px; margin: 0px; padding-top: 0px">```
<pre style="background-color:White;"><div><span style="color: #000000; ">        [ RowTest ]
        [ Row( </span><span style="color: #0000FF; ">null</span><span style="color: #000000; "> , ExpectedException </span><span style="color: #000000; ">=</span><span style="color: #000000; "> </span><span style="color: #0000FF; ">typeof</span><span style="color: #000000; ">( ArgumentNullException ) ) ]
        [ Row( </span><span style="color: #000000; ">@"</span><span style="color: #000000; ">Hello World!</span><span style="color: #000000; ">"</span><span style="color: #000000; "> )]
        </span><span style="color: #0000FF; ">public</span><span style="color: #000000; "> </span><span style="color: #0000FF; ">void</span><span style="color: #000000; "> Test1( </span><span style="color: #0000FF; ">string</span><span style="color: #000000; "> val )
        {
            Test t </span><span style="color: #000000; ">=</span><span style="color: #000000; "> </span><span style="color: #0000FF; ">new</span><span style="color: #000000; "> Test( val );
        }
</span></div>
```

</div>Strangely, this caused an internal error in MbUnit. Reading around, It looks like MbUnit is taking the first parameter of Row and treating it as an array rather than a single parameter. The complete non-obvious way around this is to cast the null to a string:

<div contenteditable="false" style="padding-right: 0px; display: inline; padding-left: 0px; float: none; padding-bottom: 0px; margin: 0px; padding-top: 0px">```
<pre style="background-color:White;"><div><span style="color: #000000; ">        [ RowTest ]
        [ Row( (</span><span style="color: #0000FF; ">string</span><span style="color: #000000; ">)</span><span style="color: #0000FF; ">null</span><span style="color: #000000; "> , ExpectedException </span><span style="color: #000000; ">=</span><span style="color: #000000; "> </span><span style="color: #0000FF; ">typeof</span><span style="color: #000000; ">( ArgumentNullException ) ) ]
        [ Row( </span><span style="color: #000000; ">@"</span><span style="color: #000000; ">Hello World!</span><span style="color: #000000; ">"</span><span style="color: #000000; "> )]
        </span><span style="color: #0000FF; ">public</span><span style="color: #000000; "> </span><span style="color: #0000FF; ">void</span><span style="color: #000000; "> Test1( </span><span style="color: #0000FF; ">string</span><span style="color: #000000; "> val )
        {
            Test t </span><span style="color: #000000; ">=</span><span style="color: #000000; "> </span><span style="color: #0000FF; ">new</span><span style="color: #000000; "> Test( val );
        }
</span></div>
```

</div>This now works. Which is nice!