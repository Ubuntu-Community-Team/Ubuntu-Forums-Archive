---
title: "where to install wine apps?"
date: 2016-11-25
forum: Wine
---

### Post by juntjoo2 on 2016-11-25
the reason I ask is that at the point the ms office installer prompts for location of installation it automatically points to my windows program files location and I would like it on my ubuntu partition but don't know where I should put it.  when I looked into this I found some info explaining that when you open up wine configuration window it automatically creates a fake c drive and program folders so if that was the case then perhaps this c drive program files folder I'm looking at in my office installer here is referring to this fake drive wine supposedly creates?  I didn't see any new "wine" folders taking a look in my ubuntu partition.  anyone know?

---

### Post by Yellow Pasque on 2016-11-25
There's a hidden folder called .wine in your user's home directory. That's where you should install programs (C:). You can also use winecfg to mount your home directory in wine as Z: (for example) if you want to access documents in your home folder.

---

### Post by juntjoo2 on 2016-11-25
> **Temüjin said:**
> There's a hidden folder called .wine in your user's home directory. That's where you should install programs (C:). You can also use winecfg to mount your home directory in wine as Z: (for example) if you want to access documents in your home folder.


Thanks.
So I should install inside the hidden folder?  will it appear inside the office installer? Also, you say I should install it there, then you typed "c:/".  Did you mean this 'fake c' I read about?  If so, when you say C:/ would this fake C location be this .wine folder itself or reside inside?  Also, when you say I can mount the home directory to Z:/ to access my documents in my home folder, are you referring to my office documents?  If so, Couldn't I just access them wherever I put them? IOW, what does specifying the home directory have to do with the location of my documents?  Thanks


oh, and another thing, this C directory shown inside the ms office installer, how do I know if it's referring to the real C path or this fake C path?

---

### Post by Yellow Pasque on 2016-11-25
> this C directory shown inside the ms office installer, how do I know if it's referring to the real C path or this fake C path? 
There is no real C: path. Linux is not DOS/Windows. "C:" is just an alias/shortcut wine uses so:
1. Windows programs don't freak out when they encounter Linux directory structure.
2. Windows programs are contained and don't touch the other files on your system

>  If so, when you say C:/ would this fake C location be this .wine folder itself or reside inside?
~/.wine/drive_c/

> Also, when you say I can mount the home directory to Z:/ to access my documents in my home folder, are you referring to my office documents? If so, Couldn't I just access them wherever I put them?  
Outside of wine, you can access them wherever you put them. Mounting your home folder (or whatever subfolder holds your docs) just makes things easier if you want to be able to access your files in non-wine programs. If you don't want to do that, then you shouldn't bother.

---

### Post by juntjoo2 on 2016-11-25
> **Temüjin said:**
> There is no real C: path. Linux is not DOS/Windows. "C:" is just an alias/shortcut wine uses so:
1. Windows programs don't freak out when they encounter Linux directory structure.
2. Windows programs are contained and don't touch the other files on your system


~/.wine/drive_c/


Outside of wine, you can access them wherever you put them. Mounting your home folder (or whatever subfolder holds your docs) just makes things easier if you want to be able to access your files in non-wine programs. If you don't want to do that, then you shouldn't bother.

hmm, I'm not quite understanding I guess.  It showed below the C drive a "Z" drive also, which I took for the partition that Ubuntu is installed on, and other drives.  So you're saying Linux doesn't see these different lettered drives like windows does?  Something is not computing lol.  Doesn't really matter as I'll just take your word that the C drive mentioned is the fake one and I'll just select it.  Anyway, thanks a lot.  I shall install it now.

---

### Post by howefield on 2016-11-26
Moved to the "*Wine*" forum.

---

### Post by jerome1232 on 2016-11-26
When you install a program via wine, wine fakes a C: partition that is really at ~/.wine/drive_c/


So if you install MS Word, for example, within wine MS Word thinks it's installed at C:/Program Files/MS Word, but really it's at ~/.wine/drive_c/Program Files/MS Word.

---

