---
title: "Opera on 64-bit (again, sigh)"
date: 2007-09-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2007-09-30
I had 9.0 32-bit working fine, installed with --force-architecture on my Feisty amd64 computer. Not terribly stable, but I did manage to get flash working in it, so I used it only for youtube. Normally I use Firefox 64-bit, where I never could get flash working. But then, it was the best of both worlds because, except for youtube, I don't need or want flash.

I also used Opera for Amazon because, for some reason that I have never figured out, Amazon insists that I do not have cookies enabled in Firefox (even though I do), so I can't place an order with Firefox.

Today Opera crashed even when opening the Amazon main page. So I decided to try to upgrade Opera from 9.0 to 9.23. I downloaded the 32-bit deb and installed it with --force-architecture, and here is what happened:

```
jjj@Devil5:~/Desktop$ sudo dpkg -i --force-architecture opera_9.23-20070809.6-shared-qt_en_i386.deb 
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package opera.
dpkg: considering removing opera-static in favour of opera ...
dpkg: yes, will remove opera-static in favour of opera.
(Reading database ... 179948 files and directories currently installed.)
Unpacking opera (from opera_9.23-20070809.6-shared-qt_en_i386.deb) ...
Setting up opera (9.23-20070809.6) ...

jjj@Devil5:~/Desktop$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.23-20070809.6/opera: error while loading shared libraries: libqt-mt.so.3: wrong ELF class: ELFCLASS64
```

So then I read on an Opera forum that I needed to add some libs, and I did, and here is what happened when I copied and pasted the command from the Opera forum:

```
jjj@Devil5:~/Desktop$ sudo apt-get install ia32-libs ia32-libs-gtk lib32asound2 linux32 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
ia32-libs-gtk is already the newest version.
lib32asound2 is already the newest version.
linux32 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

jjj@Devil5:~/Desktop$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.23-20070809.6/opera: error while loading shared libraries: libqt-mt.so.3: wrong ELF class: ELFCLASS64
```

So the problem remains. I need to order a book from Amazon, and I can't get Opera running. I should add that Konqueror and Epiphany also crash on opening Amazon's main page now. Only Firefox seems to be able to open the main page and browse, but I can't place an order with Firefox. I have read that there is an alpha version of Opera 9.5 64-bit, but after reading about it, it is too unstable for my taste. I hope someone can help me fix my 32-bit Opera.

---

### Post by Colonel Kilkenny on 2007-09-30
I'm not sure but I think you need to have ia32-libs-kde (if there is a package with that name?)..
Anyway I guess the problem is that it's trying to use 64-bit Qt-libs with 32-bit Opera.

---

### Post by Nameless_one on 2007-09-30
Yes, you need the ia32-libs-kde package: opera is built on Qt (which is KDE's visual library or smth). 

However, I think that if you look through this forum, you'll find plenty of solutions to run Firefox32 with flash and maybe even Firefox64. I would also recommend switching to Opera full-time, but that's just me :P I for one have the latest Opera version (the native 64-bit one), with flash working (via a qick hack/workaround) and everything works great - even Amazon ;)

---

### Post by John Jason Jordan on 2007-09-30
> **Nameless_one said:**
> Yes, you need the ia32-libs-kde package: opera is built on Qt (which is KDE's visual library or smth). 

However, I think that if you look through this forum, you'll find plenty of solutions to run Firefox32 with flash and maybe even Firefox64. I would also recommend switching to Opera full-time, but that's just me :P I for one have the latest Opera version (the native 64-bit one), with flash working (via a qick hack/workaround) and everything works great - even Amazon ;)
Thanks guys. 

I don't think I really want flash in Firefox. It wouldn't be so annoying if I could just turn it on and off with a button and then use it only for youtube. But I don't want it all the time.

As for Opera full time, I used to do that several years ago on Windows. I could be convinced to go back, but Opera on Ubuntu uses some screwy fuzzy font in all its menus. It's ugly and hard to read. It could be my gnome desktop settings, but it's more trouble than it's worth to troubleshoot it.

Meantime, eventually I decided that Opera 32-bit was always so unstable that I just went ahead and installed the alpha of Opera 64-bit. It runs fine and I got the book that I needed for a class ordered. However, now I have nothing that will do flash, so I'm trying to figure out how to get flash working in 64-bit Opera on 64-bit Feisty. There's a thread here on an Opera forum where apparently it can be done. 

[http://my.opera.com/community/forums/topic.dml?id=206201&t=1191200183&page=1#comment2267124](http://my.opera.com/community/forums/topic.dml?id=206201&t=1191200183&page=1#comment2267124)

If you read the last post you will see that I failed to understand the instructions. So any suggestions on getting flash working in 64-bit Opera alpha would be appreciated. Meantime, it actually seems more stable than the 32-bit version I was using before.

---

### Post by Nameless_one on 2007-10-01
AActually, the screwy fuzzy fonts where the result of the 32-bit version being used on a 64-bit environment and Qt not performing very well. If you installed the 64-bit version of the 9.5 alpha. the fonts (and the geenreal look of the program) should have been greatly improved. 

I will try to  use step by step language as you say to gt you through the flash hack, on my next post :) Right now I have to go!

EDIT: 

1) go to /usr/lib/opera/9* (where 9* is the folder named after your current opera version) and rename operapluginwrapper using:

```
$ sudo mv operapluginwrapper operapluginwrapper64
```

