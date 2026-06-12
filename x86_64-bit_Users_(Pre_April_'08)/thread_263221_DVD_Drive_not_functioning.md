---
title: "DVD Drive not functioning"
date: 2006-09-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by xstaticxgpx on 2006-09-22
I've been having a issue with my DVD driver where it is impossible for me to burn a successful disk, out of the 7~9 dvd's i've *tryed* burning all failed, i even tried just burning a .txt file to a dvd, failed.

It seems to work untill it's done and then gives me the "Empty DVD" Pop-up.

Im using a Mad-Dog "MD-16XDVD9A2" - it worked in windows xp (which i completely removed), is there anyway for me fix it and save my poor dvd's from being wasted? thanks :D

---

### Post by kuja on 2006-09-22
The disks burned are likely very corrupt. This may be caused by the version of dvd+rwtools in the Ubuntu repositories, I suggest finding and upgrading to 6.0 or newer.

---

### Post by Kilz on 2006-09-23
> **xstaticxgpx said:**
> I've been having a issue with my DVD driver where it is impossible for me to burn a successful disk, out of the 7~9 dvd's i've *tryed* burning all failed, i even tried just burning a .txt file to a dvd, failed.

It seems to work untill it's done and then gives me the "Empty DVD" Pop-up.

Im using a Mad-Dog "MD-16XDVD9A2" - it worked in windows xp (which i completely removed), is there anyway for me fix it and save my poor dvd's from being wasted? thanks :D

What software are you using to burn with?

---

### Post by xstaticxgpx on 2006-09-23
i used growisofs, i tried the regular nautilus gui burning, i try'd gravedigger (or something)

---

### Post by juicemansam on 2006-09-23
I had to toss my DVD-R because it started to write bad discs. I noticed that dmesg and /var/log/messages showed lots of errors regarding failed and recovered errors. The burns were OK, but reads failed, until recently that both failed (burns without notice). The only symptom for a failed burn was a choppy video. I even tried putting that drive in a Windows machine and ran DVDDecryptor and Nero to test both read and write. Windows did not complain about anything, and if it did it said that it had recovered. Well, that copy was broken, both the read and write. I once thought that the failed/recover errors were due to a system upgrade or a bad IDE cable, but I now know that was never case. :cry:

---

### Post by xstaticxgpx on 2006-09-23
i know there is a way to fix this, if it worked in windows theres a way to make it work in linux... btw kuja i can't find a dvd+rw-tools version 6+ that isnt source code which i can't seem to build (i havnt built anything from source successfully to this day, and i've tried ALOT.)

---

### Post by kuja on 2006-09-24
[http://fy.chalmers.se/~appro/linux/DVD+RW/tools/dvd+rw-tools-6.0.tar.gz](http://fy.chalmers.se/~appro/linux/DVD+RW/tools/dvd+rw-tools-6.0.tar.gz)

I RECOMMEND building it from source. You'd probably have troubles installing growisofs from more up-to-date releases likesay, growisofs from Debian Etch, Debian Sid, or Ubuntu Edgy. 

```
sudo apt-get install build-essential
tar zxf dvd+rw-tools-6.0.tar.gz
cd dvd+rw-tools-6.0
make
sudo make install

```

After that, be sure to configure your favorite frontend to use it instead of the old version, and burning dvds should then work fine.

---

### Post by xstaticxgpx on 2006-09-24
it's official, i CANNOT build things from source, it is obviously impossible for me

> xstaticxgpx@xstaticgpx-desktop:~/Desktop/dvd+rw-tools-6.0$ make
/bin/sh: m4: command not found
make[1]: Entering directory `/home/xstaticxgpx/Desktop/dvd+rw-tools-6.0'
make[1]: *** No rule to make target `dvd+rw-tools'.  Stop.
make[1]: Leaving directory `/home/xstaticxgpx/Desktop/dvd+rw-tools-6.0'
make: *** [all] Error 2
xstaticxgpx@xstaticgpx-desktop:~/Desktop/dvd+rw-tools-6.0$ sudo make install
/bin/sh: m4: command not found
make[1]: Entering directory `/home/xstaticxgpx/Desktop/dvd+rw-tools-6.0'
make[1]: *** No rule to make target `install'.  Stop.
make[1]: Leaving directory `/home/xstaticxgpx/Desktop/dvd+rw-tools-6.0'
make: *** [install] Error 2
xstaticxgpx@xstaticgpx-desktop:~/Desktop/dvd+rw-tools-6.0$


---

### Post by kuja on 2006-09-24
It says "m4: command not found", perhaps installing it would help?
```
sudo apt-get install m4
cd ~/Desktop/dvd+rw-tools-6.0/
make
sudo make install

```

---

### Post by xstaticxgpx on 2006-09-24
wow.... i never relized m4 was something i could get from the repos... thanks!

---

### Post by kuja on 2006-09-24
So, how is growisofs 6 working for you, DVDs writing okay now?

---

### Post by xstaticxgpx on 2006-09-24
i havnt had a chance to try it, idk if i even copied the files right (i just copied all the binaries to /usr/bin and left the other stuff in the folder) ill repost when i try to burn something

---

### Post by kuja on 2006-09-24
You shouldn't have had to copy anything. Running "sudo make install" should be enough.

---

### Post by xstaticxgpx on 2006-09-24
idk, i searched and found a dvd+rw-tools.list file, and i saw that it had 5 binaries in /usr/bin that were also in the dvd+rw-tools-6.0 folder so i copied them over...

anyway i just burned a blank .txt file and it worked, but it still gave me the annoying empty dvd message

---

### Post by kuja on 2006-09-24
You have to be careful to check which version of growisofs it uses to burn it with, now that you have two different versions installed in two different places. k3b seems to be pretty good about it

---

### Post by xstaticxgpx on 2006-09-25
i tried seeing what version growisofs was, but it doesnt seem to have a -version parameter

if im not mistaken k3b is a KDE oriented app...will it interfere with anything gnome does/uses?

---

### Post by kuja on 2006-09-25
Try mkisofs -version.

---

### Post by xstaticxgpx on 2006-09-25
mkisofs 2.01-unofficial-iconv (x86_64-unknown-linux-gnu)

---

### Post by xstaticxgpx on 2006-09-25
i think i also found my "empty dvd" message problem... I didn't have burnproof enabled for nautilus-cd-burner in Configuration Editor

---

### Post by kuja on 2006-09-25
It shouldn't interfere, though it does come with quite a few dependencies I'm sure.

Anyhow I guess I told you to do something wrong a sec ago, with the mkisofs -version... I forget how I got to that command to begin with, oh well. 
growisofs -version
should work.

Example:
> kuja@terra:~$ growisofs -version
* growisofs by <appro@fy.chalmers.se>, version 6.0,
  front-ending to mkisofs: mkisofs 2.01-unofficial-iconv (x86_64-unknown-linux-gnu)


---

### Post by kuja on 2006-09-25
> **xstaticxgpx said:**
> i think i also found my "empty dvd" message problem... I didn't have burnproof enabled for nautilus-cd-burner in Configuration Editor
It didn't have it enabled by default? How weird of them.

---

### Post by xstaticxgpx on 2006-09-25
yea... anyway it was succesful, thanks for the help kuja

> * growisofs by <appro@fy.chalmers.se>, version 6.0,
  front-ending to mkisofs: mkisofs 2.01-unofficial-iconv (x86_64-unknown-linux-gnu)


---

