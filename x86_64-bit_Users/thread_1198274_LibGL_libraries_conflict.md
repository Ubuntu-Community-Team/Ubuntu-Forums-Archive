---
title: "LibGL libraries conflict?"
date: 2009-06-27
forum: x86 64-bit Users
---

### Post by afrodeity on 2009-06-27
I'm getting this message quite a lot, not sure if its an error but it surely affects the functioning of the system, which is doing some odd things, (WINE and DOSbox not operational at the moment).

```

/sbin/ldconfig.real: libraries libGL.so.1 and libGL.so.1.2 in directory /usr/lib have same soname but different type.

```

How to rectify and eliminate potential conflict?

---

### Post by Yellow Pasque on 2009-06-27
What graphics card and driver are you using?

---

### Post by afrodeity on 2009-06-27
Its a Via P4M900 with onboard graphics that uses OpenChrome from repository but I'm trying to get the native Chrome 9 linux driver to work so that I can use the 3D graphics. I installed it, but it doesn't load properly. Is this connected?

---

### Post by Yellow Pasque on 2009-06-27
Yes, it's probably connected. For the via driver, I'd suggest you "make uninstall" any source code you built and use the Ubuntu karmic driver: [http://packages.ubuntu.com/karmic/xserver-xorg-video-openchrome](http://packages.ubuntu.com/karmic/xserver-xorg-video-openchrome)

---

### Post by afrodeity on 2009-07-22
Just an update. I removed the driver and DOSbox is now working. Haven't tried the Karma driver. Will it work on Hardy?

---

