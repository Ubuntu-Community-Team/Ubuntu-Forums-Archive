---
title: "Running 64 bit MEncoder on 32 bit Ubuntu"
date: 2006-01-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Navyblue on 2006-01-29
Is there a possibility of running 64 bit MEncoder on 32 bit Ubuntu? Like may be just download the 64 bit kernel and a few libraries and do a dirty install? Of course I am running a 64 bit capable processor.

I spend may be 90% of my time running 32 bit applications like Firefox, Openoffice, Enemy Territory and may be Wine. I guess it wouldn't make much sense to install 64 bit Ubuntu to run one or two applications that is processor intensive and mess with chroot for most of my applications. Yes I would get to use X server and its DE in 64 bit but I can't tell the speed difference anyway.

Another application that I want to run in 64 bit is may be UFRaw.

Thank you for reading.

---

### Post by Navyblue on 2006-01-30
Is there a way to force install .deb package of a different architecture?

If not a dirty install (merely copying fles to the respective places) is fine with me. Where can I download Ubuntu's package without going through apt?

---

### Post by trigg on 2006-01-30
I think you actually need to be booted into an environment with a 64-bit kernel to run 64-bit applications . . . I suppose you could try creating a 64-bit chroot environment, but I don't think it will work . . . think of it being analogous to the size of a box - 32=small 64=big, you can fit a small box into a big box, but not a big box into a small box. . .







*Edit: mispelled analogous

---

### Post by slavik on 2006-01-30
you can't run 64bit apps on a 32bit architecture ... because there is no way to translate a 64bit call (mov A, rax) (is it rax in 64bit?) into a 32bit call without any type of emulation ... 'translating' is impossible in this situation.

---

### Post by RAOF on 2006-01-30
You could try just installing a 64bit kernel.  That might work.  You can install debs from different architectures with "sudo dpkg --install --force-architecture whatever.deb".

You won't be able to set up a 64bit chroot inside your 32bit system - the reason a 32bit chroot works is that the 64bit kernel can run 32bit code.  The 32bit kernel can't run 64bit code, however.

It would probably be simpler to try the other way, though: install Breezy64 and get the few 32bit programs you want working.  Wine's (pretty) easy, firefox (with flash & java) is simple.  That's pretty much all you'll need to fix up.

---

### Post by slavik on 2006-01-30
[QUOTE=RAOF]You could try just installing a 64bit kernel.  That might work.  You can install debs from different architectures with "sudo dpkg --install --force-architecture whatever.deb".

You won't be able to set up a 64bit chroot inside your 32bit system - the reason a 32bit chroot works is that the 64bit kernel can run 32bit code.  The 32bit kernel can't run 64bit code, however.

It would probably be simpler to try the other way, though: install Breezy64 and get the few 32bit programs you want working.  Wine's (pretty) easy, firefox (with flash & java) is simple.  That's pretty much all you'll need to fix up.[/QUOTE]
make sure your CPU is 64bit though :)

---

### Post by Navyblue on 2006-01-31
I am running AMD Atlon 64 2800+.

I have tried messing with chroot with no luck. So I thought it would be easier to work the other way round since I run 32 bit application most of the time.

Where can I get the 64 bit Ubuntu .deb package without installing 64 bit Ubuntu? I really hope that by installing the 64 bit kernel, the MEncoder itself and some relevant libraries would work. So in short is this possible?

---

