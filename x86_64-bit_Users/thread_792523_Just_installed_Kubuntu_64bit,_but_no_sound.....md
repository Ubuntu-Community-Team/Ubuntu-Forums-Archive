---
title: "Just installed Kubuntu 64bit, but no sound...."
date: 2008-05-13
forum: x86 64-bit Users
---

### Post by DJSchmidty on 2008-05-13
Not sure what I should do, when I ran the 32 bit live cd it worked fine, but 64 has no sound


(BTW, FAST!!!!!!!!!!!!!!!)

---

### Post by zenwalker on 2008-05-13
Probably is u r machine a 64 bit? And i assume that u r chip wont support 64 but enabled drivers. Just a wild guess..

---

### Post by DrowningNixis on 2008-05-13
I had this problem as well.  This is what I did to fix it. (As a note, I'm running Kubuntu so I don't know how to get to this in Ubuntu.)  As a note if you have a HDA intel ALC880 you will need to delete the file /var/lib/alsa/asound.state

Under my system settings for my sound options under hardware I enabled Full duplex, enabled cutoms sampling rate of 44100 Hz.

Then in a console I did the following:

sudo alsamixer

I adjusted the master volume to 70-85%.  And I also made sure other custom settings were turned on and up.  

Press escape to return to the console.

sudo alsactl store

Reboot the system.  I hope this helps!

---

### Post by DJSchmidty on 2008-05-13
Uh, don't know what that did, but now I have no sound and no icon of a speaker on the bottom right....

Also it wouldn't let me delete the "var/lib/alsa/asound.state" it said access denied..........

I think I may just go with 32 bit, but I was REALLY hoping that 64 bit would work...:(

---

### Post by DrowningNixis on 2008-05-13
Do you have a HDA intel ALC880?

You can add the speaker icon by right clicking on the bar, Add application to the panel ---> Multimedia --->  Kmix.

---

### Post by cacycleworks on 2008-05-14
If it's of any help, on my laptop, Ubuntu 64 bit installed perfectly. As usual, I'm having to sort out kubuntu...

I've never had sound in kubuntu, but with 8.04 / Hardy, I didn't have wireless either (when installing from the kubuntu iso). So now I have ubuntu installed and am going to try to install kubuntu desktop.

I've been on the verge of going back to 32 bit due to all the problems I've been having getting a KDE desktop in 64bit... ArchLinux didn't work, I left OpenSUSE because the package search takes about 2.5 lifetimes to just open up, and neither the KDE4 nor KDE3 (normal) kubuntu ISOs will work as installed. 

I'm trying to learn as much as possible and have been looking in Dell forum, 64 bit forum, KDE forums, kubuntu forums ... I must have kde. :-)

---

### Post by cacycleworks on 2008-05-14
I stumbled across this thread on sound, too:
[http://ubuntuforums.org/showthread.php?t=628247](http://ubuntuforums.org/showthread.php?t=628247)

---

