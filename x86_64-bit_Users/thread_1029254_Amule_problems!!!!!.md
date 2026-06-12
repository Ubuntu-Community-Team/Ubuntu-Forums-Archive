---
title: "Amule problems!!!!!"
date: 2009-01-03
forum: x86 64-bit Users
---

### Post by Hellaxe on 2009-01-03
Hello people:
In December i updated my desktop from Feisty to Intrepid 64bits.
Everything went ok but I have a huge problem with amule.
The program is crashing too much with no reason and now the files after reached the final roll back over and start downloading at 98/99%.
For example I have a file that has 2.2gb and downloded 2.8gb and is not finished; yesterday went back to 98%.
The search doen't work ok and the direct links from firefox also.
I've searched here for answers but had no luck. On the aMule forum and they say the problem is from this package.
Does anybody have solutions for these common (I think) problems?
Thank you.

---

### Post by graysky on 2009-01-03
Firstly, remove the ubuntu packages:

```
$ sudo aptitude purge amule
```

You can backup your settings in ~/.aMule by moving that dir to ~/.aMule-backup.

Now reinstall it via aptitude and see if that helps.  Here is the [amule wiki](http://www.amule.org/wiki/index.php/HowTo_Compile_In_Debian#Official) entry for ubuntu.

---

### Post by Hellaxe on 2009-01-04
How does it works better to re-install the same package?
The 2.2.3 version was released a few days ago but isn't in the repos yet.

---

### Post by tjotser on 2009-01-04
Hi, you can get the debs over at getdeb 
[http://www.getdeb.net/](http://www.getdeb.net/)
good luck !

Make sure to set the site to your ubuntu version and architecture 32/64 bits/ hardy or intrepid.

---

### Post by Hellaxe on 2009-01-04
Thanks.
I installed just right now the 2.2.3 from getdeb.
It still doesn't handle the ed2k links with firefox.
It sucks.
I think that's a problem with something of Intrepid.
I&#314;l wait for some time to see if it is stable than the version 2.2.2.

---

