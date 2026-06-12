---
title: "Lightbulb"
date: 2006-09-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by kuja on 2006-09-18
Alright, I've decided to have an idea (this only happens every once in a while, so I'm going to try to take advantage of it). 

If I were to, say, create a small, simplistic PyQT graphical application whose purpose would be to take care of installing the programs in the 64-bit subforum sticky, would anyone use it? Do you like the idea? Why or why not?

---

### Post by Kilz on 2006-09-18
> **kuja said:**
> Alright, I've decided to have an idea (this only happens every once in a while, so I'm going to try to take advantage of it). 

If I were to, say, create a small, simplistic PyQT graphical application whose purpose would be to take care of installing the programs in the 64-bit subforum sticky, would anyone use it? Do you like the idea? Why or why not?

I like the idea, the 64bit needs a program like that. It would be a powerful piece of anti fud. Feel free to use any script or file I have avilable on any howto I have created if it helps.

---

### Post by kuja on 2006-09-19
I think they may come in handy, however, it's going to be a while before I get started :\

I just ran into the reason why it is very important to keep backups. Something failed and I wound up with massive corruption in both drives. Luckily I have backups of 75% of things, but it'll be a while before I'm back up :(

---

### Post by Kilz on 2006-09-19
> **kuja said:**
> I think they may come in handy, however, it's going to be a while before I get started :\

I just ran into the reason why it is very important to keep backups. Something failed and I wound up with massive corruption in both drives. Luckily I have backups of 75% of things, but it'll be a while before I'm back up :(

I know the feeing. Back when I was running Windows I bought Norton Ghost 2003. Every so often I do a partition backup. I have ati graphics and learned a lesson a few months ago when I had to reinstall. Im also starting to use Edgy. So backing up may become more frequent.
I think the things that will come in most handy to you is the firefox32.deb it will make it easy to install that application. Its on some free web space I get from comcast. I would also like to offer to mirror the application for you if you need any space. I have a few more email accounts I can make. Each comes with 25meg of free web hosting.

---

### Post by kuja on 2006-09-20
I'm finally back up and running, as of this morning-ish :D
I'm off to a pretty strong start I think, seeing as I don't know Python nor QT... hehehe

Mind taking a look at what I have started before I run to far with it?

I attached said tarball to the post... extract it and run with "python run.py".

I think the one thing throughout all this that will give the most trouble will probably be the packaging... I know nothing of packaging.

Perhaps a non-generic name would help too...

---

### Post by Kilz on 2006-09-21
> **kuja said:**
> I'm finally back up and running, as of this morning-ish :D
I'm off to a pretty strong start I think, seeing as I don't know Python nor QT... hehehe

Mind taking a look at what I have started before I run to far with it?

I attached said tarball to the post... extract it and run with "python run.py".

I think the one thing throughout all this that will give the most trouble will probably be the packaging... I know nothing of packaging.

Perhaps a non-generic name would help too...

I know just a little about making packages. As long as it isnt a source package.

I cant get it to show
```
~/Desktop/Mockup$ python run.py
Traceback (most recent call last):
  File "run.py", line 1, in ?
    from qt import *
ImportError: No module named qt
```

Maybe its because its qt and im in gnome? not real sure.

---

### Post by kuja on 2006-09-21
Try installing python2.4-qt3

---

### Post by kuja on 2006-09-21
It turns out this isn't such a bad idea afterall :) After many hours of toying with things (mostly because I don't know so many things...) I've got it capable of setting up one of the programs. I used it to install Opera for me!

---

### Post by Kilz on 2006-09-21
> **kuja said:**
> It turns out this isn't such a bad idea afterall :) After many hours of toying with things (mostly because I don't know so many things...) I've got it capable of setting up one of the programs. I used it to install Opera for me!
Nice clean simple interface. :D  I also like the fact you can only install one thing at a time. One of the things I hate about automatrix is that it installs a boatload. Just a question, will it also install the mplayer plugin for the browsers? Also how dose it know what browser to install the plugin for? I think the plugins work in both firefox and opera.
Just a note so we dont forget it, when its packaged for Edgy we are going to have to make python-qt3 a requirement.

