---
title: "Sleep won't Work on iBook"
date: 2006-02-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by ubuntuforme123 on 2006-02-11
When I close the lid on my iBook and open back up it gives me some text (to be posted if needed) and won't return to ubuntu. Any suggestions?

---

### Post by sonofcolin on 2006-02-11
[QUOTE=ubuntuforme123]When I close the lid on my iBook and open back up it gives me some text (to be posted if needed) and won't return to ubuntu. Any suggestions?[/QUOTE]

Which iBook model? This is 'normal' behaviour on G3 500 ibook - in other words sleep doesn't work with this model and Breezy.

---

### Post by ubuntuforme123 on 2006-02-11
A iBook G3 2usb 1 firewire 800 MHZ, I have had practice with lots of types of linux and this is a weird problem!

     -Andrew

---

### Post by sikity on 2006-02-12
I have a G3 500 ibook that was having similar issues I found a thread in the kubuntu area [http://ubuntuforums.org/showthread.php?t=122432](http://ubuntuforums.org/showthread.php?t=122432).  A patched kernal was linked to from there that fixed the problem for me.

---

### Post by scottlpatterson on 2006-02-14
The sleep issue has been resolved with kernel 2.6.15 in Dapper Flight 3:

[https://wiki.ubuntu.com/LaptopTestingTeam/Apple_iBookG3_12in_600Mhz]("https://wiki.ubuntu.com/LaptopTestingTeam/Apple_iBookG3_12in_600Mhz")

---

### Post by will.first on 2006-02-14
I have an iBook G3 500 and started booting with the Dapper Flight 3 2.6.15 kernel a few weeks ago. It fixed the sleep issue, automounting hotplug devices, and enabled the harddisk activity LED which also wasn't working using the Ubuntu 2.6.12.x kernel.

Give it a try.

[QUOTE=scottlpatterson]The sleep issue has been resolved with kernel 2.6.15 in Dapper Flight 3:

[https://wiki.ubuntu.com/LaptopTestingTeam/Apple_iBookG3_12in_600Mhz]("https://wiki.ubuntu.com/LaptopTestingTeam/Apple_iBookG3_12in_600Mhz")[/QUOTE]

---

### Post by jdp on 2006-02-14
I didn't think iBooks had HD activity LEDs.  Is there a hack they are using to make the sleep LED behave like one?

---

### Post by sonofcolin on 2006-02-15
[QUOTE=will.first]I have an iBook G3 500 and started booting with the Dapper Flight 3 2.6.15 kernel a few weeks ago. It fixed the sleep issue, automounting hotplug devices, and enabled the harddisk activity LED which also wasn't working using the Ubuntu 2.6.12.x kernel.

Give it a try.[/QUOTE]

I just installed it. Works like a charm. You have to hack the xorg.conf to get the video working, but after that everything works very nicely.

The HD indicator is the blinking sleep light, nothing more.

3D works as well and video performance is good. The system seems much more responsive.

---

### Post by ubuntuforme123 on 2006-02-17
Thank you so much. I will try it later as I am busy for the next few days! Once again, thanks :)

---

### Post by will.first on 2006-02-17
[QUOTE=jdp]I didn't think iBooks had HD activity LEDs.  Is there a hack they are using to make the sleep LED behave like one?[/QUOTE]

Yes, the sleep LED (next to the latch button) behaves like one using the 2.6.15  kernel on my iBook.  

It's a nice feature to have working, especially when disk activity on an older (slower) notebook is sometimes the only indicator that something's still going on and there hasn't been a program crash.

---

