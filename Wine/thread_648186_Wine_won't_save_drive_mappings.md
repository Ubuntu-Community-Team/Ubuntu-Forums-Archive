---
title: "Wine won't save drive mappings"
date: 2007-12-23
forum: Wine
---

### Post by artrimbaud on 2007-12-23
Hi,

I'm using wine-0.9.51 and trying to run MagicISO.  I go into winecfg and autodetect the drives, I click apply, then close winecfg.  If I reopen just to check my settings, my 2 cd drives are missing.  I've searched Google for a solution, but can't find one.

The problem is that when I go into MagicISO, I can't burn an image because no cd drives are recognized.

Ubuntu recognizes both drives just fine.  And so does wine's autodetect feature.  It just won't save when I click apply.

I have wine setup to emulate WindowsXP.

I would appreciate any help.  Thanks.

-b.

---

### Post by cogadh on 2007-12-23
Did you ever use sudo or a root account to run Wine at one time? If so, then your permissions are screwed up and it can't save any settings changes because you do not have permission. The only way to really fix it is to delete your .wine directory and create a new one (and never use sudo or root to run Wine again).

---

### Post by mc4man on 2007-12-23
I think there may be an issue with that app. (MagicISO) detecting drives, not wine. 
_Sometimes _having media with data on it in the drive before opening app works, then eject and insert blank disc

---

### Post by cogadh on 2007-12-23
I would think it was a problem with MagicISO and not Wine if you hadn't said that winecfg isn't retaining your drive settings. That indicates to me that the problem starts with Wine and not MagicISO.

However, after checking Wine's AppDB, it appears that drive detection is a known problem with MagicISO:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=3496](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3496)

Is there a particular reason you needed MagicISO? There are plenty of native applications that can do everything MagicISO can do without all the hassle of Wine.

---

### Post by artrimbaud on 2007-12-23
> **cogadh said:**
> Is there a particular reason you needed MagicISO? There are plenty of native applications that can do everything MagicISO can do without all the hassle of Wine.

I need to open a UIF image, and as far as I know, MagicISO is the only one that will do that.

I've tried to burn the image to a dvd, but as it's 4.3 GB, I can't get any burning program to burn it.  I've also tried compressing the file, but I can't seem to get a good gui version of something like RAR or 7zip.  I'm not too familiar with the command line versions as I'm pretty new to Linux/Ubuntu.

I'm going to try to just move the image to a Windows partition, then reboot into Windows and try it there.  Thank you for all of your quick responses.  I'll let you know if this works.

-b.

Edited to add: Not sure why I didn't think of that solution in the first place.  It will most likely work.  Thanks though.

---

### Post by righthere201 on 2007-12-25
Does anyone know how I can view the Wine, Windows XP C: drive on my desktop?

---

### Post by cogadh on 2007-12-25
Dude, don't hijack threads, its rude. Your question has nothing to do with the OP. If there isn't a thread already related to your problem (use the forum search to find one), then just create a new thread instead of trying to take over one like this.

---

### Post by melodyoutside on 2007-12-27
I am completely new to Ubuntu, Linux, etc...but I am having the same issue with Wine, except I'm not using the same application that the other person is using. I am using Exact Audio Copy with Wine. Every time I use the autodetect feature in the Wine setup, it shows my cdrom drive, and then when I re-open it, it is not saved as such....so I think it might be a Wine issue?? Or maybe both of our applications that we're using with Wine are just bunk...but that is unlikely.Also, if I manually add the drive instead of using the autodetect feature, it still does not save the drive mapping.  Any ideas?

---

### Post by markharding557 on 2007-12-27
> **artrimbaud said:**
> Hi,

I'm using wine-0.9.51 and trying to run MagicISO.  I go into winecfg and autodetect the drives, I click apply, then close winecfg.  If I reopen just to check my settings, my 2 cd drives are missing.  I've searched Google for a solution, but can't find one.

The problem is that when I go into MagicISO, I can't burn an image because no cd drives are recognized.

Ubuntu recognizes both drives just fine.  And so does wine's autodetect feature.  It just won't save when I click apply.

I have wine setup to emulate WindowsXP.

I would appreciate any help.  Thanks.

-b.
iso master found in the repositorys should do the same job

---

### Post by cogadh on 2007-12-27
> **melodyoutside said:**
> I am completely new to Ubuntu, Linux, etc...but I am having the same issue with Wine, except I'm not using the same application that the other person is using. I am using Exact Audio Copy with Wine. Every time I use the autodetect feature in the Wine setup, it shows my cdrom drive, and then when I re-open it, it is not saved as such....so I think it might be a Wine issue?? Or maybe both of our applications that we're using with Wine are just bunk...but that is unlikely.Also, if I manually add the drive instead of using the autodetect feature, it still does not save the drive mapping.  Any ideas?
Have you ever used sudo to run Wine? If so, that is likely the problem. Using sudo to run anything with Wine breaks the permissions on your .wine directory, which will prevent you from making and saving any changes in winecfg.

---

### Post by melodyoutside on 2007-12-27
I don't know if I've used sudo....my fiance has set this up for me! (I'm trying to learn it myself, no worries). I'll ask him. thanks for the suggestion.

---

### Post by melodyoutside on 2007-12-31
Nope, sudo is not being used with wine. We made sure to uninstall everything (I think he did a command that cleared up anything with sudo?), and then he reinstalled wine....and the same issue is happening. Is there another program that you can recommend that I use instead of Exact Audio Copy through wine that will allow me to rip my CD's at cd quality (so that they can be played through my mp3 player over a nice sound system)....Unless there are other suggestions that you may have as to how to work out this wine issue. Thanks!

---

### Post by rozifus on 2010-07-22
I know this is an old thread, but I was having a similar problem and managed to fix it just now by completely removing and then re-adding the drive in wine config. 

Hopefully this helps somebody.

---

