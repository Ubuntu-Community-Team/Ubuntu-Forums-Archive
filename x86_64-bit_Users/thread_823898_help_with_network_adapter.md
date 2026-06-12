---
title: "help with network adapter"
date: 2008-06-09
forum: x86 64-bit Users
---

### Post by boings on 2008-06-09
hey I'm a linux/open source noob. My old laptop used to run windows and ran very slow. so i talked to my friend and he uses linux and recommended to start running linux. I installed it but am having network problems. I have a compaq presario v2000 [http://www.tux.org/~peterw/v2000/](http://www.tux.org/~peterw/v2000/) . Supposedly it should run pretty well according to the Laptop pages, but my network adapter cannot pick up any signals. I have the driver installed for it but when i open up the networks it is shaded. I have tried to search up the problem around different places but the problem persists. When i looked at the support manuals on ubuntu's support wiki it always describes the problem in like an older version of ubuntu! I would appreciate any  help on the matter.

thanks,


-noob, boings :D

---

### Post by ptn107 on 2008-06-09
I have a v2000z which is pretty much the same thing.  Extract the contents of this attachment to your /lib/firmware folder.  You may have to restart your computer.

---

### Post by boings on 2008-06-15
well that worked great at my friends house, but once i got home it isn't able to connect to the wireless. I know i have the correct password and have entered the WEP key many times too...does anyone know what may be wrong?


I just type the password in, wait while it tries to connect and it comes back to the same password entering box.

---

### Post by PacketCollision on 2008-06-16
> **boings said:**
> well that worked great at my friends house, but once i got home it isn't able to connect to the wireless. I know i have the correct password and have entered the WEP key many times too...does anyone know what may be wrong?


I just type the password in, wait while it tries to connect and it comes back to the same password entering box.

Make sure if you're entering a hex or decimal wep key (string of numbers or numbers + A through F) that you choose that option on the password screen.  Also, sometimes if you're out of range it will pop the box up again after it fails to connect.

I'm assuming you're using WEP not WPA, right?

---

