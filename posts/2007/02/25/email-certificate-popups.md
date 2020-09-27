---
title: Email certificate popups
date: '2007-02-25T18:48:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 75
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2007/02/email-certificate-popups.html
blogger_internal:
    - /feeds/32841709/posts/default/3223891746282861535
dsq_thread_id:
    - '7859009340'
---
I recently switched to Vista and Office 2007. I set-up Outlook with the details of my email certificate. The trouble is, whenever sending a message, Vista pops up a dialog asking whether to grant or deny permission to the certificate. The exact text is:

> “Grant or Deny this application permission to use this key”.

The way around this is to not use Outlook to install the certificate but to right click on the certificate in Explorer and let Vista install it. Another important thing when doing this is to NOT click the Strong option – this is what causes the prompting – leave it as Medium.

To reinstall the certificate:

- Go to Internet Explorer/Tools/Option/Content/Certificates then Export your certificate (checking the box to delete it after export).
- Then, right click from Explorer and select Install.
- When this is done, reselect the certificate from Outlook – Tools/Trust Center/E\_mail Security.