2) get the i386 opera .deb from [here](http://snapshot.opera.com/unix/snapshot-1600/intel-linux/opera_9.50-20070928.6-shared-qt_i386.deb), and open it using Archive Manager (not double clicking). One inside the archive, open data.tar.gz and navigate to ./usr/lib/opera/9<whatever>/ and extract operapluginwrapper from there to say, your home directory.

3) copy the operapluginwrapper which you just extracted to the opera folder mentioned above renaming it to operapluginwrapper32 (you can use this command if you extrected it into your home folder:) 

```
$ sudo cp ~/operapluginwrapper /usr/lib/opera/9*/operapluginwrapper32
```

4) next you have to create a file named operapluginwrapper,and paste this into it: 

```
#!/bin/sh

if [[ -n `echo ${@} | egrep "\/[^ ]*64"` ]]; then
        exec ${OPERA_BINARYDIR}/operapluginwrapper64 ${@}
else
        exec ${OPERA_BINARYDIR}/operapluginwrapper32 ${@}
fi
```

This has to go into the opera directory as well. That directory is owned by root, so you can save this to another directory and move it with sudo mv if you don't know any other way. 

Now, install flash and it should work. If you have more problems, post.

---

### Post by kansei on 2007-10-01
Regarding the original post --you can download a .deb for static QT so that you don't have to install more 32-bit libraries :)

---

### Post by John Jason Jordan on 2007-10-01
> **Nameless_one said:**
> 1) go to /usr/lib/opera/9* (where 9* is the folder named after your current opera version) and rename operapluginwrapper using:

```
$ sudo mv operapluginwrapper operapluginwrapper64
```

2) get the i386 opera .deb from [here](http://snapshot.opera.com/unix/snapshot-1600/intel-linux/opera_9.50-20070928.6-shared-qt_i386.deb), and open it using Archive Manager (not double clicking). One inside the archive, open data.tar.gz and navigate to ./usr/lib/opera/9<whatever>/ and extract operapluginwrapper from there to say, your home directory.

3) copy the operapluginwrapper which you just extracted to the opera folder mentioned above renaming it to operapluginwrapper32 (you can use this command if you extrected it into your home folder:) 

```
$ sudo cp ~/operapluginwrapper /usr/lib/opera/9*/operapluginwrapper32
```

4) next you have to create a file named operapluginwrapper,and paste this into it: 

```
#!/bin/sh

if [[ -n `echo ${@} | egrep "\/[^ ]*64"` ]]; then
        exec ${OPERA_BINARYDIR}/operapluginwrapper64 ${@}
else
        exec ${OPERA_BINARYDIR}/operapluginwrapper32 ${@}
fi
```

This has to go into the opera directory as well. That directory is owned by root, so you can save this to another directory and move it with sudo mv if you don't know any other way. 

Now, install flash and it should work. If you have more problems, post.
Yay! I got it working! Thanks for the step by step. I'm going to post a link to this thread on the Opera Linux forum where the same thing is being discussed.

---

### Post by Nameless_one on 2007-10-01
Glad to be of help ;) 

I don't know if this will help anyone on the Opera Linux thread, though. It's just a summary of what they're discussing.

---

### Post by John Jason Jordan on 2007-10-03
Opera amd64 9.5 alpha on Feisty amd64 continues to run great for me, and no problems with flash. But I do have one niggling problem. Every time I launch it I get a popup that says:

"Before you can use your mail and newsfeed messages, Opera needs to update your mail database to a new format. Would you like to do this now?"

I have to click No in order to continue. I never intend to use Opera for mail. Does anyone know if there is a way to convince Opera to shut up about mail?

---

### Post by kansei on 2007-10-03
I think even if you never used it for mail, it still has a mail database set up under the .opera folder in your home folder. So just let it update and be on your way :)

---

### Post by Trevorius on 2007-11-06
Hi, I've installed the 64 bit version, but I haven't been able to install flash. Do I use the force architecture command to install it? If so how? (Forgive me, I'm very new to Linux and command line)

---

### Post by John Jason Jordan on 2007-11-06
> **Trevorius said:**
> Hi, I've installed the 64 bit version, but I haven't been able to install flash. Do I use the force architecture command to install it? If so how? (Forgive me, I'm very new to Linux and command line)
Yes, you can get flash working with 64-bit Opera. I don't recall exactly how I did it, as later I uninstalled Opera (didn't like it). However, I don't think it involved --force-architecture. I do remember that I found the instructions on the Opera forums. And I think I also made a link to the instructions in an Ubuntu forum post about Opera. Unfortunately, I didn't bookmark either page. But if you search the Ubuntu forums for "opera" you should be able to find it.

---

### Post by Trevorius on 2007-11-06
Thanks for the quick reply; I'll see what I can find.

---

### Post by blitze on 2007-11-07
Don't know about flash but Opera 9.5 Beta is out there now and running great.

I use it as my primary browser on Linux (Gutsy x64) and font rendering in it is great compared to running the x86 version of Opera.  Much more stable than the Alpha too and add blocking works as good as Opera's x86 and Windows counterparts which is a boon.

Some pieces of software that are good do come in from closed sourced sources, but if they excel and play fair in the market, then I am prepared to support them.

---

### Post by Paulo Calipari on 2007-12-26
Installing Opera 9.25 failed on my 64-bits AMD64 Athlon X2 on GeForce6100SM-M, resulting in "Error: Wrong architecture 'i386'" and later in "error while loading shared libraries: libqt-mt.so.3: wrong ELF class: ELFCLASS64".
The solution above did not work for me but installing "libqt-mt.so.3" according to "http://blog.isnotworking.com/2007/11/opera-9-on-ubuntu-with-amd64.html" did work for me.
Paulo.

---

