---
title: "Nautilus locking CPU at 100% on Gutsy"
date: 2007-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2007-10-30
I see several old posts about this in 32-bit forums, but now it is biting me on Gutsy amd64. I have a brand new Thinkpad T61 with core duo CPU and a fresh install of Gutsy amd64. When Nautilus does this it does it to only one CPU, so I can still function. And I can go into System > Administration > System Monitor and kill Nautilus, which doesn't seem to be a problem as apparently Nautilus regenerates itself. It's just that this should not be happening. Plus it's a PITA to have to kill Nautilus every now and then. It happens about twice a day if I'm using the computer continuously. I've been using Ubuntu amd64 on my old computer since Hoary, and I've never run into this before.

Has anyone else encountered this?

---

### Post by indosupremacy on 2007-10-31
try to see,what application is using your biggest resource ...
try using this command

$ top

after that u may to change the conf. file from that application
usually your problem happen with trackerd software.

---

### Post by Bokonon on 2007-10-31
What are your fonts set at in your desktop and firefox?  I found a few threads about setting your font size too small (desktop) was causing this.

I fiddled with my fonts, noticed this, changed them to 10/12 and it seems to have gone away.

Please search around for this on the other forums and check what the current solution is.

---

### Post by John Jason Jordan on 2007-11-02
I think I have solved the problem. A local Ubuntu user suggested that I check the preferences for Nautilus. It seems the default setup has Nautilus look for icons for all kinds of files that it does not need to do so for, and to try to load video and audio files. I turned off all that stuff and so far it appears back to normal. The reason I never noticed this before is because this is a brand new fresh install of Gutsy on a brand new computer. I probably turned off all that stuff when I started with Hoary two and a half years ago and it stayed turned off during all the subsequent upgrades. I just didn't remember having turned that stuff off.

---

### Post by LorisMaria on 2007-11-19
Hey, I'm having this issue as well and I believe it might be the reason, as this only occurs when I'm trying to access a folder which has newly added files. Could you please tell me where I can find Nautilus preferences? I am such a newbie... Killing Nautilus does work, but it's only temporary. This is happening to me in 32bits, in 64 it never did!

---

### Post by John Jason Jordan on 2007-11-19
> **LorisMaria said:**
> Hey, I'm having this issue as well and I believe it might be the reason, as this only occurs when I'm trying to access a folder which has newly added files. Could you please tell me where I can find Nautilus preferences? I am such a newbie... Killing Nautilus does work, but it's only temporary. This is happening to me in 32bits, in 64 it never did!
Actually, it's still happening to me, although less often since I turned off some of the automatic stuff. Just today I had to kill Nautilus as it was taking 100% of the CPU. 

To turn stuff off open any browser window (e.g., Places > Home), then go to Edit > Preferences. Most of the things you need to turn off are in the Preview tab, but look through the other tabs to see if there are other things you can turn off as well.

---

### Post by mate84 on 2007-11-28
Hello!
It was my problem too (nautilus 100% CPU)! I searched on the internet and I could not find any good ideal, until when I uninstalled/replaced nautilus (all files!!!) with_ thunar_ file manager from synaptic + other thunar files from synaptic. 
I did this because I only found this: [http://linuxondesktop.blogspot.com/2007/03/thunar-versatile-and-impressive.html](http://linuxondesktop.blogspot.com/2007/03/thunar-versatile-and-impressive.html)
[http://www.xfce.org/](http://www.xfce.org/)
After the second reboot I still have 2-7% CPU! 
At the moment it's working for me!
But I'm not sure what else might be missing after this action. I think I forget something, but it's working good!

---

### Post by mate84 on 2007-11-29
OK. It's still working fine, but how can I add file system and volume files to places (in to panel->places)?

---

### Post by John Jason Jordan on 2007-11-29
> **mate84 said:**
> OK. It's still working fine, but how can I add file system and volume files to places (in to panel->places)?
Navigate there manually, then Add Bookmark. The folder you are in will be added to your bookmarks.

---

### Post by logos34 on 2007-11-30
I've had these lockups occasionally too...not always in nautilus though...one slip of the keystroke in 'run application' can send the cpu to 100% and freeze the desktop such that the only way out is ctrl+alt+backspace...thought maybe it was related to my 'noatime' setting in fstab, but I don't think that has anything to do with it...it might actually be somthing to do with hdparm settings (drive spinning up after a period of inactivity). not sure. hmm

---

