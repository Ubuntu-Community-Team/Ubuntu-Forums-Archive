---
title: "New base unit on way, 64bit iso burnt are there any pitfalls to watch out for."
date: 2008-04-24
forum: x86 64-bit Users
---

### Post by philinux on 2008-04-24
This sticky from the archived forum seems a bit out of date.
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

Any help appreciated. Going to run the live cd on the new base unit and see what gives.

Its spec is

asus m3a mb
athlon 64 5200+
nvidia gforce 8600 GT
2 gig mem
on board sound
on board nic atheros I think

---

### Post by lazyart on 2008-04-24
I installed Feisty as my first 64 bit experience.  Read the directions for installing Flash, which seems to be the biggest hurdle.  I'm happy with it.

---

### Post by John.Michael.Kane on 2008-04-24
> **philinux said:**
> This sticky from the archived forum seems a bit out of date.
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

Any help appreciated. Going to run the live cd on the new base unit and see what gives.

Its spec is

asus m3a mb
athlon 64 5200+
nvidia gforce 8600 GT
2 gig mem
on board sound
on board nic atheros I think

That thread is far from out of date. In fact it was updated recently, and covers not only installs methods for previous releases but also works with the newest release 8.04.

Also there are clear explanations given regarding some known pros, and some of the known con's.

Regarding your hardware.
1) asus m3a mb This board is known working. from the info I have gathered 
2) athlon 64 5200+ This Cpu  should be recognized without issue.
3) nvidia gforce 8600 GT This gpu should be supported by the nvidia-glw-new driver.
4) 2 gig mem This should be fine.
5) on board sound. Looking over the spec's of the board it has a Realtek ALC883, and should be supported without issue. 
6) on board nic atheros I think This should be supported you can check after installing by passing the lspci command.

---

### Post by philinux on 2008-04-24
Very much appreciate replies, looking forward to getting this up and running. Got 2 hard drives and it's a clean install. No windows in sight.

---

### Post by techolous on 2008-04-24
Might be a good idea to keep in mind that some newer Atheros cards won't work out of the box with Ubuntu's drivers. However, you can use ndiswrapper (like wine, but for drivers) to get the basic functions of the card working if you can find the right windows drivers. With ndiswrapper, you won't be able to use stuff that needs to have "raw" access to the card.

---

### Post by JoBangles on 2008-04-24
After failing to get DVD burning going I lashed out and bought a box only 65 bit system and I am blown away with Ubuntu 7.10 Gutsy. DVD burning excellent, Open Arena runs spot on. So far I am on cloud 9.

---

### Post by philinux on 2008-04-25
> **JoBangles said:**
> After failing to get DVD burning going I lashed out and bought a box only 65 bit system and I am blown away with Ubuntu 7.10 Gutsy. DVD burning excellent, Open Arena runs spot on. So far I am on cloud 9.

Duh !!! 65 bit

---

### Post by Patsoe on 2008-04-25
> **lazyart said:**
> I installed Feisty as my first 64 bit experience.  Read the directions for installing Flash, which seems to be the biggest hurdle.  I'm happy with it.

Not anymore, there are amd64 packages now:
[http://packages.ubuntu.com/hardy/flashplugin-nonfree](http://packages.ubuntu.com/hardy/flashplugin-nonfree)
[http://packages.ubuntu.com/hardy/swfdec-mozilla](http://packages.ubuntu.com/hardy/swfdec-mozilla)
[http://packages.ubuntu.com/hardy/mozilla-plugin-gnash](http://packages.ubuntu.com/hardy/mozilla-plugin-gnash)

---

### Post by knavarathna92 on 2008-04-25
> **lazyart said:**
> I installed Feisty as my first 64 bit experience.  Read the directions for installing Flash, which seems to be the biggest hurdle.  I'm happy with it.

Flash hasn't been a problem since the flashplugin-nonfree update you get when attempting to view flash content. :)

---

### Post by philinux on 2008-04-25
Thanks for replies, base unit expected tomorrow. so the fun will begin.

---

