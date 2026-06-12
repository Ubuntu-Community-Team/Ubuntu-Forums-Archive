---
title: "AMD64 -&gt; Intel"
date: 2008-06-03
forum: x86 64-bit Users
---

### Post by zkab on 2008-06-03
I have AMD mobo and run Ubuntu 8.04 AMD64. Soon I will switch to another computer that will be an Intel Core Duo.
How can I move Ubuntu from AMD64 to Intel with all my settings & configurations ?

I have backuped-up with:

sudo tar cvpzf zkab_backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/zkab_backup.tgz --exclude=/mnt --exclude=/media --exclude=/sys --exclude=/tmp  / 

Is it OK to just:

1) Install Ubuntu from scratch on the Intel comp
2) Reboot
3) Then  tar zkab_backup.tgz -C /

---

### Post by dcstar on 2008-06-03
> **zkab said:**
> I have AMD mobo and run Ubuntu 8.04 AMD64. Soon I will switch to another computer that will be an Intel Core Duo.
How can I move Ubuntu from AMD64 to Intel with all my settings & configurations ?

I have backuped-up with:

sudo tar cvpzf zkab_backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/zkab_backup.tgz --exclude=/mnt --exclude=/media --exclude=/sys --exclude=/tmp  / 

Is it OK to just:

1) Install Ubuntu from scratch on the Intel comp
2) Reboot
3) Then  tar zkab_backup.tgz -C /

Unless your video hardware is exactly the same then it won't work.

Search out posts on changing video hardware.

---

### Post by zkab on 2008-06-03
My video hardware will be different - I was not aware of the problem ... thanks

---

### Post by aaron.d on 2008-06-03
You might want to think about keeping your /home directory on a separate partition, this way all your important work/files/bookmarks/music etc can persist through a clean install (provided you keep all those files in /home/username, which you should)

---

### Post by zkab on 2008-06-03
I will have the same user accounts on the new computer.
Since I have backup-ed the old comp with:sudo tar cvpzf zkab_backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/zkab_backup.tgz --exclude=/mnt --exclude=/media --exclude=/sys --exclude=/tmp /
don't I then get it right (work/files/bookmarks/music etc) when I restore with: tar zkab_backup.tgz -C /
The new /home will be overwritten with the old /home ...

---

### Post by RAOF on 2008-06-04
> **dcstar said:**
> Unless your video hardware is exactly the same then it won't work.
...

This isn't quite true; if you aren't using proprietary drivers everything should work just fine; we don't hardcode the Driver into /etc/X11/xorg.conf anymore, so X will just autodetect the appropriate driver.

---

### Post by mac143_01 on 2008-06-04
what is a MOBO? 

I think AMD is better for games coz Intel is for programs...

---

### Post by Sef on 2008-06-04
> what is a MOBO? 

MOBO = MotherBoard

---

### Post by zkab on 2008-06-04
> **RAOF said:**
> This isn't quite true; if you aren't using proprietary drivers everything should work just fine; we don't hardcode the Driver into /etc/X11/xorg.conf anymore, so X will just autodetect the appropriate driver.

I have Nvidia in my old comp. How should I proceed if I go with Nvidia or choose ATI in my new comp ... still restore and after that try to get the right driver ?

One thing that also makes me confused is AMD64 vs Intel ... now I have a lot of apps in AMD64-version ... if I coose Intel in my new comp and make a restore ... don't I get wrong architecture when restoring ... how can this be solved ... I can't download and re-install all the AMD64-apps I have for the new comp :confused:

---

### Post by RAOF on 2008-06-04
The way you've backed up, you've backed up *everything* - programs, kernels, config, the lot.  Apart from sticking some bootloader in the MBR, untarring that backup on to your new system will replicate your old system *exactly*.  As long as your new system is also x86-64 capable (and, unless you're using quite an old CPU, it will be - Core 2s and above are all definitely x86-64 capable) everything should just work.

If you have an nvidia card in your new system, you shouldn't need to do anything - the existing driver will be properly set up for your new card.  Unless it's a *very* new card, like a Geforce 9600, which isn't supported by the exsiting Ubuntu drivers.

If you have an ATI card in your new system, you'll basically just need to remove the nvidia driver and install the ATI one.  You'll be able to do this in your new system, and BulletproofX means that you should be able to do it from a GUI.

---

### Post by zkab on 2008-06-04
Thanks for your support - now I feel confident to move to new hardware :)
I migrated to Linux recently (after been stucked to Windows for ages) and the more I learn about Ubuntu to more I am impressed.
I will never turn back to Windows.

---

### Post by Sef on 2008-06-04
If you have any questions, no matter what, please ask them.

---

### Post by ByteJuggler on 2008-06-04
> **zkab said:**
> Thanks for your support - now I feel confident to move to new hardware :)
I migrated to Linux recently (after been stucked to Windows for ages) and the more I learn about Ubuntu to more I am impressed.
I will never turn back to Windows.

Just to give you some added confidence: I recently (well some time ago) upgraded hardware from an AMD64 3200+ based system with Asus motherboard and ATI graphics to Intel Core2 bases system with ABit and Nvidia graphics.  In other words, everything changed.  (This was on Gutsy still.)  The only issue I had was to do with graphics, and to fix it I simply edited the config file up front to force it to generic vesa.  My installation booted up unchanged on the new hardware, even the sound worked out of the box.  I then went about installing the Nvidia proprietary driver etc. to fix the graphics properly on the new hardware.  (By comparison, I tried many times to try and migrate my Windows installation to the new hardware via several methods to try and get Windows to redetect the hardware on bootup as during installation, but no amount of hacking, registry tweaking, coaxing, screaming or indian rain dances succeeded, so I ended up having to reinstall that... irritating.)

---

### Post by GTengineer on 2008-06-04
> **mac143_01 said:**
> what is a MOBO? 

I think AMD is better for games coz Intel is for programs...

Not true since Intel's Core 2 architecture came out which is superior clock for clock to AMD even the new Phenoms, not to mention they are clocked higher anyway.

---

### Post by GTengineer on 2008-06-04
> **mac143_01 said:**
> what is a MOBO? 

I think AMD is better for games coz Intel is for programs...

Not true since Core 2 came out which is superior clock for clock to AMD even the new Phenoms, not to mention they clock higher anyway.

---

### Post by zkab on 2008-06-05
> **ByteJuggler said:**
> Just to give you some added confidence: I recently (well some time ago) upgraded hardware from an AMD64 3200+ based system with Asus motherboard and ATI graphics to Intel Core2 bases system with ABit and Nvidia graphics.  In other words, everything changed.  (This was on Gutsy still.)  The only issue I had was to do with graphics, and to fix it I simply edited the config file up front to force it to generic vesa.  My installation booted up unchanged on the new hardware, even the sound worked out of the box.  I then went about installing the Nvidia proprietary driver etc. to fix the graphics properly on the new hardware.

I am glad to hear how you did it. Basically I am going to do the same ... and hopefully get the same good result :)

---

