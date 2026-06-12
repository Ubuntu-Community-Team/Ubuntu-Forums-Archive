---
title: "Mac Mini Dialup"
date: 2005-12-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by pixeltime on 2005-12-09
Is this possible yet, is there a HOWTO ?

This is a dealbreaker for me, me and my mini's travel all over and we have to have dialup sometimes.

---

### Post by ssam on 2005-12-09
see [http://ubuntuforums.org/showthread.php?t=98070](http://ubuntuforums.org/showthread.php?t=98070)

its very likly that the mini has a software modem. and these can be a real pain in linux.

if you are adventurous you could try and find a driver for it, but even if there is one its likely to be a pain getting it to work. last time i tried to get a software modem driver working (on a non apple laptop), i found that the drive only work with old (2.4) kernels.

unfortunatly the demand for modem drivers is quite low these days, and the best advice it to try and find a hardware one.

sorry

---

### Post by pixeltime on 2005-12-09
Well, I am sure not going to buy a new modem to use dial-up on Ubuntu, has to be a way

---

### Post by ssam on 2005-12-09
[http://qa.mandrivalinux.com/twiki/bin/view/Main/MdkPpcHardware#Mac_Mini_Jan_2005_](http://qa.mandrivalinux.com/twiki/bin/view/Main/MdkPpcHardware#Mac_Mini_Jan_2005_)
says that the modem is a MotorolaSM56, and that the only driver is a binary linux-x86 one from motorola, [http://www.motorola.com/softmodem/driver.htm](http://www.motorola.com/softmodem/driver.htm)

unless motorola publish the source code for the driver (or will compile it for powerpc), then reverse engineering it would be a huge task.

have a read of [http://linmodems.org/](http://linmodems.org/)

do you have another computer? could you use it as an internet gateway?

---

### Post by pixeltime on 2005-12-09
Well, All I have is Mini's and a have more then 2 of them ;) I guess its back to fink, Humm, I wonder if I can use the packages on the Ubuntu CD, that way I have the internet through OSX and can still use the 'goodness' of Ubuntu, no dual-booting either..

Wait, OSX IS unix, they have a driver for the modem ;)

---

### Post by ssam on 2005-12-10
if one of the minis ran mac os x it could be a gateway for the others. you can set it up in the sharing control panel.

trouble is the mac os x driver plugs in to the darwin kernel, which is very different from the linux kernel. someone would have to write a compatability layer. perhaps this is possible but it would be hard.

---

### Post by autocrosser on 2005-12-10
Shoot--I use a Older Zoom 2986L USB modem--cost me $15 + shipping off of eBay--would less that $25 total cost make it a deal-breaker? I found an answer easy enough:smile:

<EDIT> just was looking on eBay--found a "new-in box" for a start bid of $39.95-- [http://cgi.ebay.com/Zoom-V-90-56K-External-USB-Fax-Modem-For-MAC_W0QQitemZ8735781509QQcategoryZ25438QQrdZ1QQcmdZViewItem]("http://cgi.ebay.com/Zoom-V-90-56K-External-USB-Fax-Modem-For-MAC_W0QQitemZ8735781509QQcategoryZ25438QQrdZ1QQcmdZViewItem")

---

### Post by Ptero-4 on 2005-12-10
pixeltime. Doesn't Apple use conexant softmodems? If the mini have one of those, you're pretty much outlook. The conexant drivers are pricey comercial ones and the OSS driver is currently limited to 14.4k

---

### Post by autocrosser on 2005-12-10
****Off-Topic****

BTY--[B]Ptero-4--I REALLY like your  "social" comment--That IS what Windows XP feels like to me!!:smile:
[/B]

---

