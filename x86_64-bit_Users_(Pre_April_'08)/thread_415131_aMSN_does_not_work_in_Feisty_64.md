---
title: "aMSN does not work in Feisty 64"
date: 2007-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Garyu on 2007-04-20
When I load aMSN everything seems fine. But when I click to login I get the question "TLS not installed, choose your architechture" so I choose x86-64 and it says it is downloaded and installed, but same question pops up again when I click.

So I thought I would install it manually. Downloaded TLS 1.5 source and ran ./configure only to be told openssl is not installed. So I run "sudo apt-get install openssl" and that tells me openssl IS installed.

So I search the forums for an answer and find that I can just "sudo apt-get install tcltls" so I do, but then it tells me TLS is already installed!!!

Right now I am not very fond of aMSN developers. TLS is installed but they keep asking for it. Compiling TLS won't work because openssl is already installed but not found by ./configure

Anyone with a quick fix for this thing?

---

### Post by eentonig on 2007-04-20
No idea what's your problem. But aMSN works fine on my PC and has been doing so ever since I went Béta on Feisty.

---

### Post by r0nmad on 2007-04-22
After TLS is installed, exit or quit aMSN altogether and restart the application. I kept getting the same loop aswell and just restarting the application fixed it.

---

### Post by rogeriovinhal on 2007-04-22
Edit the /usr/lib/tls1.50/pkgIndex.tcl and change "package ifneeded tls 1.5" to "package ifneeded tls 1.50".

This should do it.

---

### Post by carvax on 2007-04-23
Yes, it works. , Change that line in the pkgindex.tcl is the answer. 

Thanks!!

---

### Post by Craga_89 on 2007-04-26
Having the same problem except I'm on regular 32 bit Feisty. The fix above editing pkgIndex.tcl doesn't seem to work either. Any other ideas?

---

### Post by Garyu on 2007-04-27
> **rogeriovinhal said:**
> Edit the /usr/lib/tls1.50/pkgIndex.tcl and change "package ifneeded tls 1.5" to "package ifneeded tls 1.50".

This should do it.

You're the best rogerio. This made it work. Quite strange though that one would have to go and fiddle like that with package settings... Thanks a lot. :)

---

