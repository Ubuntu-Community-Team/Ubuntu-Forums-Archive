---
title: "Black screen after boot up."
date: 2007-09-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by krazy1912 on 2007-09-06
This is my laptop [http://www.bestbuy.com/site/olspage.jsp?skuId=8397745&st=a205+s4747&type=product&id=1179877029693](http://www.bestbuy.com/site/olspage.jsp?skuId=8397745&st=a205+s4747&type=product&id=1179877029693)

I've installed Ubuntu 7.04 64_bit.

My screen goes black after boot up with a flashing caps lock button.

I first tried this site [http://my-geek-side.blogspot.com/2007/08/ubuntu-on-toshiba-a215-s4747.html](http://my-geek-side.blogspot.com/2007/08/ubuntu-on-toshiba-a215-s4747.html)

Then I tried this [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

Then i tried this [http://es.geocities.com/vice_yo/Ubuntu_on_A215-S4747.html](http://es.geocities.com/vice_yo/Ubuntu_on_A215-S4747.html)

I'm still getting a black screen after boot up.

---

### Post by krazy1912 on 2007-09-07
bump

---

### Post by John.Michael.Kane on 2007-09-07
During the initial install where there any issues errors?

You can try rebooting the machine with the ubuntu cd/dvd in the drive. At the boot/install prompt (make sure to hit F6 first), and add the command below to the boot parameter.
```
nosplash noapic nolapic
```  
note: do not remove any of the commands already shown in the boot line.Just add the above commands to it. This should allow the machine to install, and boot as normal.

The other option is to try booting the machine into rescue mode.

1) Boot-up computer

2) press Esc to enter the GRUB menu before it proceeds on.

3) Select Ubuntu, kernel "your kernel number here" (recovery mode)

4) Press Enter to boot

After it's done booting provided the caps lock does not end up flashing.you should end at a command prompt that says root@(something)

You can then try editing your xorg so that it uses Vesa. 
or running ```
dpkg-reconfigure xserver-xorg
```

Hope this helps.

---

### Post by krazy1912 on 2007-09-07
No errors.

I've tried dpkg-reconfigure xserver-xorg before, but it didn't work.
Might as well try again though.

---

