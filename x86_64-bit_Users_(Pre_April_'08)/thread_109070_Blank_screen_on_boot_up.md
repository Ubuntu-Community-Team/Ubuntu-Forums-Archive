---
title: "Blank screen on boot up"
date: 2005-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by dsierpin on 2005-12-27
Hello!

Due to problems with a winmodem, I needed to install and run the 2.6.10 kernel in place of the 2.6.12 kernel that came with my Breezy install disc.  When I select the 2.6.10 kernel from the GRUB menu, some white GRUB text flies by and then the screen blanks right away, before making it to the Ubuntu splash screen.  I had problems with my video card (Radeon 200M), but I got it to work under the 2.6.12 kernel by editing the adding a NoAccel Option to the xorg.conf file, and it was suggested that I add a NoAccel option to the menu.lst file in /boot/grub, but that didn't help anything.  Any suggestions would be very helpful!

Cheers

---

### Post by cadumg on 2005-12-28
Is it a HP Notebook ?

Take a look on this: [http://www.ubuntuforums.org/showthread.php?t=102967&highlight=xorg.conf+i810](http://www.ubuntuforums.org/showthread.php?t=102967&highlight=xorg.conf+i810)

I did it and worked.

---

### Post by nbhaskar on 2005-12-31
I installed the OS (AMD64 version), x server failed due to my ATI driver problem, all I was getting was the command line nothing else. Then I read from a forum that I should change the config file and replace "ati" with "vesa". I did that and now I get a [COLOR="Red"]**blank screen**[/COLOR] when the OS starts x server, I could not do any thing after this but push the power button to shutdown the pc.

My set up is AMD Athlon 64 X2 3800+ on ECS nForce4 mobo with 2 GB Kingston DDR400 PC3200 ram. Mobo has sound processor built in, then the problem part ATI X700 256MB DDR3 PCIe card.

I have Windows XP pro already running on my machine, I installed GRUB loader for dual boot.

When I tried the live cd too I had the same problem.

Can any body help me out solve this problem and boot Breezy?
:confused:

---

### Post by desiman on 2005-12-31
hi,
 i had the same problem last week when i tried . 
I changed to vesa. didnot help . but i commented out  "load dri10" and 
"load int10"  and kept the ATI driver. it worked .

-desiman

---

### Post by nbhaskar on 2005-12-31
I'm a noob, Can you give more details on where did you make the following changes?

Any help would be appreciated.

[QUOTE=desiman]hi,
 i had the same problem last week when i tried . 
I changed to vesa. didnot help . but i commented out  "load dri10" and 
"load int10"  and kept the ATI driver. it worked .

-desiman[/QUOTE]

---

### Post by dsierpin on 2006-01-02
Hello All!

When I originally installed the 2.6.12 kernel, I needed to pass the vga=771 boot parameter to fix the blank screen, and then I had to edit /etc/X11/xorg.conf, adding the Option "NoAccel" line to my video card device section.

I got the blank screen to go away in the 2.6.10 kernel by getting rid of the vga=771 boot parameter.  Hope this helps!

By the way, my computer is an hp zv6000. 

Happy New Year!

---

### Post by nbhaskar on 2006-01-05
My problem went away when I changed "ati" to "radeon" in xorg.conf file. When I change that to "vesa" I still experience blank screen. Hope this helps somebody.

---

