---
title: "Microsoft Office 07"
date: 2008-08-08
forum: Wine
---

### Post by gustasonfrever on 2008-08-08
I'm having a little problem while trying to install office through wine ( I have hardy, and wine 1.1.2) About halfway through the installation process I get this error message 

[CENTER]An application has made an attempt to load the C runtime library incorrectly.
Please contact the application’s support team for more information.[/CENTER]

Now, if I run the installer again, it quits very quickly and says only:

[CENTER]Microsoft Office 2007 encountered an error during setup.[/CENTER]

I can only click 'Close' then.
I'm running Wine version 1.1.2. Does someone know a solution to this problem?
I really need to be able to run Office, as I need it at work tomorrow. Please help!

BTW I followed this guide [http://ubuntuforums.org/showthread.php?t=844309&highlight=microsoft+office+WINe](http://ubuntuforums.org/showthread.php?t=844309&highlight=microsoft+office+WINe)

---

### Post by agapito on 2008-08-08
You can install a Xp virtual machine and then install office there. I think that will be faster then finding the problem with your wine-based installation. Try virtualbox. It's easy.

---

### Post by gustasonfrever on 2008-08-08
Will it run at a good speed?

EDIT:
I tried downloading it and I was immediately bombarded with error messages from Java: Invalid proxy type, unable to launch the application

---

### Post by agapito on 2008-08-08
It depends on your system, but i think it will work well on any current computer.

---

### Post by agapito on 2008-08-08
I found a good tutorial here:
[http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html](http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html)

There is a version in the repositories but it is the open source version which doesn't have usb support. To install use 

sudo aptitude install virtualbox-ose

---

### Post by agapito on 2008-08-08
I guess you have some java plugin issues (x86_64, right?)... I would try to fix those latter. Since you have a *really* tight dedline I supose the best is to create a XP virtual machine using the open source version of virtualbox that you can install from the repos. It's hardly limited at all ( [http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions) ). When you have more time you can uninstall the open source version and install the full version without destroing your xp virtual machine.

---

### Post by gustasonfrever on 2008-08-08
Thanks for the help, I'm working on the install right now

EDIT:
Would you mind telling me where I could go later to resolve the Java issue?

---

### Post by agapito on 2008-08-08
If you have a 64bit machine, solving the java issues can take 1min or 1day... I have no way of knowing what the problem is. I would start by entering "about:plugins" in firefox's address bar, and check to see if there is any java plugin installed. I have this:
[B]
GCJ Web Browser Plugin (using IcedTea) 1.0
[/B]
I think the package you have to install to get it is icedtea-gcjwebplugin. 

BTW, that :P above is a ':' and a 'p'

---

### Post by /////// on 2008-08-08
You can easily install Office 2007 within a VM in Ubuntu, however, it will not be at full times the speed and its also a pain in the *** to start the VM everytime you need to use Office. I have successfully installed Office 2007 via WINE in Ubuntu 8.04 using this guide: [http://sudosys.be/?q=office2007_wine](http://sudosys.be/?q=office2007_wine) If you need any help just ask.

---

### Post by agapito on 2008-08-08
> **/////// said:**
> You can easily install Office 2007 within a VM in Ubuntu, however, it will not be at full times the speed and its also a pain in the *** to start the VM everytime you need to use Office. I have successfully installed Office 2007 via WINE in Ubuntu 8.04 using this guide: [http://sudosys.be/?q=office2007_wine](http://sudosys.be/?q=office2007_wine) If you need any help just ask.

Yes you are right, it is a bit slower, but after messing around in wine (including crossover) for quite some time i decided to start using virtual machines instead. I work with some really windows-centric people...  To work with them i need mathtype, endnonte X, chemoffice, acrobat... You name it. It is very hard (at least for me) to keep all of that working well on wine. To improve things a bit I turn off the eyecandy in xp (and stay away from that Vi$ta thing...) and tend to hibernate instead of shutting down.

---

### Post by kajillin on 2008-08-08
start using openoffice.... microsoft are a bunch of nazi's, do you realy want to support nazi's :P

---

### Post by agapito on 2008-08-08
> **kajillin said:**
> start using openoffice.... microsoft are a bunch of nazi's, do you realy want to support nazi's :P

:) I second that!
Sadly, some people out there haven't seen the light, and until D day comes we have to live with them... ](*,)

---

### Post by hellknight_mnd on 2008-08-08
Yeah.. start using OpenOffice.Org.. its fantastic.. i'm a student so i can't afford MS Office.. but i found that OpenOffice.Org was equally good or even better.. like that PDF export option is really nice.. the size of the ODF documents are also small as compared to MS Office's docs.. use it dude.. you'll love it.. and it can even save in Office 2003's .doc. format!!

---

### Post by ooobuntooo on 2008-08-08
For us who already bought Office 2007, we would like to use it in Linux.
I bought Crossover Linux Pro which has support for Office 2007, but the installation freezes at 75%! :(

---

### Post by ooobuntooo on 2008-08-08
I have just got it to work!

You need Crossover Linux 7. Straight out of the box successful installation!

Is it ok with the moderators if I give people on the forum a free copy?

---

### Post by gatorbrit on 2008-08-08
> **agapito said:**
> :) I second that!
Sadly, some people out there haven't seen the light, and until D day comes we have to live with them... ](*,)

This is the reality for me- i tried OO but 99% compatible is not enough when the rest of the world uses MSFT.  I hate it, but it is reality.   Virtual machines seem to be the way to go, but then you wonder why not just dual boot to XP?

---

