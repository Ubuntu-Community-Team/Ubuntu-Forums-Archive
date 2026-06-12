---
title: "Ubuntu freezes during installation"
date: 2006-02-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Meuro on 2006-02-23
i searched the forums but couldnt find a solution and have been to the irc channel #ubuntu looking for help, got some good suggestions but nothing worked.

i think i have spent nearly 9 hours trying to install ubuntu.  i have downloaded the dvd and the cd,i have checked the disks i downloaded with checksums, i did a memtest, checked my hdd's were connected correctly, i have a cd-rom and a dvd-rw and have tried using both drives, i have turned off acpi and apci at when boot from install disk. nothing seems to work. it always freezes on the installing/ configuring bit right at the very end of the process. typically 70 something %. 

my hardware is: 
amd64 3400, 
foxconn mobo, 
Asus ati X850XT 256mb AGP,
1024ram and 
samsung 80gb sata hdd. 

any ideas?

---

### Post by ricka on 2006-02-23
download dapper fliight 4 cd(development version) and install it:)
also you can install hoary and dist-upgrade it to breezy
there is a bug in breezy installer

---

### Post by Meuro on 2006-02-24
Thanks ricka.  will give that a go. :D

---

### Post by marcthepunk on 2006-02-24
same same same with me.  at components install step, my machine bombs at around 39%.  
it's been 2 weeks now, and i think i've downloaded and wasted enough time, energy and media.  i am even thinking of giving up on installing ubuntu and try another distro, probably suse.
however, i'm willing to go out on a limb here and try this suggestion.  :cry:

---

### Post by wiljohnson on 2006-02-24
Just downloaded and burned live Breezy an hour ago and am working with it now--no problems with loading and running.  My hardware is P4  3G with NVidia -- Might be worth a try.

---

### Post by mpk on 2006-02-24
I suffered from the same kinds of problems as you guys, having spent weeks trying to install Ubuntu on a AMD64 based system. When my Windows installation became unstable as well, I knew something was seriously wrong. Ironically, Windows has been very stable for me :)
So, a friend of mine helped me to track down the cause of this unstable behavior. Soon after we pinpointed the two most likely culprits:

1) Corrupt hard-drive
If you're dual-booting to Windows, you could try to look for somekind of testing software from the hard-drive manufacturer. Scandisk(?) in Windows is unable to detect all kinds of errors (physical errors?)

2) Make sure that your memory modules are installed in the correct slots.
Even in one-module configurations, you might need to plug the module into a specific slot.


Having just now installed a new hard-drive and moving the memory module to the correct slot, I was able to install Ubuntu 5.10 without any problems. It's not a quarantee of a stable system, but it certainly means progress.

---

### Post by bonzodog on 2006-02-24
ATI boards are a known issue with linux installs, as the kernel is unable to talk to the hardware properly. basically, if you buy a PC with the plan of installing linux on it, avoid ATI chipsets, they are a PIA to use in linux. When I bought this AMD64 system, I made sure it was ALL nvidia. nforce3 chipset, and nvidia 6200 GPU.

---

### Post by jorty on 2006-02-24
Hello

Just today I received my brand new PC with the following components:

Asus A8R-MVP, ATI CrossFire, S939
Asus DVD 16x/48x, ATA100
Maxtor DM10 250GB, 7200RPM, 16MB SATA300
Sony DWQ30 DVD±RW, Dual Layer,
AMD Athlon64 3700+, S939, San Diego
Sapphire Radeon X1300, PCI-E, 256MB

I have no experience with Linux but choose Ubuntu because it should be very user friendly. I hope to dual boot with WinXP.
I have tried to install Ubuntu 64 bit with no luck. The installation stops with this last line:
Input: AT Translated Set 2 Keyboard on isa0060/serio0

The same thing happens when I try to run the 64 bit live CD I have downloaded. I got at worried when I read post from Bonzodog. Does this mean my new system is scrap since it has an ATI chipset?

---

### Post by Kamchatka on 2006-02-24
***[FONT="Trebuchet MS"][/FONT]***Ditto, Ditto, Ditto.  Freezes with the last line reading "BOOT:_" - Enter command does not receive a response.  Wonder why the Install cannot be made to a slave HD (I have C, D, and F, all NTFS, oodles of available storage)?  If affirmative, then I'd reconfigure the BIOS boot sequence to the HDD that received the new installation.  Searched for this answer, couldn't find it anywhere.  Come on forum - help an old man out, I'm running out of TIME.  Thank you!\\:D/

