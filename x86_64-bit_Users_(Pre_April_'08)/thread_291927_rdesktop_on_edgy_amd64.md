---
title: "rdesktop on edgy amd64"
date: 2006-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by ReddoC on 2006-11-03
Hello !

I used every day rdesktop (tsclient) on dapper amd64. a few days ago, I install a new edgy amd64. now the display of rdesktop is buggy and very slow. I use the nvidia driver. When i use the nv driver with no acceleration, the display is correct. 

When a was on dapper i used the nvidia driver too, and i had no problem.

any idea ?

---

### Post by mishranurag on 2006-11-03
Yeah the tsclient and rdesktop on edgy is extremely poor. I had to move back to dapper because of that. I use nvidia as well.

Anurag

---

### Post by ReddoC on 2006-11-03
I have tried on a 32bit system, and there is the same problem.

It's strange, because the rdesktop version seem to be the same between dapper and edgy ?!

---

### Post by mishranurag on 2006-11-06
Trying to make big applications and in an aim to achieve big goals, UBUNTU is screwing up the small but more important applications!

---

### Post by FluffyElmo on 2006-11-07
Try the Nvidia beta driver. I had various display issues with the official 
driver release and the beta seems to have cleared them up.

---

### Post by dad311 on 2006-11-08
I use rdesktop daily and had several issues with it until I upgrade the rdestop 1.5.  I only had these rdesktop performance issues on the machine that have a Nvidia video card. 
 
Do a google search for the two files listed below and upgrade to rdestop 1.5.

libssl0.9.8_0.9.8c-3_i386.deb
rdesktop_1.5.0-1_i386.deb

---

### Post by dad311 on 2006-11-08
> **dad311 said:**
> I use rdesktop daily and had several issues with it until I upgrade the rdestop 1.5.  I only had these rdesktop performance issues on the machine that have a Nvidia video card. 
 
Do a google search for the two files listed below and upgrade to rdestop 1.5.

libssl0.9.8_0.9.8c-3_i386.deb
rdesktop_1.5.0-1_i386.deb

Also if your using amd 64 make sure to use the 64 bit versions of the libssl and rdesktop.

---

### Post by schmandr on 2006-11-17
My rdesktop connection on Kubuntu Edgy was very slow too. I also use the nv driver. I just removed the 1.4.1 version of rdesktop that was installed and installed the 1.5.0 version (source) from [www.rdesktop.org](www.rdesktop.org). And it works fine.

Andreas

---

