---
title: "problem installing wine"
date: 2012-07-02
forum: Wine
---

### Post by emmathompson on 2012-07-02
Good morning, i tried installing wine in ubuntu 11.10, but got this error:

[FONT=Courier New][B]/var/cache/apt/archives/ttf-mscorefonts-installer_3.ubuntu4_all.debman-db
[/B][/FONT]
I was actually installing through the s\ware centre before I switched to terminal, it just hangs. pls help

---

### Post by sanderj on 2012-07-02
> **emmathompson said:**
> Good morning, i tried installing wine in ubuntu 11.10, but got this error:

[FONT=Courier New][B]/var/cache/apt/archives/ttf-mscorefonts-installer_3.ubuntu4_all.debman-db
[/B][/FONT]
I was actually installing through the s\ware centre before I switched to terminal, it just hangs. pls help


That is not an error message.

Just try again:

```
sudo apt-get install wine

```

HTH

---

### Post by Elfy on 2012-07-02
*Thread moved to **Wine**.*

---

### Post by ergo-proxy on 2012-07-03
Before installing wine make sure you have added repositroy:
 
*sudo add-apt-repository ppa:ubuntu-wine/ppa*
*sudo apt-get update*
*sudo apt-get install wine*

---

### Post by emmathompson on 2012-08-23
thanks

---

