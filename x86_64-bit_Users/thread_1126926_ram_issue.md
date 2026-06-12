---
title: "ram issue"
date: 2009-04-15
forum: x86 64-bit Users
---

### Post by tony12 on 2009-04-15
Hi!

I'm running ubuntu 9.04 64 bit. I have installed 2x2GB or corsair ram but its only recognising or showing 3.1GB. Why is that?

Antoni

---

### Post by Existentialist on 2009-04-16
Sounds like you may have installed the 32bit version accidentally.  From the terminal, type:

uname -m

x86_64 would indicate running the 64bit version.

---

### Post by tony12 on 2009-04-16
Hi!

I have typed in terminal uname -m and it came up with x86_64. So, it is defenetly 64 bit version. Please help.

Thank you

---

### Post by amauk on 2009-04-16
4Gb of ram should show up as approx 3.8Gb
(see 1000 / 1024 differences in calculating size)
so, you're missing over 500Mb

Do you have integrated graphics?
this could be 512Mb of Ram reserved for an integrated graphics chip

---

### Post by tony12 on 2009-04-16
Yes I'm missing over 500MB. I got a separate graphics card,it is Gigabyte 7600 GT 256 mb. ????????

---

### Post by amauk on 2009-04-16
even if you have a separate card, the BIOS still might be reserving Ram

Do you have integrated graphics on your motherboard (even if you're not using it)?

---

### Post by sanderj on 2009-04-16
> **tony12 said:**
> Hi!

I'm running ubuntu 9.04 64 bit. I have installed 2x2GB or corsair ram but its only recognising or showing 3.1GB. Why is that?

Antoni

This is a FAQ. See the first hits on Google for the solution using this link: [google-link for dmesg uname lm on this forum]("http://www.google.com.vn/search?q=dmesg+uname+grep+lm+site%3Aubuntuforums.org")


HTH

---