---

### Post by kuja on 2006-09-21
Well, soon as I dig up how that mplayer plugin is installed exactly, see about it. I figure I'll also add a symlink from mplayer32 to /usr/bin/mplayer, if /usr/bin/mplayer doesn't already exist, and if konqueror is detected, install kmplayer as well.

Yeah, if I remember right edgy did something right and started doing away with package names that include the version numbers, keeping the version information in the version field of the package.... so yes, it'll depend on python-qt3.

For the flash plugin I'll check if ~/.firefox/plugins exist, and if /usr/lib/opera/plugins exists, installing in the locations if it finds them.

---

### Post by Kilz on 2006-09-21
> **kuja said:**
> Well, soon as I dig up how that mplayer plugin is installed exactly, see about it. I figure I'll also add a symlink from mplayer32 to /usr/bin/mplayer, if /usr/bin/mplayer doesn't already exist, and if konqueror is detected, install kmplayer as well.

Yeah, if I remember right edgy did something right and started doing away with package names that include the version numbers, keeping the version information in the version field of the package.... so yes, it'll depend on python-qt3.

For the flash plugin I'll check if ~/.firefox/plugins exist, and if /usr/lib/opera/plugins exists, installing in the locations if it finds them.

If you use my deb, it installs to /usr/local/firefox32 inside is a /plugins folder. You may want to since it adds a launcher to the menu and adds some other files to make firefox interact with other programs better.

---

### Post by kuja on 2006-09-21
Well, I've overhauled much of the stuff that isn't seen. I didn't get much done at all, but I've learned so much today! 

I've still only got Opera implemented, it took a while itself, but wasn't too bad. My main obstacle in writing the program was Python and QT, the interface, and the like. I think I've got the grounds of the program done though, so I should be able to resume adding programs for it on Sunday without more delays from playing with code.

Anyone mind giving it a test to see if it works? Remember, only Opera installation is implemented, but hey, it's a solid start. Also, the program depends on the python2.4-qt3 package(dapper) or python-qt3 package(edgy). Currently to run it, pull up a terminal, cd to the directory, and run "python run.py".

Edit: It's attached to this post.
Edit: Also, do not be alarmed after accepting the license. The GUI will stop responding. I'm not entirely sure why it gives me this trouble :( If you wait patiently for a couple minutes, it will keep going. The part where it seems to hang is in fact the part where it's downloading the files it needs.

---

### Post by tzulberti on 2006-09-21
I am getting the following error while trying to install opera:
Traceback (most recent call last):
  File "/home/tzulberti/Prueba/main.py", line 99, in Install
    self.installOpera()
  File "/home/tzulberti/Prueba/main.py", line 130, in installOpera
    dialog.textLicense.setText(license.read())
AttributeError: 'str' object has no attribute 'read'

That is a great idea... =D> =D> =D>

---

### Post by kuja on 2006-09-22
Sorry, must have lost a change to the file at some point or another. Here, try this (attatched to this post).

---

### Post by Kilz on 2006-09-22
> **kuja said:**
> Sorry, must have lost a change to the file at some point or another. Here, try this (attatched to this post).

I tried it, since I didnt have opera installed. You are correct it hesitates a little once you hit install, but it installed opera just fine. 
I did get this in the terminal
```

kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
DCOP Cleaning up dead connections.
cp:
cannot stat `/tmp/libqt/usr/lib/libqt*'
: No such file or directory

dpkg - warning, overriding problem because --force enabled:

package architecture (i386) does not match system (amd64)

Selecting previously deselected package opera.
(Reading database ...
125652 files and directories currently installed.)
Unpacking opera (from .../opera_9.01-20060728.6-shared-qt_en_i386.deb) ...
Setting up opera (9.00-20060616.7) ...

kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!

