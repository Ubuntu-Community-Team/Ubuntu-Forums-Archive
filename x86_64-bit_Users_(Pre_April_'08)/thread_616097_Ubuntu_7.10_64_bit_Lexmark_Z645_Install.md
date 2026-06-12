---
title: "Ubuntu 7.10 64 bit Lexmark Z645 Install"
date: 2007-11-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by sdrobinson on 2007-11-17
[CENTER][B]Lexmark Z600 Series Printer
Ubuntu 7.10 (64 bit) Install[/B][/CENTER]

**These are the steps I took to install my Lexmark Z645 printer on my Ubuntu 7.10 64 bit system.  I don't know exactly how many forums and websites I searched for this information but never the less here it is.  I just didn't want to take credit from all of the other helpful Ubuntu users out there.  I hope this helps others like others have helped me.**
 
**Download and Install Packages**
sudo apt-get install alien printconf

**Download the Lexmark Drivers**
[URL="http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz"]CJLZ600LE-CUPS-1.0-1.TAR.gz
[/URL]
**Make a work folder**
mkdir lexmark

**Move the Lexmark file to the lexmark folder**
mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark

**Move to the lexmark folder**
cd lexmark

**Extract the Driver**
tar -xvzf  CJLZ600LE-CUPS-1.0-1.TAR.gz

**Extract the binary portion of the script**
tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz

**Extract the contents produced by tail**
tar -xvzf install.tar.gz

**Convert unusable rpm packages to tgz**
alien -t z600cups-1.0-1.i386.rpm
alien -t z600llpddk-2.0-1.i386.rpm

**Extract the tgz's to / putting the files in their right place**
sudo tar xvzf  z600llpddk-2.0.tgz -C /
sudo tar xvzf z600cups-1.0.tgz -C /

**Run ldconfig to setup the printers backend**
sudo ldconfig

**Switch to the Cups Model Director**y
cd /usr/share/cups/model

**Extract the .ppd file**
sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz

**Now Restart Cups**
/etc/rc2.d/S19cupsys restart

**Now setup your printer by goint to System > Administration > Printing**

**I'm now trying to figure out how to share my printer through Samba so any ideas would be very helpful**

---

### Post by docadams on 2007-11-19
This is as close as any one has gotten me to getting the Lexmark Z645
printer to working.

I am using Kubuntu 7.10.  All the steps worked and lpstat -t shows
printer ready.  Had to go back and setup default printer.

Queue has print job in it, but it is not printing.  Google search
showed that some one had to do a

sudo apt-get install libstdc++5, but I assume that since libstdc++6 is
installed already, that this is not the issue here.

Any help greatly appreciated on this one.  I'll set up the trusty
old Epson C44UX.

Thanks in advance

Chuck  [email]k7qo@commspeed.net[/email]  for direct reply

---

### Post by wavesound on 2007-12-05
HI 
Will this work for the C534N?
As I can't get this to work at all ( and it did in 6.06 which is anoying)
Cheers
Bob

---

### Post by Thelasko on 2008-01-08
Thanks, so much!  I have been working on this for days and your instructions finally worked!  Now on to that Samba problem.

---

### Post by 6568912 on 2008-01-09
Thank you Amigo :guitar: i hope it will work with lexmark x1160:lolflag:

---

### Post by Thelasko on 2008-01-09
As far as that Samba problem I notice that the GUI doesn't set the password (it's separate from your user password).  To do this "Type sudo smbpasswd -a username, replacing “username” with your own username. Press Return to run the command."  Retrieved from [here]("https://help.ubuntu.com/7.10/internet/C/networking-shares.html").

---

### Post by Kilz on 2008-01-09
Thank you sdrobinson, the install instructions worked on a lexmark 605 at my daughters school. I have installed a few linux desktops for them because the content filtering from dansguardian is free.

---

### Post by Thelasko on 2008-01-14
I've found that in sharing my Z611 over my network I need to de-select "enable advanced printing features" on my Windows XP machine.  I don't know why, but if you are having problems sharing your printer over Samba I recommend it.

---

### Post by wavesound on 2008-01-15
> **wavesound said:**
> HI 
Will this work for the C534N?
As I can't get this to work at all ( and it did in 6.06 which is anoying)
Cheers
Bob

OK If you have the same printer you can use one of the drivers showing in CUPS.
I have used the optra driver that gives me postscript.

If you go to this link you'll see a link to 'File information' If you click this you'll see all the machines that the driver works for. I found one in the cups menu and used the Optra driver

Seems to work fine.


Cheers
Bob

---

### Post by nbv4 on 2008-02-13
does anyone know what might have gone wrong? Averything seems to go right, up until I got to the alien part...

