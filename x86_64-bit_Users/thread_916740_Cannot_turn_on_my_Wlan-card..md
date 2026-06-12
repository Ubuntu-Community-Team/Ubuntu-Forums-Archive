---
title: "Cannot turn on my Wlan-card."
date: 2008-09-11
forum: x86 64-bit Users
---

### Post by del_diablo on 2008-09-11
Sitting here with my laptop Amila Pa 3553 and what my buildt in WLAN card to work.
Checked the buildt in tutorials and tryed it all before i gave up and bought a USB thingy to connect the the net.
But i still want it to work! This PC was buildt for Vista and it the network card needed to be turned on by pressing the "Fn"-key + "F1" that was located betwhen left "Ctrl" and the "Win"-key. This is however not possible to do, and i do not know any commands to manually turn it on.

So please help me, please remember that im a complete nub at Ubuntu....

---

### Post by phidia on 2008-09-11
What card do you have? In a terminal enter "lspci -v" also sometimes "lshw -C network" provides the card more reliably. 
Are you saying that there is no other on/off switch, other than the function keys, for the card? 
There is a laptops in ubuntu page [here]("https://wiki.ubuntu.com/LaptopTestingTeam") I don't see or recognize the model/make you listed though.

---

### Post by pytheas22 on 2008-09-11
Please post the output of:
```

lsusb
lspci -nn
```

so that we can look up your card's chipset and find a driver.

---