```
And the sudo password box had some strange code on it, Im attaching it so you can see.

All in all real nice for a for it at this stage :D

---

### Post by kuja on 2006-09-22
Thanks Kilz. I'm pretty sure I know what all of that means. 

The DCOP stuff at the beginning may very well be the fact that you're running GNOME and not KDE, but if it works, it can safely be ignored.

"cp:
cannot stat `/tmp/libqt/usr/lib/libqt*'"

This may be an error on my part. I'll have to double check where I'm putting things, but this is a fix to get the shared-qt version of Opera to work properly on 64-bit systems. Otherwise, Opera may complain that it can't find libqt3-mt even though it's installed.
dpkg - warning, overriding problem because --force enabled:

package architecture (i386) does not match system (amd64)

Selecting previously deselected package opera.
(Reading database ...
125652 files and directories currently installed.)
Unpacking opera (from .../opera_9.01-20060728.6-shared-qt_en_i386.deb) ...
Setting up opera (9.00-20060616.7) ...[/quote]

Here's where it installs Opera, I may want to set the --quiet option, or equivalent.

As per the weird commands you see in the gksu dialog, that's the command to be run. In kdesu I can diable that with the "-d" switch (do not show command), is there a similar command for gksu?
[quote]

Also, Kilz, I have a couple requests of you that will help me at some point or another. Can you give to me the location of any GNOME "system" program "*.desktop" file? Synaptic would probably do nicely. In addition, can you also give me the contents of the file either in an attachment or directly in a post? I need it to help write the programs *.desktop file for GNOME users. Oh, almost forgot to tell you, you can find these files in /usr/share/applications. Thanks!

---

### Post by Kilz on 2006-09-23
> **kuja said:**
> Thanks Kilz. I'm pretty sure I know what all of that means. 

The DCOP stuff at the beginning may very well be the fact that you're running GNOME and not KDE, but if it works, it can safely be ignored.

