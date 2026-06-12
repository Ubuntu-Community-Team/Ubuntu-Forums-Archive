---
title: "HOWTO: Install LightScribe in Gutsy x64"
date: 2007-11-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by thejammonster on 2007-11-25
First post, I hope this is in the right place.  I couldn't find a definitive answer on getting LightScribe working on Gutsy x64 so I thought I would share how I got it working:

First download the system software
[lightscribe-1.12.37.1-linux-2.6-intel.deb]("http://download.lightscribe.com/ls/lightscribe-1.12.37.1-linux-2.6-intel.deb")

Next download 4L (LaCie LightScribe Labeler for Linux):
[4l_1.0-r6_i386.deb]("http://uploads.mitechie.com/lightscribe/4l_1.0-r6_i386.deb")

I found the above link in another thread to solve the issue of converting from .rpm to .deb

Next open terminal and run:
```
sudo dpkg --force-architecture -i lightscribe-1.10.19.1-linux-2.6-intel.deb
```

Then run:
```
sudo dpkg --force-architecture -i 4l_1.0-r6_i386.deb
```

the 4L GUI needs to be run as root so I followed the instructions on another thread to create a menu item that will run it as root:

[thread]("http://ubuntuforums.org/showthread.php?t=520317&highlight=lightscribe")

Hopefully this will help somebody as it took me awhile to find all of the info in various threads.

---

### Post by K.Mandla on 2007-11-27
Moved to x86 64-bit Users.

---

### Post by slkwcy on 2008-01-09
Thanks for the How-to.

2 items to point out:

1) [http://uploads.mitechie.com/lightscribe/4l_1.0-r6_i386.deb](http://uploads.mitechie.com/lightscribe/4l_1.0-r6_i386.deb)
I don't think this link is working, instead:
```
wget http://www.yardbird.net/lightscribe/4l_1.0-r6_i386.deb
```

2) I am using 64bits Gutsy, so as I exit 4L-GUI from the terminal, I received this errors:
[COLOR="Red"]4L-cli: error while loading shared libraries: liblightscribe.so.1: cannot open shared object file: No such file or directory[/COLOR]

And that, caused my DVD-ROM unable to detect at the print dialog box.

So to fix it I copied both:
liblightscribe.so
liblightscribe.so.1

from /usr/lib to /usr/lib32

After, it worked for me.

---

### Post by hebetude on 2008-02-27
4L-cli
4L-cli: No such file or directory
then I followed the symbolic link to the directory it is installed in.

/usr/4L/4L-gui:  No such file or directory

I've seen this in other stuff in Hardy, don't know why it happens.  Files have execute and everything :/

---

### Post by flower71 on 2008-03-08
I also ran into the shared libraries error:

"4L-cli: error while loading shared libraries: liblightscribe.so.1: cannot open shared object file: No such file or directory"

Using the x86-64 Gutsy Gibbon (7.10).  I looked in my libc.conf file (linked from /etc/ld.so.conf), and the lightscribe directory was listed there.

(using the command: cat /etc/ld.so.conf.d/libc.conf)

Once I realized that, I ran "sudo ldconfig" and that fixed it!  Thanks for much for posting those first instructions, that saved me a great deal of time!

One other thing I spent some time tracking down:  
To run the LaCie gui:  sudo /usr/4L/4L-gui
To run the HP gui (SimpleLabeler):  sudo /opt/lightscribeApp*/Simple*/SimpleLabeler

Hope this can help someone else as much as that first post helped me.  :)

Meghan

---

### Post by fatbuttlarry on 2008-03-16
This install guide works well, but is anyone have problems printing with LightScribe on Lite-On SATA burners?

I get "A communication error has occurred with the LightScribe drive.  Please restart your PC and try the label again.

[img]http://www.backports.ubuntuforums.org/attachment.php?attachmentid=62810&stc=1&d=1205687375[/img]
[img]http://www.backports.ubuntuforums.org/attachment.php?attachmentid=62811&stc=1&d=1205687375[/img]

Yes, I am running it as root, and yes I did restart. :guitar:

**OS:** Ubuntu 7.10 + KDE
**Arch:** AMD64
**Burner:** LH-20A1L BL02 135

---

