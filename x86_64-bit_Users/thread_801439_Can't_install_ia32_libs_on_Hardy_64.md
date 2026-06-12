---
title: "Can't install ia32 libs on Hardy 64"
date: 2008-05-20
forum: x86 64-bit Users
---

### Post by joshuaos on 2008-05-20
Can't install ia32 libs on Hardy 64 on Dell Inspiron 1501.  I tried to install some packages that require it, and synaptic tried to install the 32 bit libraries, but each time I get this error:

E: /var/cache/apt/archives/ia32-libs_2.2ubuntu11_amd64.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib32/libQtNetwork.so.4.3.4')

HELP, please!  :)

Joshua

---

### Post by MaindotC on 2008-05-20
Can you post the contents of your /etc/apt/sources.list file please?  Do you have the necessary repositories enabled?

---

### Post by joshuaos on 2008-05-20
Wow, that was so fast, thank you Brother!

Here's /etc/apt/sources.list without any of the comments.


deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted #Added by software-properties

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by MaindotC on 2008-05-20
It looks like you have all of your repo's enabled so I think this is a bit over my head.  I thought maybe 64-bit Hardy would have different repo's but oh well.  I did a search for the ia32-libs_2.2ubuntu11_amd64.deb file and only 1 post shows - the ubuntu mailing list entry stating that this particular package was added on May 17th.  Sorry I couldn't help more.

---

### Post by Kilz on 2008-05-20
try this , open a terminal and type in
```
sudo apt-get clean
sudo apt-get install ia32-libs
```

---

### Post by Dreig on 2008-08-15
Thanks Kilz!!  That worked for me  :O)

---

### Post by opr8ive on 2008-08-16
In the sake of education over simply "This'll fix it" May I offer (for information purposes) what happened, and what kilz had you do to fix it:

The "short read in buffer_copy (backend dpkg-deb during `./usr/lib32/libQtNetwork.so.4.3.4')" looks like the package got corrupted when it was downloaded. 

In the interest of stability, and saving time, apt (or synaptic), when it downloads a package, it stores it in a temp folder locally before unpacking and installing it. Somewhere during your download of ia32-libs, it got a hiccup, and the package saved on your computer got broke. :) 

trying to re-install the package, (by typing apt-get install ia32-libs, or using synaptic) apt looks at the local cache, and says "Hey, i dont have to re-download ia32-libs, I've got it right here!" and tries to install the package again from the locally saved (broken) file.

apt-get clean goes through your local temp cache of downloaded package files, and cleans up (removes) them. Now, when you run apt-get install ia32-libs, apt looks at the local temp cache and says "Say, i dont have that one yet, Better go download it"

chances are great that lightning won't strike twice, and this time the package will download with no errors. Now apt (or synaptic) can install it with no further problems :)

Im still pretty new to linux myself, so if Im mistaken on any of this, anyone feel free to let me know, But I think that if you know _why_ something happened, and _how_ the solution works to fix it, you'll start to understand some of the inner workings, and soon will be able to start to find fixes on your own (It feels pretty cool, actually :) )

Give a man a fish, feed him for a day.... :)

-Jason

---

