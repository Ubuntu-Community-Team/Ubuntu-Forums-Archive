---
title: "Installing Modem Drivers"
date: 2007-07-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by baseballmanager on 2007-07-01
I am trying to to install the drivers for my modem and am having trouble. I found a file with them but can't figure out how to install them.  The file is "agrsm-alpha.tar.bz2" and I have it on a flash drive.  I am stuck on step 2 in the installation.  Here it is (the bold parts are what I'm having trouble with):

[I]Step 2
To install the Agere soft modem driver in LINUX, [B]extract the driver package
(unzip /tar -xzvf)[/B] in a directory under Linux and [B]run "make module" and then
"make install" from the command prompt. [/B] This will install both the Agere soft
modem controller driver agrmodem.ko and the Modem serial interface driver
agrserial.ko.
To install the modem driver you must be logged in as root.[/I]

First, which directory should I extract the package to?  Also, should I use the Terminal to extract it (how should I extract it in terminal?)?

Second, how do I run the  "make module" and "make install"? When I run them in Terminal it says that the command cannot be found.

---

### Post by razeshkale on 2007-07-06
after extracting file open terminal and drag and drop file into terminal 
it will install automagically

---

