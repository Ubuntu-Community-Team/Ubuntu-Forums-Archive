---
title: "Opera on 64-bit system"
date: 2005-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by ubernoob on 2005-10-14
I have installed:
xlibs
motif-clients
libmotif3

then:

 sudo dpkg -i --force-architecture opera-static_8.50-20050916.1-qt_en_i386.deb

When i run opera, i get this in the terminal:

ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
Qt: Locales not supported on X server

And this in a opera error window:

Opera encountered a problem during plug-in setup.
Plug-ins will not work properly.
Check your installation.

Could not start plug-in executable 'operamotifwrapper'.
/usr/lib/opera/plugins/operamotifwrapper-3
Please install Motif.

Plug-in path
(Path can be modified in Preferences dialog)

/usr/lib/opera/plugins

Opera works, but does anyone know how to remove the errors?

---

### Post by Jeldert on 2005-10-14
Having the exact same message here, but I only installed xlibs.

PS, Opera not working correctly was the main reason I used the i386 of Ubuntu 5.04. I hope I don't have to go to the i386 version of 5.10 on my AMD64...

---

### Post by Inigo Montoya on 2005-11-02
i managed to solve the 'operamotifwrapper' problem by installing the i386 lesstif2 package "by hand" (dpkg -i --force-architecture blah.package.deb). force architecture here is ok because amd64 is binary compatible to i386. if you just install lesstif2 by using synaptic you get the amd64 version of the package which opera/operamotifwrapper doesn't like.
greetings

---

### Post by rplantz on 2005-11-16
[QUOTE=Inigo Montoya]i managed to solve the 'operamotifwrapper' problem by installing the i386 lesstif2 package "by hand" (dpkg -i --force-architecture blah.package.deb). force architecture here is ok because amd64 is binary compatible to i386. if you just install lesstif2 by using synaptic you get the amd64 version of the package which opera/operamotifwrapper doesn't like.
greetings[/QUOTE]

I've tried this several times. I downloaded lesstif2_0.93.94-11.4_i386.deb and did a force-architecture install. It says that everything went okay. But I still get the operamotifwrapper error message from opera.

Did you do anything else?

Bob

---

### Post by ubernoob on 2005-11-17
If you get the lesstif/motif to work, then i think you will get the flash to work as well.

---

### Post by ubernoob on 2005-11-17
WOHOOO!!!! :D 

I got it to work with flash and motif. :)

I'll try to explain what i did as good as i can. But i should warn you that I'm not sure if this will work 100% or if you might have problems with the lesstif with other 64-bit apps.

First download [lesstif2  -i386]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fl%2Flesstif1-1%2Flesstif2_0.93.94-11.4ubuntu3_i386.deb&md5sum=80e79cdb32aba826fd35cf4d116d54a7&arch=i386&type=main")

If you have installed the 64-bit version, you might want to uninstall it.

Then do
dpkg -i --force-architecture lesstif.package.deb

I had some problems since i had tried to fix this problem by copying some lib files.

```
ubernoob@ubuntu:~$ sudo dpkg -i --force-architecture lesstif2_0.93.94-11.4ubuntu3_i38 6.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package lesstif2.
(Reading database ... 101961 files and directories currently installed.)
Unpacking lesstif2 (from lesstif2_0.93.94-11.4ubuntu3_i386.deb) ...
Setting up lesstif2 (0.93.94-11.4ubuntu3) ...
ldconfig: libraries libXm.so.2.0.1 and libXm.so.3 in directory /usr/lib have sam e soname but different type.

```

I had copied the libXm.so.2 (64-bit) over to libXm.so.3. So i had to recopy it. You might need to do the same, but i'm not sure.

```
ubernoob@ubuntu:~$ cd /usr/lib
ubernoob@ubuntu:/usr/lib$ ls -l libXm*
lrwxrwxrwx  1 root root      10 2005-11-17 12:15 libXm.so.2 -> libXm.so.3
-rw-r--r--  1 root root 1488180 2005-09-16 22:47 libXm.so.2.0.1
-rw-r--r--  1 root root 1794104 2005-10-24 21:08 libXm.so.3
lrwxrwxrwx  1 root root      15 2005-10-14 01:14 libXmu.so.6 -> libXmu.so.6.2.0
-rw-r--r--  1 root root  100960 2005-07-25 12:18 libXmu.so.6.2.0
lrwxrwxrwx  1 root root      16 2005-10-14 01:15 libXmuu.so.1 -> libXmuu.so.1.0.0
-rw-r--r--  1 root root   13984 2005-07-25 12:18 libXmuu.so.1.0.0
ubernoob@ubuntu:/usr/lib$ sudo mv libXm.so.3 libXm.so.3.bak
ubernoob@ubuntu:/usr/lib$ sudo cp libXm.so.2.0.1 libXm.so.2

```

