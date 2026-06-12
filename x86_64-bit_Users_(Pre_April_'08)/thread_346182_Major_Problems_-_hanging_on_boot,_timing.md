---
title: "Major Problems - hanging on boot, timing"
date: 2007-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by trtech on 2007-01-25
I have an interesting problem. Here's the setup:

MSi K9N Platinum mobo
NVIDIA nForce 570 chipset
AMD 64 X2 +3800
2.6.17-10-generic kernel
kubuntu 6.10

Problem #1: While booting it hangs on:
"ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1"
(btw, it took me forever to figure out how to see output while booting... that should be easily accessible)

It hangs about 2/3 of the time. I have to reboot and pray. I have tried different combinations of the following kernel options: acpi=off, noapic, nolapic No change.

But, ok, I can live with that. I don't boot it up very often anyway, because I don't shut it down very often.

Problem #2: I had a miserable time getting the video driver to work properly. I had to download and use some craxy utiltiy to get the screen in the right position, then get the output from this utiltiy and manually edit xorg.conf, which is no picnic. Then the cursor was leaving trails, so I tried to update the nvidia driver, which took ages. I finally had to use another utility, and that said it didn't think my hardware was supported. I decided to trudge on anyway (which was an option) and it seemed to work ok after I used the first utility again and edit xorg.conf again to reset the position. Sheesh.
 
Problem #3: Some things don't work. Like Firefox plugins. Again, not a huge deal, but starting to think of installing the 32-bit version...

Problem #4: Ok this is where it gets crazy. Timing is all screwed up. It started with duplicate keeey presses. (Ok, normally I would go back and delete the 2 extra "e"s, but will leave them here for effect -- in case someone's searching, though, this is about duplicate key presses.) Ii found an interesting thread here: 
[http://lists.opensuse.org/opensuse/2006-11/msg03716.html](http://lists.opensuse.org/opensuse/2006-11/msg03716.html)

And following the thread you get to this post:
[http://lists.opensuse.org/opensuse/2006-11/msg03750.html](http://lists.opensuse.org/opensuse/2006-11/msg03750.html)

> There are more than just the keyboard going nuts, however. Everything relating to timing seems to be broken, games (Torcs) doesn't work well, multimedia playback is distorted and the system clock slows down. All these problems increase in severity with increasing system load. If I use the clock as a screensaver, I can see the clock advance 3 seconds and then jump back a second or two.

Ahh, that explains why playback in Amarok is speeding up -- I thought it had to do with my network, since the music is on a smb share. And then I noticed that my clock had jumped ahead an hour. 

<rant>So, basically this system is not working. I'm not the computer genius that some of you are, but I do have a BS in computer science and 22 years of programming experience. If I can't get this thing to work after two weeks of hacking on it, then it ain't ready for prime time.</rant>

So, my question is: will going back to a 32-bit install help with these problems, or do I have to either go back to Windows XP <GASP> or older hardware and wait till ubuntu is ready for my new hardware?

<rant>Please keep in mind that I'm not doing this just for fun; I'm trying to get a business off the ground, so messing around with my OS/gdm is not at the top of my list of things I need to be doing atm.</rant>

Thanks in advance for any help...

Cheers,
Chris

---

### Post by carlb on 2007-01-25
I have a similar configuration to yours and have wrestled with the same issues.  I am not 100% resolved yet but made some progress.  Here are two thoughts

1.  It isn't clear from your post, but a lot of my keeeyyy repeating issues went away by installing the system with the boot "live noapic" setting.  I keep the APIC setting in the bios enabled.  Getting the system to boot as "live noapic" isn't intuitive so you may have to try it.    
I hit F6 and the add noapic before the two dashes of the boot command line. 

2.  A post pointed me to using Automatix2 to install the NVidia drivers.  I too struggled getting the NVidia driver and settings correct.  Automatix2 worked like a charm and is an  absolute no brainer.   You can go to the Automatix2 website and install Automatix2 directly.  It will then appear on your Applications menu.  Fire it up and select NVidia.  It somehow recognizes your hardware and gets the right driver and configures Xorg.  

Hope that provides some help.

Carl

---

### Post by Kilz on 2007-01-25
> **trtech said:**
> 
 
Problem #3: Some things don't work. Like Firefox plugins. Again, not a huge deal, but starting to think of installing the 32-bit version...


I agree, install the 32bit version of Firefox.

---

### Post by trtech on 2007-01-26
**carlb** -- Thanks for your help. I was confusing **apci** and **acpi**. Everything seems to be working now with this line in menu.lst:
```
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro acpi=off **noacpi**
```

**Kilz** -- Thanks for the support. I'll have a look the guide linked in your sig soon and will probably revert to 32-bit Firefox, but not to 32-bit ubuntu.

---

### Post by Glacier on 2007-02-09
Nothing works for me except adding "reboot=b" parameter  (in /boot/grub/menu.lst) .  It makes Linux run the BIOS reboot code.

---

