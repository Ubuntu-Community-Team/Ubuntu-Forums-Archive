---
title: "4GB installed; only some 0.5 GB used"
date: 2008-06-13
forum: x86 64-bit Users
---

### Post by cotcot on 2008-06-13
No problems; just a observation.
I have 4 GB ram installed. Most of the time some 0.4 GB is used. It is going up to 1.5 GB when i open a couple of heavy apps (gimp to rotate a 200 MB png; cinelerra rendering a video). On my gentoo install (a year ago) I only had 1 GB ram (on the same desktop) and it was all used. 
Any reason why this difference ? Is there some setting to do to allow the pc to use more ram ? Or are programmes to be compiled with some flags in order to use better the available ram ?

Thanks

---

### Post by magnus0 on 2008-06-13
Ubuntu doesn't need so much RAM. I have only 512M ram and it's superfast.

---

### Post by kingtaurus on 2008-06-13
This is a little complicated. The amount of memory being used really depends on how the executable and libraries are compiled, as well as, what is configured to run by default. You often cannot qualify the differences in memory usage in two different linux distributions (without giving us some more details).

---

### Post by Jouke74 on 2008-06-14
Wait until you have ran some more programs. Slowly all your ram will start to be used as cache. Meaning that the programs remain resident in memory and will execute much quicker next time you load them. My Ubuntu uses on average about 512 MB for programs as well. I have 2 Gb of Ram present in the system. However, this is without the cache. With cache it uses the full 2 Gb as soon as I have started Firefox, OpenOffice and a bunch of other programs and files.

I assume that Gentoo either showed your ram use with cache, or it simply uses much more ram (I have never used Gentoo). Use the command free -m to see your mem use with the various parts of use.

---

### Post by zgornel on 2008-06-14
Might also be the 'swapiness' option. If it is set on a low value, cached data from applications might or might not be released from memory. I have it on a low value, '20' I think and I constantly have 2-3 GB cached (out of 4) even if the actually committed memory is constantly under 500 MB.

---

### Post by ariel on 2008-06-14
> **cotcot said:**
> No problems; just a observation.
I have 4 GB ram installed. Most of the time some 0.4 GB is used. It is going up to 1.5 GB when i open a couple of heavy apps (gimp to rotate a 200 MB png; cinelerra rendering a video). On my gentoo install (a year ago) I only had 1 GB ram (on the same desktop) and it was all used. 
Any reason why this difference ? Is there some setting to do to allow the pc to use more ram ? Or are programmes to be compiled with some flags in order to use better the available ram ?

Thanks


With so much RAM, you can use preload to speed up applications preload.

```
sudo apt-get install preload
```

I have the same configuration and the difference in performance thanks to library preload is noticeable.

---

### Post by ibuclaw on 2008-06-14
Yes, Ubuntu is very light and works very well with old hardware.

But since you have the luxury of so much RAM. If you wish to use it more, you can set the swappiness to a low value.

The swappiness value controls which device Ubuntu/Linux prefers (Swap or RAM).
Setting it to a high value makes Ubuntu prefer the Swap, a low value the RAM.

For example, set the swappiness to 0.
```
sudo sysctl vm.swappiness=0
```
Then turn swap off and on.
```
sudo swapoff -a && sudo swapon -a
```

Then play about with Ubuntu for a bit. Open up several programs and tweak some settings on compiz (turn on more effects).

If you like what you see, you can make this setting permanent by issuing the command:
```
echo "vm.swappiness=0" | sudo tee -a /etc/sysctl.conf
```

And then rebooting your PC.

Regards
Iain

---

