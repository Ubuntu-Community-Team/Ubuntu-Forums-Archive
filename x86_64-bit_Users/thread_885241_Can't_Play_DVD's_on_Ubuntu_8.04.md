---
title: "Can't Play DVD's on Ubuntu 8.04"
date: 2008-08-09
forum: x86 64-bit Users
---

### Post by dark_zack on 2008-08-09
Whenever I attempt to view a DVD on my computer in Totem I get this message.
> Could not read from resource

---

### Post by yabbadabbadont on 2008-08-09
Do you have ubuntu-restricted-extras installed?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by dark_zack on 2008-08-09
I installed that and it still displays the same message.

---

### Post by yabbadabbadont on 2008-08-09
Did you also follow the link at the bottom about playing dvd's?

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by dark_zack on 2008-08-09
Yes I did, and I installed libdvdcss2.
Though it still displays the same message.

---

### Post by dark_zack on 2008-08-09
I just installed Medibuntu, and everything seems to be working.
Thanks for all your help. :)

---

### Post by yabbadabbadont on 2008-08-09
You're welcome... although I didn't really help it seems.  Unless you found the link to medibuntu on one of the pages to which I directed you.  Then, I guess I helped a little.  :D

---

### Post by yarn on 2009-02-04
i am having this problem also...does anyone know why?

---

### Post by evilempire on 2009-02-05
I was having the same problem a few months ago with the software installed correctly and it turned out that the region code on the DVD drive had never been set. Is it a new drive by chance?

---

### Post by yarn on 2009-02-05
kind of...it came in the laptop. it is a dell 1525 that i bought about 4 months ago.  how would i go about changing the region code on it?

---

### Post by evilempire on 2009-02-05
This would only make sense if you've never watched a DVD movie on that drive. If you had in Windows or OS X, the first time you run the DVD player it'll make you set the region code for the drive. 

sudo apt-get install regionset

Then run regionset from the terminal. If you are in north america you want region 1

---

### Post by EllieMurasaki on 2009-10-06
I'm having the same problem. I downloaded the packages from [http://packages.medibuntu.org/hardy/libdvdcss2.html](http://packages.medibuntu.org/hardy/libdvdcss2.html) and followed the sudo dpkg parts of the instructions from [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and got this:

```
[redacted]@[redacted]:~$ sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
Selecting previously deselected package libdvdcss2.
(Reading database ... 133855 files and directories currently installed.)
Unpacking libdvdcss2 (from libdvdcss2_1.2.9-2medibuntu4_i386.deb) ...
Setting up libdvdcss2 (1.2.9-2medibuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
[redacted]@[redacted]:~$ sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
dpkg: error processing libdvdcss2_1.2.9-2medibuntu4_amd64.deb (--install):
 package architecture (amd64) does not match system (i386)
Errors were encountered while processing:
 libdvdcss2_1.2.9-2medibuntu4_amd64.deb
[redacted]@[redacted]:~$ sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_powerpc.deb
dpkg: error processing libdvdcss2_1.2.9-2medibuntu4_powerpc.deb (--install):
 package architecture (powerpc) does not match system (i386)
Errors were encountered while processing:
 libdvdcss2_1.2.9-2medibuntu4_powerpc.deb
[redacted]@[redacted]:~$ sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_lpia.deb
dpkg: error processing libdvdcss2_1.2.9-2medibuntu4_lpia.deb (--install):
 package architecture (lpia) does not match system (i386)
Errors were encountered while processing:
 libdvdcss2_1.2.9-2medibuntu4_lpia.deb
[redacted]@[redacted]:~$
```What did I do wrong and how do I fix it? I'd appreciate it if the answer came in 'Ubuntu for Complete Morons' format, and whatever the answer is, it can't require my Ubuntu machine having Internet.

---

### Post by oldos2er on 2009-10-06
> **EllieMurasaki said:**
> I'm having the same problem. I downloaded the packages from [http://packages.medibuntu.org/hardy/libdvdcss2.html](http://packages.medibuntu.org/hardy/libdvdcss2.html) and followed the sudo dpkg parts of the instructions from [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and got this:

