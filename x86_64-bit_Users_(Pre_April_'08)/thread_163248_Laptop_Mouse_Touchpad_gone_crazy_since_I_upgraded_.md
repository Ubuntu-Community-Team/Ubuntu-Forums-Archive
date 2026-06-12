---
title: "Laptop Mouse Touchpad gone crazy since I upgraded to Dapper"
date: 2006-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by MarkHn on 2006-04-20
My mouse touchpad has gone crazy since i upgraded to Dapper. I can't use it any more. With the slightest touch, it opens applications, drags icons around the screen. If i click on a terminal window, it is likely to paste in anything to the command prompt, including random text from any other open windows or firefox browsers. It works fine in windows XP, so I know the touchpad is ok.

---

### Post by MarcDM on 2006-04-21
I have the very same problem. And my mouse still works fine in Breezy on another partition. I'm here looking for a solution.

---

### Post by hoomanb on 2006-04-27
I have the same problem, has anyone found a solution yet? I was Googling for it all day yesterday. ](*,) 

Changing the touchpad settings in xorg.conf didn't help and later I found out that (accourding to the xorg log), the synaptics module complains that no Synaptics device is detected and the touchpad is controlled by some other module. Weired. :-k 

This really sux considering besides the touchpad Dapper Beta has been my most smooth upgrade ever (even suspend, SD card reader work fine) but with that crazy touchpad my laptop is unusable for now.

---

### Post by MarkHn on 2006-04-28
It usually works fine for the minute or so after a reboot. Then by just touching the touchpad it has the same effect as double clicking on it, and pasteing. Sometimes it keeps changeing the focus of open windows, and you cant access the window you want. Other times it wont release a window, It drags it around the screen as you move the courser, like as if you held down the mouse button and were intentionally moving the window around the screen.

---

### Post by roba on 2006-05-01
I had this problem with 64bit Dapper on my Acer Aspire 1522WLMi laptop. To fix it I upgraded by hand to the newest version of the synaptics driver, available from [http://web.telia.com/~u89404340/touchpad/](http://web.telia.com/~u89404340/touchpad/). I have submitted a bug report here: [https://launchpad.net/distros/ubuntu/+source/xserver-xorg-input-synaptics/+bug/32400](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-input-synaptics/+bug/32400)

---

### Post by MarkHn on 2006-05-31
The touchpad mouse was working fine for the last few weeks. But now its acting funny again.
Is it just me or is there a problem with the driver again?

---

