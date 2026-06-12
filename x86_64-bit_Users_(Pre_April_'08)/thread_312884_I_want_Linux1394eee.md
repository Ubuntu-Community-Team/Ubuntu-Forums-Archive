---
title: "I want Linux1394eee"
date: 2006-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by Unterseeboot_234 on 2006-12-05
Hello,

I'm running AMD 64-bit and ubuntu 64-bit. I have run into problems installing. My experience has shown me I can download a bunch of junk that doesn't work, hogs RAM and really loads down the cpu clock-cycles. Reformat, reinstall ubuntu.

I did 
```
~$ lspci
0000:04:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
```

The Linux1394.org lists that TI chip as "very good" compatible. On the install for the driver(s) it takes some repository work.

I did 
```
~$ uname -a
Linux vcbrad-desktop 2.6.15-27-amd64-generic #1 SMP PREEMPT Sat Sep 16 01:50:50 UTC 2006 x86_64 GNU/Linux
```

The install instructions at Linux1394.org start out saying ... "If you have kernel 2.4.18+, skip to point 7."

**MY QUESTION:** is this install "generic" to the 32-bit and the 64-bit ubuntu. My goal is dvGrab working with a firewire.

---

### Post by Unterseeboot_234 on 2006-12-05
I guess I answered my own question. I post this update to help others.

Thanks to the 32-bit side of these forums I found the user-wiki for Drake

[http://ubuntuguide.org/wiki/Ubuntu_dapper]("http://ubuntuguide.org/wiki/Ubuntu_dapper")


Read, read, read between it and from
[http://www.linux1394.org/start_install.php]("http://www.linux1394.org/start_install.php")
They give fuzzy installation instructions to get going.

Downloaded the c header files so I can sudo ./configure. I still don't know about the options to connect the source builds with a gNome, or a xV but at least the .zip files extract and compile.

Because I have the chip on my firewire card and the dvCAM from the tested list, the raw1394 installed. That's about all I got done today.

I can capture with "sudo dvgrab --interactive". That gives me a blind terminal that runs my connected camera and records to the hard disc.

I can then open Kino from the menu, Open file button, navigate to the dvGrab001.avi.

I wanted Kino to use its Capture module within Kino.

There is another user-wiki
[https://help.ubuntu.com/community/HowToCaptureDigitalVideo]("https://help.ubuntu.com/community/HowToCaptureDigitalVideo")

There, they are trying to mod the kernel. I'm trying to stay away from that. I'm a java enthusiast. Java is modular. Java JMF library would have done this *IF *some kind of legal dispute 2003 had not halted development. JMF does not recognize PCIe. Beware what codec you install on your machines because that is what the java dispute is all about. Codecs are sticky and travel with distributed software.

So, if you've got i686 learn to build your own sources. :neutral:

---

### Post by doobit on 2006-12-05
6.06 32 bit already has the ieee1394 modules built in and work pretty well with the hotplug. I've used them myself with MainConcept's MainActor video editing as well as Kino with a TI based board.
I don't know about the 64 bit.

---

### Post by Unterseeboot_234 on 2006-12-05
So, I had some kind of 1394eee module in my original ubunt AMD-64bit install. However, dvGrab refused to run and the reason was it wanted raw1394eee module.

The next step is to find out how ./configure works with four packages to make up the complete modules for sound, dv, 1394eee, and libsampler. Evidentially, there is a lot of functionality, including streaming vid over the internet.

Believe me. I'm just glad I've got SOMETHING on my new 64-bit machine that is 64-bit and that can use 64-bit to SCSI.   :)

---

