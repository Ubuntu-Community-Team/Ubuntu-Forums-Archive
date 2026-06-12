---
title: "No Splash Screen"
date: 2008-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Amorget on 2008-04-16
Computer:  Sony VGN-AR670 w/ a 8600GT and a C2D proc.  WUXGA (1920x1200) screen

Ubuntu 7.10 x64 w/ the NVIDIA restricted drivers

To get it to initially load before I installed the restriced drivers I turned off splash and quiet.  Well, I like the splash and quiet personally, so I turned them back on.  It just blank screens on me, with a little orange in the lower right.

It works just fine in the 32 bit version, but not in the 64 bit version.  Anyone have any thoughts?

---

### Post by hodge24 on 2008-04-16
Hi Amorget,

Have a look at your /etc/usplash.conf file - I had a similar problem, whereby the resolution for Usplash was set to 800x600 in usplash.conf, and therefore wouldn't render on my 1280x800 screen (outputting the same blank screen as you are getting). Open usplash.conf:

```
gksu gedit /etc/usplash.conf
```

and check the resolution. If necessary, change it to:

```
# Usplash configuration file
xres=1920
yres=1200
```

Save and reboot. :) Hope that helps!

---

### Post by Amorget on 2008-04-16
Man, I so thought that had to be it!

However, it didn't work :(  I rechecked my menu.lst and the usplash.conf, but they both appear to be correct.

Thanks,
Douglas

---

### Post by hodge24 on 2008-04-16
Hi,

it could be that usplash doesn't support 1920x1200 - try setting usplash.conf to a smaller resolution, with the same ratio. Mine works with 1280x800.

Also, are you using the default Splash art, or have you installed a custom splash?

Hope that helps.

---

### Post by McMagic on 2008-04-16
I had this same problem, and this fix works as long as you set the splash resolution tot he native res of your monitor. if you have a widescreen, make sure it is in the right ratio. Mine works with 1440x900 on a 17 inch widescreen.

---

### Post by Amorget on 2008-04-16
> **hodge24 said:**
> Hi,

it could be that usplash doesn't support 1920x1200 - try setting usplash.conf to a smaller resolution, with the same ratio. Mine works with 1280x800.

Also, are you using the default Splash art, or have you installed a custom splash?

Hope that helps.

Default Splash Art.

Unfortunately setting it to 1280x800 didn't help, same black screen.  Same with 1440x900

---

### Post by McMagic on 2008-04-16
look at the Ubuntu boot line in menu.lst and paste it here

---

### Post by st0nedpenguin on 2008-04-16
I had to settle for an 800x600 splash even though I'm running a 1600x1200 desktop, lord knows why.

---

### Post by warp99 on 2008-04-16
Set the vesa resolution at boot time by appending your kernel line with vga=xxx. This help guide has all the information you need;

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Just make sure that your vga=xxx parameter is the same as your splash screen resolution.

---

### Post by elmaz on 2008-04-16
Hi,
here is my solution on my PC and it worked perfectly.[LIST=1]
[*]Comment blacklisted framebuffer drivers and save.
```
sudo vi /etc/modprobe.d/blacklist-framebuffer
```add a "#" before ```
vesafb
``` and ```
vga16fb
```
[*]Add modules in initramfs.
```
sudo vi /etc/initramfs-tools/modules
```append following 3 lines then save.
```
vesafb
vga16fb
fbcon
```
[*]Update initramfs.
```
sudo update-initramfs -u
```
[*]Check your graphic card's framebuffer mode.
```
sudo hwinfo --framebuffer
```If you don't have hwinfo installed, install it first.
```
sudo apt-get install hwinfo
```
[*]Then it will show something like this:
```
Mode 0x033c: 1920x1440 (+1920), 8 bits
Mode 0x034d: 1920x1440 (+3840), 16 bits
Mode 0x033a: 1600x1200 (+1600), 8 bits
Mode 0x034b: 1600x1200 (+3200), 16 bits
Mode 0x035a: 1600x1200 (+6400), 24 bits
Mode 0x0307: 1280x1024 (+1280), 8 bits
Mode 0x031a: 1280x1024 (+2560), 16 bits
Mode 0x031b: 1280x1024 (+5120), 24 bits
Mode 0x0305: 1024x768 (+1024), 8 bits
Mode 0x0317: 1024x768 (+2048), 16 bits
Mode 0x0318: 1024x768 (+4096), 24 bits
Mode 0x0312: 640x480 (+2560), 24 bits
Mode 0x0314: 800x600 (+1600), 16 bits
Mode 0x0315: 800x600 (+3200), 24 bits
Mode 0x0301: 640x480 (+640), 8 bits
Mode 0x0303: 800x600 (+832), 8 bits
Mode 0x0311: 640x480 (+1280), 16 bits
```Write down the mode code you want to use, eg. I'm using 1280x1024 16bits, so the code is "0x031a"
[*]Edit menu.lst
```
sudo vi /boot/grub/menu.lst
```find the following 2 lines and add your mode code at the end of each line.
```
# defoptions=quiet splash locale=zh_TW [COLOR=Red]vga=0x031a[/COLOR]
``````
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=452c3352-f739-4df0-8930-8c80a9f212d4 ro quiet splash locale=zh_TW [COLOR=Red]vga=0x031a[/COLOR]
```
[*]Reboot.[/LIST]

---

### Post by Amorget on 2008-04-16
elmaz - That worked!  However, the splash screen is crammed up in the upper left... I used 0x037d (1920x1200 24bit).

Do I need to set it to something lower?

Thanks so much!

Douglas

---

### Post by elmaz on 2008-04-17
You're welcome!

I'm not sure why you got a crammed screen, maybe you can try another mode like 1920x1200 16bits or so on...

---

### Post by Amorget on 2008-04-17
> **elmaz said:**
> You're welcome!

I'm not sure why you got a crammed screen, maybe you can try another mode like 1920x1200 16bits or so on...

Good thought.  I'll keep trying modes until one looks right.

---

### Post by popat007 on 2008-04-21
Thanks elmaz,
  that worked!!!, i gave resolution of 1920x1200 it splashed in left upper corner.i liked that place so i will keep there.do you have any help on sound and function FN keys.

---

### Post by Amorget on 2008-04-21
> **popat007 said:**
> Thanks elmaz,
  that worked!!!, i gave resolution of 1920x1200 it splashed in left upper corner.i liked that place so i will keep there.do you have any help on sound and function FN keys.

What system do you have?

---

