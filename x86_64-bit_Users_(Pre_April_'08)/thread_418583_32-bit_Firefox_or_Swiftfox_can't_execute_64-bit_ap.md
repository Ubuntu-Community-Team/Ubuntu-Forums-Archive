---
title: "32-bit Firefox or Swiftfox can't execute 64-bit applications?"
date: 2007-04-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by gbesso on 2007-04-22
Hey, is it just me or do 32bit firefox/swiftfox versions running on amd64 can't execute other 64bit applications, such as nautilus or thunderbird.
If I download something and click 'open' in the download box nothing happens.
Same thing if I right click an image and click 'send this image'.

Anyone else experiencing similar problems?

---

### Post by Kilz on 2007-04-22
> **gbesso said:**
> Hey, is it just me or do 32bit firefox/swiftfox versions running on amd64 can't execute other 64bit applications, such as nautilus or thunderbird.
If I download something and click 'open' in the download box nothing happens.
Same thing if I right click an image and click 'send this image'.

Anyone else experiencing similar problems?

That depends on how you install them. If you installed them in say a chroot, no it isnt going to use 64bit applications. There may be other problems depending on how 32bit firefox is setup if installed w/o a chroot.

---

### Post by gbesso on 2007-04-22
No, I didn't install them in a chroot.
With firefox I followed your guide(thanks for that one btw! :))
I seem to remember with firefox it worked for a few days, and eventually stopped working.
With Swiftfox I just used their 32bit deb.

What kind of other problems could cause it? I assume I may be missing a 32bit version of a certain library?

---

### Post by Kilz on 2007-04-22
> **gbesso said:**
> No, I didn't install them in a chroot.
With firefox I followed your guide(thanks for that one btw! :))
I seem to remember with firefox it worked for a few days, and eventually stopped working.
With Swiftfox I just used their 32bit deb.

What kind of other problems could cause it? I assume I may be missing a 32bit version of a certain library?

My advice, if you followed the manual howto and it doesnt work is to install the script. This will make sure everything that is needed is installed.

---

### Post by gbesso on 2007-04-23
I tried that, however it didn't really make a difference. 
But after running firefox from the terminal I noticed some libraries were missing, including libdbus-glib, libesd, libgnomevfs, etc.
I tried installing them manually but eventually I got libgnomevfs to complain about a missing libfile.so module, which I couldn't fix even by installing the 32bit version of it into /usr/lib32.

---

### Post by Kilz on 2007-04-23
> **gbesso said:**
> I tried that, however it didn't really make a difference. 
But after running firefox from the terminal I noticed some libraries were missing, including libdbus-glib, libesd, libgnomevfs, etc.
I tried installing them manually but eventually I got libgnomevfs to complain about a missing libfile.so module, which I couldn't fix even by installing the 32bit version of it into /usr/lib32.

You are the only person who has tried the script that needed those files, in fact one the libgnomevfs is the basis of the nautilus file manager . I wonder how your install was working at all without it.  Do you know the exact file name of the one that gave you problems?

---

### Post by gbesso on 2007-04-23
Well, nautilus uses the 64bit version of libgnomevfs, I guess firefox uses the 32bit version of it.
I am a bit confused as to why the script works for everyone but me, but oh well.
The exact filename was /usr/lib/gnome-vfs-2.0/modules/libfile.so

---

### Post by Kilz on 2007-04-23
> **gbesso said:**
> Well, nautilus uses the 64bit version of libgnomevfs, I guess firefox uses the 32bit version of it.
I am a bit confused as to why the script works for everyone but me, but oh well.
The exact filename was /usr/lib/gnome-vfs-2.0/modules/libfile.so

But that is a 64bit lib.......

---

### Post by gbesso on 2007-04-23
I know, but from what I've noticed applications fall back to the normal /usr/lib path if they can't find a /usr/lib32 equivalent. I tried installing one, it didn't really help

---