After this you might want to download flash:
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_7_linux.tar.gz]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_7_linux.tar.gz")

Copy these files to your plugins folder. Default: /usr/lib/opera/plugins/
libflashplayer.so 
flashplayer.xpt

If you have problems, you can try "opera --debugplugin"

Now i'll try to fix the 32-bit java.

---

### Post by rplantz on 2005-11-17
[QUOTE=ubernoob]WOHOOO!!!! :D 

I got it to work with flash and motif. :)

Now i'll try to fix the 32-bit java.[/QUOTE]

Fantastic! Thank you for sharing what you did; it also worked for me!

I'm looking forward to your comments about java.

I've been using opera mail. The way they organize things is very different. I'm not sure I like it, but that's probably because it's so new to me. I like learning new things, so I'll keep on working with it.

Bob

---

### Post by ubernoob on 2005-11-21
I have managed to get suns java to work with opera, but the applets opens in a new window instead of in the webpage.

This is how i did it:

[http://javashoplm.sun.com/ECom/docs/Welcome.jsp?StoreId=22&PartDetailId=jre-1.5.0_05-oth-JPR&SiteId=JSC&TransactionId=noreg]("http://javashoplm.sun.com/ECom/docs/Welcome.jsp?StoreId=22&PartDetailId=jre-1.5.0_05-oth-JPR&SiteId=JSC&TransactionId=noreg") 
Download jre-1_5_0_05-linux-i586.bin

If you have or want a 64bit java, you should rename the old one before installing a new one. Sun's java is in /usr/local/. 

```
sudo cp jre-1_5_0_05-linux-i586.bin /usr/local/
cd /usr/local/
sudo mv jre1.5.0_05/ jre1.5.0_05-amd64/ (only if you already have the jre installed)
sudo ./jre-1_5_0_05-linux-i586.bin
sudo mv jre1.5.0_05/ jre1.5.0_05-i585/
sudo mv jre1.5.0_05-amd64/ jre1.5.0_05/ (move the 64-bit java back where it was)

```

Start Opera. Go to Tools-->Preferences-->Advanced-->Enable Java. Then Java options. Insert the java path: "/usr/local/jre1.5.0_05-i585/lib/i386/".

Restart Opera. Then try java on this page: 
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

If anyone have any ideas how to get the java inside the webpage, please tell me.

---

### Post by rplantz on 2005-11-21
[QUOTE=ubernoob]
Start Opera. Go to Tools-->Preferences-->Advanced-->Enable Java. Then Java options. Insert the java path: "/usr/local/jre1.5.0_05-i585/lib/i386/".

Restart Opera. Then try java on this page: 
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

If anyone have any ideas how to get the java inside the webpage, please tell me.[/QUOTE]

One minor correction:
Go to Tools-->Preferences-->Advanced-->Content-->Enable Java

A weirdness is that you cannot close the new java applet window. You need to close the original one. But you can resize the applet window, etc. Hmmm....

---

### Post by ubernoob on 2005-11-22
Thank you for the correction. :)

I think the reason for you can't close the window is since applets doesn't inherit the window stuff. The "X" in the corner isn't programmed to shut down the program. So if you include it in your applet when you make it, i think you would be able to close it. (But noone does :-))

[COLOR="Red"][B]But be aware that a new security update was released today! So you should grab [Opera 7.51]("http://www.opera.com") Remember to choose the static deb file.

[Technical Description]("http://www.frsirt.com/english/advisories/2005/2519")
[/B][/COLOR]

