---
title: "Can't watch youtube and some other streaming video"
date: 2008-07-12
forum: x86 64-bit Users
---

### Post by drunkmatador on 2008-07-12
I've never been able to get youtube videos to work well on my x64 installation of Hardy. I installed flash using the instructions that used to be stickied in this forum, and for awhile they would work but would be choppy, especially while fullscreen. My computer specs aren't great but are most certainly good enough to view you tube videos clearly. Compiz was turned off too, btw.

Now some videos work but some don't. The video will load and play for about one second and then the progress bar continues but no video. It's really frustrating.

Has anybody else encountered this problem?

---

### Post by philinux on 2008-07-12
You'll find something useful here.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by nikgare on 2008-07-12
Full screen playback of flash is choppy, this is a know problem.
Why don't you try the easy way and just install flash via synaptic?

---

### Post by drunkmatador on 2008-07-12
Flash will install fine on an x64 through Synaptec? Should I un-install the one I have currently somehow, other than in Synaptec itself maybe?

---

### Post by nikgare on 2008-07-12
Make sure you remove the Flash you installed, and all of its config files.

You nees to make sure that the Multiverse repo is on, and then install Flashplugin-nonfree

---

### Post by drunkmatador on 2008-07-12
First, thanks so much for helping me. But I was wondering if I remove in Synaptec, will it get rid of the config files as well? And if not, how do I do this? 

Sorry I am and off-and-on newb.. every time I start to really understand things I take a few months away from computers, then I come back and it's all new again.

---

### Post by nikgare on 2008-07-12
How did you install Flash in the first place? Was it via synaptic?
I notice that there is v10 of flash in the backports repo, this would pobably help.

---

### Post by Lycus on 2008-07-12
> **nikgare said:**
> How did you install Flash in the first place? Was it via synaptic?
I notice that there is v10 of flash in the backports repo, this would pobably help.

You can install flashplugin-nonfree via synaptic. I don't have backports installed (so I haven't messed with flash v. 10), but the fashplugin-nonfree worked out-of-the-box for me after installation in Ubuntu 8.04.1 on amd64. Youtube etc. play, video, streaming, all that, perfectly fine.

---

### Post by bford16 on 2008-07-12
OK. Here's my prescription for getting multimedia to work in Ubuntu Hardy.

1. Replace totem-gstreamer with totem-xine.  The xine version of Totem plays most media well, and allows use of DVD menu navigation.```
sudo apt-get remove totem-gstreamer && sudo apt-get install totem-xine
```2. Install the restricted-extras package.```
sudo apt-get install ubuntu-restricted-extras
```(Use kubuntu-restricted-extras for KDE or xubuntu-restricted-extras for Xfce.)

3. Enable the Medibuntu repository.  See <https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories>.  Install media enablers.```
sudo apt-get install libdvdcss2 w64codecs
``` (Use w32codecs if you are running 32-bit Ubuntu.)

4. Install the Adobe flash plugin.```
sudo apt-get istall flashplugin-nonfree
```(You will have to accept the license agreement.)

A word about Java.  If you haven't installed it already, the proprietary Sun Java runtime environment is now available for 64-bit, but there is still no Sun Java Plugin for 64-bit.  However, the icedtea plugin does work for many sites (I have read that it does not always work).```
sudo apt-get install sun-java6-bin sun-java6-jre icedtea-gcjwebplugin
```(You will have to agree to the license agreements to install the Sun Java software.)

In general, I try to use the tools provided by the distribution to achieve my goals (Medibuntu is a necessary exception).  I have found that many things in Linux are often far easier than I think.  Kudos to the individuals who have donated so much of their time and effort to making Ubuntu a superb distribution.

EDIT: For some kinds of media, it may be necessary to install extra plugins.  Since I am not familiar with all of the pugins, I haven't discussed them in this post.

---

### Post by drunkmatador on 2008-07-15
i tried all of those steps, didn't work. i can't listen to music on projectplaylist.com either.. and have tried using both firefox and opera. i'm almost thinking about just re-installing ubuntu but i don't want it to come to that.

---

### Post by steveneddy on 2008-07-17
> **nikgare said:**
> How did you install Flash in the first place? Was it via synaptic?
I notice that there is v10 of flash in the backports repo, this would pobably help.

And I just manually installed Flash 10 manually last week.

Nice to know it's there, though.

---

