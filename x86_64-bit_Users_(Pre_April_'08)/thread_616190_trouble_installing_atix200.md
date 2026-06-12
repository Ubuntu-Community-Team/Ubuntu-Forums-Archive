---
title: "trouble installing atix200"
date: 2007-11-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by raman_uppal86 on 2007-11-17
plz help me......i am having hard time configuring my graphics........ i have onboard ati 200 graphics card. i installed the drivers from the ati website. but i am not able to turn on the gvisual effects, it says" composite section is not availaible" ......can u plz guide what to do.............thx

---

### Post by Yellow Pasque on 2007-11-18
> **raman_uppal86 said:**
> plz help me......i am having hard time configuring my graphics........ i have onboard ati 200 graphics card. i installed the drivers from the ati website. but i am not able to turn on the gvisual effects, it says" composite section is not availaible" ......can u plz guide what to do.............thx

You need to be using the latest driver 8.42.3 and have compositing enabled in your /etc/X11/xorg.conf file

---

### Post by raman_uppal86 on 2007-11-19
i m using latest drivers(downloaded from ati.com) and also my composite section is enabled

---

### Post by Yellow Pasque on 2007-11-19
Ok then, see if you can post your xorg.conf

Also, make sure you have the Compiz package installed and the fglrx driver in the WHITELISTED string in usr/bin/compiz. You may also need to remove your card (rs480) from the blacklisted section. Overall, I wouldn't be too optimistic about getting the eye candy to run, and if you do, don't expect it to run at a decent/usable speed. My X1200 integrated didn't do too well with the effects and I have a 2.5GHz X2 and 2GB of DDR2-667 to go along with it.

Good luck though.

---

### Post by dralokyn on 2007-11-19
that worked for me, thanks! for the record, i'm using the radeon xpress 1150, running the driver labelled for the 1200 from the ati website.

---

