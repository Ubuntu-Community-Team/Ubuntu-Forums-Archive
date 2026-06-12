---
title: "Install of ati-drivers"
date: 2006-02-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Peter Sommer-Larsen on 2006-02-26
Hey everybody

I am a very new linux user, and i would like to install ati-drivers for my
"ati radeon xpress 200m" - grafik card. I have looked at all your guides, but
the problem is, that the older driver from [www.ati.com](www.ati.com) that is used in the
guides is way different from the newst one they have got. 
It is called 9.22.5-x86_64.run. I have extrated it to a directory. But now I dont
know what to do. I guess i need to run the ati-installer.sh, but i have no idea
how to run this file in Brezeer. Ive tryed to type
"sudo sh ati.installer.sh --install" like the README says, but i just keep show the
help file for the ati.installer.

Does someone have any idear of how to install it ??

Ciao
Peter

---

### Post by pestilence on 2006-02-26
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

---

### Post by Peter Sommer-Larsen on 2006-02-27
hey body

Thx but i allready know this site... its like I said.. my problem is that the NEW driver
from [www.ati.com/](www.ati.com/) cannot be install this way..!! :-k

---

### Post by newuser111 on 2006-02-27
Wrong.

The link pestilence posted has already been updated to use the latest driver (8.22.5), it generates .deb files, just follow the guide

[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

---

### Post by Peter Sommer-Larsen on 2006-02-27
Ok ill tell you what i do, because I still dont get *.deb files. :( 

first I download the ati-driver at [www.ati.com](www.ati.com).. its called ****9.22***.run
then i go to the root dir, and type

(command) "sudo mkdir atidriver"

(command) "sudo cp *****9.22***.run --extract /atidriver --buildpkg Ubuntu/breezy"

then it extracts all the files to /atidriver.
i can do a "ls" or "dir" and the result is ive got tons of files, but all called
somethinh like *.sh

Do i do something wrong ? Or well.. of course i do.. but what ? :-k 

The dpkg-reconfigure does not work with my ati-card.. it makes an error every
time i try to start X. Ive allready tryed to disable int10..

Ciao

Peter :confused:

---

### Post by newuser111 on 2006-02-27
I don't know what you are downloading but the linux driver for xorg is 8.22.5

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

---

### Post by cabber on 2006-02-28
newuser111,

I'm a new user to Linux (ubuntu) as well, and have many questions related to that guide.

Do you just open a terminal window and start typing?  I downloaded the driver from ATI's website, but am stuck at trying to get it installed. 

Just as a side note, the only way I could get the xserver to boot was to change  to the VESA driver.  My ATI card would not load any other way.

 I open a terminal session and run into problems.  Please advise on "it generates .deb files" for the rookie community.  Sorry to bug you with this generic question, but I have to start somewhere.

---

### Post by amosbatto on 2006-03-01
> Do you just open a terminal window and start typing? I downloaded the 
> driver from ATI's website, but am stuck at trying to get it installed.

Yes, just open the terminal window and type each command and hit the return key.

> I open a terminal session and run into problems. 

Do you get error messages?  If so, post them for help. (To copy text from the terminal window, highlight it and press shift + ctrl + c )

> Please advise on "it generates .deb files" for the rookie community. 

Programs for Linux distributions coming in packaging formats which compress the programs and provide information about the various dependencies for each program.  Red Hat and Mandriva use rpm packaging format.  Debian based distros like ubuntu use deb; Slackware uses tgz.  (If you ever need a program which only comes in rpm, you can use alien to convert it to deb so it will run on your computer. To install alien: sudo apt-get install alien  )

ATI uses its installer to create deb files, so you can install the ati driver on your computer.  After you run the commands:

sudo apt-get install gcc-3.4 module-assistant build-essential fakeroot dh-make debconf libstdc++5 gcc-3.3-base
sudo sh ./ati-driver-installer-8.22.5-i386.run --buildpkg Ubuntu/breezy

you should see that it created a couple files that end in .deb  Follow the rest of the instructions...

---

### Post by ankouts on 2006-03-08
The right driver for Amd64 users, is ati-driver-installer-8.22.5-i386.run or ati-driver-installer-8.22.5-x86_64.run ?

---

### Post by mdmarmer on 2006-03-08
For 64-bit install you need the 64-bit driver with 64 on the end


Mike

---

### Post by ankouts on 2006-03-09
Thank you, i will try again.

---

### Post by stupidel on 2006-03-23
alright i definitly feel that i am getting further than i have in the past.  I think i know where everything is going wrong, there is a package that needs to be downloaded call module-assistant.  When i type the command 

sudo apt-get install module-assistant

It returns "package module-assistant is no longer available"

everything else seems to download fine but this one package.

Any help would be greatly apreciated,

[B]Update: found solution to problem
[/B]
Ok, anyone else who may run into this issue here is a possible fix.  You may need to edit the file by typing

sudo gedit /etc/apt/sources.list

and remove all '#' signs in front of any lines starting with 'deb'

after this run sudo apt-get update and try retrieving the file again and it should come down.

thanks.

---

