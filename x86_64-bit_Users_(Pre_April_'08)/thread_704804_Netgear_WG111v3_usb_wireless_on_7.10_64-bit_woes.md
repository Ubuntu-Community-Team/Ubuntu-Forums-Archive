---
title: "Netgear WG111v3 usb wireless on 7.10 64-bit woes"
date: 2008-02-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by radtek on 2008-02-22
I had no problems at all installing Netgear WG111v3 usb on the 7.10 32-bit version. On the 64-bit I was unable to install. Drivers were installed but Ndiswrapper -when "modprobe'd" returned nothing. Hardware recognized in lsusb but adapter not present in network manager. 

Is there a 64-bit driver I need to use? Do I need to force Ndiswrapper?

I really liked the snappiness of 64-bit. I see a significant improvement in response in all areas. But I need wireless access so I'm using 32-bit. I want to revert to the better option, so please guys any help or advice?

---

### Post by gianchi on 2008-02-23
Maybe this can help you work it out:

[http://ubuntuforums.org/showthread.php?t=474446](http://ubuntuforums.org/showthread.php?t=474446)

---

### Post by radtek on 2008-02-23
There Is a Vista 64-bit driver for this device. I tried to get it to work.
I'm not sure if Vista drivers work in Ndiswrapper. Help anyone?

---

### Post by gianchi on 2008-02-23
I checked Ndiswrapper site... it doesn't support Vista drivers yet, they're working on it.

---

### Post by dustynus on 2008-05-25
Can anyone verify the chipset on these wg111v3's ?? 
I think it's a: 
RTL8187B

If so on the manufacturer site, they have drivers for it, and there are x64 drivers that might work ? I'll try this out tomorrow and post what I find

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)

:guitar:

---

