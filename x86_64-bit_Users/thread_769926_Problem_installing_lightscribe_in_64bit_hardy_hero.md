---
title: "Problem installing lightscribe in 64bit hardy heron"
date: 2008-04-27
forum: x86 64-bit Users
---

### Post by famous3warriors on 2008-04-27
I was wondering how to install lightscribe deb package in hardy heron.  When I was using the 32 bit version it was easy but in the 64 bit just a little bit different.  I would appreciate the help.  Thanks.

---

### Post by Perfect Storm on 2008-04-27
Which of the package?
[http://www.lightscribe.com/downloadSection/linux/index.aspx](http://www.lightscribe.com/downloadSection/linux/index.aspx)

---

### Post by famous3warriors on 2008-04-27
I tried with the system software then I was going to download the system labler.  Since the system software did not work I didnt even try the system labler.

---

### Post by Perfect Storm on 2008-04-27
Needed tools for this process;

<deleted nonsens>

---

### Post by Perfect Storm on 2008-04-27
ok forget what I just said...been testing it. This it;

Tools;
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install ia32-libs build-essential dpkg-dev fakeroot
wget http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb
sudo dpkg -i getlibs-all.deb
```

Lightscribe system
---------------------

```
cd ~/Desktop
getlibs -i lightscribe-1.12.37.1-linux-2.6-intel.deb
```

LIGHTSCRIBE SIMPLE LABELER
--------------------

```
cd ~/Desktop
mkdir lightscribe-simple-labeler
dpkg-deb --extract lightscribeApplications-1.10.19.1-linux-2.6-intel.deb lightscribe-simple-labeler
dpkg-deb --control lightscribeApplications-1.10.19.1-linux-2.6-intel.deb lightscribe-simple-labeler/DEBIAN
nano lightscribe-simple-labeler/DEBIAN/control

```

change Architecture: **i386** to Architecture: **amd64**
change Depends: **lightscribe** to Depends: **getlibs**

Save [ctrl]+[o]
Exit [ctrl]+[x]

```
dpkg --build lightscribe-simple-labeler
sudo dpkg -i lightscribe-simple-labeler.deb
```

Now the label stuff working (hopefully).

---

### Post by famous3warriors on 2008-04-27
Thank you artificial intelligence for that tutorial.  I did everything you ask me to do but I get this error. After I did everything on the tutorial I restarted my computer and it still did not work when I started my lightscribe labeler.

---

### Post by Perfect Storm on 2008-04-27
Sorry, I have no idea with such hardware. Doens't your label machine works default in Ubuntu? Have you tried some of the label sodtware in the repo?

---

### Post by phannigan on 2008-04-27
Thank you for all this information. I am new to Ubuntu and I am asking for help for Lightscribe. I have done all of the steps above and there seems to be no problem. Icons were not generated for this program. How do I start the labeling software and which program should I use to burn Lightscribe discs? Any assistance is much appreciated.

---

### Post by famous3warriors on 2008-04-27
you have to go into the opt/lightscribe folder.  I know there is an easier way of doing this but I went on to the menu/places/homefolder/filesystem/opt/lightscribe.  I hope this helps.

---

### Post by phannigan on 2008-04-27
Thanks very much. I was able to do this. The Lightscribe program is very simple. Is there a way of being able to add pictures to the label?

---

### Post by beartard on 2008-04-27
There are two lightscribe labelers that work under LInux.  One is put out by HP (simple labeler) and the other is by LaCie.  Both put out their own version of "system software" and "application" files.  Each can run under the other's system software, but both system softwares can't be installed simultaneously.  Was that clear? ;)

Anyway, Simple Labeler is just that: text in a ring around the outside of the disc.  LaCie's is closer to the Windows lightscribe software and even uses the same graphics packs.  Upon playing with it, however, it seems like LaCie's software wants you to have your text already on your image before importing it.  There doesn't seem to be a way to add text within or on an image once in the app.

---

### Post by beartard on 2008-04-28
Ok, I played with the LaCie software a little bit, and thanks to Artificial Intelligence, it works the same way.
All the following is done from the ~/Desktop.  Make sure AI's instructions above are already done, as LaCie's labeler needs the same system/host software as Simple Labeler.

1. Download the LaCie labeling application: [http://www.lacie.com/download/drivers/4L-1.0-r6.i586.rpm](http://www.lacie.com/download/drivers/4L-1.0-r6.i586.rpm)

2. use fakeroot (or sudo) to convert the rpm to a deb. 
```
fakeroot
alien -d 4L-1.0-r6.i586.rpm
exit
```It won't do so cleanly since I've found no way to tell alien to ignore the architecture of an rpm file.  At any rate, this step leaves you with a folder called 4L-1.0

3. Go into the 4L-1.0 folder.
3a. Rename debian to DEBIAN
3b. Go into the DEBIAN folder inside.
3c. Trash the "4l" folder you find there.

4. Edit the control file in the DEBIAN folder.  Change the architecture to amd64 and depends to getlibs.
Dependencies don't really matter since you already took care of that in AI's install above.
4a.  Add the following line to the file if it's not there already:
```
Version: 1.0-1
```

5. Save the control file, cd back to your Desktop,  and build and install the deb file.
```
dpkg --build 4L-1.0
dpkg -i 4L-1.0.deb
```

6. Can be run with
```
4L-gui
```

I think that covers it.  AI's instructions above just happened to work for the more capable labeling software as well.  The only problem I see is that it installs the software in /usr/4L which is annoying to me.  If you can live with that, cool.  If not, you may want to move the files into something like. /usr/local/4L before building the deb file.    If you go this route, be sure to edit the symlinks in ./usr/bin to show the new locations.  

As for trying it out, I haven't yet, as I don't have any lightscribe media to waste on a test run.

Again, this is all good if you want to let the package manager know it's installed.  If that's not a problem, you can always just copy the contents of the ./usr folder to wherever intact and set up a symlink somewhere you like it.

---

### Post by Julius on 2008-04-28
nvm

---

### Post by phannigan on 2008-04-28
> **beartard said:**
> Ok, I played with the LaCie software a little bit, and thanks to Artificial Intelligence, it works the same way.
All the following is done from the ~/Desktop.  Make sure AI's instructions above are already done, as LaCie's labeler needs the same system/host software as Simple Labeler.

1. Download the LaCie labeling application: [http://www.lacie.com/download/drivers/4L-1.0-r6.i586.rpm](http://www.lacie.com/download/drivers/4L-1.0-r6.i586.rpm)
2. use fakeroot (or sudo) to convert the rpm to a deb. 
```
fakeroot
alien -d 4L-1.0-r6.i586.rpm
exit
```It won't do so cleanly since I've found no way to tell alien to ignore the architecture of an rpm file.  At any rate, this step leaves you with a folder called 4L-1.0
3. Go into the folder and then into the DEBIAN folder inside.  Trash the "4l" folder you find there.
4. Edit the control file in the DEBIAN folder.  Change the architecture to amd64 and depends to getlibs.  It won't really matter about the depends, since you already took care of that installing the "system software" for simple labeler.  Add the following line to the file if it's not there already:
```
Version: 1.0-1
```5. Save the control file and build and install the deb file.
```
dpkg --build 4L-1.0
dpkg -i 4L-1.0.deb
```6. Can be run with
```
4L-gui
```I think that covers it.  AI's instructions above just happened to work for the more capable labeling software as well.  The only problem I see is that it installs the software in /usr/4L which is annoying to me.  If you can live with that, cool.  If not, you may want to move the files into something like /usr/local/4L before building the deb file.    As for trying it out, I haven't yet, as I don't have any lightscribe media to waste on a test run.

Again, this is all good if you want to let the package manager know it's installed.  If that's not a problem, you can always just copy the contents of the usr folder to wherever intact and set up a simlink somewhere you like it.

I got as far as:
dpkg --build 4L-1.0
I get the following error:
root@paul-desktop:~# dpkg --build 4L-1.0
dpkg-deb: failed to open package info file `4L-1.0/DEBIAN/control' for reading: No such file or directory
4L-1.0 folder is on my desktop yet it is not seen.
Any suggestions?
Thx.

---

### Post by beartard on 2008-04-28
> **phannigan said:**
> I got as far as:
dpkg --build 4L-1.0
I get the following error:
root@paul-desktop:~# dpkg --build 4L-1.0
dpkg-deb: failed to open package info file `4L-1.0/DEBIAN/control' for reading: No such file or directory
4L-1.0 folder is on my desktop yet it is not seen.
Any suggestions?
Thx.
I ran into that problem the first time around.  That's what made me run alien on it under fakeroot.  When alien sees that the rpm file is for i386, it won't finish extracting the files.  This leaves you with a 4L-1.0 folder on your desktop, but without a lot of files inside that you'd need to make the package. I think your problem comes from me forgetting to say to rename the lowercase debian folder to an all-caps DEBIAN folder.  The instructions are modified now to be correct.

---

### Post by phannigan on 2008-04-28
> **beartard said:**
> I ran into that problem the first time around.  That's what made me run alien on it under fakeroot.  When alien sees that the rpm file is for i386, it won't finish extracting the files.  This leaves you with a 4L-1.0 folder on your desktop, but without a lot of files inside that you'd need to make the package.  Also, make sure that the debian folder is renamed DEBIAN.  I forgot to mention that in the instructions.  I'll modify it after I post this.

Still having problems locating the file. I am sure I am not doing something correctly in Terminal. Here's what I get:
paul@paul-desktop:~$ cd /home/paul/Desktop
paul@paul-desktop:~/Desktop$ fakeroot
root@paul-desktop:~/Desktop#  alien -d 4l-1.0-r6.i586.rpm
File "4l-1.0-r6.i586.rpm" not found.
root@paul-desktop:~/Desktop# cd
root@paul-desktop:~#  alien -d 4l-1.0-r6.i586.rpm
File "4l-1.0-r6.i586.rpm" not found.
root@paul-desktop:~# 
Can you spot anything?
Thx.

---

### Post by doorknob60 on 2008-04-28
Hmm.... could be any of these problems

* You didn't download the file
* You're in the wrong directory
* You typed the fine name wrong

---

### Post by beartard on 2008-04-28
> **phannigan said:**
> Still having problems locating the file. I am sure I am not doing something correctly in Terminal. Here's what I get:
paul@paul-desktop:~$ cd /home/paul/Desktop
paul@paul-desktop:~/Desktop$ fakeroot
root@paul-desktop:~/Desktop#  alien -d 4l-1.0-r6.i586.rpm
File "4l-1.0-r6.i586.rpm" not found.
root@paul-desktop:~/Desktop# cd
root@paul-desktop:~#  alien -d 4l-1.0-r6.i586.rpm
File "4l-1.0-r6.i586.rpm" not found.
root@paul-desktop:~# 
Can you spot anything?
Thx.
The filename of the rpm file starts with 4L (note capital letter).  You were typing 4l.  Just in case you're not used to working in the terminal, you could type "4L" without quotes, hit tab, and bash will type the rest of the filename out for you to save some keystrokes.  It works the same with most file operations. For example, to get to your desktop, you could probably type cd /h<tab>/p<tab>/De<tab><enter>

---

### Post by tk03759 on 2008-06-03
I just installed lightscribe on my x64 hardy install and wrote up a quick step by step tutorial, which is here:

[http://ubuntuforums.org/showthread.php?t=106197&page=22]("http://ubuntuforums.org/showthread.php?t=106197&page=22")

Hope it saves you some time.

---

