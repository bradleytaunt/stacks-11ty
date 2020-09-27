---
title: Problems with Forms Authentication and ASP.NET Themes
date: 2006-10-20
status: publish

author: stevedunn
excerpt: ''
type: post
id: 90
tags:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2006/10/forms-authentication-and-stylesheet.html
blogger_internal:
    - /feeds/32841709/posts/default/7016856304778492200
dsq_thread_id:
    - '6352487577'
---
[](http://dunnhq.com/formsauth2.png)

It’s sometimes the strangest (and seemingly irrelevant) combinations of technology that give you the most problems. For a good few hours I’ve been wondering why my web site, which uses [Forms Authentication](http://msdn2.microsoft.com/en-us/library/ykzx33wh.aspx) and Themes, was not displaying any formatting or images.

It turns out that the URLs specified in the authentication section in web.config are used for ALL resources. So, in my case, the page was trying to load a .css file but ASP.NET was redirecting the request to default.aspx, which of course, is not a style-sheet and has a different MIME type. Here’s the section of my web.config file:

```
<authentication mode="Forms">
      <forms  loginUrl="Default.aspx"
        defaultUrl="Default.aspx"
        protection="All"
        timeout="30"
        path="/"
        requireSSL="false"
        slidingExpiration="true"
        cookieless="UseDeviceProfile"
        domain=""
        enableCrossAppRedirects="false"/>
    </authentication>
```

To fix this, I allow unauthenticated access to the resources, which was straight-forward. I added the following to the web.config file:

```
<pre style="background-color:#FFFFFF;;overflow: auto;"> <location path="App_Themes">
    <system.web>
      <authorization>
        <allow users="*"/>
      </authorization>
    </system.web>
  </location>
```

The tricky part in finding this was that the page’s HTML looked fine, there were no errors, and saving the resulting HTML to a file and viewing it produced the right results.

Firefox’s JavaScript Console proved incredibly helpful in finding the problem:

[![](https://2.bp.blogspot.com/_bIhihWOyLpw/RkX8P_97lVI/AAAAAAAAAAc/6DtARTWtex4/s400/formsauth2.png)](https://2.bp.blogspot.com/_bIhihWOyLpw/RkX8P_97lVI/AAAAAAAAAAc/6DtARTWtex4/s1600-h/formsauth2.png)   
Once I saw this, it all fell into place!