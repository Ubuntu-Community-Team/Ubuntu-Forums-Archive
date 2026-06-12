---
title: "HOWTO install opera in amd64?"
date: 2006-10-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by eskimokid on 2006-10-22
as what i typed in the title, can anyone please teach me how to install opera in amd64? since the opera only released i386 version.

> sudo dpkg --force-architecture \
opera_8.54-20060330.6-shared-qt_en_etch_i386.deb is this code available ?
i tried but the error says that no such command

---

### Post by s_spiff on 2006-10-22
i woudl sucggest a easy way, install simple64, and it'll run a script to install whateva you want. try it out.

---

### Post by eskimokid on 2006-10-22
o, but how to install simple64 ?

---

### Post by fabertawe on 2006-10-22
> **eskimokid said:**
> o, but how to install simple64 ?

[This thread]("http://www.ubuntuforums.org/showthread.php?t=266290"). I must try this myself soon.

Paul

---

### Post by basementgeek on 2006-10-23
> **eskimokid said:**
> as what i typed in the title, can anyone please teach me how to install opera in amd64? since the opera only released i386 version.

 is this code available ?
i tried but the error says that no such command


You need to navigate (using cd in terminal) to where you have the file on you computer first.  Then use the same command you already tried, but without the "/".

---

### Post by eskimokid on 2006-10-23
I tried another code

> sudo dpkg -i --force-all opera*.deb

and it works

but the problem is Opera is not installed well
i cant find the opera button near my KDE menu
i need to start opera by type > opera in the terminal.

---

### Post by eskimokid on 2006-10-24
> error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory


This error appear when i try to load my opera with using the Terminal
in my KDE menu, Internet section, Opera Browser appear...
but when i clicked it, Opera is loading...but it's just loading...
after 1 minute...the loading icon disappear and i cant load my opera
please help me troubleshooting :( 

ps:sorry for my poor english

---

### Post by kuja on 2006-10-24
To get rid of that error, install the ia32-libs-kde package. (which really would have more appropriately been called ia32-libs-qt, but oh well)

---

### Post by hajk on 2006-10-24
I have just recently installed a 32-bit chroot environment with debootstrap, as per the recipe in the Ubuntu Wiki page DebootstrapChroot. I found it easy to do. Then I proceeded to install a bunch of 32-bit multimedia software in this environment, and also Opera (version 9), Firefox, Flash and Java. My only regret is that I haven't done this earlier and messed with using 32-bit stuff directly in AMD64... I highly recommend the debootstrap method.

---

### Post by eskimokid on 2006-10-24
what is debootstrap?
and which u're using for ur ubuntu ?
x86 ? or x86_64 ?

---

### Post by hajk on 2006-10-24
> **eskimokid said:**
> what is debootstrap?
and which u're using for ur ubuntu ?
x86 ? or x86_64 ?

I'm using x86_64 (Edgy), debootstrap is a package that can be installed, the way to do it (for Dapper, but Edgy is similar) is described on the DebootstrapChroot page of the Ubuntu Wiki.

---

### Post by kuja on 2006-10-24
Personally, I think debootstrapping a chroot just for installing opera (which is what eskimokid wants) sounds like a really stupid idea. Overkill to the umpteenth degree.

---

### Post by hajk on 2006-10-24
> **kuja said:**
> Personally, I think debootstrapping a chroot just for installing opera (which is what eskimokid wants) sounds like a really stupid idea. Overkill to the umpteenth degree.

May be... in another post he wants to install RealPlayer, and who knows what else once he gets around to it. At least now he can choose between the way Kilz (for example) does it (and very well, too IMHO) and the full-Monty way.

BTW, I think you could express yourself a bit more respectfully...

---

### Post by eskimokid on 2006-10-24
Oh well..
since I'm failed to install by using other ways..
it's worth for me to try with the debootstrap way
and I might need other application from it
anyway, thanks for your opinion Kuja.

---

### Post by kuja on 2006-10-24
> **hajk said:**
> May be... in another post he wants to install RealPlayer, and who knows what else once he gets around to it. At least now he can choose between the way Kilz (for example) does it (and very well, too IMHO) and the full-Monty way.

BTW, I think you could express yourself a bit more respectfully...
I probably could. On a small side note, I'm really not a morning person. I suppose I should go get my coffee now :rolleyes: 


Anyway, for just a few small things, I still think it's overkill to do a couple hundred mb of downloading and doing an install within a chroot, just for them. Not to mention that a chroot probably seems pretty technical complicated to well, anyone who hasn't done one before, especially new users.

I think I gave the solution on how to make it work without the chroot a few posts back, have you tried that eskimokid? Something along the lines of ```
sudo apt-get install ia32-libs-kde
``` really should do the trick.

---

### Post by eskimokid on 2006-10-24
Wow! It's working !
Thanks Kuja!
I can browse web with using opera now !
Thanks alot !

---

### Post by Kilz on 2006-10-24
> **kuja said:**
> 
Anyway, for just a few small things, I still think it's overkill to do a couple hundred mb of downloading and doing an install within a chroot, just for them. Not to mention that a chroot probably seems pretty technical complicated to well, anyone who hasn't done one before, especially new users.


I totaly agree. Installing a chroot is a lot of work and hard drive space if all you want is a few 32bit applications. You shouldnt need that many that it would make it worth it.

---

