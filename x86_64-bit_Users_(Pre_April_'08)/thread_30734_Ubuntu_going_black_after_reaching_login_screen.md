---
title: "Ubuntu going black after reaching login screen"
date: 2005-04-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by lukey on 2005-04-30
Anyone able to help me out with what's going on, please? Ubuntu will load, and then get to the login screen, wait about one second, and then go to black screen. The black screen has under-score cursor thing flashing in top left hand corner, and that's it. I can't type or anything, just have to restart. It's not letting me log in to Ubuntu at all, because of this, Any idea's please?

---

### Post by heimo on 2005-04-30
EDIT: Before you try anything explained below. Try ctrl+alt+f1, login and type startx. Watch for errors. Post them back. 
_______________

Sounds like X (Xorg the base for graphical userinterface in Ubuntu) dies for some reason. You can change to console using ctrl+alt+F1. Login and reconfigure Xorg using:
```
sudo dpkg-reconfigure xserver-xorg
``` That'll ask you bunch of questions (~15) about your hardware - it also tries to do some automatic configuring by probing the hardware.

Pay attention to graphics card driver and monitor details. If you don't know what to choose, choose vesa for driver. After reconfiguring you can restart X with *startx *or *sudo /etc/init.d/gdm restart* I suggest using startx and wathing if you get any errors. Post those errors.

Sudo will ask your password.

---

### Post by lukey on 2005-04-30
Ok, I started it back up, and choose Ubuntu from GRUB. It does same thing and goes to black screen, with cursor thing in top left corner. I hit ctrl+alt+F1, and it goes to this screen. 

There was a problem installing the selected software. 

One or more packages failed to install. This may to be bugs in the packages, or you may be out of disk space or experiencing some other problem. 

Simply trying to install those packages (or a slightly different set of packages) again may work around the problem, or at least move the installation process along a little further. You will now enter aptitude, a package management frontend, which will give you the opportunity to do this. 

If you decide not to try again, bear in mind that some packages on your system will be in a broken state until you manually resolve the problem. 

That's all that it says, what now? Don't want to hit something, because last few times i've restarted, then the GRUB (or what ever it is, blanked on name) decides not to work and give me error's, and the only way I can load anything, includeing Xp Pro, is to re-install Ubuntu, again.

---

### Post by heimo on 2005-04-30
It's a bit difficult to give comprehensive isntructions for your situation. It may be impossible to make your system working (without checking that install CD is fine, possibly downloading it again, and reinstalling). Or it may be very simple. Depends on what is missing and broken.

I'd try something like:
 ```
sudo apt-get install -f
sudo dpkg-reconfigure -a
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

---

### Post by lukey on 2005-04-30
Hmmm, ok. This time it actually let me hit enter, and continue. It's got installed packages, not installed, virtual packages, and tasks. 
Here is the list of installed packages: 

admin 
base 
comm 
devel 
doc 
editors 
games 
gnome 
graphics 
interpreters 
libdevel 
libs 
mail 
math 
misc 
net 
oldlibs 
otherosfs 
perl 
python 
science 
shells 
sound 
text 
translations 
utils 
web 
x11 

Ok, sorry about list, but, am I missing anything? 
Bah, just clicked on, Not Installed Packages, here's what it say's there: 
base 
devel 
editors 
gnome 
interpreters 
libdevel 
libs 
mail 
net 
otherosfs 
python 
text 
translations 
utils 
x11 

Now i'm confused, it says they are installed, but not at the same time? Also, how do I get to the box where I could try type that stuff you sugegsted, please?

---

### Post by heimo on 2005-04-30
Oh. Sorry for inaccurate instructions. You can do some of those steps that I listed in aptitude too. And you can get back to aptitude from shell / command prompt by typing aptitude or sudo aptitude.

In aptitude, hit u. Then hit g. Is any packages installed? You can get to menus by hitting F10 and exit to shell with q. You should definitely have package *base *installed.

If you hit enter on base, you'll get list of packages under base which are not installed. Those are just groups of packages. Hrhm... I can't explain. You have lots of packages already installed, some may be missing, some may have not been configured. Some have not been configured.

Those apt-get commands may be useful.

---

### Post by lukey on 2005-04-30
Ok, well I just exited Aptitude, and it is working!?!?!? What is going on witht his thing? Anyway's, i'm loged in and stuff. I've got terminal open, but i've got no idea what the "root", password is? Or can I Sudo <command of some sort>, to access computer on my network, because at moment it say's i don't have enough rights to... now that i'm in and console is open and such, what should I type in to get it all installed and everything, what you said before?

---

### Post by heimo on 2005-04-30
You can use sudo to run commands as root. I'd run these commands, if I were uncertain that everything was installed properly. Password sudo asks is your password (the one you set for your normal user account).
 ```
sudo apt-get install -f
sudo dpkg-reconfigure -a
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by lukey on 2005-04-30
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

That's what it said when I tried to run them.

---

### Post by heimo on 2005-04-30
And it's a very good suggestion. Why not run:
 ```
sudo dpkg --configure -a
``` 

It should configure packages that are installed, but not yet configured. And skip the  *dpkg-reconfigure -a *step on my instructions. It's probably unneccassary.

---

### Post by lukey on 2005-04-30
Ok, i've done your steps and they seemed to work fine. Some things in the configure flashed past and think some said they had error or something, but it let me use the other commands, so must have worked in some respects. I've got hub inbetween computers, and net is working for Ubuntu now. I'm using my Xp Pro machine to share the internet connection. Though i'm wondering how to be able to transfer files between the two. Any ideas, please?

---

### Post by heimo on 2005-04-30
You'll probably have to set default gateway on your Ubuntu machine to point to XP machine (for Internet connection to work, or is it already?) and later you can use sambaclient to connect to shares on XP and sambaserver to share files from Ubuntu to XP.

But did you get the graphical userinterface up? What does *startx* do? You may still need to run the dpkg-reconfigure (my first post on this thread) to get X working correctly. From there, filesharing and rest of configuring will be quite much easier if you're unfamiliar with shell / command prompt.

---

### Post by lukey on 2005-04-30
Do I have to type "sudo xstart", or just "xstart"? I tried just "xstart", and it came up with some errors saying i didn't have permission, then tried sudo xstart, and it came up with some more errors. The root prompt thing closed, and isn't wanting to open now. Once it open's i'll post what it says. Though is it just xstart, or is it sudo xstart? 


Also, whilst I remember. Internet is working on Ubuntu machine. Just can't view other computer's files, and such.

---

### Post by heimo on 2005-04-30
You don't need root privileges to run startx. Actually I advice against using desktop with root privileges, that's unneccessary and dangerous. Use your regular user account to log on to shell (command line) and type startx. (it's not xstart).

You can also try to restart gdm, which is graphical logon manager. To do that, type [i]sudo /etc/init.d/gdm start

[/i]If it doesn't start, you probably need to reconfigure xserver-xorg (see earlier posts).

---

### Post by lukey on 2005-04-30
Ok, well I can't get the command line to work at present. I'll post later when it will open for me. Here is another problem i'm having, though. 

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences. 

[ftp://ftp.nerim.net/debian-marillat/dists/stable/Release:](ftp://ftp.nerim.net/debian-marillat/dists/stable/Release:) Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
[ftp://ftp.nerim.net/debian-marillat/dists/testing/Release:](ftp://ftp.nerim.net/debian-marillat/dists/testing/Release:) Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?) 

It happened when I tried to update software. It also happened when I ran script from this site earlier. What's going on here, and what actually are repositories, please? 


Ok, rebooted and it's fine now. When i hit startx, it comes back with: 
X: user not authorized to run the X server, aborting. 
Couldn't get a file descriptor referring to the console

---

### Post by heimo on 2005-04-30
Probably your internet connection is not working. Or you can't connect nerim.net (debian-marillat). Don't worry about that, yet.

Repositories are collections of software packages, prepackaged in a easy to install, easy to manage manner. Package management takes care of dependencies, if some package requires another package to work, also those packages will be installed.

I'd be more worried about not getting back to shell. Do you get login screen? Can you cycle through differenct consoles: ctrl+alt+F1, F2, F3 and so on? Does it accept your login? No? That'd be bad sign.

---

### Post by lukey on 2005-04-30
Ok, it was just that I needed to reboot, didn't like something I did... This is what it said when I ran startx: 

X: user not authorized to run the X server, aborting.
Couldn't get a file descriptor referring to the console

---

### Post by heimo on 2005-04-30
[QUOTE=lukey]Ok, it was just that I needed to reboot, didn't like something I did... This is what it said when I ran startx: 

X: user not authorized to run the X server, aborting.
Couldn't get a file descriptor referring to the console[/QUOTE]

Uh... Not a very good sign. What's going on here... Sounds like something's broken. Do you have enough disk space? Yes? (run *df* to make sure)

This sounds quite bad. At this moment, I'd probably check the ISO you used to burn the CD (using md5sum) and reburn if neccessary and reinstall. You may have something wrong in your install. 
[http://www.linuxiso.org/viewdoc.php/verifyiso.html](http://www.linuxiso.org/viewdoc.php/verifyiso.html)

Did you get any other error messages while installing? Other problems? Did the installation format the disk without errors?

---

### Post by lukey on 2005-04-30
Got more than enough disk space. I'm not sure what to refer the md5sum to? As it isn't just an iso file. It's on the cd rom disk. I used Nero to put the image onto it. Help please?

---

### Post by heimo on 2005-04-30
Well. You downloaded iso file to burn CD, didn't you? At the same directory you downloaded it, was MD5SUMS file, which contains MD5 values for files in that directory. For example:
[http://ftp.cs.umn.edu/pub/ubuntu-releases/5.04/MD5SUMS]("http://ftp.cs.umn.edu/pub/ubuntu-releases/5.04/MD5SUMS")

Compare the value on line with same filename to the output of MD5SUM program. If it matches, isofile is fine, but the CD may still be corrupted. 

If it's not, you can try to do server install. Enter *server* at the very beginning of installation and you'll get minimal installation. If that doesn't work either, you probably have some kind of hardware-software incompatibility. If that works, you can run *apt-get install ubuntu-desktop *to get dekstop installed.

I'd also consider trying 386-version. 32-bits, yes - sucks, but you really don't get too much benefits from 64-bits if you don't have lots of memory (>4GB). And at this moment, you'll get some annoyances and lack of some software - as far as I've understood people on these forums with their 64-bit systems.

---

### Post by lukey on 2005-04-30
Ok, well i've just started to set it all up and everything. It seems to be working ok? I'm not just trying to install flash player... Anyways, don't really want to have to download whoe 32 bit. Will it work like this at all please? Still seems workable to me, at moment.

---

### Post by heimo on 2005-04-30
386 version should run fine (very, very fine) on AMD64 processors. I understand it'd be shame to use it in 32-bit mode, but if you don't have software which really needs and benefits of 64-bits, it may be just easier to use 32-bit version. 

Watch for any error messages during install. Even during first stage of installation, you can switch to other consoles (ctrl+alt+F2 and so on) and on one of them you should see what's going on on the background. If there are any errors, make some notes.

---

### Post by lukey on 2005-04-30
Ok, i'm better off to install it again on Xp Pro machine currently running my net connection, and then letting it do default install? Also, how should I set my HDD? I've got 160 GB HDD, it is partitioned in half. And think it made another smaller spot for something else in last install. Anyways, I'll just clear the second part of partition when I have new iso file downloaded and put to cd. Though i'm not to sure about files types, able to give me hand with what to set about them, please?

---

### Post by heimo on 2005-04-30
[QUOTE=lukey]Ok, i'm better off to install it again on Xp Pro machine currently running my net connection, and then letting it do default install? Also, how should I set my HDD? I've got 160 GB HDD, it is partitioned in half. And think it made another smaller spot for something else in last install.
[/QUOTE]
The small partition is probably swap. In Linux is custom to make swap partition instead of "pagefile". That's ok. For desktop it's ok to have everything else in one partition, that's called root partition ( mountpoint / ). 

[QUOTE=lukey]
 Anyways, I'll just clear the second part of partition when I have new iso file downloaded and put to cd. Though i'm not to sure about files types, able to give me hand with what to set about them, please?[/QUOTE]

What file types are you talking about? Oh... Filesystems? You should probably use ext3 for your root partition. That's what most people are using. Don't use ext2 - ext3 is journaled and handles unclean unmounts much more nicely (for example power loss).

---

### Post by lukey on 2005-04-30
Ok, i'm browseing through Ubuntu 5.04 download sites for bittorrents. Am I going for the Intel x86 install cd? Also, is it ok to download bittorrent, just that my net has 10 hour connection, and, it might not finish before then. 


This look right? 
ubuntu-5.04-install-i386.iso.torrent

---

### Post by heimo on 2005-04-30
My experience is that bittorrents are much faster than ftp/http. Yes, Intel x86 / 386 is right platform for 32-bit (and AMD64 is backwards compatible to this). So yes, that torrent looks fine.

To get that file in 10 hours, you need to avarage around 150kbps, under 20kB/s.

---

### Post by lukey on 2005-04-30
Ok, that's cool. Probably take me about 13 hours or so to download it, touch wood. So i'll probably be posting back again in not to much time. Thank's for all that help so much.

---

### Post by Briggzee on 2005-04-30
I'm having a similiar problem.
When Ubuntu is just about to start the login for KDE the screen goes black with a blinking underscore in the top left.

I have two Graphic Cards, and when I plug in my monitor into the second card the Login Page is loaded up and ready to go. Perhaps you have a similiar setup?

---

