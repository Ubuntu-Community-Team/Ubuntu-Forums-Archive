---
title: "restricted format issue no flash after compiling gplflash"
date: 2005-12-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by T31 on 2005-12-20
After a fresh new installation of breezy to get flash in firefox I have been following these steps 

[https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Flash#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Flash#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b)

one by one if after finish compiling it, I restart the browser and it says no plugin installed :confused: 

then I did

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

just in case but didnt help as well :???:  I did becouse the ubuntu plugin from its repositories doesnt work out for me, the browser keeps loading loading loading

any idea please, I can live without flash but not my wife :(

---

### Post by localzuk on 2005-12-20
Take a look at [http://www.ubuntuguide.org/#flash-mozilla](http://www.ubuntuguide.org/#flash-mozilla) - this instructs you how to install flash from the other repositories. In order to set these up, take a look at [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories) (change hoary to breezy if using Breezy (5.10)

---

### Post by T31 on 2005-12-20
Thanks a lot for such a quick answer localzuk but.... I need the flash player for ppc arch and you are giving me the link for x86 arch and Im already in breezy,

problably you did like I do often, just read to fast ;)

---

### Post by localzuk on 2005-12-20
Ah, my mistake - I saw mention of a mac mini and then couldn't see it again. Now I notice it was your avatar and your sig. Silly me.

I'm waiting for Ubuntu to work on imac g5 + isight edition... Could be a long wait. When I do, I will have a look at installing this software myself.

---

