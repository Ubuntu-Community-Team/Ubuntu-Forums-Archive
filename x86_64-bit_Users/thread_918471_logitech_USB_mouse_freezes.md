---
title: "logitech USB mouse freezes"
date: 2008-09-12
forum: x86 64-bit Users
---

### Post by Dr_Newhart on 2008-09-12
I've just downloaded and installed the latest Ubuntu (ubuntu-8.04.1-desktop-amd64.iso) from the official d/l website. But every time I boot into Ubuntu, my wireless USB mouse freezes. My keyboard is wireless USB also, but it does not freeze. I've read several older threads and tried some of the suggestions there, but nothing has worked. It doesn't seem to be a USB problem, since like I said my wireless USB keyboard never has a problem. The mouse typically will freeze anywhere from 1 to 3 minutes into my session. Rarely it will freeze during sign in. Any suggestions?

Here's my hardware setup if that helps:
AMD Phenom 9850 Quad-core(not over clocked)
4GB Corsair DDR2 memory
Western Digital Raptor WD740GD SATA hard drive
Soundblaster Audigy 2 ZS platinum
ATI Radeon HD 3870 (pci express)
logitech MX620 USB mouse
logitech MX 3200 USB keyboard
ASUS DRW-1612BL
ASUS DVD-E616P2****

---

### Post by stanyo on 2008-09-13
Hello
very intresting post
I want to know too, because I think to buy one laser wireless mouse by logitech. Is there will be problem for me to use this mouse with my ubuntu??? On logitech web site there`s haven`t any drivers for linux.
thanks for answares

---

### Post by Dr_Newhart on 2008-09-13
I think I found my problem. Since I had just installed Ubuntu and installing Ubuntu is such a fast easy process (compared to Windows), I decided to reinstall my Ubuntu. I then realized my i-rocks media card reader(model# IR-5400) was plugged into my USB hub. So, I unplugged that and reinstalled Ubuntu and now I am having no problems with my mouse anymore. I haven't plugged my media card reader back in, but when I do, I'll update whether it causes the problem to reappear or not.

---

### Post by Dr_Newhart on 2008-09-23
Well, I both hot plugged my card reader and booted up with it already plugged in and both times the result was my logitech wireless USB mouse froze up within 2 or 3 minutes. So, it looks like it's a problem with the i-rocks IR-5400 card reader and ubuntu or a conflict between the card reader and my logitech cordless laser mouse MX-620 under ubuntu hardy heron (latest release) (in case anyone is interested).

---

### Post by lisati on 2008-09-23
The only solution I've tried works on a 32-bit copy of Feisty (7.04) and covers a freezing USB keyboard too: [http://ubuntuforums.org/showthread.php?t=854684](http://ubuntuforums.org/showthread.php?t=854684)

---

### Post by geclos on 2008-09-23
I have the same problem. the mouse freeze in the screen and exerything runs except the USB Mouse.

Also i have the IO APIC Bug that i think it must be some relation between both problems... i've tried modifyng menu.lst introducing apic off and force irqroll but nothing works...

please someone can help me? i really need linux to work in university and i'm loosing my faith in this OS...

my motherboard is a asus p5nsli

thanks

---

### Post by eluminx on 2008-12-06
i am also experiencing this problem.  Here is my situation, hopefully someone can help me because is really frustrating trying to get this thing to work; If i restart the box the mouse works fine for a few minutes (maybe 20-30 min).  If i just use it normally, it will stop responding after afew minutes.  Now if i just turn my computer on and leave it running for a whole day and i come back to use it, again after a few minutes the mouse ceases to move, or register any right or let button clicks.  But if i press the find button on the mouse it works just fine.  I've tried adding some lines to my xorg.conf that deal with the mouse (logitech mx620) but unfortunately nothing works.  It just stops responding after a few minutes.  Any help would be greatly appreciated.

---

### Post by matthew.k.seibert on 2009-06-26
I'm having a similar issue with a Logitech Wireless mouse. I am using Unbuntu 9.04, which I just upgraded to. I'm guessing it's the 64-bit version, but I'm not sure yet. 

Anyway, there was no problem with 8.10, 64-bit. I can click on something, such as a menu or bar with the left clicker, but then it locks the mouse. The only way to unlock the cursor is to right click on various menus and bars until I find one that is recognized. And then I
can use the left clicker again.

I am not an AMD user but this was the only thread I found on the issue. Maybe you folks could pass this along?

Intel Q6700
nVidia 8800
Logitech Wireless Mouse

---

### Post by rathervague on 2009-06-30
Hmm I'm been using Ubuntu 9.04 with a Logitech G7 without any issues, that is until today. Now my mouse has started to freeze intermittently  for a few seconds at a time, then it unfreezes and works as normal. I haven't changed anything since the last reboot, so I have no idea why it would start doing this.

Any ideas more than welcome, maybe its time to get myself a new mouse.

---

### Post by a2z on 2009-07-02
I too had a wireless mouse freeze not long ago. Like right after an update. Just when I was about to start pulling my hair out, I changed the battery;):lolflag:

---

### Post by Craigwell on 2009-08-05
I'm having an odd problem, my system will hang if I remove the dongle for my logitech USB mouse, requiring a hard reboot. 

More info here: 

[https://answers.launchpad.net/ubuntu/+question/78837](https://answers.launchpad.net/ubuntu/+question/78837)

---

