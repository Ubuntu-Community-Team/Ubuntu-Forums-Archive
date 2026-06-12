---
title: "Marvel LAN settings lost after reboot in 8.04 and 8.10"
date: 2008-12-23
forum: x86 64-bit Users
---

### Post by TheAlteredState on 2008-12-23
Right, so I have an [ASUS M2N32-SLI Deluxe Wireless]("http://www.asus.com/products.aspx?modelmenu=2&model=1163&l1=3&l2=101&l3=0&l4=0") mobo what has 2x onboard gigabit LAN cards.

Now every time I enter static IP information via the GUI, the settings are lost after reboot? Tis quite annoying. Everything then gets reset to DHCP :confused::confused::confused:

---

### Post by cariboo on 2008-12-23
I removed dhcp3-client to get around the problem of my static ip address disappearing after a reboot. to do this in a Applications-->Accessories-->Terminal type:

```
sudo apt-get purge dhcp3-client
```

Jim

---

### Post by TheAlteredState on 2008-12-24
Hmm, thanks. That seems to be working :-)

Silly that it does that though...

---

