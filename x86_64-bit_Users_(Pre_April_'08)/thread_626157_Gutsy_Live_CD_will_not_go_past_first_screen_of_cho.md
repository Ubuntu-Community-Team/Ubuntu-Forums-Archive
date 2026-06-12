---
title: "Gutsy Live CD will not go past first screen of choosing Start or Install Ubuntu"
date: 2007-11-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by anakrich on 2007-11-28
I am trying to install Ubuntu 7.10 amd64 on my HP Pavilion dv 2000 consisting of
AMD Athlon 1.7 GHz 64 x2 TK-53
2 GB RAM
Nvidia GeForce GO 6150
120 GB HDD

After I pop in the live CD and choose Start/Install Ubuntu, the CD Drive keeps on blinking on activity and even after 30 minutes nothing happens.
I tried F6 and removed quiet splash. The screen remains for all the time and I dont see the next screen or progress bar or anything except the first screen.
I tried hitting escape and pass noapic nolapic and vga=771, still nothing happens after 20 mins
I tried passing noapic nolapic and vga=791, still nothing happens.
I tried safe graphics mode, nothing happens.
I even tried nosmp.
I went through most of the forums, no mention about this.
Tried checking MD5 checksum, looks fine. If I select check CD for defects, nothing happens except CD ROM light blinking for 20 mins.
There is something obviously wrong. Can anybody suggest something?

Thanks,
Ananth

---

### Post by PmDematagoda on 2007-11-28
Did you try the [Alternate CD]("http://www.ubuntu.com/getubuntu/download")?
Check the check box near the end of the web page to enable you to download the Alternate CD.

---

### Post by Clancy_s on 2007-11-28
and/ or burn a new CD?

---

### Post by ZachSka87 on 2007-11-28
Nono!  All you have to do is press F6 to see your boot commands, delete "quiet" from that line and change "splash" to "nosplash"

You will also need to configure this in Grub after the install.  Happy Ubuntu-ing!

---

### Post by cforceleritas on 2007-11-28
> **ZachSka87 said:**
> Nono!  All you have to do is press F6 to see your boot commands, delete "quiet" from that line and change "splash" to "nosplash"

You will also need to configure this in Grub after the install.  Happy Ubuntu-ing!

I will vouch for this... the same problem was plaguing me but this solved it.  Just to clarify, to configure in grub after you install do:
```
sudo gedit /boot/grub/menu.lst
```
and remove the same boot arguments as before.

---

### Post by anakrich on 2007-11-29
Thank you very much folks.
The fix was very simple. Burnt another CD but with VERY LOW WRITE SPEED. worked out of the box with no optional boot parameters parsed to the installer.

---

