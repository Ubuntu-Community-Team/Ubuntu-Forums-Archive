---
title: "Flash 9 + X-FI no sound. Hardy Heron"
date: 2008-04-28
forum: x86 64-bit Users
---

### Post by cody001 on 2008-04-28
Linux newb here.

System Specs.

CORE 2 DUO E6600
4GB DDR2
8800 GTS 512MB
X-FI Extreme Music
Dual Boot Vista x64/ Hardy Heron AMDx64

-----------

I downloaed XFiDrv_Linux_US-1.18.tar.gz off of creatives website but could not get it to work properly.

make: *** [all] Error 2
make: *** [install] Error 2
Installation Unsuccessful

Searching the forums, there seems to be problem and currently solution is to use OSS.  Now movies/mp3's etc have sound.

Installed Flash by using Firefox's own plugin finder.

Flash files now play fine but no sound.  Anyone give me some pointers on what to do next thnx.

---

### Post by Kilz on 2008-04-28
> **cody001 said:**
> Linux newb here.

System Specs.

CORE 2 DUO E6600
4GB DDR2
8800 GTS 512MB
X-FI Extreme Music
Dual Boot Vista x64/ Hardy Heron AMDx64

-----------

I downloaed XFiDrv_Linux_US-1.18.tar.gz off of creatives website but could not get it to work properly.

make: *** [all] Error 2
make: *** [install] Error 2
Installation Unsuccessful

Searching the forums, there seems to be problem and currently solution is to use OSS.  Now movies/mp3's etc have sound.

Installed Flash by using Firefox's own plugin finder.

Flash files now play fine but no sound.  Anyone give me some pointers on what to do next thnx.

[You might want to look at this thread.]("http://ubuntuforums.org/showthread.php?t=655825")

---

### Post by jocko on 2008-04-28
Flash is by default only capable of output to ALSA, so if you use OSS you will need to get [adobe's flashsupport]("http://labs.adobe.com/wiki/index.php/Flash_Player:Additional_Interface_Support_for_Linux") (not the one provided in the repos, that's a crippled version that only supports pulseaudio, not OSS. If pulseaudio works fine for you, perhaps the repo version will do anyway...).
Adobe's instructions are not very good, but [here]("http://ubuntuforums.org/showpost.php?p=1716845&postcount=61") are some better instructions (but some of the required packages have changed their names slightly. search in synaptic for the package names, but without any numbers).

---

### Post by Shakaboom on 2008-07-16
On the 32 bit version I was finally able to do it. On the 64 bit version I couldn't install the Adobe version, as opposed to the one in the ubuntu repositories. With the one from the repositories I was't able to succeed.

Now though, there are a few flash sites/films that make firefox crash, example:

[http://www.thedailyshow.com/full-episodes/index.jhtml?episodeId=176626](http://www.thedailyshow.com/full-episodes/index.jhtml?episodeId=176626)

Also, I've noticed the sound and video are no longer in sync. Could someone give advice on this or how to make a bugreport/something else so that the people in charge know what to fix?

---

### Post by wilowilo on 2008-08-26
Go to

[http://www.uburocks.com/2008/08/18/flash-is-fixed-in-ubuntu/](http://www.uburocks.com/2008/08/18/flash-is-fixed-in-ubuntu/)

and follow explanation. Worked perfectly for me!

Good luck

---

### Post by Yellow Pasque on 2008-08-26
cody, did you see the the section in the OSS4 guide on Flash? [http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2)

Just download this file to your Desktop: [http://ubuntuforums.org/attachment.php?attachmentid=69426&d=1210377383](http://ubuntuforums.org/attachment.php?attachmentid=69426&d=1210377383)
Then: 
```
cd ~/Desktop
gunzip libflashsupport.so.gz
sudo mv libflashsupport.so /usr/lib
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox/plugins
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/mozilla/plugins
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox-addons/plugins
sudo cp /usr/lib/libflashsupport.so /usr/lib32/
```
It may not work until after a reboot.

---

