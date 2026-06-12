---
title: "Lexmark X1195"
date: 2005-11-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by tiagobt on 2005-11-06
I am trying to install the multifunctional printer/scanner Lexmark X1195 (X1100 series) on my Mac Mini. I followed the tutorial at [HOWTO: Lexmark Printers]("http://ubuntuforums.org/showthread.php?t=49714") and it seemed to be working until the last step... However, when I tested it using the command "./z600", I got the following output:

```
bash: ./z600: cannot execute binary file
```

Does anyone know why it didn't work? Could it be because I'm using Linux/PPC (instead of Linux/x86)? Any other way of making my printer work? It's weird that there was no error message during installation.

---

### Post by farruinn on 2005-11-06
Your assumption is most likely right - that the binary is for x86 and not PPC. From reading the howto it looks to me like the ppd is installed though, so I would suggest trying to set up the printer through the System>Administration>Printing dialog anyway.

Edit: Had a thought, do 'file z600' to see what architecture it's for.

---

### Post by tiagobt on 2005-11-07
[QUOTE=farruinn]Your assumption is most likely right - that the binary is for x86 and not PPC. From reading the howto it looks to me like the ppd is installed though, so I would suggest trying to set up the printer through the System>Administration>Printing dialog anyway.

Edit: Had a thought, do 'file z600' to see what architecture it's for.[/QUOTE]

```
tiago@ubuntu:/usr/lib/cups/backend$ file z600
z600: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), not stripped
```

Yes, it seems that the binary is for x86. I tried to add the printer anyway (the Z600 printer, actually), but it doesn't seem to respond to the tests. Thanks for the help though. If anyone has an idea that may help me, please tell me! It's kind of frustrating not being able to use my new printer...

---

### Post by tiagobt on 2005-11-13
I made some progress trying to get the scanner working. What I did was install the CVS backend and frontend of sane, and also the package xsane from Ubuntu repositorries. I only got something working running xsane as root (though I receive a message saying it's not safe). When I try to preview the image, the scanner responds and starts making noise. The first times I tried, the scanner even moved with the light on, as if it were working. But it stopped moving halfway and only a blank image was displayed in xsane. Does anyone know how to fix that?

About the printer itself, I found a PPD file that is supposed to work:
[http://www.linuxprinting.org/pipermail/lexmark-list/2005q1/002907.html](http://www.linuxprinting.org/pipermail/lexmark-list/2005q1/002907.html)
I'm just not sure how to use it. I opened it and I was able to add the printer (a new pritner appeared), but I don't think the file replaces the driver, right? Does this file help anyhow?

Thanks

---

### Post by Ubuntist on 2005-11-17
I doubt that this will be of much help, but, 
[INDENT]
1. If you're running Breezy, there is an updated version of the Lexmark help thread: 
[http://www.ubuntuforums.org/showthread.php?t=83456&highlight=lexmark+printer](http://www.ubuntuforums.org/showthread.php?t=83456&highlight=lexmark+printer)
2. I've just installed a Lexmark Z55 (on a Pentium, not a PPC, though), and I found that the printer seems to work just fine even though the backend (z55) produced no output when I ran it.
[/INDENT]

---

### Post by tiagobt on 2005-11-28
[QUOTE=Ubuntist]I doubt that this will be of much help, but, 
[INDENT]
1. If you're running Breezy, there is an updated version of the Lexmark help thread: 
[http://www.ubuntuforums.org/showthread.php?t=83456&highlight=lexmark+printer](http://www.ubuntuforums.org/showthread.php?t=83456&highlight=lexmark+printer)
2. I've just installed a Lexmark Z55 (on a Pentium, not a PPC, though), and I found that the printer seems to work just fine even though the backend (z55) produced no output when I ran it.
[/INDENT][/QUOTE]
Thanks for trying! But it didn't work either...

---

