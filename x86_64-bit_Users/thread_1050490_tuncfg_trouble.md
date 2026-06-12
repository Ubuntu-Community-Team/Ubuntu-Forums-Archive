---
title: "tuncfg trouble"
date: 2009-01-25
forum: x86 64-bit Users
---

### Post by spynappels on 2009-01-25
Hi Guys,

I posted this in Server Platforms, but did not get any replies, so I thought I'd try here.

I'm having trouble with a Hamachi Installation on 64 bit Server Edition 8.10. When I try to run tuncfg to set up the Tun/Tap drivers, I get the following error message:

unable to execute /sbin/tuncfg: No such file or directory.

Ive checked and there is a tuncfg file in /sbin, so I'm not sure what the problem is. I've checked, and there is a /dev/net/tun file, but it is 0kb in size, so does that mean that the tun/tap drivers are not installed on my Ubuntu system?

Any help would be gratefully accepted...

---

### Post by Yellow Pasque on 2009-01-25
IIRC, Hamachi uses 32-bit stuff.
```
sudo apt-get install ia32-libs
```

If that doesn't help, try getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by spynappels on 2009-01-26
That's fixed it.

Thanks very much.

---

### Post by jurfid on 2009-04-02
I had the same problem and this fixed it.  Much thanks and appreciation.

---

### Post by cleyan on 2009-07-21
muchas gracias me di contra el muro mucho rato, sin solucion.

----

Thank you very much, you save me!

:KS

---

