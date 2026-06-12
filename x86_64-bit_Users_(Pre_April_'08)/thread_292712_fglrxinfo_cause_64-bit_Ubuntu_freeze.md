---
title: "fglrxinfo cause 64-bit Ubuntu freeze"
date: 2006-11-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by ginyip on 2006-11-04
Hello, thx for stopping by. Recently, I install 64-bit dapper. After a fresh install. I also did all the official upgrade as well. Then I install the new 8.30 ATI driver for my X1600 pro 512mb. I have keeping track of the installation process. Everything is fine.
[The tutorial]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") I have followed to do.
However, once I rebooted into X. I tried to check if the new driver works with "fglrxinfo". It prints nothing but freeze my computer. I need to manually restart my computer afterward.

I have been having this problem since using not only this 8.30 new driver as well as the Ubuntu official driver, and also 8.28, 8.29. The only way I could use fglrx is using a 32-bit Ubuntu. But what's the point, my pc is a 64-bit. I really need some help to get my 64-bit pc & Ubuntu working.

---

### Post by driadan on 2006-11-04
I had the same problem, but this morning i could get my 3D acceleration back. I went into the bios and disabled the sideport option of my graphic card (leaving only UMA).

BTW my card is an ATI Xpress 200M on a laptop, if you are not using a laptop it may not work for you, since this has to do with video and shared ram between the graphic card and the laptop.

---

### Post by ginyip on 2006-11-04
I do not know what's happen. I have surf the net over and over again. However, there is no luck.

I also got a feeling of if that's cause by my bios setting as well. Since my X1600 pro is a 512mb card. However, my bios setting can only set to 256mb max. I don't know.
On the other hand, I have got this work on a 32-bit dapper. Why 64-bit does not work. :-k 

Thanks for your reply thou :mrgreen: That's good to hear that you got that work. =)

---

### Post by xstaticxgpx on 2006-11-04
If you can, try upgrading to edgy and using [this tutorial]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide"). If you can't, try doing Method 2 where you manually extract ubuntu packages from the installer and then install and compile them. All the instructions are on the page.

---

