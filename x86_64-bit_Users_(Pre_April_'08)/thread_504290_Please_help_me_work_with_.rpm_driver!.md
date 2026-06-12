---
title: "Please help me work with .rpm driver!"
date: 2007-07-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by s3a on 2007-07-19
Ok so I bought this modem (Amigo AMI-CA52/CW52+ P9006-02 (chipset is Conexant HSFi CX11252-11)) from this guy who didn't need it anymore and have found its drivers on this website ([http://members.driverguide.com/driver/detail.php?driverid=606596](http://members.driverguide.com/driver/detail.php?driverid=606596)). I downloaded the driver and it came in a .rpm format. I read a bit about this and I need something called alien and some other stuff in order to get it into .deb format so that it works under Ubuntu 7.04 (Feisty Fawn). Can you people please help me with this process?

---

### Post by borris.morris on 2007-07-19
Do, "sudo apt-get install alien". this'll take a while.
Next, do "alien ~/Desktop/hsfmodem-7.18.00.03oem-1.i386.rpm" This should make it into a .deb at which point you can "sudo dpkg -i /path/to/file"

---

### Post by s3a on 2007-07-19
Doesn't "sudo apt-get install alien" require an internet connection? I do not have any functional internet connection in Linux which is why I am trying to install this 56k modem driver. I am using Windows XP for my internet/forum help. Assuming I am right and that the "sudo apt-get install alien" command does require an internet connection, is there a way that I can download alien through windows so that I can simply bring it over to Linux and then do the rest of what you said?

Thanks in advance!

---

### Post by s3a on 2007-07-19
[IMG]K:\problem.png[/IMG]

---

### Post by s3a on 2007-07-19
Sorry for my weird previous post, I don't know how to upload the screenshot I took of the problem I experienced after typing in "sudo apt-get install alien". I will type the problem instead.

Here is exactly what the terminal window displays:

deniz@deniz-desktop:~$ sudo apt-get install alien
Reading package lists...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package alien
deniz@deniz-desktop:~$

---

### Post by borris.morris on 2007-07-19
you're going to need  libbeecrypt6, librpm4, rpmdebhelper, gettext, html2text, intltool-debian, po-debconf and alien from [http://packages.ubuntu.com/feisty/allpackages](http://packages.ubuntu.com/feisty/allpackages)

then use "sudo dpkg -i /media/cdrom0/*.deb"
and alien will be installed

---

### Post by s3a on 2007-07-20
> **borris.morris said:**
> you're going to need  libbeecrypt6, librpm4, rpmdebhelper, gettext, html2text, intltool-debian, po-debconf and alien from [http://packages.ubuntu.com/feisty/allpackages](http://packages.ubuntu.com/feisty/allpackages)

then use "sudo dpkg -i /media/cdrom0/*.deb"
and alien will be installed
Sorry to bother you again but, I downloaded what you told me to download and I have it on the desktop and I did the command you told me to do (sudo dpkg -i /media/cdrom0/*.deb) and got this:

deniz@deniz-desktop:~$ sudo dpkg -i/media/cdrom0/*.deb
dpkg: unknown option -/

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
deniz@deniz-desktop:~$

---

### Post by IanW on 2007-07-20
Looks like there should have been a space between "sudo dpkg -i" and "/media/cdrom0/*.deb"

Although, you say you have all those .deb files on your desktop?
In that case the command should be "sudo dpkg -i ~/Desktop/*.deb"

---

### Post by s3a on 2007-07-20
> **IanW said:**
> Looks like there should have been a space between "sudo dpkg -i" and "/media/cdrom0/*.deb"

Although, you say you have all those .deb files on your desktop?
In that case the command should be "sudo dpkg -i ~/Desktop/*.deb"
After I added that space I still get:

deniz@deniz-desktop:~$ sudo dpkg - /media/cdrom0/*.deb 
Password: 
dpkg: need an action option 

Type dpkg --help for help about installing and deinstalling packages [*]; 
Use `dselect' or `aptitude' for user-friendly package management; 
Type dpkg -Dhelp for a list of dpkg debug flag values; 
Type dpkg --force-help for a list of forcing options; 
Type dpkg-deb --help for help about manipulating *.deb files; 
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*]. 

Options marked [*] produce a lot of output - pipe it through `less' or `more' ! 
deniz@deniz-desktop:~$

---

### Post by s3a on 2007-07-20
> **s3a said:**
> After I added that space I still get:

deniz@deniz-desktop:~$ sudo dpkg - /media/cdrom0/*.deb 
Password: 
dpkg: need an action option 

Type dpkg --help for help about installing and deinstalling packages [*]; 
Use `dselect' or `aptitude' for user-friendly package management; 
Type dpkg -Dhelp for a list of dpkg debug flag values; 
Type dpkg --force-help for a list of forcing options; 
Type dpkg-deb --help for help about manipulating *.deb files; 
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*]. 

Options marked [*] produce a lot of output - pipe it through `less' or `more' ! 
deniz@deniz-desktop:~$
I didn't see the desktop part...I'll try it.

---

### Post by s3a on 2007-07-20
I tried the desktop code and got:

deniz@deniz-desktop:~$ sudo dpkg -i ~/Desktop/*.deb
dpkg: error processing /home/deniz/Desktop/*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/deniz/Desktop/*.deb
deniz@deniz-desktop:~$

---

### Post by borris.morris on 2007-07-20
yes, that is correct ian. i was assuming that his files were on a cd...

---

### Post by s3a on 2007-07-20
Can someone please help me with my new error?

---

### Post by xc3RnbFO8P on 2007-07-20
what happends when you double click the deb?

---

### Post by s3a on 2007-07-20
> **Ringi said:**
> what happends when you double click the deb?
It's still in .rpm format.

---

### Post by xc3RnbFO8P on 2007-07-20
> **s3a said:**
> It's still in .rpm format.

sorry!

---

### Post by s3a on 2007-07-20
> **Ringi said:**
> sorry!
It's ok, thanks for trying to help anyway...

---

### Post by borris.morris on 2007-07-20
the exact code would be "sudo dpkg -i ~/Desktop/*.deb"  
Copy and paste it.
the first command tells the computer to be the administrator to install the program, the second is the command to run as, "root," the administrator, and the -i tells it to install all of the .deb packages in the ~/Desktop/*.deb, hence the *.deb, all files that end in .deb.

---

### Post by borris.morris on 2007-07-20
actually, try "sudo dpkg -i -R ~/Desktop/"

that'll do the desktop folder recursivly.

---

### Post by xc3RnbFO8P on 2007-07-20
Another stupid question, did you unzip it before you tried to change it to deb?

---

### Post by s3a on 2007-07-20
> **Ringi said:**
> Another stupid question, did you unzip it before you tried to change it to deb?
I have a unzipped and zipped version on desktop because I wasn't sure what to do so I just put both.

---

### Post by xc3RnbFO8P on 2007-07-20
Look at this [http://www.linuxant.com/drivers/hsf/install.php]("http://www.linuxant.com/drivers/hsf/install.php")

---

### Post by s3a on 2007-07-20
> **Ringi said:**
> Look at this [http://www.linuxant.com/drivers/hsf/install.php]("http://www.linuxant.com/drivers/hsf/install.php")
That's not free....I had attempted to try it on my previous 56k modem.

---

### Post by s3a on 2007-07-20
I am so lost....can we restart? I am having problems understanding what Ringi gave me (sorry first time, I didn't fully read the page). Can someone give me SIMPLE (for linux beginners like myself) step by step instructions for EVERYTHING in one message please? I'd appreciate if someone can add me on msn and help me in a live way.

Thanks in advance!

---

### Post by xc3RnbFO8P on 2007-07-21
Here is deb  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php]("http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php")
Check out your kernel  **uname -r** in terminal window 
Download the deb.zip
extract
dobble clik on hs**fmodem_7.60.00.09full_k2.6.20_16_generic_ubuntu_i386.deb** (I think it is yours)

---

### Post by borris.morris on 2007-07-21
he needs the 64 bit, i think.
im on msn quite often. add me as jessie at confettiantiques.com

---

### Post by s3a on 2007-07-21
Gnome-ppp is succesfully installed as is the speed limited driver that Ringi gave ([http://www.linuxant.com/drivers/hsf/...ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/...ubuntu-x86.php)), however, when I try to dial my connection, the modem is not detected!

Help!

---

### Post by xc3RnbFO8P on 2007-07-22
Dont you have any other options to access the Internet, adsl, cabel? Unlocked wireless net in your neighbourhood? :)

---

### Post by s3a on 2007-07-27
> **Ringi said:**
> Dont you have any other options to access the Internet, adsl, cabel? Unlocked wireless net in your neighbourhood? :)
Unfortunately not.

---

### Post by amaurynieto on 2007-08-12
Hey there.

Make it easy for you:

Dell has the 56k DEB file which works for all hsfmodems. I promise.

just download the DEB from this link, install, and REBOOT (you'll have to reboot, since it's listed as a "restricted driver", and it will tell you so when you log back in).

This is not a Ctrl Alt Backspace restart. an actual Reboot is required.

Good luck. It SHOULD work. (the deb is packaged for 32 bit Feisty Fawn), trying to install in 64 bit will NOT work.

When you install, it will prompt you in the command line to list where something or other is, and then a path of /usr/src/ etcetera.... just press enter. don't fiddle around with it.

[http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&amp;amp;devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745](http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&amp;amp;devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745)

---

### Post by s3a on 2007-08-25
> **amaurynieto said:**
> Hey there.

Make it easy for you:

Dell has the 56k DEB file which works for all hsfmodems. I promise.

just download the DEB from this link, install, and REBOOT (you'll have to reboot, since it's listed as a "restricted driver", and it will tell you so when you log back in).

This is not a Ctrl Alt Backspace restart. an actual Reboot is required.

Good luck. It SHOULD work. (the deb is packaged for 32 bit Feisty Fawn), trying to install in 64 bit will NOT work.

When you install, it will prompt you in the command line to list where something or other is, and then a path of /usr/src/ etcetera.... just press enter. don't fiddle around with it.

[http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&amp;amp;devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745](http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&amp;amp;devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745)
I just read this now...I will try it! Thanks alot! I will post back later to confirm if I have my modem running succesfully!

Thanks once again!

*EDIT* What do I download/install (aka acquire) to be able to dial my connection? Keep in mind that I have no internet AT ALL on Ubuntu until I get this problem fixed! *EDIT*

---

### Post by s3a on 2007-08-26
IT WORKS!!!!!!! OMG!!!!! amaurynieto, you are an angel! lol Seriously though, I've been trying to connect to the internet since March! Thank you so much! You have no idea how much I appreciate this! Thanks to everyone else as well who tried to help!

*In case, someone has the same problem and is using google or the search tool on the forums or whatever to fix their problem, I fixed my problem by installing this driver, making a full reboot and then clicking on system->administration->network and then clicking once on the dial-up icon and clicking properties and then checking the box where it says "Enable this connection" and then fill in all your data and on the options tab, check all 3 boxes.*

---

### Post by gcoram on 2007-08-26
Worked for me to, thanks your a champion. I didnt bother tracking down what modem it was, it just worked, yah !

---

### Post by s3a on 2007-08-27
> **gcoram said:**
> Worked for me to, thanks your a champion. I didnt bother tracking down what modem it was, it just worked, yah !
Now all the dial-up users who've given up with Ubuntu............rise! Now all I need is a HCF driver for my other modem for when I put it in another computer....but that can wait :P. I'll just check dell later and post the link in my sig if I find it!

---

### Post by s3a on 2007-08-29
Can I have the link to a driver that will make my ESS 2838 chipset HCF modem work please?

---

