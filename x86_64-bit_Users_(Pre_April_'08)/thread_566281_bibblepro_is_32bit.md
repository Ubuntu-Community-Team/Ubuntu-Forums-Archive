---
title: "bibblepro is 32bit"
date: 2007-10-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by trucker33377 on 2007-10-03
this app only comes as 32bit is there an ez way for a newbie like myself to use it with 64 bit. otherwise i may need to stay with 32 bit ubuntu

---

### Post by Kilz on 2007-10-03
> **trucker33377 said:**
> this app only comes as 32bit is there an ez way for a newbie like myself to use it with 64 bit. otherwise i may need to stay with 32 bit ubuntu

[Yes there is if you have a deb file. ]("http://ubuntuforums.org/showthread.php?t=474790") But if its a windows application running under wine it will be even simpler since wine is 32bit.Just install it as you would on the 32bit. If it is a windows application you might want to look into linux applications that are similar. I like Gnomesword myself

---

### Post by trucker33377 on 2007-10-03
ok ive downloaded the getlibs but i must be doing something wrong package is on desktop.

bibblepro_4.9.8-6_i386.deb

but when i follow dir to install i get error. and its also says 32 bit must show sudo dpkg -i --force-all bibblepro_4.9.8-6_i386.deb i dont see that in term at all

---

### Post by Kilz on 2007-10-04
> **trucker33377 said:**
> ok ive downloaded the getlibs but i must be doing something wrong package is on desktop.

bibblepro_4.9.8-6_i386.deb

but when i follow dir to install i get error. and its also says 32 bit must show sudo dpkg -i --force-all bibblepro_4.9.8-6_i386.deb i dont see that in term at all

Please copy the error or the attempted install messages from the terminal and paste them into a reply please.
You might also want to use ```
sudo dpkg -i --force-architecture packagename_i386.deb
``` instead of sudo dpkg -i --force-all bibblepro_4.9.8-6_i386.deb

---

### Post by trucker33377 on 2007-10-04
i did that Im not sure but i think i may have other issues here. never could boot the new kernel after 1st update so for the moment ive gone back 32 bit. I'll give this another shot after i get these photos edited. time is ticking away

---

### Post by Kilz on 2007-10-04
> **trucker33377 said:**
> i did that Im not sure but i think i may have other issues here. never could boot the new kernel after 1st update so for the moment ive gone back 32 bit. I'll give this another shot after i get these photos edited. time is ticking away

Did you install Feisty or the Gutsy Beta? If you installed the Gutsy Beta and had problems, as a good community member you should [report any bugs or problems on Launchpad.]("https://bugs.launchpad.net/ubuntu")

---

### Post by trucker33377 on 2007-10-04
it was feisty i think i need to get my video card to work right b4 i do anything else here. res is not going past 1024x768 i should get alot more out of this. im thinking this is why it wont boot the updated kernel. but im not sure

---

### Post by Kilz on 2007-10-04
> **trucker33377 said:**
> it was feisty i think i need to get my video card to work right b4 i do anything else here. res is not going past 1024x768 i should get alot more out of this. im thinking this is why it wont boot the updated kernel. but im not sure

Thats a good plan. if you have room and can install the 64bit version to another partition it may also be a good idea. That way you have your 32bit working setup while you work out any problems.

---

### Post by trucker33377 on 2007-10-05
just so you know i found the release for 64 bit gutsy. seems to work very good running 64 bit with navida driver 3D is neat. now to see if i can get bibble to install

---

