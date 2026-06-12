---
title: "Freezes when applying changes"
date: 2007-09-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by pnotequalsnp on 2007-09-08
I installed 7.04 after some hassle with grub.  I finally logged on and proceeded to install the updates.  It downloaded all the packages and froze on the part where it says: "applying changes" and "preparing packages".

Any help would be great!

p.s. if anybody knows if acpi=off is bad, please let me know...

---

### Post by Cappy on 2007-09-08
I had this happen the first time I updated ubuntu also.

You can check your system logs in System--> Administration --> System Log but it probably isn't worth digging through to find the problem.

Try running
```

sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

```
and see if it runs successfully this time. If it freezes again try Alt+control+Backspace and see if that restarts X (X is Ubuntu's windowing system).

If your hardware won't boot without turning acpi off the recommendation is to use
```
noapic nolapic
```
instead.

---

