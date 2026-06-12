---
title: "Ubuntu Live Question"
date: 2006-03-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by FoggyMtn on 2006-03-25
Hey Ya'll

I am completely new to this.  I wanted to try and run Ubuntu-Live on my eMac 1.25 GHz PowerPC G4.  It is currently running 10.4.5.

I downloaded ubuntu-5.10-live-powerpc.iso and burnt it to a cd (actuallly, a cdr).  I rebooted from the cd.  It goes thru all of the local options asking about keyboard and country and such.  Then I get the orange-ish lettered ubuntu screen.  It continues loading (they all say 'ok').  When that is finished, the screen goes back to black.  The cd stops spinning, everything seems dead in the water.  

I tried re booting, this time I selected the help menu. Then tab.  Then selected the live-powerpc setting.  Same thing.  I then followed the instructions saying type something else if it sticks on a white page.  When that loaded, it still got to the colorful ubuntu logo (defferent, but still colored), loaded with "ok's" and then froze.  

Can any one help?

thanks a bunch

rob

---

### Post by ssam on 2006-03-25
there is a bug in the autodetection of the monitor on the emacs. the work around is discussed [http://ubuntuforums.org/showthread.php?t=95545](http://ubuntuforums.org/showthread.php?t=95545)

unfortunatly the live cd does not save any information between restarts so you would have to do this everytime you used the live cd. if you installed ubuntu you would only need to do it once.

has anyone tested if this is fixed in dapper?

the bug report is at [https://launchpad.net/distros/ubuntu/+source/xorg/+bug/26898/](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/26898/)

---

### Post by FoggyMtn on 2006-03-25
Thanks!  I'll give that shot first chance I get.  If all goes well, I may consider a dual boot setup.  But at least this should get me going where I can experiment a little

Thanks for the quick reply

rob

---

### Post by FoggyMtn on 2006-03-25
Hey ssam

I read both posts you referenced (as well as any others that showed up searching fro "emac" and "blank screen").  I went thru the steps again.  Once I got past the black screen with brown "ubuntu", the screen went black.  There was one brief glimpse of an underscore (maybe a dash, hard to tell with no other reference point) in the top left, and then all black. The ctrl-opt-F1 did nothing.  There was no change.  It's basically like the monitor turns off.

I saw in one post where they suggested another monitor to check operation, but that's not an option for me.  Is dapper a newer version?

Any idea where I'm going wrong?  Maybe this is a sign that I don't need to enter the world of linux!  :)

Thanks for the help.

rob

---

### Post by 3rdalbum on 2006-03-26
Dapper is a newer version of Ubuntu, but it's still in development stage.

When you get into the Yaboot menu on the CD, press Tab. One of the options Yaboot should list is something like "live-expert". Type that option and press Return.

When you get to the part where the installer asks if you want to do video card autodetection, say NO. The video driver you should choose is "ati", and the default settings for this should work.

When the installer asks for monitor autodetection, say NO. When it asks how you want to specify your monitor settings, choose Advanced. Then you'll be able to type in the information you got from those two above posts. Hopefully then everything should work out fine.

---

### Post by FoggyMtn on 2006-03-26
3rdalbum

Well, I'm a little slow, so I had to go thru the process twice (the first time I screwed something up and had no GUI).  But, the second go-round got it done!  Everything went fine!

Thanks so much for the help

(ps, this was sent from ubuntu firefox :)  )

rob

---

