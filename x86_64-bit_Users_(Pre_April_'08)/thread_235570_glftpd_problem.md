---
title: "glftpd problem"
date: 2006-08-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by reutel on 2006-08-13
Hi,

While installing glftpd, I encountered this problem:

Copying required shared library files:
   ld-linux-x86-64.so.2: OK
   libc.so.6: OK
   libdl.so.2: OK
   libm.so.6: OK
   libncurses.so.5: OK

Copying your system's run-time library linker(s):
(NOTE: Searches can take a couple of minutes, please be patient.)
   ld-linux.so.2: Searching . . . Failed!
You must install and copy the missing libraries to /etc/glftpd/lib manually.

My question, can I fix this or is it just impossible to install it on a 64bit box?

Any help would be nice

Tia

---

### Post by em3raldxiii on 2006-08-13
I'm not entirely certain, but you should be able to find the 64-bit version of **ld-linux.so.2**.  If you've added some additional repositories to your sources.list, then you might be able to get it in synaptic, or by opening your terminal program (applications>Accessories>terminal) and typing:
 
```

sudo apt-get install ld-linux.so.2

```
 
Now, I could indeed be wrong, I am at work and I have no way of verifying this until I get home.  Give it a try, and let us know what you come up with.
 
If you don't know how to add to your sources.list, there are a number of threads around here about it.  if I get a chance, I'll drop a link here - until then do a search and see if you can find it ;)
 
Good luck!

---

### Post by reutel on 2006-08-13
Hi,

Thx for the input, but that doesn't work ;) That package is not listed (I don't even think it is a package) on packages.ubuntu.com, so I doubt it couldn't find it because of my sources.list.

Because I'm using a 64bit box, I'm using ld-linux-x86-64.so.2 instead of ld-linux.so.2 and I think you must use the one or the other? My guess is there's a problem with the glftp installation configuration because first it detects the 64 bit version:
[I]Copying required shared library files:
ld-linux-x86-64.so.2: OK[/I]
But after that it fails when searching for the regular version.

I could be wrong, but I don't thing I'm able to use the regular ld-linux.so.2. But if so, where can I get it?

Thx

---

### Post by reutel on 2006-08-14
(17:08:25) (fiyamon) apt-get install ia32-libs

bullzeye! :)

thx to #glftpd

---

### Post by em3raldxiii on 2006-08-14
Thanx for the fix!

---