I would like to see Internet Explorer make updates that fast... They have known about [this security issue]("http://www.microsoft.com/technet/security/advisory/911302.mspx") since may this year [-X , but haven't bothered to fix it.](*,)

---

### Post by eightysix on 2005-11-22
I'm getting this problem:

```
$ sudo dpkg -i --force-architecture opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 111893 files and directories currently installed.)
Preparing to replace opera 8.50-20050916.5 (using opera_8.50-20050916.5-shared-qt_en_sarge_i386.deb) ...
Unpacking replacement opera ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on libqt3c102-mt; however:
  Package libqt3c102-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera

```

I would install libqt3c102-mt, but it automatically uninstalls all of the KDE apps that I have installed. Any help?

Edit: Never mind, I just downloaded a different version of Opera.

---

### Post by daedalusman on 2005-11-28
Can someone help me out here, I'm getting a problem when I try to run opera.
In the terminal...

ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/8.51-20051114.6/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

and then opera does not start up.
Thanks

---

### Post by rplantz on 2005-11-29
[QUOTE=daedalusman]Can someone help me out here, I'm getting a problem when I try to run opera.
In the terminal...

ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/8.51-20051114.6/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

and then opera does not start up.
Thanks[/QUOTE]

It looks like you're trying to run the shared library version, which will attempt to use the 64-bit libraries. You need to use the static one, which includes the 32-bit library functions it uses.

Read from the beginning of this thread and I think you will see what you need to do.

---

### Post by rplantz on 2005-11-29
[QUOTE=ubernoob][COLOR="Red"][B]But be aware that a new security update was released today! So you should grab [Opera 7.51]("http://www.opera.com") Remember to choose the static deb file.

[Technical Description]("http://www.frsirt.com/english/advisories/2005/2519")
[/B][/COLOR]

I would like to see Internet Explorer make updates that fast... They have known about [this security issue]("http://www.microsoft.com/technet/security/advisory/911302.mspx") since may this year [-X , but haven't bothered to fix it.](*,)[/QUOTE]

Thank you for the heads up. I just installed it and am using it now.

The IE notice seems to have been written by a lawyer, not a developer. Perhaps there is another market for MS -- ass covers. They seem to be very good at it. As a long time Mac person (March 1984), they are almost as good. :-)

---

### Post by daedalusman on 2005-11-29
Ok, so I ran what ubernoob posted, and I'm still not getting it to work. When I run the ls -l libXm* comand there is no mention of libXm.so.3, I'm thinking that is what my problem is. Can someone help me out here? Thanks

---

### Post by ubernoob on 2005-11-29
If you got libXm.so.2. You should copy it to libXm.so.3.

If you don't have it, you have to install it. Can't remember where i found it.

---

### Post by rplantz on 2005-11-30
[QUOTE=daedalusman]Ok, so I ran what ubernoob posted, and I'm still not getting it to work. When I run the ls -l libXm* comand there is no mention of libXm.so.3, I'm thinking that is what my problem is. Can someone help me out here? Thanks[/QUOTE]

Did you try doing it without the libXm* stuff?

ubernoob had done some things with his libXm* libraries, so had to perform these additional operations. I had not, so I did not need to do them, and it worked for me.

For reference, I have:
```

lrwxrwxrwx  1 root root      14 2005-11-17 20:00 libXm.so.2 -> libXm.so.2.0.1
-rw-r--r--  1 root root 1488180 2005-09-16 13:47 libXm.so.2.0.1
-rw-r--r--  1 root root  195968 2005-07-25 03:18 libXmu.a
lrwxrwxrwx  1 root root      15 2005-10-17 19:56 libXmu.so -> libXmu.so.6.2.0
lrwxrwxrwx  1 root root      15 2005-10-03 12:49 libXmu.so.6 -> libXmu.so.6.2.0
-rw-r--r--  1 root root  100960 2005-07-25 03:18 libXmu.so.6.2.0
-rw-r--r--  1 root root   18400 2005-07-25 03:18 libXmuu.a
lrwxrwxrwx  1 root root      16 2005-10-17 19:56 libXmuu.so -> libXmuu.so.1.0.0
lrwxrwxrwx  1 root root      16 2005-10-03 12:49 libXmuu.so.1 -> libXmuu.so.1.0.0

```

---

### Post by ubernoob on 2005-11-30
This is where i got the libXm.so3 from. I followed some part of this guide. It might help you as well.

[https://wiki.ubuntu.com/OperaBrowser?action=show&redirect=Opera]("https://wiki.ubuntu.com/OperaBrowser?action=show&redirect=Opera")

> Operamotif problems

Add multiverse sources and do 

sudo apt-get install libmotif3 lesstif1 lesstif2 motif-clients

You might also want to try this: 

cd /usr/lib; cp libXm.so.2 libXm.so.3

But to get the lesstif2 with flash to work, you need to install the 32-bit version which i explained in an earlier post (#6).

---

### Post by rplantz on 2005-12-09
I figured out how to get realplayer working in my Opera. Here's what I did:


1. Follow the procedure at
[http://ubuntuforums.org/showthread.php?t=91035&highlight=acroread](http://ubuntuforums.org/showthread.php?t=91035&highlight=acroread)
to create a 32-bit chroot and install realplay32. (I installed it in /usr/local/bin instead of /usr/sbin.)

2. In Opera go to Tools->Preferences.

3. Click on the Advanced tab.

4. Edit the entry:
         MIME type applications/smil with File extension(s) smi,smil

   to Open with other application:
          /usr/local/bin/realplay32

I can now listen to npr while I play!

Any errors, improvements, etc. are very welcome.

---

### Post by bernardfrancois on 2006-01-02
Thank you people!

I'm going to install opera one of these days.
Since there's a lot of information in this thread, I'll write a bash script for installing opera and all plug-ins automaticly.

I'll post it here.

---

### Post by Terracotta on 2006-02-06
Hye, is the bash script getting along? I don't know about anyone of you, but are there some people who'ld be interested in getting something like automatix up and running for 64-bit? which might install a chroot or stuff like that? I'm new, and willing to help, but I have absolutely no idea of how that stuff works.

---

### Post by bernardfrancois on 2006-02-06
I didn't start with the script yet... the exams just finished and they gave us a lot of work already. And because nobody replied on my last post, I thought nobody would be waiting for a script.
For now I have too much tasks to do for school, but after next week there will probably be a little time... or when I have a break I could work on it.
I'll do my best to keep my promise.

[edit]
I'll start working on it right now.
[/edit]

[edit2]
I will quit working on it for today. Probably next week I'll continue. For curious people: [here](http://www.evonet.be/~bfran/extern/operaInstall_WIP01.sh) is what I have till now. It doesn't install anything, it's just an introduction and a few tests (to check if the script is running on Ubuntu on the amd64 kernel).
It will be an interactive script (probably with command line options later on in case someone would like to use it in another script). There could be two ways to install opera; in a chrooted environement (already existing or not) or using the static version. While running the script, the user will be able to choose which plug-ins to install.
[/edit2]

---

### Post by Aithnea on 2006-03-04
I must be really stupid, I can't seem to figure out how to install Opera on my 64bit machine.  I've tried following what the thread says but I think you need to already have it installed to do what people suggest so I tried following the Opera Browers Wiki entry <a href="https://wiki.ubuntu.com/OperaBrowser?highlight=%28opera%29">here</a> but all I get is errors when I do what it suggests.  Can I please have some help?  I loved using Opera when I still using Windows and miss it terrably.  Thanks for the help.

---

### Post by bernardfrancois on 2006-03-06
I'm running opera 8.02, of which I installed the static version. The installation wasn't difficult (just by using dpkg), but I still have the ads in opera (since it's an older version of opera).

[edit]
I noticed this torrent: [http://www.opera.com/download/torrents/opera-8.52-20060201.1-static-qt.i386-en.tar.gz.torrent](http://www.opera.com/download/torrents/opera-8.52-20060201.1-static-qt.i386-en.tar.gz.torrent)
It's a static version of opera 8.52
Unfortunately I won't be able to put the download of a torrent in a script I guess...
[/edit]

[edit2]
I got it working. 
[/eidt2]

---

### Post by bernardfrancois on 2006-03-06
[This script](http://www.evonet.be/~bfran/extern/operaInstall_WIP02.sh) wil install opera on your 64bit system, using the 32-bit static version. Just run it using **sudo bash operaInstall_WIP02.sh**. The script still has 'work in progress' in it's name because it doesn't support installing a chrooted environment yet.
Anyone who wants to change the script to extend it or to improve it, go ahead and post it here...

---

### Post by linuxNewb555 on 2006-03-09
Ok Bernard, i think i might try your script. I'm like Aithnea, I loved Opera in Windows (while it worked) and i can't wait to get back to it in my new environment (Ubuntu Linux with AMD64) This is my current hurdle, getting opera to work. Thanks for your time.

---

### Post by eladamri on 2006-03-12
This question seems idiotic, but I seriously cannot find the static version of Opera on Opera's site.

Any suggestions?

---

### Post by bernardfrancois on 2006-03-14
[http://www.opera.com/download/torrents/](http://www.opera.com/download/torrents/)

Or try the [script](http://www.evonet.be/~bfran/extern/operaInstall_WIP02.sh) I wrote. It will download and install it automatically.

---

### Post by tegwilym on 2006-03-15
[QUOTE=bernardfrancois][http://www.opera.com/download/torrents/](http://www.opera.com/download/torrents/)

Or try the [script](http://www.evonet.be/~bfran/extern/operaInstall_WIP02.sh) I wrote. It will download and install it automatically.[/QUOTE]

The script seemed to run fine.  Downloaded Opera, did the install, but I still can't make the thing start.  Should this put an icon someplace?  When I try just typing in "opera" I get:

[I]ERROR: ld.s: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
opera: cannot connect to X server[/I]

Until earlier this week, I was running Fedora 4 linux, but reading about Ubuntu being so good, I installed this insteade.  Opera worked fine (and it was easy to install) in Fedora.  (Note: I was running the 64 bit version of Fedora also, and opera installed just fine - my computer is an AMD64).

I'm so frustrated with Linux all the time, but I just keep working at it since I spent 4 years working at MS and can't stand seeing that thing on the screen all the time!  All I want is my favorite browser and mouse gestures to work again.  Why does this stuff have to be such a pain all the time.  Arrrggghh!!!!!   :mad: 

Tom
- Trying very hard to avoid the dark side.

---

### Post by bernardfrancois on 2006-03-18
Thanks for the feedback!

I forgot to include the installation of an icon in the gnome menu since I already had an icon from a previous installed version... I'll add it to the script next time I modify it.
For now you can add the icon using *Gnome Menu > System Tools > Applications Menu Editor* in Breezy or with SMEG (a menu editor, search the forums for more info) on Hoary. The icon can be found in */usr/share/pixmaps/Opera.xpm*.

When I run opera in xterm, I get the following errors:
```

ERROR: ld.s: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
Qt: Locales not supported on X server

```
Opera works fine though here.

Did you try to run opera as a regular (= non-root) user? It shouldn't be run as root offcourse. If it doesnt work to run it as root, please verify if the permissions on /usr/bin/opera are set like this:
```

# ls -l /usr/bin/opera
-rwxr-xr-x  1 root root 5635 2006-03-06 15:38 /usr/bin/opera

```

If you still can't make it work, try to execute **xhost +** before executing opera. This is only a temporary solution.  But you shouldn't run opera as root, since this implies a safety risk.

---

### Post by tegwilym on 2006-03-19
[QUOTE=bernardfrancois]
```

# ls -l /usr/bin/opera
-rwxr-xr-x  1 root root 5635 2006-03-06 15:38 /usr/bin/opera

```

If you still can't make it work, try to execute **xhost +** before executing opera. This is only a temporary solution.  But you shouldn't run opera as root, since this implies a safety risk.[/QUOTE]

Hmmm...I'll give this a try on monday.  It's my computer at work, and I haven't yet installed Linux here at home.  I bet I probaby did try running it from the command line as Root.  I think I may have run the script then just gave it a try after that before exiting to the normal user mode.

I'll see what happens!
Thanks,

Tom

---

### Post by jamesrw on 2006-03-22
if i install opera using your script will it install flash? I am running firefox and I am missing flash, and i guess im too lazy to try the chroot install.

---

### Post by ubernoob on 2006-03-22
[QUOTE=jamesrw]if i install opera using your script will it install flash? I am running firefox and I am missing flash, and i guess im too lazy to try the chroot install.[/QUOTE]

If you see [post #6 in this thread]("http://ubuntuforums.org/showpost.php?p=499157&postcount=6") you will see how to install flash.

---

### Post by bernardfrancois on 2006-03-23
The script won't install flash. I would like to extend the script to install a chrooted environement automatically and install flash, replayer/gmplayer plugins et,... But since I'm very busy for school this might take a long time before I do that.

You can use the script to install opera and then use the solution of ubernoob.

Note that you should verify that you don't need the 64 bit version of lesstif2 for any other pdf applications (for example, I cant use this solution since I use xpdf and ddd, which require lesstif2).
You can verify this by checking if you have lesstif2 in synaptic. If you have, you can try to uninstall it and see if it will show a list of other programs that will be uninstalled.

---

### Post by alesdoc on 2006-03-28
Hi guys....

have someone of us problem using gmail through opera? I've problem with the contacts. When i write a new message the contact is not automic completed. I tried to solve the problem cleaning a lot of times the cache and the cronolgy ](*,)  (it's a suggest of the Gmailteam), but it doesn't work.

Someone can maybe help me?

Tkanks

---

### Post by bernardfrancois on 2006-03-29
I don't know a solution, but I also have problems with gmail. Often nothing happens when I click some button or link. One example: sometimes when I try to archive files (by clicking the Archive button after checking some checkboxex) nothing happens. 

If that happens, I just start firefox...

---

### Post by alesdoc on 2006-03-30
...it's a bit crazy...if write an address and send to it an email...then if i re-wirte it...it will be automatic completed...i don't understand.....it works properly since two days ago....:-k 

BY THE WAY....I LOVE OPERA!!!!!

---

### Post by bernardfrancois on 2006-03-30
I think you should post this on the Opera forums. Maybe they know a solution for it, or maybe they will take it into account for one of their next releases.

---

### Post by bernardfrancois on 2006-04-05
A new opera version has been released: 8.54

I updated the script, it's the 3rd work-in-progress version now.
I checked it out here, and it worked.

It can be downloaded [here](http://www.evonet.be/~bfran/extern/operaInstall_WIP03.sh).

[edit]
[b]I've started a new thread for the script. From now on, information about the opera installation script can be found [here](http://ubuntuforums.org/showthread.php?p=893182#post893182).
Please post any issues about the script in that thread.[/b]
[/edit].

---

### Post by EvanPMeth on 2006-10-24
After following this How-To, opera worked perfectly (unlike firefox/swiftfox). I had so many problems installing firefox w/ flash and java (above blackdown) that i was about to re-format my hardrive and go to 32-bit. Luckily i found this thread. Thnks  a million ubernoob. 

Regarding java opening in new window:
I used jre1.5.0_06 not jre1.5.0_05 and i had no problem with it opening in a new window. 
Also when going to Tools->Prefrences->Advanced->Content the java path was already there, no need to paste it unless you already had java installed then the path would be different.

I still get errors in  the terminal but it does not seem to affect anything.

another thing when using past and go in the url bar it doesnt work it just pastes the current web page. This may just be a bug.

I might post another how-to that cleans everything up and brings everything into one how-to because this worked perfect for me.

Thanks so much,
-Evan

---

### Post by jsrivo on 2006-10-29
when i try to run opera, i keep on getting the error message:

exec: 263: /usr/lib/opera/9.02-20060919.1/opera: not found

can anyone please help me with this?
thanks!

---

### Post by plcdfa on 2006-11-15
I don't know if you still have the problem, I just found this thread yesterday. (And managed to get opera running with flash and java on 64 bit, thank you all!)
As for you problem: I had it too, but installing the ia32-libs package resolved it.

---

### Post by HeSh on 2006-11-27
How about writing a tutorial? ;)

I have a similar problem. Installed 32bit version and when i run it i get this message:
```
exec: 263: /usr/lib/opera/9.02-20060919.6/opera: Accessing a corrupted shared library
```

---

### Post by Zilog Jones on 2006-11-27
I tried using Simple64 to install Opera (in Kubuntu Edgy AMD64), but it won't load and gives these errors:

```
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.02-20060919.6/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
```

OK, I know I haven't set up Java yet - do I need to install the 32-bit version of the Java RE for the plugins to work in Opera?

However, it should still start if it wasn't for the last error. I have libqt3-mt, libqt4-core, libqt4-gui, libqt4-qt3support and libqt4-sql installed - is there anything else I should have?

Any ideas? I tried posting on the simple64 thread too but got no response :(

---

### Post by RAOF on 2006-11-27
> **Zilog Jones said:**
> ...
However, it should still start if it wasn't for the last error. I have libqt3-mt, libqt4-core, libqt4-gui, libqt4-qt3support and libqt4-sql installed - is there anything else I should have?
...

Yes: **ia32-libs-kde**, which contains the **32-bit** qt libraries.

---

### Post by Zilog Jones on 2006-11-28
Oh thank you - I was not aware of those libraries! How come apt-get was not informing of me missing packages i needed for programs to run?

Anyway, I also had [this](http://ubuntuforums.org/showpost.php?p=1789367&postcount=3) problem, and had to manually make a symlink for libXcursor.so.1 in the opera directory as well. After those two things it worked!

Now to get Flash working :D

---

### Post by RAOF on 2006-11-28
> **Zilog Jones said:**
> Oh thank you - I was not aware of those libraries! How come apt-get was not informing of me missing packages i needed for programs to run?
...

Because you're installing things outside of the package manager's ken.  It just doesn't know what packages you need, because the package doesn't tell it.

---

### Post by lliseil on 2007-01-06
About libjvm.so and libawt.so: those seem to be java SDK related.
So if (like me) you do not have SDK packages installed, you can ignore those errors or edit opera binary as following :
```
# Uncomment the next lines to workaround the "libjvm.so & libawt.so preloaded" error message
#LD_PRELOAD="libjvm.so:libawt.so:${OPERA_LD_PRELOAD}"
#export LD_PRELOAD
```
/me chose 2nd solution on Archlinux64 (with lib32 installed) & have goptten rid of those 2 errors

---

### Post by williams112 on 2007-06-01
[COLOR="black"][COLOR="black"]BELOVED
It is by the grace of God that I received Christ, knowing the truth and the truth have set me free. Having known the truth, I had no choice than to do what is lawful and right in the sight of God for eternal life and in the sight of man for witness of God´s mercy and glory upon my life. I have the pleasure to share my testimony with you, having seen your contact from the Internet.As directed by the holy spirit.
I am Barrister TAD WILLIAMS, the legal adviser to late mr and Mrs.crounch British couple[MISSIONARY] that lived in my Country Africa for 25 years before they both died in a plane crash late last year. These couples were good Christians, they where so dedicated to God but they had no child till they died. Throughout their stay in my country, they acquired a lot of properties like lands, house properties, etc. As their legal adviser, before their death, the husband Mr. crounch instructed me to write his WILL.
 
Because they had no child, they dedicated their wealth to God. According to the WILL, the properties have to be sold and the money be given out to a ministry for the work of God. As their legal adviser, all the documents for the properties were in my care. He gave me the uthority to sell the properties and give out the fund to the Ministries for the work of God.
 In short, I sold all the properties fter their death, as instructed by Mr.crounch before his death. And as a matter of fact, after I sold all their properties, I realized more than $8.5,000,000.00 (EIGHT million five hundred thousand US dollars plus), and what supposed to be the percentage interest of my right legal fee was firstly deducted by me out of the total amount realized from the sold properties, this was base on the initial agreement between me and the owner of the properties before his death. Therefore the total amount left to be invested into God's work as instructed by the owner, is US$8.5 MILLION only.
 But Instead of giving the main fund out for the work of God as instructed to me by the owner before his death. I converted the fund to myself with the intention of investing the fund abroad for my personal use. I had encounter with Christ when Pastor Benny Hinn was preaching on elevision concerning Ananias and Saphira in Acts 5:1-11. After hearing the word of God, I gave my life to Christ and became a born again Christian. As a born again Christian, I have asked God for forgiveness and I know that God have forgiven me. But I have to do what is lawful and right in the sight of God by giving out the fund to the chosen ministry/individual for the purpose of God's work as instructed by the owner before his death.
I then came across your address on the Internet as I was browsing through a Christian site, and as a matter of fact, it is not only you or your ministry that I picked on the Christian site initially, but after my fervent prayer over it, you were nominated to me through divine revelation from God, so these are how I received such a divine revelation from the Lord, how I got your contact information, and I then decided to contact you for the fund to be used wisely for things that will glorify the name of God. I have notified the bank where I deposited the fund that I am moving the fund abroad and the finance company has since been waiting for my authority for the fund to leave my country to abroad. if you know that you will use this fund honestly and wisely for things that will glorify God's name, You should also forward to me your telephone and fax number for easy communication. Your prompt response will be highly appreciated. Note reply to my private
e-mail address:info_desk112@hotmail.com
 :please indicate your ministry you would want to invest the fund.
Yours in Christ.
TAD WILLIAMS[/COLOR][/COLOR]

---

### Post by iBART on 2007-07-05
installed

it doesnt work

i need to uninstall it, but i cant ... i can't see any opera package on synaptic. help?

---

### Post by jpkotta on 2007-07-05
[https://help.ubuntu.com/community/OperaBrowser#head-8b233e94ad0c1adc2f768dd1dd7c403b6f8ddd75](https://help.ubuntu.com/community/OperaBrowser#head-8b233e94ad0c1adc2f768dd1dd7c403b6f8ddd75)

---

