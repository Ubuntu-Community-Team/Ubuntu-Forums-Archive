---
title: "Setting up DELL A920 Printer"
date: 2005-04-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by smb2004 on 2005-04-24
I am in love with ubuntu.  i have hoped around from disto to distro and have found my one.  i have everything set up how i want (even chroot with flash) but i cant get my printer to work

it is a (usb) dell A920 ~ research tells me it is a rebranded lexmark Z600 or X1100

i've messed around with those different drivers and the ones under the dell section but no sucess.  any ideas?  this is the last thing from makeing me a linux only user!

---

### Post by Xerampelinae on 2005-04-24
Maybe do some searching... *shrug*  I don't have the printer, but I found this...

[http://forums.gentoo.org/viewtopic.php?t=149001](http://forums.gentoo.org/viewtopic.php?t=149001)

And in particular...

[QUOTE=marwyg]The Motherlode!
I, among thousands of newbies, apologize for my beginner status. I have been trying to install the Lexmark Z605 within my XANDROS (Debian-based) desktop. I know virtually nothing about Gentoo, but I am familiar with browsing. Here is a link that every Lexmark Z600 series printer should have, if you are also using a Debian or Debian-based distro...

[http://members.cox.net/twsnnva/Linux.html](http://members.cox.net/twsnnva/Linux.html)

Scroll toward the bottom of the page, and look for the heading "Setting up Printing". Download the RedHat Linux Z600 printer driver from Lexmark. (There is a link.) Download the install script.(There is a link.) Follow Thomas's directions. (Put both files in the same folder and run his script.) Go to your printer control panel. Select as Default "Lexmark_x1150". Open a text editor. Type something. Now print it. And , Wow! It works. Every Linux forum populated with woebegotten Lexmark printer owners should post this link. I wanted to thank Thomas, whoever and wherever he may be, but there was no email link. But thanks, Thomas. It could not have been easier.
[/QUOTE]

---

### Post by brim4brim on 2005-07-06
Hi I have this printer too, I searched Dell's forums and it says the following driver should work


[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:390:0:0&emeaframe=&fileID=1151](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:390:0:0&emeaframe=&fileID=1151)

from Lexmarks webpage however I'm having trouble installing it so if anyone knows how to install this then can you post it up here.  I followed the instructions in the readme but they are only for Red Hat/Suse so when I go to add the printer after running the program I can't see it in the list under Lexmark or Dell.

---

### Post by Footer on 2005-08-13
[QUOTE=brim4brim]Hi I have this printer too, I searched Dell's forums and it says the following driver should work


[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:390:0:0&emeaframe=&fileID=1151](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:390:0:0&emeaframe=&fileID=1151)

from Lexmarks webpage however I'm having trouble installing it so if anyone knows how to install this then can you post it up here.  I followed the instructions in the readme but they are only for Red Hat/Suse so when I go to add the printer after running the program I can't see it in the list under Lexmark or Dell.[/QUOTE]

I see this thread is old but your post is only a month old.  Did you ever get your printer installed?  I'm having the exact same problem.

Thanks.

---

### Post by Footer on 2005-08-13
Never mind!  I followed the directions in post #2, especially this link:

[indent][http://members.cox.net/twsnnva/Linux.html](http://members.cox.net/twsnnva/Linux.html)[/indent]
and got the printing to work!  Now, to get the scanner portion of this printer/scanner working.  Any ideas?  When I fire up Kooka, it only gives me the choice of:

[indent]vrl:/dev/video0[/indent]
as the scanner ... ?

Any help, greatly appreciated!

---

### Post by qgil on 2005-09-27
My parter got this printer as a gift and, just for the statistics, now there is one more Ubuntu user with this Dell A920.  :)

It would be good to have it automatically recognized, or generate a Ubuntu friendly dirver, or at least with .deb package to install. Apparently <a href="http://www.beretti.org/blog/index.php/2005/03/17/19-packages-debian-et-ubuntu-pour-limprimante-dell-a920">someone tried</a> and got the packages, but Dell wouldn't allow this legally.

Myself can't do this because of lack of skills, sorry.  :(

---

### Post by Baphijmm on 2006-01-16
Hooray for digging up threads like this, eh?

Anyway, I followed the instructions on the pages given, and for some reason, it still refuses to print.  Any ideas as to why this might be?  The computer behaves as though it sent the file to the printer, but nothing is printed, and the job closes as though it had.

---

### Post by darundal on 2006-08-28
Ok, trouble getting the .debs, can anyone post them or e-mail them to me? Thanks!

---

### Post by blent07 on 2006-08-30
Same situation, and I'm trying the linux driver for the Lexmark Z600, as brim4brim pointed to. Hopefully that'll do something. 

And what's Kooka?

---

### Post by darundal on 2006-09-14
Ok, found another guide that worked here: 
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters)
After about 1 minutes of blind copying and pasting, and a restart (the last command at the very bottom didn't work, but it didn't need to) I am now printing from my printer. BOOYA!

---

### Post by ner0tic on 2006-10-29
> **darundal said:**
> Ok, found another guide that worked here: 
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters)
After about 1 minutes of blind copying and pasting, and a restart (the last command at the very bottom didn't work, but it didn't need to) I am now printing from my printer. BOOYA!

