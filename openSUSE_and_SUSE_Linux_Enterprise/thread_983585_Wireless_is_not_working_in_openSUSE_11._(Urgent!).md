---
title: "Wireless is not working in openSUSE 11. (Urgent!)"
date: 2008-11-15
forum: openSUSE and SUSE Linux Enterprise
---

### Post by kaldor on 2008-11-15
My girlfriend had too many problems with Vista, so she burned off openSUSE 11 and installed it. Everything went smoothly, but wireless will not work on her laptop. Her wireless card is "BCM94311MCG wlan mini-PCI". 

What can we do? She loves openSUSE and does not want to reinstall Vista.

---

### Post by pytheas22 on 2008-11-16
I haven't used SUSE in several years so I'm not sure which wireless modules it includes by default these days.  But I do know that, in Ubuntu at least, this card works using either ndiswrapper or the b43 driver.  b43 should be built into modern Linux kernels (at least 2.6.24 and up, I think).  You can also download and compile the Linux wireless stack from linuxwireless.org; it includes the b43 driver.

Note that this card won't work with bcm43xx, an older driver for Broadcom wireless cards (but not the 94311) that was shipped with earlier kernels, but which has been replaced by b43.

Hope it helps.  If your girlfriend were using Ubuntu, I could tell you precisely what to do!

---

### Post by derhundchen on 2008-12-01
check [this]("http://www.blakeanthonyjohnson.com/?p=125") to help you configure your broadcom wireless card, if you need further assistance please head over [here]("http://forums.opensuse.org/")

---

