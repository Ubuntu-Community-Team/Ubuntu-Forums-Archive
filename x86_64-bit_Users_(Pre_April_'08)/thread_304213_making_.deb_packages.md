---
title: "making .deb packages"
date: 2006-11-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sqwishy on 2006-11-21
i'm wondering how i sould go about making .deb packages from compiled source code for other ubuntu user's use. i want it to include a list (or something) of the requiered dependacys and stuff.
i wana do this because theres a lack of packages for edgy amd64.
so i kinda need probobly just the commands and stuff. tell me if i'm wrong about this
```
./autogen.sh
./configure
make
make install-schemas
sudo checkinstall
```
then i think theres something for making it apear in synaptic and  stuff so its easy to remove, also i wana know how to make a deb package. i'm not sure so much what the above comands do :D

---

### Post by ciscosurfer on 2006-11-21
You should ask an admin to move this thread to Programming Talk or Installation / Upgrades.

But yes, that looks correct--don't really know though, so you should look in the two forums I mention above.  Usually a standard ./configure, make, sudo checkinstall can do the trick but from what I understand, checkinstall strips symlinks.

---

### Post by christhemonkey on 2006-11-21
Checkinstall produces .deb's that are basically not good.

For proper packaging of debs, see here:
[http://www.debian.org/doc/maint-guide/ch-build.en.html](http://www.debian.org/doc/maint-guide/ch-build.en.html)

---

### Post by ciscosurfer on 2006-11-21
> **christhemonkey said:**
> Checkinstall produces .deb's that are basically not good.

For proper packaging of debs, see here:
[http://www.debian.org/doc/maint-guide/ch-build.en.html](http://www.debian.org/doc/maint-guide/ch-build.en.html)I use checkinstall for all source that I compile...and every app works great -- this may be different if you plan on disseminating the .deb to many people though and especially if you need certain options enbaled.  Thanks for the link christhemonkey, I will check it out.

---

### Post by Sqwishy on 2006-11-21
:D thanks <3
although the guide is a little bit confuzing

---

### Post by christhemonkey on 2006-11-21
For personal use, checkinstall is fine.

But the OP sounded like they were going to be distributing .deb files for others.
The archives produced from checkinstall (so i understand) are not good for this.

---

### Post by Sqwishy on 2006-11-21
> **christhemonkey said:**
> But the OP sounded like they were going to be distributing .deb files for others.
 yeah i wanted to host the files (maybe as a repository) on my website. i pirmarily wana do this for games.

---

### Post by christhemonkey on 2006-11-21
For creating your own repository, see here:
[http://www.debian-administration.org/articles/286](http://www.debian-administration.org/articles/286)

---

### Post by finite9 on 2006-11-23
I wish I could find the link again, but there is a guide to packaging DEBS in the Ubuntu wiki that is shorter and more focused on Ubuntu than the Debian manual.  Have a look in the wiki..I will ujpdate this post if I find it.

---

