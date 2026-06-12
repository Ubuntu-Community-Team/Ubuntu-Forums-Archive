---
title: "Codecs on amd 64 architecture"
date: 2006-09-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by The Tronyx on 2006-09-27
I'm very new to linux and no matter how many threads I search or things I google I cannot find a simple answer, or even a simple place to start.  My question is how can I install codecs that will actually play videos on an AMD 64, I tried installing a few things and even after restarting, I try to play a movie or a .mpg file and my screen clicks and kicks me back to the log in.  

Sorry if I sound irritated, I'm trying to learn a lot at once and the amount of time it takes to accomplish certain things compared to my previous operating systems is a bit daunting.  Thanks for your help.

---

### Post by mrehorst on 2006-09-27
Go to the wiki page (that tab at the upper right corner of your screen) and serach for codecs.  There is a detailed explanation of where to get them and what packages you need to DL and install.

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

I followed these instructions and it worked fine for me.  I can now play most videos I have run into, and all audio formats I have tried to play.

The wiki is pretty useful- bookmark it- you'll be using it a lot.

---

### Post by DRF on 2006-09-28
Sounds like a bug should be filed if not already if your forceably logged out when trying to play a video. (with or without codecs that shouldn't happen)

If your still having problems with being logged out by your media player (not something I've had happen to me) you might want to try using an alternative media player. The most popular alternatives being xine, mplayer and vlc. All of which I think should be installable using the Add/Remove applications or synaptic.

But for your codecs follow the link from the previous poster. (Note that the w32codecs package that supports various windows media player codecs isn't installable though the package manager on the AMD64 version of ubuntu)

Daniel

---

### Post by kopilo on 2006-09-28
I had the same issue until I installed the xine libary to replace the one that totem (Movie Player) was using.

I think I did it by going to System -> Administration -> Synaptic Package Manager, pressing ctrl + f to bring up 'find'. Then typing in totem-xine, marked it for installation and then hit apply.

Can not garantee that will work or solve the issue though.

---

### Post by GrooveHobbit on 2006-09-28
I am currently having the same problem.  My Video Card is a Radeon X1600 and running the most recent drivers on Dapper 6.06.  I have uninstalled and reinstalled several combinations of players and Codecs but all have the same result right now.  Any time a video is launched (other than flash embedded) the GUI resets completely.  I've got everything else working in AMD64 since install yesterday.  Any help would be great, this distro is a couple days away from making me leave MS completely.

---

### Post by RAOF on 2006-09-29
> **GrooveHobbit said:**
> I am currently having the same problem.  My Video Card is a Radeon X1600 and running the most recent drivers on Dapper 6.06.  I have uninstalled and reinstalled several combinations of players and Codecs but all have the same result right now.  Any time a video is launched (other than flash embedded) the GUI resets completely.  I've got everything else working in AMD64 since install yesterday.  Any help would be great, this distro is a couple days away from making me leave MS completely.

That is almost certainly a graphics-card-driver problem.  It sounds like whenever XV (the **X**org **V**ideo acceleration extension) is being used, it crashes X (the GUI).  You might want to try looking at the video-output options of whatever you're using (under mplayer it's preferences->something, under totem-xine it's in the file ~/.gnome2/totem_config under video.driver, for gstreamer run gstreamer-properties).  Try any of the other options; xshm (X Shared Memory), opengl, etc.

If that fixes it, blame the graphics drivers, and pester ATI for better ones.

---