### Post by lime4x4 on 2008-03-19
the links for the packages are dead

---

### Post by fatbuttlarry on 2008-03-20
You can still get the RPMs though. :beer:

---

### Post by pbeesley on 2008-05-09
can someone help this still isn't work for me :( This is the last thing I need windows for :)

---

### Post by fatbuttlarry on 2008-05-09
> **pbeesley said:**
> can someone help this still isn't work for me :( This is the last thing I need windows for :)

I can get the app to load on AMD64, but problems with SATA burners... :/

---

### Post by thejammonster on 2008-05-15
got a PM about the links...should be updated

---

### Post by fatbuttlarry on 2008-05-18
Its really cool people got this working on AMD64... any updates?

---

### Post by GreatGariny on 2008-05-27
I succesfully installed Lightscribe on Hardy Heron 64-bit with a SATA burner using information from several posts.  I put together a guide because I had to look in so many different places for all the information I needed.

[http://howtopenguin.blogspot.com/2008/05/how-to-install-lightscribe-software-on.html](http://howtopenguin.blogspot.com/2008/05/how-to-install-lightscribe-software-on.html)

Let me know if there are any errors.

---

### Post by slick1a on 2008-05-29
yup dead links above for sure.

I used the terminal options too : 

[http://ubuntuforums.org/showthread.php?t=623251](http://ubuntuforums.org/showthread.php?t=623251)   is the page

First download the system software
lightscribe-1.12.37.1-linux-2.6-intel.deb

Next download 4L (LaCie LightScribe Labeler for Linux):
4l_1.0-r6_i386.deb

etc etc ....no joy so i tried the lightscribe page directly :

[http://www.lightscribe.com/downloadSection/](http://www.lightscribe.com/downloadSection/)

linux/index.aspx?id=1372

The LightScribe System Software is validated on SuSE 9.1, 9.2, 9.3 and 10.0. However, the LSS should install on any x86-based Linux distribution using Linux kernel 2.6 and RPM or Debian.

You will also need to install a labeling program such as the Simple Labeler or LaCie's 4L labeler.

[http://www.lightscribe.com/ideas/labelgallery.aspx?id=219#](http://www.lightscribe.com/ideas/labelgallery.aspx?id=219#)

hope this helps.

---

### Post by yragrelluf on 2008-06-05
Worked for me finally after trying everything else! Thanx!!!!!!

---

### Post by GreatGariny on 2008-06-18
Sorry about the dead link and a typo.  They only caused problems for the icon, but it is fixed now.  The above post should work now.  This should work on 32-bit and 64-bit systems.  Let me know if there are any problems.

[http://howtopenguin.blogspot.com/2008/05/how-to-install-lightscribe-software-on.html](http://howtopenguin.blogspot.com/2008/05/how-to-install-lightscribe-software-on.html)

---

### Post by rjbbc on 2008-07-01
> **thejammonster said:**
> First post, I hope this is in the right place.  I couldn't find a definitive answer on getting LightScribe working on Gutsy x64 so I thought I would share how I got it working:

First download the system software
[lightscribe-1.12.37.1-linux-2.6-intel.deb]("http://download.lightscribe.com/ls/lightscribe-1.12.37.1-linux-2.6-intel.deb")

Next download 4L (LaCie LightScribe Labeler for Linux):
[4l_1.0-r6_i386.deb]("http://uploads.mitechie.com/lightscribe/4l_1.0-r6_i386.deb")

I found the above link in another thread to solve the issue of converting from .rpm to .deb

Next open terminal and run:
```
sudo dpkg --force-architecture -i lightscribe-1.10.19.1-linux-2.6-intel.deb
```

Then run:
```
sudo dpkg --force-architecture -i 4l_1.0-r6_i386.deb
```

the 4L GUI needs to be run as root so I followed the instructions on another thread to create a menu item that will run it as root:

[thread]("http://ubuntuforums.org/showthread.php?t=520317&highlight=lightscribe")

Hopefully this will help somebody as it took me awhile to find all of the info in various threads.

After several attempts I find that Lightscribe will not run on Ubuntu 8.04. It seems that it will not recognize my burner, and of course therefore not operate. Wish someone could help me. Thanks for the info anyways.

---

