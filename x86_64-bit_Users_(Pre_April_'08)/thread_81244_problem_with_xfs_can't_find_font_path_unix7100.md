---
title: "problem with xfs? can't find font path unix:/7100"
date: 2005-10-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by madfitz on 2005-10-24
Simi-newbe to linux. Still trying to figure out some things here. I finally got the nVidia drivers to work and I had 3d acceleration working!!!.

My system is Ubuntu 5.04 amd64.

I tried to use a tutorial for getting dual head to work with my video card. It didn't so I restored the backup (previously working copy) of the /etc/X11/xorg.conf file to get X to work again. Instead I got the error that X couldn't find the font path element unix:/7100

I have not found anything specifically for this, the other solutions seem to mention there might be a problem with xfs, however there doesn't seem to be an xfs in the /etc/init.d as explained in several suggested fixes (other distros and ix86 processor systems)

The only thing I edited was a copy of the xorg.conf file and even after restoring it & even trying to restarting the system. X crashes with that last error.

Any help would be great. I don't want to have to re-install ubuntu again if I don't have to. I finally got many media items to work and don't know if I could do it again.

Also if anyone can point me in the correct direction  into getting dual head to work with an nvidia 5200 (I think) that would be nice too.

thanks

---

### Post by madfitz on 2005-10-27
Anyone have a clue?

---

### Post by madfitz on 2005-10-27
well this is interesting:
sudo startx
works, but not for my login.
I have a friends login on my system as well and this works fine.

So my question is what would be the cause for this?
Why would my login alone not have x work?
Why would it say there's a problem with the font path unix:/7100?

Is there some kinda x config in my home directory that could have been messed up?

---

### Post by madfitz on 2005-10-27
haha!!! got it... it was a permission problem, I found a log file:

.xsession-errors

in my home directory that said x couldn't access the 

.ICEauthority

file, checking the permissions it was user and group of root, once this was changed, everything seemed to have worked.

I don't know if this thread will help anyone. But, I'm still trying to get dual head to work (that's another thread though)

---