---

### Post by enno on 2006-02-25
I have gotten past the first "freeze" and succesfully installed ubuntu on an AMD64 (Turion)
in a Compaq V5015US which also has an ATI graphics card.
I booted/installed with:
linux vga=771
(as the online help suggested)

However - after an appearantly succesful install, the system trys to launch X11 and ends up
in a garbled screen mode from which there seems no recovery.
Recovery mode (text only) works ok.

SUSE works succesfully on this, but I can't get the wireless to work in that distribution.

---

### Post by PrivateDonut on 2006-02-28
Yeah, me too. I just got a laptop with AMD Turion 64 and 2 GBs of RAM. Couldn't wait to boot to my live cd to check out if it would recognize my wireless card. But, it freezes when booting to the live cd too. I've done the "live vga=771" too, only to end up with garbled screen.

---

### Post by RAOF on 2006-02-28
For those with (newish) ATI cards getting garbled screens.  Boot into recover mode, and set the Xorg graphics driver to vesa, using "dpkg-reconfigure xserver-xorg".  There'll be a lot of options, the defaults are fine (unless you know better).  Then when it gives a list of graphics drivers (ati, radeon, nv, etc), select "vesa".  This is a failsafe driver, which should always work.

Then, once you've got into a GUI it'll be easier to follow the "Ati drivers" link of my sig :)

Once more, with feeling:  **ATI suck in linux**.

---

### Post by ztirffritz on 2006-02-28
Where does one get the Dapper discs?  I can't find them on the download site.

---

### Post by RAOF on 2006-02-28
[cdimage.ubuntu.com/releases/dapper/flight-4](cdimage.ubuntu.com/releases/dapper/flight-4)

---

### Post by Meuro on 2006-03-02
hi, i was advised by various sources that the best thing to do was to install ubuntu 5.04 (hoary hog) and then do a distro upgrade.  
  But the install has frozen again.  Its during the second half of installation and its during the "setting up xserver-xorg (6.8.2-10)".
  Anyone got an idea what the problem might be this time?

Btw, i also tried dapper flight and it froze during the grub install and messed up the grub :(

----------------------------
amd64 3400,
foxconn mobo,
Asus ati X850XT 256mb AGP,
1024ram and
samsung 80gb sata hdd. 
----------------------------

---

### Post by Meuro on 2006-03-02
woohoo.

finally got it to work.  did a sever install of 5.10 and then did:
sudo apt-get install ubuntu-desktop

but it now freezes on the desktop for no apparent reason.  any one want to hazard a guess?

---

### Post by RAOF on 2006-03-02
[QUOTE=Meuro]woohoo.

finally got it to work.  did a sever install of 5.10 and then did:
sudo apt-get install ubuntu-desktop

but it now freezes on the desktop for no apparent reason.  any one want to hazard a guess?[/QUOTE]
I'd hazard a guess that you weren't using the VESA driver ;)

From a console, run "sudo dpkg-reconfigure -phigh xserver-xorg" and select the "vesa" driver from the first list presented to you.  That should then work.

Then, check out the "ATI drivers" link in my sig.

---

### Post by Aaron E. Mast on 2006-03-05
I think I might have the same problem. I tried to install Ubuntu 5.10-64bit on my system, and it keeps freezing up. I can usually get fairly far along on the instalation process. I get to where after it finishes copying everything from the CD to the hard drive, reboots, then when it was finishing the installation it froze up at 75%.

My hardware is a AMD 64 3000, Gigabyte mb, 768 mb Kingston RAM, ATI 9200SE video card.

---

### Post by Aaron E. Mast on 2006-03-05
I think I might have the same problem. I tried to install Ubuntu 5.10-64bit on my system, and it keeps freezing up. I can usually get fairly far along on the instalation process. I get to where after it finishes copying everything from the CD to the hard drive, reboots, then when it was finishing the installation it froze up at 75%.

My hardware is a AMD 64 3000, Gigabyte mb, 768 mb Kingston RAM, ATI 9200SE video card.

What should I do so that it will completely finish the installation?

---

