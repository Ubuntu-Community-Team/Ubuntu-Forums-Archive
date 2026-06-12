---
title: "What is wrong ? My video ?"
date: 2009-01-15
forum: x86 64-bit Users
---

### Post by Noctaa on 2009-01-15
Hi everybody,

I bought a new laptop last week and I'm trying to install Linux but I couldn't.

I love Ubuntu but I don't know why I can't install it.

First, I tried with Ubuntu 8.10 64-bits and I could run the LiveCD but couldn't install it because I got an error about some serial i/q, I don't know exactly. I tried the LiveCD and worked fine but when I tried to install Ubuntu from it (LiveCD) my hdd didn't appear.

Second, I tried with Kubuntu 8.10 64-bits but after booting, I got this (Really weired)

[IMG]http://i39.tinypic.com/2qvsj13.png[/IMG]

[IMG]http://i41.tinypic.com/vcx5zb.png[/IMG]

Finally, I tried with WiFiSlax and I got the same that with Kubuntu and with Backtrack the only way to use it was by using the "VGSA KDE" option, but I could not install it either.

So, if anyone knows a possible solution, please tell me.

Sorry if my english is not the best, it's not really my natural language.

I have a Intel T2390 (Dual Core 1,86 GHz), 4 GB RAM (Dual Channel) and 160 GB HDD (SATA). And I forgot, my video is a SiS 3 Mirage, chipset SiS 672.

---

### Post by timcredible on 2009-01-15
looks like you'll need to install in safe graphics mode, then install the correct video driver.

---

### Post by Noctaa on 2009-01-15
Thanks for your answer but what's the exactly command for that ? Because the only options I have is install, livecd, memory test and a few more, it doesn't say anything about safe graphics mode.

Thanks again.

---

### Post by Yellow Pasque on 2009-01-15
Add **xdriver=vesa** to the extra boot options.

---

### Post by Noctaa on 2009-01-15
Thanks, I'll now try that command.

This is what I'm talking, take a look. I booted from LiveCD and...:

[IMG]http://i43.tinypic.com/1onkfl.png[/IMG]

  Empty!

EDIT: Temujin, could you please tell me how would the exactly commnad be to install Ubuntu from terminal or text-mode ? Thanks!

I tried "sudo  apt-get install ubuntu-desktop xdriver=vesa but couldn't. Sorry, I'm a newbie

Welll, I tried the safe graphic mode to install and I got this, that is the same that I get from Ubuntu (This shot was with Kubuntu):

[IMG]http://i41.tinypic.com/wakpli.png[/IMG]

[IMG]http://i41.tinypic.com/2zeaxky.png[/IMG]

[IMG]http://i41.tinypic.com/b4dzm9.png[/IMG]

I will now try with Ubuntu 32-bits. The last 3 images are of Kubuntu 64-bits.

---

### Post by Kilz on 2009-01-15
The error you see is the result of a bad burn or bad image to start with. Its also possible that the cd drive is bad. I recently had that issue at the school my daughter goes to.

1. Did you checck the md5sum of the image you downloaded?
2. Did you burn the image at a slower than max speed?

---

### Post by Noctaa on 2009-01-15
> **Kilz said:**
> The error you see is the result of a bad burn or bad image to start with. Its also possible that the cd drive is bad. I recently had that issue at the school my daughter goes to.

1. Did you checck the md5sum of the image you downloaded?
2. Did you burn the image at a slower than max speed?

Sweet! I'll try now with a blank CD and burn it at 40x instead of 52x. I was using a CD-RW that it's not new and that besides I burned it at top speed, 4x.

Thanks for you answer!

---

### Post by Kilz on 2009-01-15
> **Noctaa said:**
> Sweet! I'll try now with a blank CD and burn it at 40x instead of 52x. I was using a CD-RW that it's not new and that besides I burned it at top speed, 4x.

Thanks for you answer!

I would do it at 24x to be safe. Make sure to run the cd check from the install menu.

---

### Post by Noctaa on 2009-01-15
I burned Kubuntu 64-bits at 24x and still got nothing. I'm gonna try with Ubuntu 32-bits now.

---

### Post by cariboo on 2009-01-15
When burning the LiveCD image you should burn at the lowest speed possible, I get the same error burning at 12X, lately I've burned the image at 4X and don't get the error.

Jim

---

### Post by Noctaa on 2009-01-15
The last CD I burned, that was Ubuntu 32-bits, was at 4x because I wanted to make sure that was all right. Burning process took almost 20 minutes!!!

I still have the same problem :(

[IMG]http://i39.tinypic.com/2jfbr4p.png[/IMG]

[IMG]http://i40.tinypic.com/2llfvyt.png[/IMG]

[IMG]http://i41.tinypic.com/9gfq4i.png[/IMG]

I tried the Inside-Windows-instalation from the CD (And from WIndows) and in the 99,99% of the step "Create image", it says that the disk is busy and failed :/

---

### Post by Noctaa on 2009-01-15
I mounted the ISO image with Daemon Tools in Windows and then made the inside-Windows-installer. It worked perfectly thanks God, but how can I now definitely remove Windows from my hdd ? I mean, I can format the NTFS partition and add the space to the ext3 one but will it generate any problem at the boot time with GRUB ?

Thanks

EDIT: I also have problemas with my Realtek 8187b wireless card. Ubuntu detects it and connects to my wireless network but internet doesn't work, even my router webpage in the network doesn't work. God sake! I feel like being tested or something like that.

---

