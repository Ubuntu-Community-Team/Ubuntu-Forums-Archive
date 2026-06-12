---
title: "cannot make epson stylus c86 print"
date: 2007-09-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by hardinge on 2007-09-19
Hello all, I hope that I can get some help here. I am a long time reader but first time poster.

I have an AMD64 dual core with 512 ram running the 64bit version of fiesty. I have connected the printer and set it up using gutenprint and according to fiesty it is ready. The problem is that every time I print something the status goes         immediately to job stopped and will not resume. If there is any other info that is needed please let me know and I will post it ASAP. Thank you in advance for your help.

---

### Post by dabl on 2007-09-19
For my C84, I needed to install the package "foomatic-db-gutenprint" first, and then set up the printer in CUPS.

---

### Post by hardinge on 2007-09-19
Thanks for the help. I installed foomatic-db-gutenprint which added the last two choices of driver when I set up the printer. The results I got with the choices are below.

High Quality Image (gutenprint CUPS) (Epson)  = Job Stop

High Quality Image (gutenprint CUPS) (Epson) = Job Stop

High Quality Image (gutenprint CUPS) (Expert) = Job Stop

High Quality Image (gutenprint CUPS) (Simple) = Job Stop

High Quality Image (gutenprint IJS) = Garbage Printing

High Quality Image(gutenprint IJS, Simplified) = Garbage Printing

Which choice did you use when you set up your printer, or how did you configure it to stop the garbage?

---

### Post by dabl on 2007-09-20
I'm running Kubuntu, so the "add printers" dialog may be a bit different.  Basically, after installing that foomatic-db-gutenprint package, I went in to System Settings>Printers>Add Printer, which is a KDE utility and probably won't help you on Ubuntu.  I've got a recording going on at this moment and can't reboot into Ubuntu, but I will later if you can't get it going.  I was able to see the C84, and then after I clicked on it, I chose one of the two Gutenprint options that I was presented.  It is called "Foomatic + Gutenprint-ijs-simplified.5.0".

---

### Post by hardinge on 2007-09-20
I appreciate your help, because I still have no joy printing yet.

---

