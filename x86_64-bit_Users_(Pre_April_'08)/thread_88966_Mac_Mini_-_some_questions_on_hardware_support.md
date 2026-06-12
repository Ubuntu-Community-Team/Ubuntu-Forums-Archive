---
title: "Mac Mini - some questions on hardware support"
date: 2005-11-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Writh on 2005-11-11
So, I'm probably getting a new Mac Mini - most certainly with an Airport Extreme card and probably with a SuperDrive. Does Ubuntu support both?

Also, any good compression tools on Linux? I wouldn't much like paying for StuffIt.

EDIT: Also, my network is an encrypted one that requires Mac addresses (like any smart WLAN) and is kept up by a ZyXEL device. Can Ubuntu handle it? (if connecting via the Mac's Airport - I've already determined that Ubuntu cannot find the USB WLAN adapter I use)

---

### Post by ssam on 2005-11-11
the superdive should be ok (the one on my titanium powerbook works fine).

the airport extreme wont work. there are projects to write a drive but the manufacturer has not helped. you'll need to find a usb adapter that works.

once you have got linux working then it should be able to connect to any wireless reuter. (although WPA can be trick to set up. WEP works fine).

there are lots of free compression tools on linux. most of them use gzip or bzip as backends. there is everything from commandline tools to graphic archive browsers that you can drag and drop to and from. you can right click (f12 if you only have a one button mouse) on a compressed file and and choose 'expand here'. also some applications let you save to compressed formats by putting the type .txt.gz or .xcf.gz for example.

---

### Post by Writh on 2005-11-13
Crap. Gotta hate hardware manufacturers.

Well, guess I'll have to make do with a shuttle-pc then. (Or just buy a new USB WLAN card. Any ideas on the "supported" list?) Crap, just crap...

---

### Post by ssam on 2005-11-13
it seems that the broadcom drivers is making good progress.

they have got basic functionality out of it, but not got it connecting to a network yet. see

[http://ubuntuforums.org/showthread.php?t=89113](http://ubuntuforums.org/showthread.php?t=89113)

---

### Post by Writh on 2005-11-15
Hmm...

Any not-too-expensive USB WLAN cards that work on OS X, Linux and Windows alike? (The last is not overly important. It's fine if it works on *NIX)

---

### Post by ssam on 2005-11-15
have a look aroung the networking forums and you should be able to find one. but anything that people make work by using ndiswrapper wont work on a powerpc computer.

---

### Post by Writh on 2005-11-16
Hmm... I just may go by simply switching to a new HD and WLAN adapter (Windows/Linux dualboot). Just checked, it's WEP-encrypted. Yay ^_^

So, now to find a working WLAN adapter, whether for a dual-*NIX box or...

---

### Post by majkmil on 2005-11-20
I have a G4 ibook with the broadcom chip. Is it true that you cannot get it (airport) to work with ubuntu ppc even with ndiswrapper? I cant find ndiswrapper-utils in synaptic anyway, ccan any of you? One last thing I noticed the sources.list file is different, something about planetmirror but I only get errors.    Thanks

---

### Post by ssam on 2005-11-21
ndiswrapper wont work on powerpc because it uses the windows drivers, which are compiled for x86. maybe if somebody put lots of work in then some sort of hack with qemu might be possible. I think that getting qemu to work at a kernel/driver level is probably not easy.

---

### Post by Writh on 2005-12-01
Yay! Finally found one!

[http://www.a-link.com/uk/WL54USB.html](http://www.a-link.com/uk/WL54USB.html)

That thingy seems to have Linux drivers offered on the manufacturer's website...

Can anyone confirm of that stuff working on the Mac, either out-of-the-box or after installing the drivers provided on the page?

---

