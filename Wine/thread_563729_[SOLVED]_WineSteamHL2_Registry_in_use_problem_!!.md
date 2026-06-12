---
title: "[SOLVED] Wine/Steam/HL2 Registry in use problem !!"
date: 2007-09-30
forum: Wine
---

### Post by reset3x on 2007-09-30
I'm using Wine 09.33 on Xubuntu 7.04. System specs are: AMD Athlon64 3200+, 1 GB RAM, GeForce 8600GT w/newest nVidia drivers... 

Wine works great with all of my apps except one.

I can't get around that Registry in use error when I try to play STEAM games... I've hit every forum, The Wine AppDB and googled my behind off and tried everything I could find...upgraded to 09.45(which broke everything),  wineboot, wineprefixcreate, killall wineserver, delete client registry blob, open & close STEAM, game cache integrity.... rebooting.... 

Only HL2 works.. Episode 1, Lost Coast, CS:S and HL: Source peter out...  Anyone have some info on how to fix this? I'm quickly going bald!!! :confused:

Thanks in advance.....

---

### Post by Sockerdrickan on 2007-09-30
Just re run it until it works

---

### Post by Ant1jr on 2007-09-30
validate game cache

---

### Post by reset3x on 2007-09-30
> **Tux0r said:**
> Just re run it until it works

Tried this ... after a few attempts STEAM crashes...

> **Ant1jr said:**
> validate game cache

Tried this too as stated above... :)

Ive also tried purging Wine and my .wine dir and re-installing STEAM and my HL2 games... ](*,)

---

### Post by reset3x on 2007-09-30
This was remedied by enabling Fiesty Backports in Software Sources.. Upgrading Wine from 0.9.39 to 0.9.41... Problems disappeared!!! =D>

---

