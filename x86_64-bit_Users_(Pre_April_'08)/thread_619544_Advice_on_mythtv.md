---
title: "Advice on mythtv"
date: 2007-11-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by c-m on 2007-11-21
I am about to install Mythtv as Kaffeine doesn't seem to work properly with my Nexus-s satellite card. 


Is installing mythtv as simple as opening up synaptic and selecting the myth package?

thanks

---

### Post by newlinux on 2007-11-21
Installing, maybe, but configuring, definitely not...

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by Beaucephus on 2007-11-21
Even with step by step guides, MythTV is still a pain.  A single machine backend/frontend is not that bad but connecting other machines to a backend involves some mysql voodoo.  I still have no idea what I did to make it work.

---

### Post by newlinux on 2007-11-21
> **Beaucephus said:**
> Even with step by step guides, MythTV is still a pain.  A single machine backend/frontend is not that bad but connecting other machines to a backend involves some mysql voodoo.  I still have no idea what I did to make it work.

Didn't involve any voodoo for me, just setting the right IP address and mysql passwords. I think each person's experience varies. It is a pain for some, and pretty straightforward for others, depending on what you are trying to do, and your hardware. 

Playback on one of my Mythmachines was a pain while another one was straight forward. There are just a lot of variables...

---

### Post by c-m on 2007-11-23
I have installed myth oka dn setup was straightforward but my card isn't on the list of devices.

I am using a thecnotrend premium or nexus-s - the card is well known to work in linux and ubuntu in particular

---

### Post by newlinux on 2007-11-23
It usually won't list your specific card. You just need to know what tyupe of card it is (DVB, MPEG 2 encoder, V4L analog, etc.). I don't know that card so I'm not sure which one you would specify. If it's a digital tuning card, chances are you want DVB.

---

### Post by c-m on 2007-11-23
I selected dvb Dtv, and it finds the card ok and has good signal strength and quality but it won't scan for channels. 

it asks for parameters, surely i don't have to manually enter every single frequnecy, symbol rate etc.. for over 500 channels

---

