---
title: Visual Studio Build Tip
date: '2006-10-18T08:18:00+00:00'
status: publish

author: stevedunn
excerpt: ''
type: post
id: 92
category:
    - tips
    - 'visual studio'
tag: []
post_format: []
blogger_blog:
    - stevedunns.blogspot.com
blogger_author:
    - 'Steve Dunn'
blogger_permalink:
    - /2006/10/visual-studio-build-tip.html
blogger_internal:
    - /feeds/32841709/posts/default/1348535320739378504
dsq_thread_id:
    - '5941367379'
---
By default, Visual Studio will build all of the projects in your solution regardless of any errors.

The problem with this is that if the first project it builds contains an error, the resulting binary will not get generated. If any other projects depend on this (which is normally the case, as it was the first to be built) then they’ll fail too, and so on to the end of the project heirarchy.

Pointless; you’ll spend ages sitting around in a locked IDE unable to edit the error until the build finishes.

You might as well stop at the first error. You could of press Ctrl+Break (several times) and hope that VS will eventually stop. But, there’s a better way: get Visual Studio to stop automatically after an error.

1. Go to Tools/Macros/Macro Explorer
2. Expand MyMacros
3. Double click Module1
4. This will bring up the macro in a new window. In that window, double click the EnvironmentEvents entry.
5. From the drop-down (currently ‘General’, select ‘Build Events’)
6. Select ‘OnBuildProjConfigDone’ and paste this in:

<span><span><span></span></span></span>

```
If Success = False Then 'The build failed...cancel any further builds.
DTE.ExecuteCommand("Build.Cancel")
End If<div><p>The whole method should look like this:</p>

Private Sub BuildEvents_OnBuildProjConfigDone( _  
ByVal Project As String, _ 
ByVal ProjectConfig As String, _ 
ByVal Platform As String, _ 
ByVal SolutionConfig As String, _ 
ByVal Success As Boolean) Handles BuildEvents.OnBuildProjConfigDone   
    If Success = False Then 'The build failed...cancel any further builds.     
        DTE.ExecuteCommand("Build.Cancel")   
    End If 
End Sub

</div>
<p></p>
```