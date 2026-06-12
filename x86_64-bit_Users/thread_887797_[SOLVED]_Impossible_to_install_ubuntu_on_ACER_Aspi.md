---
title: "[SOLVED] Impossible to install ubuntu on ACER Aspire M1201 ?"
date: 2008-08-12
forum: x86 64-bit Users
---

### Post by dinofelis on 2008-08-12
Hello,

I have a problem: I have installed Ubuntu on several machines, I am pretty satisfied with it, and my old (8 years old) XP box needed replacement.  As I didn't want to pay for a windows licence (again!) I thought I did a good thing by buying a linux-installed ACER Aspire M1201 (amd athlon 64 x2 +5000), and wanted to install ubuntu on it.  Ordered the stuff by web, received it 2 days later in the mail, great.
So I ran my ubuntu installer disk on it... doesn't work.  Well, I can boot on the live disk, I can select the language, and then I get the menu, but there it stops.  Whatever I do, I "load the kernel" up to 100%, and then the screen goes black, and that's it.

Then I realized that this was an AMD machine, so I downloaded an image and I burned another CD, this time with the AMD-64 version of the ubuntu live disk.  

Same story.  Well, it goes a bit further, it tells me something like "kernel alive" and then something like "direct mapping" with some numbers (could give you the details if you ask).

So it seems that I won't be able to get ubuntu on this machine.  It runs under a text-version of linux by a company linpus.  ([www.linpus.com](www.linpus.com)).

Any hints to get ubuntu on it ?

Or is this hopeless ?  I could get ubuntu working (without the slightest problem) on my laptop ACER Aspire 5315, and I could also install it in different ways on different DELL machines.

---

### Post by ajgreeny on 2008-08-12
Perhaps worth trying the Alternate Install CD also available from the ubuntu website.

---

### Post by woelf on 2008-08-12
try this
1 go to this screen[ATTACH]81298[/ATTACH]
2 go with the arrow keys to install ubuntu
3 press f6
4 type all_generic_ide
5 press enter

---

### Post by dinofelis on 2008-08-12
Ok, I made some progress.  Indeed, using the F6 option, and selecting the first one in the list of options, I could now boot from the live CD.  I could even play around a bit with the live cd ; then I decided to install, the installation procedure went normal, but upon reboot, I got the right grub boot, but upon selecting the normal ubuntu kernel, I got again the same error:
the window becomes black, and there's written:
"kernel alive
kernel direct mapping tables up to " and then some hex numbers.

Booting in the fail safe mode gives me a dump of a lot of 
statements on the screen and then hangs too.

I did install an old version of Windows XP (just to test the hardware), and I can boot more or less normally under XP (but a lot of drivers missing of course).

Nevertheless, it seems that one CAN boot under ubuntu (live cd) so there must be a solution...

(I'm pretty vague in the description because I'm telling this from memory right now ; I can do things more in detail if needed).

EDIT: the option that allowed me to boot from the live CD was: (F6) acpi=off
I have no idea what it does, but it allows the system to boot correctly from the CD.  
Is there a way to do this (modifying the grub menu lst or so) from the installed version on the hard disk ?
BTW, the all_generic_ide didn't let me boot from the CD (black screen and "kernel alive...")

---

### Post by dinofelis on 2008-08-12
Ok, seems to work: I added acpi=off in the menu.lst file (booting from the CD), and now I can boot from my hard disk !  Thanks...

---

