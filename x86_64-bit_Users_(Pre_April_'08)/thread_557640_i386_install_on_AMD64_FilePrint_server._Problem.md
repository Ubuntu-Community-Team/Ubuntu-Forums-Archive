---
title: "i386 install on AMD64 File/Print server. Problem?"
date: 2007-09-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by mfreeman73 on 2007-09-22
I just made a file and print server with 1gb Ram and an older AMD64 Athlon chip (single-core). Also, no GUI installed. I'm just using the CLI.

Without thinking, I installed the server with the i386 disk (7.04) instead of the 64bit disk. Now I have things like I like it and really don't want to do a reinstall.

Is there any benefit to going with the 64 bit version when all I'm doing is using it for a file and print server?

---

### Post by Kilz on 2007-09-22
> **mfreeman73 said:**
> I just made a file and print server with 1gb Ram and an older AMD64 Athlon chip (single-core). Also, no GUI installed. I'm just using the CLI.

Without thinking, I installed the server with the i386 disk (7.04) instead of the 64bit disk. Now I have things like I like it and really don't want to do a reinstall.

Is there any benefit to going with the 64 bit version when all I'm doing is using it for a file and print server?

Yes, you paid for all the performance from the hardware. But with using a i386 build is like buying a corvette and pulling out 4 spark plug wires.

---

### Post by Yellow Pasque on 2007-09-23
As usual, Kilz is exaggerating. You'd get a significant performance improvement on CPU-limited tasks, like encoding video or compiling software. In your case, the performance of your server is disk-bound, so there would only be a small (probably negligible with your usage) performance benefit. It's not worth a reinstall.

(You still have all the cylinders firing in your 'Vette, you're just using slightly lower octane fuel. :P)

---

### Post by Kilz on 2007-09-23
> **Temüjin said:**
> As usual, Kilz is exaggerating. You'd get a significant performance improvement on CPU-limited tasks, like encoding video or compiling software. In your case, the performance of your server is disk-bound, so there would only be a small (probably negligible with your usage) performance benefit. It's not worth a reinstall.

(You still have all the cylinders firing in your 'Vette, you're just using slightly lower octane fuel. :P)

I dont think so. Its running the chip full time in 32bit mode. Are you suggesting that a server cant be a high usage application? Since we have no idea of the load on the machine no one can tell the exact numbers. But he is not getting all the performance from the hardware.

---

### Post by Yellow Pasque on 2007-09-23
> **Kilz said:**
> Are you suggesting that a server cant be a high usage application? Since we have no idea of the load on the machine no one can tell the exact numbers.

I'm suggesting that file serving to a small network (which I'm assuming this is based on the other hardware) isn't a CPU-intensive task, and that the users of the network won't be able to tell the difference whether their files come from a 32-bit or 64-bit server.

> **Kilz said:**
> But he is not getting all the performance from the hardware In this scenario, the benefit reaped from reinstalling with 64-bit isn't worth the time/cost it would take to do so. Think of it as a very poor Return On Invetment (ROI).

---

### Post by Kilz on 2007-09-23
I think its best to agree to disagree since we dont have all the information. We also don't know the time involved. Since its the only cost that we know about. Hardware already is bought, and the software should be free.

---

### Post by mfreeman73 on 2007-09-23
It's actually a small home network with several windows computers and one ubuntu desktop. So, not much use at all. Basically, a place to store files and also to handle printing. That's why i wasn't sure if it would actually make any difference.

---

### Post by Kilz on 2007-09-23
> **mfreeman73 said:**
> It's actually a small home network with several windows computers and one ubuntu desktop. So, not much use at all. Basically, a place to store files and also to handle printing. That's why i wasn't sure if it would actually make any difference.

Maybe it wont. But if you ever have to reinstall the os you might consider the 64bit version. That or if you just want to try something new. Eventually everything will be moving that way anyway. For a server its basically the same install.

---

