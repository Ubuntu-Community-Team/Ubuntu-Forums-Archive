---
title: "nVidia chaos"
date: 2008-12-14
forum: x86 64-bit Users
---

### Post by marchar on 2008-12-14
My setup:  HP Pavilion Desktop; Athlon 64 x2 5600; 3 GB;nvidia GeForce 6150 SE nForce 430; Samsung SyncMaster 2232BW  I run Ubuntu on a second internal hard drive and Vista (??!) on the first hard drive.... which I use very rarely.  I am committed to Ubuntu... so will do anything to get back home...

Using Ubuntu for several years....Love it!  Just upgraded from 8.04 to 8.10... went OK.

At First, I didn't enable the non-community nVidia driver.. and everything worked OK, but later decided to do it... and still it seemed to worked fine with the commercial driver.

THEN, I think I made a gross error in letting the UpDate Manager install some KDE stuff... I did this absent-mindedly!! and after that I began to have video problems... with FireFox taking up the whole desktop, even not having the minimize buttons etc. on the top right...only way to close was by going to File and closing it.  So, decided to "deactivate" nVidia Driver, (I assumed), the earlier video config.

Disaster.  Display began blinking etc.  Re-booted and at Log-in a popup said wrong display size.. should be 1680X1050... but when going to screen resolution, this setting would not stick.  Chose lesser one and the display turned GREY... with only light around edges.  Rebooted several times and same result...jiggly screen and then grey screen at "drum music" point.  Dead End!

Re-booted to Recovery Mode and tried everything... dpkg, fsck, and X-FIX.  Inserted 8.10 disk into machine to see if I could re-boot from that.... same grey screen.

I am incompetent with command line stuff, but it seems I need to boot to Rescue Mode and use commands to reconfig X Server, but don't know what to enter...

Anyone got any solution?   Thanks for the help...

---

### Post by cariboo on 2008-12-14
Have you tried the xfix option when you boot in recovery mode?

If xfix doesn.t seem to work try this at the prompt:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

The way to fix the firefox problem is to press F11 twice, this will resize the window back to it's normal size.

Jim

---

### Post by marchar on 2008-12-14
Hi Cariboo

I did try the command that you recommended.... didn't work.

I tried lots of stuff, always with negative results.

Finally, I ran the live 8.10 CD and it didn't work either....same jiggly screen and wrong resolution... I was able to go into the restricted drivers and download and install the nVidia driver... but, of course, one has to reboot.  But, this time for some weird reason, I didn't get the grey screen of death but a jiggly poor resolution screen.  But once there, I was able to go to the restricted drivers and re-install the nVidia driver.  Upon reboot the screen was stable... with wrong resolution... which was easily fixed.  

I still don't know why this whole mess happened... but am very happy it now works.

Thanks for helping out.

So, I am back with my favorite Ubuntu.

---

