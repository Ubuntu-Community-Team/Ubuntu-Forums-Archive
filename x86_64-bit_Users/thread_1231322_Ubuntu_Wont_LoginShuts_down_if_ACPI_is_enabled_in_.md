---
title: "Ubuntu Wont Login/Shuts down if ACPI is enabled in bios"
date: 2009-08-04
forum: x86 64-bit Users
---

### Post by frmdstryr on 2009-08-04
I built a new computer (phenom x3 720, 8gb ram, radeon hd 3300 onboard) a month or so ago.  Installed a fresh copy of jaunty amd64 version.  After the first few updates that ubuntu kept bugging me to do, the system started acting up. Several things are going wrong...

1st) My rosewell pci serial card doesn't detect anymore says /dev/ttyS0 (or ttyS1) device not found and I cannot use my serial ports. They did work on a fresh install, and it works with the live cd.

2nd) When I have acpi enabled in bios the computer will automatically shutdown, right after loading up or like 5 mins after login,  it did this during the install and said something like "cpu reached critical temperature 130C" or some bs like that. The computer runs at 41C, never overheated, bios will shut it down if it reaches 71C so 130C is way off.  It does it with the live cd.

3nd) When I disable acpi in the bios so I can use the computer (stops problem 2), my sound doesnt work, as soon as it plays the first login sound, the audio locks up and keeps repeating the small part loaded in memory.

I would appreciate the help or any kind of input...  The main issue is the 1st one because I need to use my serial ports.... Thanks.

---

### Post by fballem on 2009-08-04
I don't wish to hijack this thread, but I'm still going through the learning curve.

What is ACPI?
Why would I use it?
How do I set it up in BIOS - such as are there specific terms that I would look for in bios?
Assuming that I would want it to work (based on these answers), can I enable it in ubuntu 9.04 AMD 64?

Many thanks,

---

### Post by philinux on 2009-08-04
> **fballem said:**
> I don't wish to hijack this thread, but I'm still going through the learning curve.

What is ACPI?
Why would I use it?
How do I set it up in BIOS - such as are there specific terms that I would look for in bios?
Assuming that I would want it to work (based on these answers), can I enable it in ubuntu 9.04 AMD 64?

Many thanks,

Tur tut you did hijack. Always best to create your own thread. Otherwise gets very confusing. :confused:

---

### Post by frmdstryr on 2009-08-04
I don't fully know what acpi is, from what I know (correct me if I'm wrong) it is something that gives information of power management like cpu temp, shutdown, sleep, etc. stuff that has to deal with power saving...  

You'd use it because it makes more info about the computer (and functions like sleep) available.

It's enabled in bios by default, you can disable it. It says ACPI on my computer and you can disable/enable it.

It should be working there just seems to be a problem with my setup or 9.04's acpi code (maybe both?).

Somebody correct me if im wrong on all that, i didnt look it up.

So any help with my problems?  Thanks.

Decided to look it up, check here [http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)

---

### Post by fballem on 2009-08-04
frmdstryr - thanks for answering my question. I hope that you get an answer for yours.

philinux - thanks for the suggestion

---

### Post by frmdstryr on 2009-08-06
Still no help... Anyone???

---

