---
title: Problems adding an XBox 360 Media Center Extender
date: '2009-02-24T22:53:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 53
category:
    - Uncategorised
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2009/02/problems-adding-xbox-360-media-center.html
blogger_internal:
    - /feeds/32841709/posts/default/3106196704250181196
dsq_thread_id:
    - '7686537087'
---
Skip this if you’re not using a Linksys Wireless N device, Media Center, or an XBox 360!

After my umpteenth Seagate disk packed up yesterday, I’ve just reinstalled Windows 7 X64. I have spent the last couple of hours trying to get an XBox 360 connected to Windows Media Center.

Not too long ago I went through the exact same thing: Start WMC, Start the XBox, type the number on the XBox’s screen into WMC, and get nothing. The last time I did this, it was too late in the day to discover what was wrong or how to fix it – but the next day, everything worked perfectly!

This time, I went through exactly the same ritual. I looked at the Security event log and it said that :

> Event 5032 – Audit Failure – Windows Firewall was unable to notify the user that it blocked an application from accepting incoming connections on the network.

After ensuring that I’d allowed Media Center Extenders through the home network (shortly followed by turning the damn firewall off altogether), I started getting (from the Media Center log under Applications and Services Logs in Event Viewer):

> Event 538 – Media Center Extender Setup failed as the Extender was detected on the network but the UPnP search for the Extender failed (timed out after 20000ms).

This all seemed very familiar and nothing I was doing was making a difference. It was at this point on my last attempt that I went off to do something else. This time though, the something else’s opening hours hadn’t yet arrived, so I persevered!

In the corner of the screen (remember, this is a fresh install), was the Windows Update icon. I checked to see what it needed to update, and along with the 294 Office 2007 security patches was an update for a *Marvell – Network – Wireless-N USB Network Adapter*. I wondered if this had anything to do with my Linksys Wireless N USB, and it looks like it does. And after restarting, everything worked great!

The information from Windows Update showed this information:

> Marvell – Network – Wireless-N USB Network Adapter
> 
> Update type: Optional
> 
> DriverUpdate: Marvell Network software update released in October, 2007
> 
> More information:   
> <http://winqual.microsoft.com/support/?driverid=20110859>

The URL wasn’t much good as it was broken. The driver information from device manager reads:

*Marvell Semiconductor, Inc, version 1.00.04.03 – filename MRVW24C.sys.*

This replaced the Vista drivers that I downloaded and installed from the Cisco site.

In fact, I’ve just done a search for *Marvell Linksys driver*, and it showed [this page](http://forums.linksys.com/linksys/board/message?board.id=Wireless_Adapters&thread.id=10108). This shows how to force the driver on Vista/Windows 7 if it doesn’t show up via Windows Update.

I hope some of these keywords will help others with this problem. My heart sank when I searched for the Media Center error and didn’t get 1 single hit! That shouldn’t happen any more!