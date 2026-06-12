---
title: "Virtualbox AMD64 is HERE!"
date: 2007-06-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by lazyart on 2007-06-07
[Version 1.4.0 supporting AMD64 hosts is available!]("http://virtualbox.org/wiki/Downloads")

I'm happy today. \\:D/

---

### Post by jamesford on 2007-06-07
that is such great news!
anyone tried it yet? whats it like?
how does it compare to vmware player?

---

### Post by capecove on 2007-06-07
Well, you have intrigued me. I am going to install it and give it a whirl. :)

Thanks for the heads up on that. I'll let you all know if I was too stupid to get it working correctly. ;)

---

### Post by Didjit on 2007-06-07
Never tried it. Faster and as stable as Vmware?

Didjit

---

### Post by capecove on 2007-06-07
Welp, it installed fine. Now I just have to make it work its magic! I don't have time this morning, maybe when I get home. Windows XP SP2 will be the test. Thanks again for letting us know...

---

### Post by joe0joe on 2007-06-07
Thank you guys! Please keep updating us.

Joe

---

### Post by shad0w_walker on 2007-06-07
Working just fine here (Ubuntu 7.04) installed it, made sure i was in the vboxusers group and it was running. No stability issues so far (Only been running a short while but iv not found any issues in the earlier versions) and in comparison to most of the other virtualisation tools iv used its beautifully fast (Cant say in comparison to VMware server, never tried it)

---

### Post by jamesford on 2007-06-07
hmm, i tried installing gutsy tribe1 64 bit in virtualbox but it says my cpu doesent support it or something. can it only use 32 bit guest os'es?

---

### Post by lazyart on 2007-06-07
I had a bit of an issue on installation but I used both it and VMware Server when I was in 32bit land and they both ran great.

Configuring a bridged network, however is a royal PITA compared to VM.

---

### Post by jamesford on 2007-06-07
xp isntalled in vbox then, all worked fine, no tweaking needed. i must say virtualbox seems a way faster than vmware player
no luck installing gutsy tribe1 64 tho as mentioned above

my only problem is i cant figure how to change the screen resolution of my virtual xp. its stuck at 1024x768, and ive got a 1680x1050 monitor. id like to make the virtual machine 1440x900 or something

---

### Post by lazyart on 2007-06-07
Probably need to install the Linux guest additions (or Windows guest additions if you're running MS inside).

Devices>Install Guest Additions

---

### Post by jamesford on 2007-06-07
ah thanks, i wondered where the guest additions were. for some reason i wasnt able to spot it.still unable to make it widescreen tho

---

### Post by JAPrufrock on 2007-06-07
Easy install. Very nice. Now I can get rid of my dual boot. I noticed that increasing the resolution seems to be the only way to increase screen image size.  Means I have to go into xorg.config and add a higher resolution.

---

### Post by kalpik on 2007-06-07
Any good guide for setting up a bridge netwok?

---

### Post by tgm4883 on 2007-06-08
[http://www.virtualbox.org/wiki/VBox_vs_Others](http://www.virtualbox.org/wiki/VBox_vs_Others)

64 bit guest OS support is planned

---

### Post by cookieofdoom on 2007-06-08
Hah, I just compiled the OSS version 3 days ago to get it to work. It actually did work. When I went to install Fedora on it the bootloader thing crashed. I'll have to try this. Thanks for the link, by the way.

---

### Post by Didjit on 2007-06-08
Got XP loaded and running. So far, I'm impressed over the speed vs. VMware Workstation. It seems much faster. 

Didjit

---

### Post by tgm4883 on 2007-06-08
> **Didjit said:**
> Got XP loaded and running. So far, I'm impressed over the speed vs. VMware Workstation. It seems much faster. 

Didjit

Doing all my Win 2000 updates.  Now only if I could run mythbuntu 64 on it :(

---

### Post by capecove on 2007-06-08
Morning all...

Yup, working fine here with Windows XP Home. Had a little trouble at first with installing things from CD but worked those out by simply starting Ubuntu and then Virtualbox. 

This is some seemingly great stuff! Audio works like a champ (ALSA)....

It even plays DVDs, time for the old :popcorn:

---

### Post by dreadlord_chris on 2007-06-12
I recently spent 4 days banging at vmware-server. It installed and setup pretty easily. The XP install went without a hitch, took about 47 minutes. Both host & guest connections worked fine - they could both ping each other & surf the Intertubes. For the life of me though I could not get shares set up. I know I had Samba set up correctly, share worked fine with another (real) XP box in the same workgroup.

After much frustration I decided to give VirtualBox a go. Boy have I been surprised! First shock - XP installed in 21 minutes! This was actually 7 minutes faster then the last time I did a full, real XP install on this box. Next to set up shares - no Samba necessary. Just install the guest additions, create the shares, and mount the folders.

I am very impressed.

---

### Post by Spccowboy on 2007-06-22
Anybody got this working of an actual partition rather than a virtual drive?

---

### Post by Twintop on 2007-06-22
Any experienced virtual machine gurus, I have a question for you...would you recommend VirtualBox, VMWare, KVM, or...? I've got Hardware-level visualization, and have been having pains with KVM (and have done a little VMWare), but am looking at all the possibilities.

---