```
[redacted]@[redacted]:~$ sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
Selecting previously deselected package libdvdcss2.
(Reading database ... 133855 files and directories currently installed.)
Unpacking libdvdcss2 (from libdvdcss2_1.2.9-2medibuntu4_i386.deb) ...
Setting up libdvdcss2 (1.2.9-2medibuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
[redacted]@[redacted]:~$ sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
dpkg: error processing libdvdcss2_1.2.9-2medibuntu4_amd64.deb (--install):
 package architecture (amd64) does not match system (i386)
Errors were encountered while processing:
 libdvdcss2_1.2.9-2medibuntu4_amd64.deb
[redacted]@[redacted]:~$ sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_powerpc.deb
dpkg: error processing libdvdcss2_1.2.9-2medibuntu4_powerpc.deb (--install):
 package architecture (powerpc) does not match system (i386)
Errors were encountered while processing:
 libdvdcss2_1.2.9-2medibuntu4_powerpc.deb
[redacted]@[redacted]:~$ sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_lpia.deb
dpkg: error processing libdvdcss2_1.2.9-2medibuntu4_lpia.deb (--install):
 package architecture (lpia) does not match system (i386)
Errors were encountered while processing:
 libdvdcss2_1.2.9-2medibuntu4_lpia.deb
[redacted]@[redacted]:~$
```What did I do wrong and how do I fix it? I'd appreciate it if the answer came in 'Ubuntu for Complete Morons' format, and whatever the answer is, it can't require my Ubuntu machine having Internet.

 Why are you trying to install libdvdcss2 for so many different architectures? The first command worked, btw.

 Installing packages without a 'net connection, can be done, but it's tedious (plus, Linux was built from the ground up to be a networking OS).

---

### Post by EllieMurasaki on 2009-10-06
> **oldos2er said:**
> Why are you trying to install libdvdcss2 for so many different architectures? The first command worked, btw.

The why would probably be 'because this is all Greek to me and it looked like I was supposed to do all of them'. Thanks.

---

### Post by kirbyfan101 on 2009-10-06
agggggggg i need help i downloaded the CD drive at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
I have WindowsXP I put the .iso file on a disk and  loaded it
it didnt work 
 
 
 
PS:  i would start my own forum but i don't know how:(

---

### Post by oldos2er on 2009-10-06
> **kirbyfan101 said:**
> agggggggg i need help i downloaded the CD drive at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
I have WindowsXP I put the .iso file on a disk and  loaded it
it didnt work 
 
 
 
PS:  i would start my own forum but i don't know how:(

 Go here: [http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)
Click 'New Thread'

---

### Post by oldos2er on 2009-10-06
> **EllieMurasaki said:**
> The why would probably be 'because this is all Greek to me and it looked like I was supposed to do all of them'. Thanks.

 So...do DVDs work now?

---

### Post by EllieMurasaki on 2009-10-07
I put in a DVD and it started playing, which is an improvement, but what it started playing was the first episode on the disc, not the menu from which I can pick an episode. And because there's three forty-minute episodes on the disc and Totem thought it was one two-hour movie, I don't think I can get to the special features at all. (Or to get to later episodes except by playing through the earlier ones, because I tried skipping ahead and it didn't work so well.) But it played! So things are better!

(This is now a problem with the default movie-playing software, solvable by picking out better movie-playing software, isn't it?)

---

### Post by Enriquecaribe on 2009-10-07
Do you have libdvdcss installed?
You can get it here: [http://downloads.videolan.org/pub/videolan/libdvdcss/1.2.9/deb/](http://downloads.videolan.org/pub/videolan/libdvdcss/1.2.9/deb/)

OR try VLC player, its in your repos.

---

### Post by EllieMurasaki on 2009-10-08
oldos2er says my attempt at installing libdvdcss2 worked, and I assume this to be a reliable statement because now the computer acknowledges the existence of video files on the DVD.

Repos? And is installing VLC Player going to require that computer being online? Because if it is, I need a workaround; all the Internet-connected computers I have access to run Windows.

---

### Post by oldos2er on 2009-10-08
I don't use Totem, and don't really know anything about it. 

 Package installation on Ubuntu cries out for an internet connection. But if that's not possible, look into Keryx ([http://keryxproject.org/](http://keryxproject.org/)) or AptonCD ([http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)).

---

