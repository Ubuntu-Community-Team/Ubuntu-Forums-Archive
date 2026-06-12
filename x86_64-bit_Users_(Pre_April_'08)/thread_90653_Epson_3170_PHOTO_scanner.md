---
title: "Epson 3170 PHOTO scanner"
date: 2005-11-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by waster on 2005-11-15
This is not a linux friendly scanner, although there is a 32 bit application with some open source plus some proprietary binary, which is 32 bit. Putting my anger and frustration aside...

I have installed libsane-extras which claims to have the epkowa driver I need. (NB the epkowa iscan software has binary elements, but these are not needed for all scanners, 3170 included. Google for iscan-free rpm to see how they did it.) However, no scanner is detected by
<code>
scanimage -L
</code>

Same applies using the proprietry stuff (aliened rpm from avansys.jp)

Using a 32 bit chroot, the scanner is half-detected (scanimage -L works). I can launch any of the scanning programs, but none can send commands to the scanner.

USBView gives away the reason which I can't fix: the scanner shows up in red, meaning that it is detected but no driver is loaded. NB this is true in 32 bit chroot or 64 bit native.

Please help me work out how to get the driver loaded, ideally in 64 bit mode. Nothing useful in /var/log/messages - just lots of "cmd failed," presumably when it is failing to contact the scanner.

Many thanks,
Jack

---

### Post by etitor on 2005-11-15
Maybe you just want to take a look at this:

[http://ubuntuforums.org/showthread.php?t=65656]("http://ubuntuforums.org/showthread.php?t=65656")

Hope it helps.

H&#233;ctor

---

### Post by waster on 2005-11-16
Thanks for the link. Unfortunately, these scanners use completely different back-ends. the 3170 needs the epkowa back-end.

anyone know why the epkowa backend in libsane-extras doesn't work? this is presumably compiled nicely for amd64.

---

### Post by etitor on 2005-11-17
[QUOTE=waster]Thanks for the link. Unfortunately, these scanners use completely different back-ends. the 3170 needs the epkowa back-end.

anyone know why the epkowa backend in libsane-extras doesn't work? this is presumably compiled nicely for amd64.[/QUOTE]
Are you sure my 4990 is not using epkowa?

I will quote my post in the above-mentioned thread:
[QUOTE=etitor]But Sane seems to support the 4990 through one of its external backends, epkowa. See:

    [http://www.sane-project.org/lists/sa....html#S-EPKOWA](http://www.sane-project.org/lists/sa....html#S-EPKOWA)[/QUOTE]

---

### Post by waster on 2005-11-30
Well, not really, because I had to use a 32 bit chroot. I had read that the binary components were not needed for the 3170, but this turned out not to be true. I did NOT need to install iscan.

I did install libsane-extras which has an epokwa library, but only the free bits.

modifications to default setup were:
Comment the "epson" line in /etc/sane.d/dll.conf
otherwise it detects the scanner twice, and sends epson commands

Then, using an environment variable
SANE_DEBUG_EPKOWA, I discovered that two files were missing: one library which is only in the iscan package, and a .bin file. I had previously compiled iscan, so I just took the relevant .so (from a choice of five) and stuck it directly in /usr/lib
the bin file had to go in /usr/share/sane/epkowa which needed to be created.

seems to work well now, although it's incredibly annoying that there is no 64 bit library.

---

### Post by jspies on 2006-08-26
I have installed epson 2.1.0 in a chrooted 32-bit environment and I cannot find any .bin files in the installation.  I have succeeded in getting the iscan interface running as root but iscan (and xsane) cannot send any commands to the scanner.

Any solution?

---

