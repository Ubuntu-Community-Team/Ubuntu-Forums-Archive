---
title: "How can I install Opera 9.5 Kestrel beta on Gutsy 64-bit?"
date: 2007-10-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Condoulo on 2007-10-29
I am wanting to install the latest beta of Opera 9.5 Kestrel, but I'm running a 64-bit system, so is there any clue as what I should do?
Also, bare with me, I am new to the whole 64-bit architecture, and a few of the things that are not as easy to get/not there

---

### Post by sawjew on 2007-10-29
You can install Opera 9.5 alpha for 64 bit from here [http://snapshot.opera.com/unix/9.50-Alpha-1/x86_64-linux/]("http://snapshot.opera.com/unix/9.50-Alpha-1/x86_64-linux/") but there doesn't seem to be a 64 bit version of the beta yet.  You can either install the alpha, wait for a 64 bit version of the beta or install the 32 bit version using ```
sudo dpkg -i --force-architecture opera-*.deb
```

---

### Post by Condoulo on 2007-10-29
ok, thanks. :)
Wish they would keep thier releases of 32-bit and 64-bit more together,.

---

### Post by Condoulo on 2007-10-29
tyler@TylerPC:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.50-20071024.6/opera: error while loading shared libraries: libqt-mt.so.3: wrong ELF class: ELFCLASS64
 
=/ yikes

---

### Post by Case_f on 2007-10-29
> **sawjew said:**
> You can install Opera 9.5 alpha for 64 bit from here [http://snapshot.opera.com/unix/9.50-Alpha-1/x86_64-linux/]("http://snapshot.opera.com/unix/9.50-Alpha-1/x86_64-linux/") but there doesn't seem to be a 64 bit version of the beta yet.

The 64bit beta is not available through the download dialog on the main page, however it can be found at Opera's ftp: [ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/](ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/)

I've been using it since the day the beta came out and there's nothing wrong with it, exactly the same build as i386 version, same features, same bugs ;). Don't know why it isn't available the normal way.

---

### Post by Condoulo on 2007-10-29
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
opera: X Shared memory extension is not available. ZPixmap not supported
Floating point exception (core dumped)

I am still getting that with the 64-bit version of the beta. Any help?

---

### Post by Case_f on 2007-10-30
> **Condoulo said:**
> ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
opera: X Shared memory extension is not available. ZPixmap not supported
Floating point exception (core dumped)

I am still getting that with the 64-bit version of the beta. Any help?

For the shared memory warning, try  adding

```
tmpfs                /dev/shm             tmpfs      defaults              0 0
```

to your fstab (this enables shared memory). Or you could try running Opera with something liks 

```
exportOPERA_NUM_XSHM=0 & opera &
```

As for the crash, it's more likely not related to the shared memory warning. How about this:

[http://my.opera.com/community/forums/topic.dml?id=210130](http://my.opera.com/community/forums/topic.dml?id=210130)

Is this a possibility?

---

### Post by nynoah on 2007-11-02
I just loaded the newest version of opera at this link. I took me a little while to find it..........but it is a 64bit version of opera and it is the BOMB.......

Follow the link and download it. My computer stopped freezing like it was when I was using firefox. Plus it is SUPER fast. This release is only a few days old and seems to work great. All my plugins work without having to configure anything. SO far........LOL

Download the Deb file and have fun.

[ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/](ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/)

---

### Post by djtm on 2008-06-11
btw. if your problem with opera and x shared memory is still not fixed, maybe you're running the intel driver or another driver where this helps:

* change the acceleration settings to XAA

here is a quick howto for that:
[http://linux-tipps.blogspot.com/2008/06/operaintel-x-shared-memory-problem.html](http://linux-tipps.blogspot.com/2008/06/operaintel-x-shared-memory-problem.html)

---

