---
title: "What 64bit distro sould I instill for this computer?"
date: 2006-12-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by kurisutofuaa on 2006-12-01
Here are the specs. of my computer:
[LINK to manufacture of my computer.]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00485646&lc=en&cc=us&dlc=en&product=1127366&lang=en")

I put 2GB of Corsair Ram in and I also put in a ATI RADEON X800 XL 256MB video card. 

So What should I install on it Dapper64 or Edey64?

---

### Post by tzulberti on 2006-12-01
I found Drapper much more stable, so I recommend it... Nevertheless, newer things are included in Edgy...

---

### Post by xopher on 2006-12-01
I did upgrade to edgy as soon as I dared - in the middle of the development process. Actually yeah, there's not a lot new features for the normal user. I need the newer libraries etc. But all this really makes it more unstable than Dapper. For me Edgy works like a charm, solid as a rock.

Anyway, Id recommend Edgy. (Just to make tzulberti mad ;))

---

### Post by kurisutofuaa on 2006-12-01
Oaky I have tryed to install both Dapper64 and Edgy64 but I get same error when loading from the live cd. 
The error that am geting: X server Fatal server error: No screens found. 

Now that is a vary stuid error. Now am going to need some help with this.

---

### Post by tzulberti on 2006-12-02
> **kurisutofuaa said:**
> Oaky I have tryed to install both Dapper64 and Edgy64 but I get same error when loading from the live cd. 
The error that am geting: X server Fatal server error: No screens found. 

Now that is a vary stuid error. Now am going to need some help with this.

Which is your video card?

Once X fails to load, from console try:
sudo dpkg-reconfigure xserver-xorg

then:
sudo /etc/init.d/gdm restart

---

### Post by donatell0 on 2006-12-02
And to use a console you probably need the alternate install cd.

---

### Post by Kilz on 2006-12-02
> **kurisutofuaa said:**
> Here are the specs. of my computer:
[LINK to manufacture of my computer.]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00485646&lc=en&cc=us&dlc=en&product=1127366&lang=en")

I put 2GB of Corsair Ram in and I also put in a ATI RADEON X800 XL 256MB video card. 

So What should I install on it Dapper64 or Edey64?


Dapper is nice and stable, and it has 3 years of support. You might alos want to try OpenSuSE 10.2 when it is released Dec 7th. I tried the RC1 and its multiarch makes it one of the best 64bit distro's I have ever tried.

---

