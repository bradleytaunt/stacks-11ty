---
title: Announcing a new version of the Gleed 2D XNA tool
date: '2012-01-08T20:35:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 31
thumbnail: /static/images/imported_from_wp/2012/01/gleed-original_thumb.jpg
category:
    - .net
    - 'c#'
    - open-source
    - tool
    - xbox-live-indie-games
    - xna
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2012/01/announcing-new-version-of-gleed-2d-xna.html
blogger_internal:
    - /feeds/32841709/posts/default/4252386929704098458
dsq_thread_id:
    - '5941359991'
---
I’ve spent some time over the Summer and Autumn of 2011 rewriting the [Gleed 2D tool](https://github.com/SteveDunn/Gleed2D/wiki). This is a tool for editing levels for 2D games and is a very popular tool in the XNA community for games running on XBox and Windows Phone.

Most of the changes in the new version are under-the-hood. The biggest change has been to make it have a plug-in architecture. There has also been a few UI changes though; here’s some screen-shots.

##### The original tool before being re-written:

[![gleed-original](/static/images/imported_from_wp/2012/01/gleed-original_thumb.jpg "gleed-original")](/static/images/imported_from_wp/2012/01/gleed-original_thumb.jpg)

##### and here’s the new version:

##### [![new-annotated](/static/images/imported_from_wp/2012/01/new-annotated_thumb.png "new-annotated")](/static/images/imported_from_wp/2012/01/new-annotated_thumb.png)

The main reason for rewriting the tool was that I wanted to add more features to it but found that it wasn’t easy. It wasn’t easy because it was originally written to just handle the basics needed for creating and editing levels.

The features that I wanted to add were for the next version of [my game](http://marketplace.xbox.com/en-US/Product/Crazy-Balloon-Lite/66acd000-77fe-1000-9115-d80258550914) ([video here](http://www.youtube.com/watch?v=-H3099NgokM)). I wanted to include lighting and shadows and I wanted to design these on the canvas.

Instead of shoe-horning my changes into the original Gleed 2D source, I decided it’d be best to rewrite it and change it to a plug-in based tool.

So, now everything is a plug-in. The basic shapes (rectangle, circle, path) and textures are now plug-ins. Lighting (lights and shadows) is now a plug-in. There’s also a plug-in for simple ‘behaviour’.

Here’s a quick video showing how to use the basic shapes and textures:

<div style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; float: none; padding-top: 0px"><div><object height="252" width="448"><param name="movie" value="http://www.youtube.com/v/9UitcINDDjc?hl=en&hd=1"></param><embed height="252" src="http://www.youtube.com/v/9UitcINDDjc?hl=en&hd=1" type="application/x-shockwave-flash" width="448"></embed></object></div><div style="width:448px;clear:both;font-size:.8em">Basic shapes and textures</div></div>Here’s a short video showing lighting:

<div style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; float: none; padding-top: 0px"><div><object height="252" width="448"><param name="movie" value="http://www.youtube.com/v/2a4shMgRQrk?hl=en&hd=1"></param><embed height="252" src="http://www.youtube.com/v/2a4shMgRQrk?hl=en&hd=1" type="application/x-shockwave-flash" width="448"></embed></object></div><div style="width:448px;clear:both;font-size:.8em">Lights and shadows</div></div>and lastly, here’s a short video showing simple behaviours:

<div style="padding-bottom: 0px; margin: 0px; padding-left: 0px; padding-right: 0px; display: inline; float: none; padding-top: 0px"><div><object height="252" width="448"><param name="movie" value="http://www.youtube.com/v/rFReB6OzYT0?hl=en&hd=1"></param><embed height="252" src="http://www.youtube.com/v/rFReB6OzYT0?hl=en&hd=1" type="application/x-shockwave-flash" width="448"></embed></object></div><div style="width:448px;clear:both;font-size:.8em">Simple behaviours</div></div>The tool is still currently a bit rough. There’s various [bugs](https://github.com/SteveDunn/Gleed2D/issues) that need to be fixed, but none of them stop the tool from doing what it was designed to do. The project is now quick big, so I’m hoping that the community will jump in and add/fix stuff. I’d like to see plug-ins for physics and particle systems.

Feel free to download the source and play around.