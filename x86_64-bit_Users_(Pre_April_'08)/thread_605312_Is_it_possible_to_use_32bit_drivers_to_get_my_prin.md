---
title: "Is it possible to use 32bit drivers to get my printer working?"
date: 2007-11-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cawgee on 2007-11-06
I am trying to get my Brother MFC6800 to work in Ubuntu 7.10 64bit. When I installed Ubuntu I see the printer listed there, but when I try and print data is received at the printer, but nothing happens. I am assuming that whatever data is sent is erroneous. The printer works fine in Windows XP with the Brother drivers. I found 32 bit Linux drives on Brother's site for my printer. They are i386 though and do not install. I have tried forcing the install of as mentioned here [http://ubuntuforums.org/showthread.php?t=425107](http://ubuntuforums.org/showthread.php?t=425107) 

It did not work. Here is the text from the terminal window.

$ sudo dpkg -i --force-architecture mfc6800lpr-1.1.2-1.i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package mfc6800lpr.
(Reading database ... 103479 files and directories currently installed.)
Unpacking mfc6800lpr (from mfc6800lpr-1.1.2-1.i386.deb) ...
Setting up mfc6800lpr (1.1.2-1) ...
mkdir: cannot create directory `/var/spool/lpd/MFC6800': No such file or directory
chown: cannot access `/var/spool/lpd/MFC6800': No such file or directory
chgrp: cannot access `/var/spool/lpd/MFC6800': No such file or directory
chmod: cannot access `/var/spool/lpd/MFC6800': No such file or directory
/var/lib/dpkg/info/mfc6800lpr.postinst: 4: /etc/init.d/lpd: not found
dpkg: error processing mfc6800lpr (--install):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 mfc6800lpr

From what i can see here it is telling me that it cannot make a directory because it doesn't already exist?:confused: The rest of the errors seem to stem from this error. I believe this is some sort of permission thing...

Am I pursuing a wise course of action here? If so, I am going about it right? If so, do you have any ideas why this is not working?

Thanks in advance for any and all help!

Adam.

---

### Post by psyburn on 2007-11-07
I have a Brother MFC-8500, however the Brother drivers have their problems installing on 32-bit
So I went and looked for a "native" or built-in driver
I found that choosing "Brother" -> "MFC-9050 (hl7x0)" worked great

2 mins with google (search: brother mfc-6800 linux cups) gave me this:
[http://www.linux-foundation.org/en/OpenPrinting/Database/BrotherFAQ#Brother_MFC-6800](http://www.linux-foundation.org/en/OpenPrinting/Database/BrotherFAQ#Brother_MFC-6800)

It says for you to use the MFC-9050 driver like I have to...

EDIT: I have ran my MFC-8500 on both 32-bit and 64-bit through both its parallel and USB ports and it works perfectly as a printer.
I have not worked very hard on using it as a scanner.

---

### Post by dcstar on 2007-11-07
> **Cawgee said:**
> I am trying to get my Brother MFC6800 to work in Ubuntu 7.10 64bit. When I installed Ubuntu I see the printer listed there, but when I try and print data is received at the printer, but nothing happens. I am assuming that whatever data is sent is erroneous. The printer works fine in Windows XP with the Brother drivers. I found 32 bit Linux drives on Brother's site for my printer. They are i386 though and do not install. I have tried forcing the install of as mentioned here [http://ubuntuforums.org/showthread.php?t=425107](http://ubuntuforums.org/showthread.php?t=425107) 

It did not work. Here is the text from the terminal window.

$ sudo dpkg -i --force-architecture mfc6800lpr-1.1.2-1.i386.deb
..........
From what i can see here it is telling me that it cannot make a directory because it doesn't already exist?:confused: The rest of the errors seem to stem from this error. I believe this is some sort of permission thing...

Am I pursuing a wise course of action here? If so, I am going about it right? If so, do you have any ideas why this is not working?

Thanks in advance for any and all help!

Adam.

I have been able to install the brhl2040lpr-2.0.1-1.i386.deb package with that method ok, it seems to have created all of its directories ok.

Actually, I usually use the "real" root account to do my stuff like this (and not sudo), so perhaps the Brother debs need this sort of thing due to some sloppy scripting?, it could be worth a try in your case.

---

### Post by cjazz on 2007-11-07
I've installed the 32-bit driver files (both the lpr file and the cups wrapper) for my Brother MFC-420CN and have them working on my 64-bit system now. I used the "sudo dpkg -i --force-architecture" command as well, so I don't think it has to be done from a genuine root account.

If memory serves, I also got the "No such file or directory" errors, but that didn't kill the process. The drivers installed anyway. I suspect your problem may be arising after that.

Do you have csh installed?That was necessary in my case before the driver debs would install. Even then, I had problems printing  and had to run "sudo aa-complain cupsd."

---

### Post by Cawgee on 2007-11-07
Thanks guys.
I checked and did not have csh installed. It is installed now and this is what I get now :

sudo dpkg -i --force-architecture mfc6800lpr-1.1.2-1.i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 103502 files and directories currently installed.)
Preparing to replace mfc6800lpr 1.1.2-1 (using mfc6800lpr-1.1.2-1.i386.deb) ...
Unpacking replacement mfc6800lpr ...
/var/lib/dpkg/info/mfc6800lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing mfc6800lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 mfc6800lpr-1.1.2-1.i386.deb

It appears to me it is not finding a file to overwrite now... Should it not just put the new file there and not report an error? Also once these files are installed how would I go about telling Ubuntu to use them? I am new to Linux. Sorry.

cjazz, what does :  aa-complain cupsd do? I like to learn what I am doing as I go along here.

Thanks to psyburn I was able to get the printer working via the 9050 driver supplied with Ubuntu. *BUT* it is my nature to have it working with the drivers I got from Brother. Once I start something like this I need to finish... :)

As far as scanner support, it is not a high priority. I have the scanner mostly for doing copies independent of the computer, faxing independent of the computer too. I really just need the printer. 

Thanks again,
Adam

---

### Post by cjazz on 2007-11-08
> **Cawgee said:**
> cjazz, what does :  aa-complain cupsd do? I like to learn what I am doing as I go along here.

Good for you. That's my approach, too. My understanding is that "aa-complain cupsd" disables AppArmor, which is an additional security layer introduced in Ubuntu 7.10. The problem, according to my reading, is that its support for cups printing is less than ideal. After you get printing working, if my understanding is correct, you can re-enable AppArmor with the command "sudo aa-enforce cupsd."

I'm not sure if I can be any additional help as far as the Brother drivers for your printer are concerned. I should mention that I had to completely uninstall (purge) my driver debs before reinstalling to get them to work.

---

