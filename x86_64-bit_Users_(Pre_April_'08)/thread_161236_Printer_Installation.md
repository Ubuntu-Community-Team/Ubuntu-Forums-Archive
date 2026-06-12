---
title: "Printer Installation"
date: 2006-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-04-16
I guess CUPS doesn't have Help files. 

I have a Samsung CLP-500 printer that I am trying to install on Ubuntu-64 Breezy computer. I have it connected to a USB port, turned on, and a demo page prints fine. But I can't seem to get a driver installed.

I downloaded and untared a driver file from Samsung (20050425144910781_lpp-1.1.7-27-i386.tar.gz). The first thing I noted is that it seems to be for i386, so I guess that means it is a 32-bit driver? After untaring it there were numerous folders created, and a shell script. I ran the shell script and it just blinked for a minute and then I was back at the prompt in the terminal window. I can't see that it did anything. 

There is a Readme.txt file, but it refers to the CD that comes with the printer, which supposedly has Linux drivers and setup stuff on it. However, after inserting the CD my browser (Konqueror, Krusader, Xfe) can't see the CD drive. I can't browse to the drive to see what's on the CD. I don't know why that is -- I'm relatively new to Linux and viewing the CD drive has always been a problem. I can see it from some applications (e.g., Totem, RealPlayer), but I've never been able to get a file manager to see it.

I opened the CUPS Printers folder and used File > Add Printer, but that doesn't work either. The first problem is it asks where the printer is installed. I have it on a USB port, but CUPS lists USB1, USB2, USB3, and so on. I have no way of knowing which USB port I stuck it into. There are three on my computer, but they are not numbered. Regardless of which I choose, Ubuntu doesn't "see" the printer. And I can't find any Help files or CUPS documentation that explains this.

I googled and found a web site that had a lot of user comments. Most everyone said things like "I got it installed but the resolution was only 600 dpi ..." -- and not one of the comments said HOW they got it installed.

I do have a chroot environment that I created for Firefox, RealPlayer and Adobe Reader 7.0. But the only way I know to install something in the chroot environment is to open synaptic32. 

Has anyone ever installed one of these printers in 64-bit Ubuntu? Or can someone tell me how to install it in chroot?

---

### Post by John Jason Jordan on 2006-04-16
OK, I managed to get it installed. Evidently the secret was to run the setup.sh script (which appears to do nothing), and THEN open the CUPS printer folder and click on Add Printer. At first Add Printer was useless, but after running the script it sees the driver. 

Now my only remaining problem is to get the newly installed driver talking to the printer. In the Properties for the printer (in CUPS) it says it is USB1, but I have sent it repeated test pages and the printer does not respond. Something must be bogus in the connection. 

But I'm making progress!

---

