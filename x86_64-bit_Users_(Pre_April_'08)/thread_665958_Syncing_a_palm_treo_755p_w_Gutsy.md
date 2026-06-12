---
title: "Syncing a palm treo 755p w/ Gutsy??"
date: 2008-01-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by ljoslin on 2008-01-12
Someone please help, before I smash my computers and my Treo into little tiny pieces!   I was running edgy on my laptop and was able to sync my treo using Jpilot, however I have now upgraded (clean install) to Gutsy and have lost this ability.  Before I had to play with timing by hitting sync on the treo, waiting 3-5 seconds then hitting sync in Jpilot.  This no longer seems to work.  Any ideas??

-=Ljoslin=-

---

### Post by Tommy on 2008-01-15
> **ljoslin said:**
> I was running edgy on my laptop and was able to sync my treo using Jpilot, however I have now upgraded (clean install) to Gutsy and have lost this ability.  Before I had to play with timing by hitting sync on the treo, waiting 3-5 seconds then hitting sync in Jpilot.  This no longer seems to work.  Any ideas??

how did you specify the USB port in jpilot? 

was it something like    /dev/ttyUSB2  (not ideal)
or was it simply      usb:     (much faster and more reliable IF the device is recognized)

[i'm considering replacing my ancient palm with a 755p so i'm hoping the data will "just work" as it has in the past.]

[edit: i found this post via a search and just noticed the forum is for amd/64 bit... i use x86 & powerpc so ymmv.]

---

### Post by firecat53 on 2008-01-15
I don't know if this will help or not, but I added a rule to /etc/udev that helped recognize my palm tungsten. Don't know about the Treo, but they're all made by Palm , so it might work!

     sudo gedit /etc/udev/rules.d/10-Palm-Rule

Paste into that new file:
     BUS=="usb",SYSFS{manufacturer}=="Palm,Inc.",NAME="pilot",OWNER="root",KERNEL=="ttyUSB[13579]",GROUP="tty"

Save and either restart udev (sudo /etc/init.d/udev restart) or reboot.

I have jpilot set to look at /dev/pilot, which should be created by udev in /dev when you push the sync button.

Good luck!
Scott

---

### Post by Tommy on 2008-01-16
> **firecat53 said:**
> I have jpilot set to look at /dev/pilot, which should be created by udev in /dev when you push the sync button.


Have you tried 
```
usb:
```instead of ```
 /dev/pilot
```?

That uses a different  USB driver which is reputed to be much faster. (I discovered it reading the docs in /usr/share/jpilot or somewhere similar.) I just don't know whether it works on all hardware platforms. 

[edit: I originally wrote that you put usb: in your udev rule as well as the jpilot prefs, but now that I"m looking I can't find it in udev so it may bypass udev completely. Let me know what works for you. Your mileage may vary. Standard disclaimers apply.]

---

### Post by firecat53 on 2008-03-06
Yes, the  usb:  device worked much better and didn't require adding the complicated udev rule.

So -- 
1. Install jpilot
2. 'sudo modprobe visor' and add visor the list in /etc/modules
3. To sync only when jpilot is open,  open jpilot -> preferences -> settings -> serial port and enter "usb:"  (not including the quotes)
4. To have it sync when you push the hot-sync button (without opening jpilot), open main menu -> system -> preferences -> removable drives and media -> PDA's , check the sync palm box, and add "/usr/bin/jpilot-sync -p usb:" as the command.

Scott

---

### Post by Luderacer on 2008-06-15
awsome thanks alot work perfect:KS

---

