---
title: "ATi Catalyst 8.6 x86_64, no GLX or 3d"
date: 2008-07-03
forum: x86 64-bit Users
---

### Post by CalcProgrammer1 on 2008-07-03
I tried the new 8.6 ATi driver on my Radeon PC (an AthlonXP 2600+, AGP4x, 32-bit, X1600Pro 512MB PC) and it totally failed, locked up before anything even would happen.

So, I took my card out and put it in my Sempron 2600+ 64 bit AGP8X PC.  The drivers installed fine and they even give me a usable desktop, but any time I try to load a 3d application (glxgears) I get a message about GLX not being enabled on my display.  I don't know why this is happening, as my xorg.conf's Module section has Load "glx" in it.

My PC:
ATi Radeon X1600Pro 512MB AGP
Sempron 2600+ 1.85GHz 64 Bit (stable overclock)
1.5GB DDR RAM
Ubuntu 8.04 x86_64

What do you have to add to fglrx 64 to enable GLX?

---

### Post by lavinog on 2008-07-04
I cannot get 8.6 to work on my 64bit system currently. 8.5 works with no problems except maybe a random crash when playing ut2004 (after 4 hours).

---

### Post by soxs on 2008-07-04
remove your ati driver and try this (of course you need some basic library stuff like build-essential fakeroot ...):
[http://ubuntuforums.org/showthread.php?t=840092](http://ubuntuforums.org/showthread.php?t=840092)
Note: You will have to adjust the xorg.conf yourself.

Attached my xorg.conf (Note: I have a other card aka RadeonHD 3870 and you will have to slighttly adjust them.)
Note: Copy paste is 100% evil!

---

### Post by lavinog on 2008-07-04
I have 8.6 installed currently with no errors during the install.
the problem is I get severe corruption when I exit a full screen opengl app.
glxgears works fine. glxinfo and fglrxinfo will display information but will segfault at the end. When I get the corruption I just have to restart X and it is fine. I haven't tried changing anything i bios yet, but as I mentioned before these problems didn't exist in 8-5.
I am using an ATI 3200 IGP
I am saving up for another card soon.

---

### Post by soxs on 2008-07-04
> **lavinog said:**
> I have 8.6 installed currently with no errors during the install.
the problem is I get severe corruption when I exit a full screen opengl app.
glxgears works fine. glxinfo and fglrxinfo will display information but will segfault at the end. When I get the corruption I just have to restart X and it is fine. I haven't tried changing anything i bios yet, but as I mentioned before these problems didn't exist in 8-5.
I am using an ATI 3200 IGP
I am saving up for another card soon.
I don't really know about IGP 3200, but I can assure you that segfaults are not funny at all when it comes to 3D acceleration :-S btw. I don#t get any when running glxgears.

---

### Post by Sed Levis on 2008-07-08
Hey all, I am a super newbie.  With that said, I recently installed ATI catalyst drivers and I have the control center in my applications but when I go to open it. I get this.

"There was a problem initalizing Catalyst Control Center Linux edition. It could be caused by the following.

No ATI graphix driver is installed, or the ATI driver is not functioning properly.  Please install the ATI driver appropriate for you [sic] ATI hardware, or configure using aticonfig"

I've reinstalled the ATI drivers a couple of times and get the same result.  Any ideas?  

If this has been discussed before i'm sorry.. Just point me where to go.

oh yea!  I'm using Hardy on a x64 2gz AMD (HP Pavillion zv6000 series notebook)  My video card is an ATI Radeon Xpress 200M.

Thanx!


Thanx.

---

### Post by soxs on 2008-07-08
> **Sed Levis said:**
> Hey all, I am a super newbie.  With that said, I recently installed ATI catalyst drivers and I have the control center in my applications but when I go to open it. I get this.

"There was a problem initalizing Catalyst Control Center Linux edition. It could be caused by the following.

No ATI graphix driver is installed, or the ATI driver is not functioning properly.  Please install the ATI driver appropriate for you [sic] ATI hardware, or configure using aticonfig"

I've reinstalled the ATI drivers a couple of times and get the same result.  Any ideas?  

If this has been discussed before i'm sorry.. Just point me where to go.

oh yea!  I'm using Hardy on a x64 2gz AMD (HP Pavillion zv6000 series notebook)  My video card is an ATI Radeon Xpress 200M.

Thanx!


Thanx.

Plx don't hijack threads, start new ones.

Did you adjust your /etc/X11/xorg.conf?
If not, have a look here:
[http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide)
from where it says: "Finishing the Install: Configuration"
If this won't work, a) send me your current xorg.conf ( to make a r/w backup copy it to your desktop and adjust permissions with this command: ```
sudo cp -vf /etc/X11/xorg.conf ~/Desktop/xorg.conf.txt; sudo chmod 755 -vf ~/Desktop/xorg.conf.txt
```
 b) start all over with method 2 mentioned in the given link again.

---

### Post by lavinog on 2008-07-25
8.7 is available now...it fixed a bunch of issues for me.

---

### Post by markbuntu on 2008-07-27
The directions for correctly installing the 8.7 driver on amd64 are here:


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

The directions for tweaking it are here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

Release notes for 8.7

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_87_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_87_linux.html)

Release Notes for 8.6

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html)

Release notes for 8.5

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_85_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_85_linux.html)

---