the last command on the bottom is a typo

should be something more like:
> sudo /etc/init.d/cupsys restart

but my issue i have is i can't find z600.ppd or a listing of z600 driver after following those steps.

it's seeing it as a lexmark a920 now but i can't locate the driver anywhere.

---

### Post by bollix47 on 2006-10-30
This routine worked for me in Dapper but now in Edgy I'm having the same issue as above.  No z600 driver listed when trying to add the printer.  

If anyone has this working in Edgy the solution would be appreciated.

Thanks.

---

### Post by bollix47 on 2006-10-30
Was able to get this working in Edgy by clicking on 'Install Driver' in the add printer routine and navigating to /usr/share/cups/model

Select the Lexmark*.ppd driver and apply.

The Z600 driver will now be listed under the lexmark drivers in the add printer dialog.

Only thing I can think of is there's some kind of different structure or method between dapper and edgy as I did not have to do this in dapper.  It was simply listed under the lexmark drivers after running the instructions in this howto.

---

### Post by vendejp on 2007-03-10
I have the exact same issues... I went through all the steps in that other post and I still dont see the ppd or z600 in the driver list.



> **ner0tic said:**
> the last command on the bottom is a typo

should be something more like:


but my issue i have is i can't find z600.ppd or a listing of z600 driver after following those steps.

it's seeing it as a lexmark a920 now but i can't locate the driver anywhere.

---

### Post by vendejp on 2007-03-18
Got it....
this is the correct command for the very end, but otherwise I followed things pretty much exact.
sudo /etc/init.d/cupsys restart 

At the end, when adding the printer, I browsed to "/usr/share/cups/model" and actually clicked on the gzip file (Lexmark-Z600-lxz600cj-cups.ppd.gz).  I was looking for a ppd file.

This installed the printer and it works now (printing, havent tried scanning or copying, though I dont expect much from that.  I just wanted printing).

> **darundal said:**
> Ok, found another guide that worked here: 
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters)
After about 1 minutes of blind copying and pasting, and a restart (the last command at the very bottom didn't work, but it didn't need to) I am now printing from my printer. BOOYA!

---

### Post by bently4677 on 2007-11-24
I just got my a920 scanner working through xsane. I had to setup the backend drivers from [http://ca.geocities.com/freshshelf@rogers.com/scanner_driver/download.html](http://ca.geocities.com/freshshelf@rogers.com/scanner_driver/download.html) and then it worked.

---

### Post by Commander Keen on 2008-01-10
> I just got my a920 scanner working through xsane. I had to setup the backend drivers from [http://ca.geocities.com/freshshelf@r.../download.html](http://ca.geocities.com/freshshelf@r.../download.html) and then it worked.

Hi. Could you walk me through the installation of a driver for the scanner in the A920?

(I want to install the driver on my server(backend) and then use it on the network using xsane as frontend)

I'm using ubuntu 7.10 and am relatively new to the linux-world thus I'm quite unsecure on the command line

---

### Post by superTP on 2008-02-16
I finally got this working on Gutsy.  

If you see something like "Cannot Process Raster. (/usr/lib/cups/filter/rastertoz600) stopped with status 1" in /var/log/cups/error_log, try running this command.

chmod -R 755 /usr/local/z600llpddk

The rastertoz600 executable needs the utilities in that directory but the default install adds them so only root can access them.  You might want to be more discreet with the permissions settings (like setting up a printer group) if you are paranoid but 755 works for all users.

---