"cp:
cannot stat `/tmp/libqt/usr/lib/libqt*'"

This may be an error on my part. I'll have to double check where I'm putting things, but this is a fix to get the shared-qt version of Opera to work properly on 64-bit systems. Otherwise, Opera may complain that it can't find libqt3-mt even though it's installed.
dpkg - warning, overriding problem because --force enabled:

package architecture (i386) does not match system (amd64)

Selecting previously deselected package opera.
(Reading database ...
125652 files and directories currently installed.)
Unpacking opera (from .../opera_9.01-20060728.6-shared-qt_en_i386.deb) ...
Setting up opera (9.00-20060616.7) ...

Here's where it installs Opera, I may want to set the --quiet option, or equivalent.

As per the weird commands you see in the gksu dialog, that's the command to be run. In kdesu I can diable that with the "-d" switch (do not show command), is there a similar command for gksu?


Also, Kilz, I have a couple requests of you that will help me at some point or another. Can you give to me the location of any GNOME "system" program "*.desktop" file? Synaptic would probably do nicely. In addition, can you also give me the contents of the file either in an attachment or directly in a post? I need it to help write the programs *.desktop file for GNOME users. Oh, almost forgot to tell you, you can find these files in /usr/share/applications. Thanks!


Cool , was just telling you the errors in case they help get rid of the delay. I dont think the errors in the terminal are a big thing because once the application has an installer users wont see a terminal. I tested this by [making a quick package]("http://home.comcast.net/~deletebox/Simple64-0.4.1-dapper.deb") and it installs and runs nice. The delay is going to have some newbie thinking its broken, when in fact its just working.
The synaptic.desktop file is in /usr/share/applications. But there are 2 of them. Looking at them in a text editor it appears one is for kde and the other gnome.

---

### Post by kuja on 2006-09-23
Cool, so how did you build the package exactly? 

I'm not sure what the problem with the pausing of it, in fact, at first, I thought it wasn't working myself, then I thought again. Seems anything that takes a long time will give it lots of troube with painting, I guess. Perhaps I should find a python/qt developer that knows more on this matter... Oh, and I'd like to repeat one of my other questions, does gksu have an option for not displaying the command? (ie: gksu --help). 

Thanks for the two .desktop files also, I had figured I'd probably  need one for each, guess I figured right. Ah well, gonna go eat.

---

### Post by Kilz on 2006-09-23
> **kuja said:**
> Cool, so how did you build the package exactly? 

I'm not sure what the problem with the pausing of it, in fact, at first, I thought it wasn't working myself, then I thought again. Seems anything that takes a long time will give it lots of troube with painting, I guess. Perhaps I should find a python/qt developer that knows more on this matter... Oh, and I'd like to repeat one of my other questions, does gksu have an option for not displaying the command? (ie: gksu --help). 

Thanks for the two .desktop files also, I had figured I'd probably  need one for each, guess I figured right. Ah well, gonna go eat.

There is a [good page on how to make packages here. ]("http://linuxdevices.com/articles/AT8047723203.html") It only works with already existing binaries, and I'm seein now python. Thats how I make the firefox32 .deb file.
If you could somehow let the user know its working that would be good. Because thats whats happening. Its downloading and running the setup. Otherwise you are going to have newbies force killing it while its working.

---

### Post by kuja on 2006-09-25
Major update here:

*Reworked a lot of stuff, fixed some bugs, yadda yadda yadda
*Pointed Opera at the latest version
*Added firefox support
*Added a shell script for building the deb: build.sh

As per the firefox support, Kilz, I based it on your Kubuntu Firefox32 script, as I figured it probably  had to include extra deps. Not sure if my assumption was right or not. Also, one question about that script. Why does it download ia32-libs-gtk from an external repository? It looks like the same version, 16, is also in the ubuntu repos... so I pointed at it instead. 

Assuming that's not a major problem, I still get a lot of errors when launching firefox32 from the terminal:

ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
esd: no process killed
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(firefox-bin:21424): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libqtengine.                                                                                                   so: cannot open shared object file: No such file or directory

(firefox-bin:21424): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libqtengine.                                                                                                   so: cannot open shared object file: No such file or directory
GConf Error: Failed to launch configuration server: Failed to execute child process "/usr/lib/libgconf2-4/gconfd-2" (No such file or directory)

*** about to copy smart keywords
*** done copying smart keywords

(firefox-bin:21424): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libqtengine.                                                                                                   so: cannot open shared object file: No such file or directory

(firefox-bin:21424): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libqtengine.                                                                                                   so: cannot open shared object file: No such file or directory
GConf Error: Failed to launch configuration server: Failed to execute child process "/usr/lib/libgconf2-4/gconfd-2" (No such file or directory)

It still starts from the gui okay though, so I guess it's not really that much of a problem. Perhaps I should add *.desktop files for it so it will be added to the menu as well? I think I'll go do that. 

The tarball and deb package can be found a these two  urls, respectively.
[http://www.xnowherex.net/ubuntu/simple64-0.5.0.tar.bz2](http://www.xnowherex.net/ubuntu/simple64-0.5.0.tar.bz2)
[http://www.xnowherex.net/ubuntu/simple64_0.5.0_amd64.deb](http://www.xnowherex.net/ubuntu/simple64_0.5.0_amd64.deb)

Notice:
The GUI hanging still occurs when you click install. It can safely be ignored. It's just downloading things.

When installed, you should be able to simply launch it from your menu, if it's not there in GNOME, let me know, that's not something I tested. (Everything's fine in KDE-land.)

---

### Post by Kilz on 2006-09-25
> **kuja said:**
> Major update here:

*Reworked a lot of stuff, fixed some bugs, yadda yadda yadda
*Pointed Opera at the latest version
*Added firefox support
*Added a shell script for building the deb: build.sh

As per the firefox support, Kilz, I based it on your Kubuntu Firefox32 script, as I figured it probably  had to include extra deps. Not sure if my assumption was right or not. Also, one question about that script. Why does it download ia32-libs-gtk from an external repository? It looks like the same version, 16, is also in the ubuntu repos... so I pointed at it instead. 

Assuming that's not a major problem, I still get a lot of errors when launching firefox32 from the terminal:

ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
esd: no process killed
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(firefox-bin:21424): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libqtengine.                                                                                                   so: cannot open shared object file: No such file or directory

(firefox-bin:21424): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libqtengine.                                                                                                   so: cannot open shared object file: No such file or directory
GConf Error: Failed to launch configuration server: Failed to execute child process "/usr/lib/libgconf2-4/gconfd-2" (No such file or directory)

*** about to copy smart keywords
*** done copying smart keywords

(firefox-bin:21424): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libqtengine.                                                                                                   so: cannot open shared object file: No such file or directory

(firefox-bin:21424): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libqtengine.                                                                                                   so: cannot open shared object file: No such file or directory
GConf Error: Failed to launch configuration server: Failed to execute child process "/usr/lib/libgconf2-4/gconfd-2" (No such file or directory)

It still starts from the gui okay though, so I guess it's not really that much of a problem. Perhaps I should add *.desktop files for it so it will be added to the menu as well? I think I'll go do that. 

The tarball and deb package can be found a these two  urls, respectively.
[http://www.xnowherex.net/ubuntu/simple64-0.5.0.tar.bz2](http://www.xnowherex.net/ubuntu/simple64-0.5.0.tar.bz2)
[http://www.xnowherex.net/ubuntu/simple64_0.5.0_amd64.deb](http://www.xnowherex.net/ubuntu/simple64_0.5.0_amd64.deb)

Notice:
The GUI hanging still occurs when you click install. It can safely be ignored. It's just downloading things.

When installed, you should be able to simply launch it from your menu, if it's not there in GNOME, let me know, that's not something I tested. (Everything's fine in KDE-land.)

Thank you for the errors, it may help fix a problem with running 32bit firefox on Kubuntu I have been ](*,)  over.
Try this to fix one of the missing qtengine, and tell me if the controlls improve or if they are still just plain

```
sudo apt-get install gtk2-engines-gtk-qt
```

Also , yes until reciently I didnt know there were different .desktop files. Synaptic showed us. I am planing on adding one for kde to the firefox32 deb file. Im also going to make one without a version and upload it so you dont have to keep making new versions each time firefox upgrades.

---

### Post by kuja on 2006-09-25
Turns out it was already installed, also, The Firefox32.desktop file works for both KDE and GNOME.... I just looked over it because the icon wasn't displaying(makes things significantly harder to notice IMO), silly me, but I do things like that. Wait, come to think of it, it's pretty obvious why. Firefox32 can't load 64-bit libraries, silly me.

---

### Post by Kilz on 2006-09-25
> **kuja said:**
> Turns out it was already installed, also, The Firefox32.desktop file works for both KDE and GNOME.... I just looked over it because the icon wasn't displaying(makes things significantly harder to notice IMO), silly me, but I do things like that. Wait, come to think of it, it's pretty obvious why. Firefox32 can't load 64-bit libraries, silly me.

Im going to have to add the 32bit gtk2-qt package then. There is no icon in the menu on kde for firefox32?

---

### Post by kuja on 2006-09-25
As per adding that library, I welcome you to try. It looks like it has A LOT of dependencies.

And yeah, The Firefox32 Menu item doesn't show an icon in KDE.

---

### Post by kuja on 2006-09-26
No package right now, however:

*Acrobat Reader support implemented
*Bonfire support implemented
*DVD::Rip support implemented
*Firefox32 support implemented
*Sun Java 5 (ia32-sun-java5-bin) support implemented
*Listen support implemented
*Opera support implemented
*PartImage support implemented

That leaves Flash, Matlab, Mplayer32, Rar, Realplayer, Skype, Wengophone, and Wine to go yet.

---

### Post by tzulberti on 2006-09-26
GREAT =D> 
It would be great if this threat is put as an Sticky...

---

