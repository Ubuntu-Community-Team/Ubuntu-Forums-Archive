---
title: "error message"
date: 2007-06-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Trew on 2007-06-12
Hello,

Can anybody tell me something about the following error message? What is it, and what should i do about it.

[2154.082483] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed

Thanks
 
Trew

---

### Post by capecove on 2007-06-12
I found this information for you, it may be of assistance...

[https://answers.launchpad.net/ubuntu/+question/329](https://answers.launchpad.net/ubuntu/+question/329)

> I had the same error: 'bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.'

The broadcom driver needs to load some firmware before the device will work. Fortunately Dapper has a script to get this firmware for you. This worked for me:

sudo aptitude install bcm43xx-fwcutter
sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh

Of course, this is specifically for Dapper and I don't know what you are trying to run. It may be still applicable (or similar solutions may be) if you are working with anything else.

Good luck, let us know how it all works out

---

### Post by Trew on 2007-06-12
thanks,

so its something for the wireless network card. Great.....

and it worked!!

dont get the error message any more.

thanks,

trew

---

### Post by capecove on 2007-06-12
Excellent, glad it helped! :)

---

