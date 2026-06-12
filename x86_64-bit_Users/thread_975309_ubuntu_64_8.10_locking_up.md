---
title: "ubuntu 64 8.10 locking up"
date: 2008-11-08
forum: x86 64-bit Users
---

### Post by pneumonic81 on 2008-11-08
I got my video working for my Ubuntu 64 bit system, however it only stays on for about 2 hours, then crashes. its a hard lock that I cant alt-f2 through or anything else. it simply locks up. any ideas what this might be?

---

### Post by Artemis3 on 2008-11-08
Temperature, check. If nvidia video, use nvclock -i 

lm-sensors for CPU/mobo. The package sensors-applet (or ksensors) is a pretty gui for them.

Also do a memtest booting from the install cd just in case. A weak PSU might also be a reason.

---

### Post by pneumonic81 on 2008-11-08
this was an upgrade and prior to that, I had no issue. I am wondering if there is something happening with this new version of linux.

---

### Post by Sef on 2008-11-09
> this was an upgrade and prior to that, I had no issue. I am wondering if there is something happening with this new version of linux.


A clean install might work if the problem is not hardware related.

---

### Post by Sockerdrickan on 2008-11-09
No it's a known problem it happens to me too when a lot of flash elements are rendered. And I have a good PSU/airflow so it has to be flashplayer interfering with Ubuntu somehow.

---

### Post by teddks on 2008-11-09
Does your capslock key flash, or does the system just go dead?

I've found that some rogue X apps can hijack input, rendering alt-f2 and even ctrl-alt-backspace useless. The fix is to find out which app it is, then log in through SSH and kill the app.

---

