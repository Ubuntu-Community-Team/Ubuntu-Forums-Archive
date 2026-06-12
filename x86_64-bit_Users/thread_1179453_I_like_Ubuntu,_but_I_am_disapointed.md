---
title: "I like Ubuntu, but I am disapointed"
date: 2009-06-05
forum: x86 64-bit Users
---

### Post by 1richard on 2009-06-05
Generally the people on Ubuntu are great in giving help to those that want it, but when it comes to printers, very little or no help is given, even when it will not take to much effort on someone's part. I know that making a 64 bit version of a 1320c Dell Color Laser driver out of a i386 version will take a little effort.  I am merely a end user who needs help and each time I usually get it, so I am thankful for that help that is given, but Ubuntu or a tech should read and try to get drivers for all the old printers for x64 bit systems, thanks for listening to my rant.

---

### Post by logos34 on 2009-06-05
do you have the source pkg for the i386 version driver? You could try compiling it

---

### Post by 1richard on 2009-06-05
No, it is a Fuji driver for the xerox 585 and they made it only for the i386

---

### Post by logos34 on 2009-06-05
bummer...printers in linux can be a drag

---

### Post by paulisdead on 2009-06-05
Is there a PPD file for the printer?  I've gotten unsupported printers to work by extracting the PPD file from the windows drivers and using the "Have PPD file" option when setting up the printer in ubuntu.

---

### Post by bolweval on 2009-06-05
> **paulisdead said:**
> Is there a PPD file for the printer? I've gotten unsupported printers to work by extracting the PPD file from the windows drivers and using the "Have PPD file" option when setting up the printer in ubuntu.
 
Thats kinda what I did to get my Dell 3115 printer to work with Linux, someone here was kind enough to post the driver in text form, I copied it to a text editor, saved it and renamed it 3115 dell.PPd and used the "Have PPD file" option when I set it up. 
 
Burned that baby to a CD  ; )

---

### Post by ddales on 2009-06-07
Download the Linux driver for the Xerox DocuPrint C525 Printer

---

### Post by 1richard on 2009-06-08
I did download the 525 driver and converted it on a 386 computer and it will not see the computer with this driver and the 386 ppd, so that is where I am now, have a printer I need, and cannot use it

---

### Post by 3Miro on 2009-06-08
Unless you have the source code for the printer driver, you cannot just go from 32-bit to 64-bit.

My solution was to use Virtual Box, install the printer in a 32-bit Ubuntu version and then share it over the network (the printer was a IP1800 Cannon). I can now print from any of my 64-bit machines.

Other options are: recompiling (only if you have the source) or 32-bit emulation (which I don't know how to set up, it may or may not work here)

PS: Unlike Mac and Windows, Linux actually supports drivers. In the few cases where something isn't working, it is manufacturer's issue and not Linux.

---

### Post by LucasCordina on 2009-06-08
Well a virtual machine is always a good idea...


but maybe you should leave my opinion to last, since I'm new at this myself =]

---

### Post by linux4life88 on 2009-06-09
I like to use a lot of the "extra" features of my printer and I have found that no matter what I do they will not print right (usually the alignment is off) unless I print from a Windows operating system with the drivers and software installed. It is a little frustrating and I can understand your complaints because I have experienced the same problems myself.

---

### Post by Sef on 2009-06-10
Have you thought about a i386 print server?

---

### Post by 1richard on 2009-06-26
still no help on the 1320 maybe I will have to pay somebody to make a driver for the 64 bit systems, any takers????

---

### Post by 3Miro on 2009-06-26
VirtualBox is not a hard solution, just ugly. Some printers just won't work with 64-bit systems (my canon is an example).

Sef's idea on the 32-bit print server is interesting. I am not sure what it will take, but it might work.

---

### Post by 1richard on 2009-06-26
It will not work, as you cannot install the drivers on a 64 bit computer

---

### Post by markharding557 on 2009-06-27
if you need 32bit compatabiltily then use 32bit ubuntu

---

### Post by philcamlin on 2009-06-27
my canon mp360 is suported by a bjc 8200 driver :D 

good printouts too

---