```
nbv4@nbv4-desktop:~/Desktop/lexmark$ tar -xvzf install.tar.gz
globals.tcl
install
lexinstall
lexinstall.tcl
license
setup.tcl
testpage
usb.tcl
xlexinstall
xlexinstall.tcl
z600cups-1.0-1.i386.rpm
z600llpddk-2.0-1.i386.rpm
nbv4@nbv4-desktop:~/Desktop/lexmark$ alien -t z600cups-1.0-1.i386.rpm
Warning: alien is not running as root!
Warning: Ownerships of files in the generated packages will probably be wrong.
Warning: Skipping conversion of scripts in package z600cups: postinst postrm preinst
Warning: Use the --scripts parameter to include the scripts.
z600cups-1.0.tgz generated
nbv4@nbv4-desktop:~/Desktop/lexmark$ alien -t z600llpddk-2.0-1.i386.rpm
Warning: alien is not running as root!
Warning: Ownerships of files in the generated packages will probably be wrong.
Warning: Skipping conversion of scripts in package z600llpddk: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
z600llpddk-2.0.tgz generated
nbv4@nbv4-desktop:~/Desktop/lexmark$ sudo tar xvzf z600llpddk-2.0.tgz -C /
./
./usr/
./usr/include/
./usr/include/lexmark/
./usr/include/lexmark/linuxinkjetprinter.h
./usr/include/lexmark/cleaningdata.h
./usr/include/lexmark/clock.h
./usr/include/lexmark/portmonitor.h
./usr/include/lexmark/cartridgeuserinterface.h
./usr/include/lexmark/cartridgemanager.h
./usr/include/lexmark/errorcommunicator.h
./usr/include/lexmark/alignmentdata.h
./usr/include/lexmark/printjobmanager.h
./usr/include/lexmark/mediamanager.h
./usr/include/lexmark/printerdevice.h
./usr/local/
./usr/local/z600llpddk/
./usr/local/z600llpddk/utility/
./usr/local/z600llpddk/utility/lxbcalgn.out
./usr/local/z600llpddk/utility/bnsi1.lut
./usr/local/z600llpddk/utility/bnsi2.lut
./usr/local/z600llpddk/utility/lxbccln.out
./usr/local/z600llpddk/utility/bnsi3.lut
./usr/lib/
./usr/lib/liblexprintjob.a
./usr/lib/liblexz600core.so.0.0.0
./usr/lib/liblexprintjob.la
./usr/lib/liblexprinter.so.0.0.0
./usr/lib/liblexz600core.la
./usr/lib/liblexprintjob.so.0.0.0
./usr/lib/liblexprinter.a
./usr/lib/liblexprinter.la
./usr/lib/liblexz600core.a
nbv4@nbv4-desktop:~/Desktop/lexmark$ sudo tar xvzf z600cups-1.0.tgz -C /
./
./usr/
./usr/share/
./usr/share/cups/
./usr/share/cups/model/
./usr/share/cups/model/Lexmark-Z600-lxz600cj-cups.ppd.gz
./usr/lib/
./usr/lib/cups/
./usr/lib/cups/filter/
./usr/lib/cups/filter/rastertoz600
./usr/lib/cups/backend/
./usr/lib/cups/backend/z600
nbv4@nbv4-desktop:~/Desktop/lexmark$ sudo ldconfig
nbv4@nbv4-desktop:~/Desktop/lexmark$ cd /usr/share/cups/model
nbv4@nbv4-desktop:/usr/share/cups/model$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz
nbv4@nbv4-desktop:/usr/share/cups/model$ /etc/rc2.d/S19cupsys restart
open: Permission denied
 * Restarting Common Unix Printing System: cupsd                                start-stop-daemon: warning: failed to kill 5115: Operation not permitted
cupsd: Child exited with status 1!
nbv4@nbv4-desktop:/usr/share/cups/model$ 
```

I did it a second time, but with sudo in front of the aliens as well as the part where cups is restarted, but it's still not working. when I try to print a test page under Syetem -> Administration -> Printing, I get this error:


There was an error during the CUPS operation: 'client-error-document-format-not-supported'.

EDIT: drr, I'm stupid, you have to click "change" beside "make and model", then select Z600 for it to work.

---

### Post by Thelasko on 2008-02-13
So, nbv4, everything is working for you?:guitar:

---

### Post by weh on 2008-04-09
First off, thanks for the HowTo.  It made my z710 work.  :grin: However, the margin's wrong.  It prints at the edge of the left side of the paper. Anybody know how to move it over some?

---

### Post by Thelasko on 2008-04-09
Sorry, I don't know how to fix the margin thing.  But if this worked for you, you should [vote]("http://brainstorm.ubuntu.com/idea/4175/") to have these drivers installed by default in Ubuntu.

---

### Post by LaurasMom on 2008-06-18
I sure wish I understood how to do all that "script" stuff.  Can anyone tell me in very simple terms how I can install my z600 series printer?  I downloaded that file but that's as far as I got.

---

### Post by Thelasko on 2008-06-19
> I sure wish I understood how to do all that "script" stuff. Can anyone tell me in very simple terms how I can install my z600 series printer? I downloaded that file but that's as far as I got.

I'm guessing your are having problems using the terminal.  It's like the command line in windows.  Just go to Applications>Accessories>Terminal to open it. You should be able to cut and paste from the instructions into the terminal.

---

### Post by Thelasko on 2008-06-19
P.S. The parts of the instructions that aren't in bold are what goes into the terminal.

---

