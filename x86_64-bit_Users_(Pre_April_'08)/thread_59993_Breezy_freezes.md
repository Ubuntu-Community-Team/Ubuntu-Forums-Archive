---
title: "Breezy freezes"
date: 2005-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by haakon on 2005-08-26
Hi,

I have just put together my new AMD64 system. Specs:

Abit AV8 motherboard
AMD Athlon 64 3700+ 2.2GHz Socket 939, 1MB L2
2 X 1024 Kingston PC3200 ram

These are brand new parts. From before I have a 160GB disk with swap, /boot, /, and /home partitions. /home is reiserfs, / and /boot is ext3. I also have a Chieftech PSU at 340W or 360W (can't remember exactly, but one of those), and a NEC DVD burner.

I got the Hoary Hedgehog Kubuntu DVD for amd64. It comes with a live version which I loaded first to get some backups done. This didn't go very well: as soon as I pressed the K-menu ("start button") in KDE, the system froze. I could still move the mouse pointer around, but the keyboard was unresponsive (even pressing caps lock did not trigger the keyboard LED), and I could not press any buttons or anything on the screen. Reset button was the only option. Well, I loaded Knoppix and got the backups done fine.

Next, I got kubuntu installed, and that went fine. However, after a short while of using it, it froze in exactly the same way as the live version had. I also installed ubuntu-desktop to see if the same thing would happen in GNOME, and it seemed to do so (I received a message in Psi (jabber client) both times I tried, but that could be a coincidence). This was of course highly annoying, but by now it was pretty late, so I went to bed.

This morning when I started the system, I went into GNOME and used Firefox and Evolution for a while. Halfway through a mail in Evolution, the display went black, and then my screen went into stand-by mode (as it does when the system is turned off). Again the keyboard seemed unresponsive. Reset button ahoy.

Now after it booted, the screen went black in the same fashion, but this time as soon as KDM appeared. Reboot again, and the same thing happened. At this point I had to leave, so I haven't tried anything else so far.

Searching the forum I see several people having had freezing problems, but none match my problem exactly.

It seems unlikely to me to be a hardware problem, but then again I'm not a hardware buff. I'm pessimistically thinking that 64-bit distros are still a bit immature and not as well tested as their 32-bit siblings. Still I would hate to have to resort to a 32-bit distro, and I'll try whatever you may suggest to get a stable usable 64-bit system.

Thanks for any assistance :)

EDIT: Sorry, I meant Hoary, not Breezy ... so confusing with all the names ;)

---

### Post by Tamir on 2005-08-26
You are on Hoary Hedgedog amd64 forum ;-) I know there is not a forum for amd64 on breezy, but you should report about your problem on forum "Breezy Badger Development Release":
[http://ubuntuforums.org/forumdisplay.php?f=70](http://ubuntuforums.org/forumdisplay.php?f=70)

---

### Post by haakon on 2005-08-26
[QUOTE=Tamir]You are on Hoary Hedgedog amd64 forum ;-)[/QUOTE]

Argh, I was just confused about the names. I *am* using Hoary Hedgehog, 5.04. Not Breezy. Don't know where I got that from. :)

---

### Post by Tamir on 2005-08-26
[QUOTE=haakon]Argh, I was just confused about the names. I *am* using Hoary Hedgehog, 5.04. Not Breezy. Don't know where I got that from. :)[/QUOTE]
 Can you please show us the Xorg log after it frozes (from console)?

---

### Post by haakon on 2005-08-26
[QUOTE=Tamir]Can you please show us the Xorg log after it frozes (from console)?[/QUOTE]

Good idea, I'll do so when I get back home.

---

### Post by Kuolio on 2005-08-26
Are you sure that this is not a hardware issue? I mean, does your system overheat? could that cause the crash? or is your PSU stable and can it handle the load of your new parts? 

I've encountered many similar situations, where after a while of using a pc it shutsdown, reboots or locks-up or something because off insufficient dispatching of heat a.k.a. overheating or because PSU doesn't meet up with the power consumption of the system.

Check that your HeatSink is correctly in place, and that you have silver/copper/heat-paste between it and the prosessor. If these are ok, then how about cheking your PSU voltage output?

To check for system temperatures, go to bios after using your pc with some heavy load or after a crash, and check your temperatus if they are shown there.. most bios'es show system-temps either on boot-up or in some menu (in bios).

---

### Post by haakon on 2005-08-26
[QUOTE=Kuolio]Are you sure that this is not a hardware issue? I mean, does your system overheat? could that cause the crash? or is your PSU stable and can it handle the load of your new parts?[/QUOTE]

I haven't checked the temperature, and I'll do that later. I double-checked the fan/heatsink when I installed them because of some other (unrelated) problem, and from what I can tell, there is no problem there. But again, I'll check the temperature, thanks.

I was able to use Knoppix for a pretty long time without a crash or a freeze, so I have been thinking it is not heat or power related. After all, Knoppix runs the DVD drive pretty hard and that alone should generate more heat/power than simply booting a disk based OS and reading some web pages, or at least that's what I assume :)

I am considering installing 32-bits Ubuntu instead. But first I have to determine if my problems are software or hardware related.

---

### Post by haakon on 2005-08-27
Update: I could find nothing in the xorg logs (or any other log) indicating anything out of the ordinary. One of the first things I did on the new system was to enable "Cool'n'Quiet" in the BIOS. I don't know if the Hoary kernel supports this, so just in case this is the culprit, I disabled it again. I will see if that helps.

By the way, I caved and installed 32-bits Ubuntu instead, and for the longest time it looked like that helped, but then it froze again. So technically this thread doesn't belong here anymore (I plan to stay on Ubuntu32 regardless). :-)

---

### Post by Velox Letum on 2005-09-02
I have this same exact problem...user inputs freeze, but some programs continue running, nothing suspicious in Xorg.log, and a hard reboot is the only way out.

---

### Post by mlomker on 2005-09-02
[QUOTE=Velox Letum]I have this same exact problem...user inputs freeze, but some programs continue running, nothing suspicious in Xorg.log, and a hard reboot is the only way out.[/QUOTE]

Yup, I've had this happen twice so far.  Basically the keyboard just stops working on my laptop.  The mouse and everything else on the system seems to be fine.

The only thing that I noticed was that I had a ton of these in my dmesg:
[B]
APIC error on CPU0: 40(40)[/B]

The problem is that I get these even when things are working right, but on those occassions there were a couple screens full of it.

---

### Post by DancingSun on 2005-09-02
You guys probably need to file a bug.  Or else it's likely this will go on unresolved.

---

### Post by DancingSun on 2005-09-02
That's odd, I couldnt' see the post I just posted.

Anyway, I was saying that you guys should file a bug so that the devs can fix this.

---

