---
title: "Sound doesn't work at all."
date: 2007-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Metaleks on 2007-10-20
Just yesterday I installed Gutsy on my Dell laptop (1520), and it's been quite a struggle.  Almost nothing worked out out of the box.  Well, I've managed to get everything working thanks to this very forum, this includes wireless, video card drivers etc.  However, the sound just doesn't seem to work!

When I double click on the volume control I get a message like "No volume control GStreamer plugins and/or devices found".  Now, I have visited every thread on this forum related to this problem.  I have compiled alsa and that good stuff a countless amount of times, however nothing seems to work.

I have an intel core 2 duo, with 2GB of ram if that helps.  My sound card is an Intel HDA ICH8.  If you follow this link: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel) you will see that ICH 8 isn't even on the list!

Any help would be greatly appreciated.

(Also a little side question, since creating a thread for this seems useless.  I have installed wine, but I don't know if there is a 32bit wine and a 64bit wine, and how I know which one I have.  And if there is a 64bit wine, how would I go about getting it?)

---

### Post by Metaleks on 2007-10-21
Bump!

---

### Post by Nero_Flint on 2007-10-21
Sound doesn't work at all or doesn't work with certain applications?

---

### Post by Metaleks on 2007-10-21
At all.  I get this when I double click the sound icon.

[http://xs220.xs.to/xs220/07420/ubuntusoundproblem.jpg](http://xs220.xs.to/xs220/07420/ubuntusoundproblem.jpg)

I can't enter the mixer or anything.  I don't think it knows I have a sound card.

---

### Post by Ghaagsheblah on 2007-10-21
I also had a lot of problems when i first installed 7.10. I managed to solve my problem by adding the following line to /etc/modprobe.d/alsa-base

options snd-hda-intel model=fujitsu 

(since your computer is dell you are most likely to change fujitsu to dell or something like that)

the link below might have some more information:
[http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)

---

### Post by Nero_Flint on 2007-10-21
Read the thread that Ghaagsheblah suggested and if you don't find any answers there I found this for you:

[http://packages.ubuntu.com/feisty/libs/gstreamer0.8-plugins](http://packages.ubuntu.com/feisty/libs/gstreamer0.8-plugins)

There is also someone with the same problem as yours here:

[https://answers.launchpad.net/ubuntu/+question/1834](https://answers.launchpad.net/ubuntu/+question/1834)

---

### Post by Metaleks on 2007-10-21
I thank you all for your help.  I have tried all the solutions from the threads you posted.  I even followed the wiki found [here](https://help.ubuntu.com/community/HdaIntelSoundHowto) that one of those threads linked to.  None of the solutions worked.  Not even adding that extra line to the alsa-base.

The solutions assume that your sound card can be detected I think.  However, take a look at my system.
```
aplay -l
aplay: device_list:205: no soundcards found...

```

Would it matter if my family sound card ( ICH 8 ) isn't even supported?  [http://www.alsa-project.org/main/ind...x:Vendor-Intel](http://www.alsa-project.org/main/ind...x:Vendor-Intel)  Because I think a similar driver should still do the trick.

Again, thanks for your help, but I am still at square one.  I still get the same error:(

---

### Post by Metaleks on 2007-10-22
Many apologies for the double post, my friends.  But the problem has been solved.  It was as simple as 1 line of the terminal combined with a reboot.

Apparently, I had to install the linux-generic-backport package.  More info for the fix is found here:

[http://ubuntuforums.org/showthread.php?t=565873&highlight=ich8&page=2](http://ubuntuforums.org/showthread.php?t=565873&highlight=ich8&page=2)

64 bit users with no sound, take note!

---

