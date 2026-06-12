---
title: "How to set up dual boot (Linux &amp; Windows)?"
date: 2008-07-21
forum: x86 64-bit Users
---

### Post by Prohib on 2008-07-21
I have search, but I didn't find nothing, so can you tell me how to set up two OS (Windows & Linux) to work properly.

Dual boot (Linux & Windows). Now I've installed Linux and I need to install Windows for my work (graphic).

How to set up dual boot?
Thanks for the answers!

---

### Post by anees_a on 2008-07-21
follow this and ur up and runnining
[http://ubuntuforums.org/showthread.php?t=779934&highlight=vmware%20hardy]("http://ubuntuforums.org/showthread.php?t=779934&highlight=vmware%20hardy")

:lolflag::guitar:

---

### Post by Prohib on 2008-07-21
I read this, but this is not what I need, I need separate systems, Linux & Windows, and when I starts my computer that I can chose what system will starts?

Is it possible?
If isn't I will do that way!

---

### Post by DerHesse on 2008-07-21
Do yourself a favour, install Microsoft first, then linux. You will have a working dual-boot system with no problems.    If you install Windows after linux, your linux will not start anymore. To get linux working again after windows install follow [http://articles.techrepublic.com.com/5100-22_11-5109523.html](http://articles.techrepublic.com.com/5100-22_11-5109523.html) first and copy your existing bootsector to a file on an usb-stick and use it later with the nt-bootloader.

---

### Post by Sealbhach on 2008-07-21
Of course you can set up a dual boot. There's a nice tutorial here, but it's really easy anyway.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

However, you need to install Windows first, then Ubuntu. The reason is that Windows cannot see that Ubuntu is another operating system and will not be able to create an option for it in the boot menu.

On the other hand, the Ubuntu installation handles all of this with ease.


.

---

