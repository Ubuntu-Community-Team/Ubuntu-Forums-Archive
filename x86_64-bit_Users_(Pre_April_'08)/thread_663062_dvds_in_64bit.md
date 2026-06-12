---
title: "dvds in 64bit"
date: 2008-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by MikeSz on 2008-01-09
I know this has probably been asked 10,000 times but of all the threads ive read I just end up getting lost.  Is there an easy way to get DVDs to play in the 64bit version of Gutsy or am I better of just going back to the 32 bit version?  I know there are flash issues as well in 64 bit (which I also cant get working despite following some of the walkthroughs!) Can anyone help before I start from scratch with the 32bit version?

p.s., ive installed VLC and movie player already - plus the codecs that Ive seen available in add/remove programs (gstreamer etc)

---

### Post by John.Michael.Kane on 2008-01-09
> **MikeSz said:**
> I know this has probably been asked 10,000 times but of all the threads ive read I just end up getting lost.  Is there an easy way to get DVDs to play in the 64bit version of Gutsy or am I better of just going back to the 32 bit version?  I know there are flash issues as well in 64 bit (which I also cant get working despite following some of the walkthroughs!) Can anyone help before I start from scratch with the 32bit version?

p.s., ive installed VLC and movie player already - plus the codecs that Ive seen available in add/remove programs (gstreamer etc)

The steps I used, and tested are listed here [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

if you are using a version other than gutsy look here [https://help.ubuntu.com/community/Medibuntu#head-57a5050d451985de1b87ea87a3ccc1a4895e57d3](https://help.ubuntu.com/community/Medibuntu#head-57a5050d451985de1b87ea87a3ccc1a4895e57d3)

---

### Post by ~LoKe on 2008-01-09
**Flash**
```
cd ~/ && wget http://home.comcast.net/~ubuntume/nspluginwrapper-install-0-1.8.5-3.tar.gz && tar xzvf nsplugin*.tar.gz && cd nsplugin*install && sudo ./GetFlash
```
**Codecs**
Add the Medibuntu repositories to */etc/apt/sources.list*
> ## Medibuntu - Ubuntu 7.10 "hardy gibbon"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

```
sudo apt-get update; sudo apt-get upgrade
```
```
sudo apt-get install w64codecs libdvdcss2
```

---

### Post by crjackson on 2008-01-09
Make sure you have all your repositories enabled and then ccpy this code and past it into a terminal session:

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install libdvdcss2 w64codecs gxine libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem totem-xine xine-ui
```

All should go without a hitch...

---

### Post by MikeSz on 2008-01-09
Many thanks for that - there are a number of threads that I have tried to follow (so much so that ive probably messed my machine up a bit now) Alas, on going through this walkthrough again, which I did earlier, the terminal just seems to 'stick'

zer0cool@zer0cool-laptop:~$ gksudo aptitude install w64codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  nspluginwrapper 
The following NEW packages will be installed:
  w64codecs 
0 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 226kB of archives. After unpacking 279kB will be used.
Do you want to continue? [Y/n/?] y

The above is what I get, on pressing 'y' and enter, it just sits there flashing a cursor which is the same problem I got last time :(
Is it going to be easier to revert to 32bit?  Im more than happy to learn, unfortunately I have a lot of DVDs to watch for my Open University and the laptop is the only way of watching them!

---

### Post by MikeSz on 2008-01-09
wow - thanks for all the replies, there was only 1 when I last posted, will try advice and catch up in 10 mins!!!  Many thanks!!!

---

### Post by John.Michael.Kane on 2008-01-09
Pass the command without gk, and then press y, and all should install fine.

```
sudo aptitude install w64codecs
```

---

### Post by ~LoKe on 2008-01-09
gksu and gksudo are for graphical applications only.

---

### Post by MikeSz on 2008-01-09
Well what can I say - you guys have done it again!  My DVDs now work fine and I can also watch video clips on the skynews website!!!  Many thanks indeed.  

The only hard thing about this is I actually have no idea what I have done to get that to work - how did you guys learn all this?  Are there Linux schools or classes?  I used to be able to pick this up with no bother at all back when I cut my teeth on 286s and 386s but not, I havent got the first clue!

---

