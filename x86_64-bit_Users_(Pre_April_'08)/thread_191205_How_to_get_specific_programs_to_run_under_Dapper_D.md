---
title: "How to get specific programs to run under Dapper Drake 64-bit edition"
date: 2006-06-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hendrik van den Boogaard on 2006-06-07
[SIZE="5"][COLOR="Red"]How to get specific programs to run under Dapper Drake 64-bit edition.[/COLOR][/SIZE]

[SIZE="4"]**Why this thread?**[/SIZE]
Upgrading to a 64-bit Operating System is not an easy process. Things that were 'normal' or 'common' in the 32-bit world are different when using a 64-bit processor and their equivalent 64-bit applications. You might run into some troubles, as we all did :). This thread is here to help you overcome most common problems when switching to Ubuntu 64-bit.

[B][SIZE="3"][COLOR="Navy"]Feel free to add programs, solutions or workarounds.
Since the thread is sticky I will do my best to think of solutions and include all solutions suggested by 64bit pioneers like you![/COLOR][/SIZE][/B]

[SIZE="4"]**Things you might try first**[/SIZE]
When switching to a 64-bit operating system, there are still programs that are not natively compiled for the AMD64 architecture. The first thing you can try, if there is a i386 version available, is to force the program to install using the i386 architecture. For other architectures this does not work (when you for instance try to force to install a SPARC compiled application) but luckily the AMD64 architecture is backwards compatible with i386, so these 32bit applications should run fine. The downside of this is that some calls to libraries might not work and need their 32-bit version as well. If you omit the 'force architecture' option dpkg will tell you:

[I]dpkg: error processing packagename_i386.deb (--install):
 package architecture (i386) does not match system (amd64)[/I]

You can do a forced i386 installation like this:
```

sudo dpkg -i --force-architecture *packagename_i386.deb*

```

Another thing you might try if you already installed an application which does not run, is 'linux32'. This program does not really do anything, except for the fact that if you use it as a wrapper for a program, this program will think the machine type is a i686.

An example of this:
```

hendrik@hendrik:~$ *uname -a*
Linux hendrik 2.6.15-25-amd64-k8 #1 SMP PREEMPT Wed Jun 14 11:39:18 UTC 2006 **x86_64** GNU/Linux
hendrik@hendrik:~$ *linux32 uname -a*
Linux hendrik 2.6.15-25-amd64-k8 #1 SMP PREEMPT Wed Jun 14 11:39:18 UTC 2006 **i686** GNU/Linux


```

[SIZE="4"]**'Native' compiled 64-bit programs that do not seem to work from standard repositories**[/SIZE]
[LIST]
[*][SIZE="4"]*PartImage*[/SIZE] - Partimage thinks a DWORD must be 32bit long, so it fails to start and tells me: '*Error: sizeof(DWORD) != 4 (8)*'. If you try the i386 version it will give an error about libslang.so.2.
[INDENT]**Solution:** Install the standard Ubuntu package and then replace the binary with the statically built version from the PartImage website (so installing the package is only for getting all documentation and other stuff, it's not necessary to get partimage running, therefore you may skip the 'apt-get' line):

```

sudo apt-get install partimage
cd /tmp
wget http://switch.dl.sourceforge.net/sourceforge/partimage/partimage-0.6.4-static.tar.bz2
tar xjf partimage-0.6.4-static.tar.bz2
sudo mv partimage /usr/sbin/

```[/INDENT]
[*][SIZE="4"]*dvd::rip*[/SIZE] - Altough all depenencies are found and installed, dvd::rip keeps on complaining that *all* dependencies are missing. It cannot find transcode and imagemagick, although both were installed automatically with 'apt-get install dvdrip'.
[INDENT]**Solution:** I made the changes to the sourcecode as harro0209 pointed me to in his post in this thread. Made a new ubuntu package with a changed version number so the 'old' Ubuntu version won't overwrite it.
```

sudo apt-get install dvdrip
cd /tmp
wget http://bombazyn.mine.nu/Ubuntu/dvdrip_0.52.5-0.1_amd64.deb
sudo dpkg -i dvdrip_0.52.5-0.1_amd64.deb
rm ~/.dvdriprc &> /dev/null
rm ~/.dvdrip/tc_filter_list &> /dev/null

```[/INDENT]
[/LIST]

[SIZE="4"]**Programs that are not available under Dapper Drakte 64-bit**[/SIZE]
[LIST]
[*][SIZE="4"]*Firefox with plugins like Flash/Java/Realplayer*[/SIZE] - Many 64bit plugins are not available. *Kilz* set up a nice [Howto]("http://www.ubuntuforums.org/showthread.php?t=202537") about running Firefox 32bit in Dapper64 with 32bit plugins.
[INDENT][SIZE="3"]**You might wanna give this a try instead of the stuff listed below (gnash, nspluginwrapper etc)**[/SIZE][/INDENT]
[*][SIZE="4"]*Adobe Acrobat Reader 7*[/SIZE] - There does not seem to be a 64 bit edition of Acrobat Reader at all. Trying to apt-get the package will tell you '*E: Package acroread has no installation candidate*'. [INDENT]**Solution:** get the i386 package and do a forced-architecture installation:
```

sudo apt-get install libstdc++5
cd /tmp
wget ftp://ftp.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread_7.0.1-0.0.ubuntu1_i386.deb
sudo dpkg -i --force-architecture acroread_7.0.1-0.0.ubuntu1_i386.deb

```
or use the 'Debianized' version in the Marillat repository, which has a newer version (AcrobatReader 7.0.5) : [ftp://ftp.nerim.net/debian-marillat/pool/main/a/acroread/](ftp://ftp.nerim.net/debian-marillat/pool/main/a/acroread/)
[/INDENT]
[*][SIZE="4"]*Realplayer*[/SIZE] - Only RealPlayer 8 is in the standard Dapper 32 repositories. Installing RealPlayer 10 from the Real website however seems to run fine in Dapper 64. I have not really tested this (if a movie needs RealPlayer, it's probably not worth checking it out ;)). You can download the binary installer from: [http://www.real.com/linux](http://www.real.com/linux)
[*][SIZE="4"]*Java 5.0*[/SIZE] - I haven't tried this myself, there seem to be repositories available and you can download Java 5 from Sun's website, but the mozilla plugin is not available (yet?). You can however stick with 'j2re1.4 - Blackdown Java(TM) 2 Runtime Environment, Standard Edition'. That works fine. 
[*][SIZE="4"]*Flashplayer*[/SIZE] - There is no 64bit version of the flash player available. You can use a 32bit firefox from 'getfirefox.com' and there is a howto available in the Ubuntu Wiki (anyone has a good direct link or howto at hand?).
[INDENT]**Workaround 1:** Try to use the *nspluginwrapper* which makes it possible to use the Macromedia 32bit flash version in 64bit Dapper. 
Follow the [howto]("http://ubuntuforums.org/showthread.php?t=193893&page=3") or see [this thread]("http://ubuntuforums.org/showthread.php?t=160318") for more information.
[/INDENT]

[INDENT]**Workaround 2:** You can use 'gnash' from the RAOF repositories (add these lines to you /etc/apt/sources.list):
```

deb http://ubuntu.moshen.de/ dapper all
deb http://raof.dyndns.org/falcon/ dapper eyecandy flash multimedia mythtv all

```
then do a
```

sudo apt-get install gnash gnash-plugin

```
Note: Gnash cannot handle all Flash movies properly yet and the plugin seems to be enabled in firefox only. If you use the mozilla-suite (like I do) it won't work (has to do with the 'plugins.ini' file, haven't figured out how to solve it yet)
[/INDENT]
[*][SIZE="4"]*Mplayer W32codecs*[/SIZE] - Mplayer works fine, but to use the W32codecs which include WMV9 support, you need to use a 32bit Mplayer with 32bit libraries. A guide how to do this is found in this thread: '[http://www.ubuntuforums.org/showthread.php?t=188974]("http://www.ubuntuforums.org/showthread.php?t=188974")'
[*][SIZE="4"]*Rar*[/SIZE] - There is no AMD64 package available in the standard repositories
[INDENT]**Solution:** Either try my first 'experimental' package (All I did was add 'amd64' to the 'architecture' types in the DEBIAN/control file)
```

sudo apt-get install libstdc++5
cd /tmp
wget http://bombazyn.mine.nu/Ubuntu/rar_3.30-2ubuntu2_amd64.deb
sudo dpkg -i rar_3.30-2ubuntu2_amd64.deb

```
Or use the i386 version:
```

sudo apt-get install libstdc++5
cd /tmp
wget ftp://ftp.ubuntu.com/ubuntu/pool/multiverse/r/rar/rar_3.30-2ubuntu2_i386.deb
sudo dpkg -i --force-architecture rar_3.30-2ubuntu2_i386.deb

```[/INDENT]
[*][SIZE="4"]*Opera*[/SIZE] - Opera is not available in Dapper64. Here's a thread that might help, it mainly says that you need a statically copiled 32bit version of opera: [http://ubuntuforums.org/showthread.php?t=75940](http://ubuntuforums.org/showthread.php?t=75940)
[*][SIZE="4"]*Wine*[/SIZE] - Wine can give you some troubles. Here's a HowTo that might help: [http://www.ubuntuforums.org/showthread.php?t=185557](http://www.ubuntuforums.org/showthread.php?t=185557)
[*][SIZE="4"]*Listen*[/SIZE] - You can use the AMD64 package from the 'Janvitus' repository. More info: [http://ubuntuforums.org/showthread.php?t=196093](http://ubuntuforums.org/showthread.php?t=196093).
[*][SIZE="4"]*Bonfire*[/SIZE] - This package is also in the 'Janvitus' repository.
[*][SIZE="4"]*Matlab 7.0*[/SIZE] - Matlab does not understand the AMD64 architecture. It might tell you: '*matlab: No MATLAB bin directory for this machine architecture. ARCH = glnxa64*'
[INDENT]**Solution:**Use the linux32 wrapper to start Matlab. In my case this looks like this
```

linux32 /usr/local/Matlab7/bin/matlab

```[/INDENT]
[*][SIZE="4"]*Wengophone*[/SIZE] - Users have reported problems with this VOIP application, see [http://ubuntuforums.org/showthread.php?p=1137372](http://ubuntuforums.org/showthread.php?p=1137372) for more info
[*][SIZE="4"]*Skype 1.3*[/SIZE] - You can get the Debian package for skype 1.3 (which can use ALSA) from [this]("http://skype.com/go/getskype-linux-deb") website. When you try to run skype, it may complain about *libasound.so.2* and/or *libqt-mt.so.3*. The trick is to download these libraries and put them in the /usr/lib32 dir. Or just copy the codelines below :). The archive on my site is just a tar.bz2 which includes the actual i386 library files that you need to run Skype. I initially had a problem with my microphone input, but someone else already posted a [strange but working solution]("http://ubuntuforums.org/showthread.php?t=214273").
[INDENT]
```

cd /tmp
wget http://skype.com/go/getskype-linux-deb
sudo dpkg -i --force-architecture skype_debian-1.3.0.53-1_i386.deb
wget http://bombazyn.mine.nu/Ubuntu/asound32-qtmt32.tar.bz2
cd /usr/lib32
sudo tar xjvf /tmp/asound32-qtmt32.tar.bz2

```[/INDENT]
[*][SIZE="4"]*Wine*[/SIZE] - I had this info here before, but somehow it got lost. The link to the Wine HowTo is: [http://www.ubuntuforums.org/showthread.php?t=185557](http://www.ubuntuforums.org/showthread.php?t=185557)
[/LIST]

[SIZE="4"]**Things that do not seem to work when you upgrade from Dapper 32bit to Dapper 64bit**[/SIZE]
[LIST]
[*]Upgrading to [SIZE="4"]*Thunderbird*[/SIZE] in my case made my thunderbird crash upon start. Just setting it up again (with my IMAP mailboxes) works fine.
[*]When using [SIZE="4"]*Mozilla calendar plugin*[/SIZE] (by pressing ctrl-8 in mozilla-suite) it crashes mozilla completely. Removing calendar settings makes the calendar-plugin start again, but after added a caldav calendar it crashes again.
[*]When installing [SIZE="4"]*Revelation,*[/SIZE] it does not seem to work directly. Please re-start X and that seems to solve the problem.
[/LIST]

---
[SIZE="1"](cr)edits:
12 june 2006 - Included info how to get Adobe acrobat running, thanks Conq
12 june 2006 - Thread is sticky now :), will try to maintain the thread with all latest info
12 june 2006 - Added 'Kilz' howto for Wine
12 june 2006 - Found a way to get partimage running
12 june 2006 - JoWilly gave some more helpful insights, added to this topic
13 june 2006 - Added RAR and made AMD64 package for RAR
14 june 2006 - Changed Calendar plugin and Listen information
14 june 2006 - Made new AMD64 package with fix and install instructions, thanks harro0209 for the info
18 june 2006 - Added link to Wine32 Howto, thanks Kilz
21 june 2006 - Added nswrapper info, thanks JoWilly
26 june 2006 - Added Kilz 'Firefox32' howto
05 july 2006 - Traced down the *aMule* and *Listen* problems. I needed nfs-common to support proper file-locking over NFS!
06 july 2006 - Refreshed topic
04 aug 2006 - Added Skype, changed Firefox link (again :S), added Wine (also: again :S)
15 oct 2006 - Long time no see... Changed info about Skype 1.3 beta to Skype 1.3 Final[/SIZE]

---

### Post by FluffyElmo on 2006-06-07
Java 5.0 is available by downloading the JVM from Sun ([http://java.sun.com]("http://java.sun.com")) or alternately JRockit from BEA ([http://bea.com]("http://www.bea.com/framework.jsp?CNT=index.htm&FP=/content/products/jrockit/")). Both work perfectly on my system, but you're right, neither include a Mozilla or Webstart plug-in. For desktop apps (Azureus, Eclipse) and Java development use they are both fast and stable.

Raof and Doc.Horn have kindly provided amd64 repositories for XGL/Compiz and other hard to find multimedia packages. I've had XGL running smoothly thanks to them :) The thread where I was introduced to them is here: [http://ubuntuforums.org/showthread.php?t=187887]("http://ubuntuforums.org/showthread.php?t=187887") while the repository adresses are:
```
deb http://ubuntu.moshen.de/ dapper all
deb http://raof.dyndns.org/falcon/ dapper eyecandy flash multimedia mythtv all
```

---

### Post by kufford on 2006-06-07
what's the status of multimedia codecs that are available for 64bit? anything missing? 

what about nvidia drivers?

sorry for message, on pda... ty

---

### Post by angkor on 2006-06-07
I'd like to add mplayer to the list. 

I do have a 32bit mplayer now thanks to [this guide]("http://www.ubuntuforums.org/showthread.php?t=62685")

---

### Post by FluffyElmo on 2006-06-07
Nvidia drivers aren't a problem, they are in the repository and more recent versions are downloadable from Nvidia. You do have to install them though, the open-source nv drivers are installed by default.

Multimedia codecs are available with the exception of wmv9. It's possible to get them to play but it's rather involved.

What I meant in my previous post was multimedia applications like transcode, ffmpeg and avidemux. There are 64bit versions available, but historically they've been hard to get working. Things have improved with Dapper though and right now since Dapper is current, 3rd party packages will work as well.

---

### Post by henriquemaia on 2006-06-08
[quote=Hendrik van den Boogaard][...][LIST]
[*]*Mplayer W32codecs* - Mplayer works fine, but to use the W32codecs which include WMV9 support, you need to use a 32bit Mplayer with 32bit libraries. A guide how to do this is found in this thread: '[http://www.ubuntuforums.org/showthread.php?t=62685]("http://www.ubuntuforums.org/showthread.php?t=62685")'[/LIST][...][/quote]

Hi, nice list. I just want to point out that there is a newer and better thread for the *Mplayer W32codecs*. Here:

[http://www.ubuntuforums.org/showthread.php?t=188974](http://www.ubuntuforums.org/showthread.php?t=188974)

Thanks anyway.

---

### Post by Hendrik van den Boogaard on 2006-06-08
Thanks, I changed the URL to point to that topic.

---

### Post by tzenes on 2006-06-08
wine obviously doesn't work, however somebody posted this work around: [http://www.ubuntuforums.org/showthread.php?t=184050](http://www.ubuntuforums.org/showthread.php?t=184050)

however, I haven't been able to make it work under dapper.

---

### Post by fragos on 2006-06-08
If you download the AdobeReader_enu-7.0.5-1.i386.tar.gz you will be able to install acroread by using the INSTALL shell script in the tarball.  Works fine on my Ubuntu 6.0.6 LTS AMD64.  dpkg and the other Debian package managers won't install 32 bit code on a 64 bit machine.  The IA32 libraries are required but they should have been installed with Dapper.

---

### Post by RAOF on 2006-06-09
Actually, if anyone wants a program packaged for AMD64, I'd be happy to extend my repository to include it.  When I have time ;)

---

### Post by Naonak on 2006-06-09
[QUOTE=RAOF]Actually, if anyone wants a program packaged for AMD64, I'd be happy to extend my repository to include it.  When I have time ;)[/QUOTE]

What about Listen Gnome Player? It would be great to have that one \\:D/

Thanks in advance!

---

### Post by Conq on 2006-06-10
If you want acrobat reader, you can allways install the 32-bit version and use that. 

This is what you do:
```

wget http://mirror.freax.be/ubuntu/archive.ubuntu.com/pool/multiverse/a/acroread/acroread_7.0.1-0.0.ubuntu1_i386.deb

sudo dpkg -i --force-architecture acroread_7.0.1-0.0.ubuntu1_i386.deb

```

---

### Post by Hendrik van den Boogaard on 2006-06-12
Thanks Conq, the version from the 32bit repositories seem to work fine. I included them on the first page. However the ftp you referred to gives me a '403' so I changed it to the main Ubuntu.com site. I also needed some old libraries.

---

### Post by henriquemaia on 2006-06-12
Can this thread be made sticky on this forum? I think this is trully helpful for the 64bit newcomers.


Ps: I have added a thread with this request on the Forum Site Discussion. Link [here]("http://ubuntuforums.org/showthread.php?t=195007").

---

### Post by Kilz on 2006-06-12
I have a howto to install wine if you want to add it to the sticky. 
[http://www.ubuntuforums.org/showthread.php?t=185557](http://www.ubuntuforums.org/showthread.php?t=185557)

---

### Post by JoWilly on 2006-06-12
[B]
Amule[/B] from the repos works perfectly here without doing anything special (I just tried again to make this sure).

**Adobe reader newer version 7.0.5** deb is availlable in the marillat repos, direct link here : [ftp://ftp.nerim.net/debian-marillat/pool/main/a/acroread]("ftp://ftp.nerim.net/debian-marillat/pool/main/a/acroread")

**Sun java 5** has always been in the dapper multiverse repo. You plugin fix with  blackdown 1.4 is good though.

**Swiftfox** is not a 64bit app and does not install 64bit flash, its all 32bit (even the amd64 version is 32bit), this is why it works. So it's essentially the same as getting firefox32 from getfirefox.com . You could add a link to the ubuntu firefox32 + plugins on dapper64 wiki.

** Gnash** is in the raof repo (as well as latest xgl/compiz, rhythmbox, etc...); unfortunately it does not play all the flash movies yet :mirror  [http://ubuntu.moshen.de/]("http://ubuntu.moshen.de/")

---

### Post by Hendrik van den Boogaard on 2006-06-12
I added your link to the Marillat repositories. The installation will probably be just like the 7.0.1 version and need the same libraries (?). aMule I still cannot get to work. It tells me again that there is an instance running and it tries to raise that running instance, but nothing comes up:
```

hendrik@hendrik:~$ amule
Initialising aMule
Checking if there is an instance already running...
There is an instance of aMule already running
Raising current running instance.

```

I will look into Swiftfox and the gnash/flash thingy later. Thanks for your reply!

---

### Post by JoWilly on 2006-06-12
[quote=Hendrik van den Boogaard]I added your link to the Marillat repositories. The installation will probably be just like the 7.0.1 version and need the same libraries (?). aMule I still cannot get to work. It tells me again that there is an instance running and it tries to raise that running instance, but nothing comes up:
```

hendrik@hendrik:~$ amule
Initialising aMule
Checking if there is an instance already running...
There is an instance of aMule already running
Raising current running instance.

``` 
I will look into Swiftfox and the gnash/flash thingy later. Thanks for your reply![/quote]

Yep, acroread 7.0.5 installs in the same way.

Regarding your amule problem, this is strange. Could it be a tmp lock file wich was not removed previously ? I dont'see anything else than some old remains on your filesystem as it is working properly here.

---

### Post by Hendrik van den Boogaard on 2006-06-13
I have no idea what causes the problem with aMule in my case. Perhaps it has to do with the fact that my homedir is mounted over NFS. If I unmount the nfs share amule will start correctly. If I mount it again and delete the .aMule dir, it won't start anymore. However, if I make a symlink ~/.aMule which points to /tmp/aMule (an empty dir created by me) it works fine again.

It would be strange though if aMule had problems with NFS, because on Dapper32 this all seemed to work fine.

---

### Post by realruntime on 2006-06-13
Well, Firefox behaves absolutely weird on Dapper-64bit. Sometime it hangs up completely. Then it trys to download PHP-Files - after hitting reload the php works.

Then it sends bad requests to the server (several servers giving me a "bad request" error). After hitting reload it works again.

This is a little bit disappointing. How can a good piece of software (have Firefox on Ubuntu Dapper 32-bit on an other computer - works excellent) become so awful by being compiled with a 64bit compiler?

Mozilla/5.0 (X11; U; Linux x86_64; de; rv:1.8.0.4) Gecko/20060608 Ubuntu/dapper-security Firefox/1.5.0.4

---

### Post by harro0209 on 2006-06-14
Had the same problem of dvdrip not finding its dependencies (imagemagick and others).
I could solve this by disabling the NPTL workarounds in the preferences.
See
[http://www.exit1.org/archive/dvdrip-users/2006-01/msg00018.html]("http://www.exit1.org/archive/dvdrip-users/2006-01/msg00018.html")

---

### Post by CyberAngel on 2006-06-14
[QUOTE=harro0209]Had the same problem of dvdrip not finding its dependencies (imagemagick and others).
I could solve this by disabling the NPTL workarounds in the preferences.
See
[http://www.exit1.org/archive/dvdrip-users/2006-01/msg00018.html]("http://www.exit1.org/archive/dvdrip-users/2006-01/msg00018.html")[/QUOTE]


From the main page of [official dvd::rip site]("http://www.exit1.org/dvdrip/index.cipp")

2005/05/17

        * Tip of the day: if you encounter problems with dvd::rip 0.52.5 on your system (e.g. Gentoo, or AMD64 architecture) while 0.52.3 works try disabling the Workaround transcode NPTL bugs switch in dvd::rip's Preferences and restart dvd::rip.

---

### Post by Princey on 2006-06-14
Getting problems with acroread 7.05 from the nerim repos listed above.
> emmjay@SpeezyGonz:~$ cd /tmp
emmjay@SpeezyGonz:/tmp$ wget [ftp://ftp.nerim.net/debian-marillat/pool/main/a/acroread/acroread_7.0.5-0.1_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/a/acroread/acroread_7.0.5-0.1_i386.deb)
--09:03:42--  
09:50:02 (0.00 B/s) - `acroread_7.0.5-0.1_i386.deb' saved [19921952]

emmjay@SpeezyGonz:/tmp$ sudo dpkg -i --force-architecture acroread_7.0.5-0.1_i386.deb
Password:
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package acroread.
(Reading database ... 67472 files and directories currently installed.)
Unpacking acroread (from acroread_7.0.5-0.1_i386.deb) ...
dpkg: dependency problems prevent configuration of acroread:
 acroread depends on libatk1.0-0 (>= 1.7.2); however:
  Package libatk1.0-0 is not installed.
 acroread depends on libgtk2.0-0 (>= 2.6.0); however:
  Package libgtk2.0-0 is not installed.
 acroread depends on libpango1.0-0 (>= 1.8.1); however:
  Package libpango1.0-0 is not installed.
dpkg: error processing acroread (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acroread
emmjay@SpeezyGonz:/tmp$ sudo apt-get install libgtk
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libgtk
emmjay@SpeezyGonz:/tmp$ sudo apt-get install libgtk2
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libgtk2


any ideas as what I can do to resolve the dependencies issues? I did install libstdc++5 as stated.

---

### Post by JoWilly on 2006-06-14
[quote=Princey]Getting problems with acroread 7.05 from the nerim repos listed above.


any ideas as what I can do to resolve the dependencies issues? I did install libstdc++5 as stated.[/quote]

You did not download the latest version of the deb:
[URL="ftp://ftp.nerim.net/debian-marillat/pool/main/a/acroread/acroread_7.0.5-0.3_i386.deb"]
ftp://ftp.nerim.net/debian-marillat/pool/main/a/acroread/acroread_7.0.5-0.3_i386.deb[/URL]

Try installing this one and make sure the listed dependencies are instaled (with synaptic).

---

### Post by CyberAngel on 2006-06-14
As I have realized (at least for me and two other amd64 users) wengophone amd64 package from the repositories is broken..

Test it yourself too and add it to your first post :)

Take a look on [that]("http://ubuntuforums.org/showthread.php?p=1137372") thread for more info.

It`s easy to make wengophone 2 beta 32bit work though.

---

### Post by juah on 2006-06-14
Excellent tips so far, still missing RealPlayer or Helix Player to play Real Audio files and I'd like to get rid of chroot.

---

### Post by CyberAngel on 2006-06-14
[QUOTE=juah]Excellent tips so far, still missing RealPlayer or Helix Player to play Real Audio files and I'd like to get rid of chroot.[/QUOTE]

For me just downloaded, installed and plays without chroot!!
RealPlayer 10.0.7.785 Gold

Do you get any errors when you are trying to install it??

---

### Post by Princey on 2006-06-14
[QUOTE=JoWilly]You did not download the latest version of the deb:
[URL="ftp://ftp.nerim.net/debian-marillat/pool/main/a/acroread/acroread_7.0.5-0.3_i386.deb"]
ftp://ftp.nerim.net/debian-marillat/pool/main/a/acroread/acroread_7.0.5-0.3_i386.deb[/URL]

Try installing this one and make sure the listed dependencies are instaled (with synaptic).[/QUOTE]

Thanks, I installed the missing libraries via adept (I'm using kde) then redownloaded the one you linked to. Installed without any errors. Thanks much. Now on to getting sun java installed so I can fire Opera up.

---

### Post by Princey on 2006-06-14
[QUOTE=CyberAngel]For me just downloaded, installed and plays without chroot!!
RealPlayer 10.0.7.785 Gold

Do you get any errors when you are trying to install it??[/QUOTE]

Does that mean I don't have to use --force-architecture to install real player? I've downloaded it but yet to install it.

---

### Post by JoWilly on 2006-06-14
[quote=juah]Excellent tips so far, still missing RealPlayer or Helix Player to play Real Audio files and I'd like to get rid of chroot.[/quote] 
The Realplayer deb package is also in the marrillat repos (install with "dpkg -i --force-acchitecture").

[ftp://ftp.nerim.net/debian-marillat/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb]("ftp://ftp.nerim.net/debian-marillat/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb")

Warning: the web plugins crashes firefox64 when trying to access a realmedia link (works fine with firefox32). If you are using firefox64 (and don't want to use firefox32) delete the plugin and open your links directly with realplayer (should be located in /usr/lib/firefox/plugins or /usr/lib/mozilla/plugins).

---

### Post by CyberAngel on 2006-06-15
[QUOTE=Princey]Does that mean I don't have to use --force-architecture to install real player? I've downloaded it but yet to install it.[/QUOTE]

I have not installed it from a deb file..
I just downloaded the file from [here]("http://www.real.com/linux/"),
made the downloaded file executable ```
chmod 755 RealPlayer10GOLD.bin
``` and then ran ```
sudo ./RealPlayer10GOLD.bin
```

It has it`s own installer.

---

### Post by juah on 2006-06-15
[QUOTE=CyberAngel]For me just downloaded, installed and plays without chroot!!
RealPlayer 10.0.7.785 Gold

Do you get any errors when you are trying to install it??[/QUOTE]
Stupid of me I admit, but I feel little uncertain and could use some help here: where to download from and how to build or install? I found this [http://linux.softpedia.com/progDownload/RealPlayer-Download-2742.html](http://linux.softpedia.com/progDownload/RealPlayer-Download-2742.html)
but no instructions of any kind. Is this .bin file executable and does it do the trick for me? (Sorry I cannot just try this out being at the office and only dreaming of my Linux toaster while temporarily forced to use MS once again)

---

### Post by juah on 2006-06-15
:confused:

---

### Post by juah on 2006-06-15
Ok. I can see the instructions above ok, so my questions were REALLY stupid. Sorry. I don't even know how to delete those previous posts.

---

### Post by CyberAngel on 2006-06-15
[QUOTE=juah]Ok. I can see the instructions above ok, so my questions were REALLY stupid. Sorry. I don't even know how to delete those previous posts.[/QUOTE]

Good luck :)
If you have any other problem let me informed to see if I can help you :)

:arrow: As for editing or deleting your own posts click on the scissors

---

### Post by JoWilly on 2006-06-15
@juah

.. and don't forget that the best way to install software, if you have the choice, is to get the deb file (link a few posts above). This way you can keep tracking of your installation (with synaptic) and uninstall/update easily.

---

### Post by juah on 2006-06-15
[QUOTE=CyberAngel]Good luck :)
If you have any other problem let me informed to see if I can help you :)

:arrow: As for editing or deleting your own posts click on the scissors[/QUOTE]


Thanks. It Real(Player)ly works! Wasn't hard at all. :smile: 

As for deletion my own messages: I can see the scrissors and they  let me only edit Cannot comprehend how to delete.:oops: Hopeless one.

---

### Post by CyberAngel on 2006-06-15
[QUOTE=juah]Thanks. It Real(Player)ly works! Wasn't hard at all. :smile: 

As for deletion my own messages: I can see the scrissors and they  let me only edit Cannot comprehend how to delete.:oops: Hopeless one.[/QUOTE]

Nice to hear that it works :)

As for the scissors I have used them myself just for editing. Not for deleting something but when you go with the mouse over it, it say edit/delete :P :P

So I don`t really know how to delete a post :)

---

### Post by Princey on 2006-06-16
[QUOTE=CyberAngel]I have not installed it from a deb file..
I just downloaded the file from [here]("http://www.real.com/linux/"),
made the downloaded file executable ```
chmod 755 RealPlayer10GOLD.bin
``` and then ran ```
sudo ./RealPlayer10GOLD.bin
```

It has it`s own installer.[/QUOTE]

Ok, followed your lead but ran into error messages. Strange thing is whatever it said I've missing is already installed. I had to install them for Acroread to install properly. Here's the output: > emmjay@SpeezyGonz:~$ chmod 755 RealPlayer10GOLD.bin
emmjay@SpeezyGonz:~$ sudo ./RealPlayer10GOLD.bin
Password:
Some required libraries seem to be missing from your system.  Installation
can continue without them, but you will be unable to run the HelixPlayer
without them.  You will need to install them (or if they are already present
you may simply need to update your system's library paths or LD_LIBRARY_PATH
environment variable.
        GTK+ 2.0 (libgtk-x11-2.0.so)
        ATK 1.0 (libatk-1.0.so)
        Pango 1.0 (libpango-1.0.so)
        PangoX 1.0 (libpangox-1.0.so)
continue with installation? [y/n]

I chose NO until I can get some clear directives. I read elsewhere that there's a deb package in the marilat repos. Not sure if that will suit me better.

---

### Post by CyberAngel on 2006-06-16
[QUOTE=Princey]Ok, followed your lead but ran into error messages. Strange thing is whatever it said I've missing is already installed. I had to install them for Acroread to install properly. Here's the output: 

I chose NO until I can get some clear directives. I read elsewhere that there's a deb package in the marilat repos. Not sure if that will suit me better.[/QUOTE]

Have you installed all the ia32 libraries??

Do an "apt-cache search ia32" and apt-get install all the packages that it will find. For me it is six packages

```
# apt-cache search ia32
ia32-libs-kde - KDE ia32 shared libraries for with OpenOffice.org
ia32-libs-openoffice.org - ia32 shared libraries for with OpenOffice.org
ia32-libs - ia32 shared libraries for use on amd64 and ia64 systems
ia32-libs-gtk - gtk+ ia32 shared libraries for with OpenOffice.org
ia32-libs-sdl - ia32 shared libraries of sdl related packages for use on amd64 and ia64 systems
ia32-sun-java5-bin - Sun Java(TM) Runtime Environment (JRE) 5.0 (32-bit)

```

---

### Post by guido_sohne on 2006-06-16
I've been tearing my hair out trying to install Oracle 10G Release 2 (64 bit Linux version) on Dapper (also the 64 bit version) and managed to work things out to at least get the installer running.

I had to import various 32 bit libraries from a 32 bit installation of Dapper.

Specifically,

The 32 bit installer program wants to find a 32 bit ld-linux.so.2 in /lib. Appears to be hardcoded, so I copied one over from a 32 bit Dapper install. That led to other dependencies not being found at dynamic link time and the libraries below were what I needed to resolve all the link dependencies

libdl.so.2   
libm.so.6    
libpthread-0.10.so  
libSM.so.6   
libXau.so.6   
libXp.so.6  
libXtst.so.6
libc.so.6      
libICE.so.6  
libnsl.so.1  
libpthread.so.0     
libX11.so.6  
libXext.so.6  
libXt.so.6

You can place all these 32 bit shared libraries into any random directory and do an export LD_LIBRARY_PATH=/path/to/random/directory before launching the Oracle 10GR2 installer (which comes with it's own JRE with evil JNI code in it, if you use Sun's JRE or JDK, you'll get null pointer exceptions almost immediately you load the installer).

Show stopper is that the installer throws up a wieird error dialog containing this message, S_OWNER_SYSTEM_NOENT, at the second screen in the installer, where you are selecting the oraInventory details ... It doesn't matter what I put in that screen, what group or directory I choose etc. 

It just refuses to go past that. I'm left scratching my head as to how you and Dizwell managed to get things running. Maybe it's a 64bit issue, but somehow I doubt it because the installer is a 32 bit program and I have all the libraries for that as 32 bit code.

Very frustrating. I have heard reports of people getting this to work under Breezy but no joy for Dapper yet. I'd be very interested in knowing what this problem is and am willing to work with anyone else on this who is knowledgeable and interesting ...

I suspect it's something going on in the installer ... I'm hoping you've seen that error message before ... The last thing I'm going to try is a bit desperate, to install the GUI on the server and try and launch it locally instead of via remote X11 to my Powerbook ... 

Very long shot, but that's how desperate I am at this point :-) I even took a look at downloading SuSE Enterprise since it's certified for Oracle but retreated when I saw it was five CDs !!! Yikes!

-- G.

---

### Post by juah on 2006-06-16
Has anybody else been trying gnash out. For me it's a big disappointment. Installation runs smoothly but that's about it. It is moderate to say it doesn't show all the flashes, while the truth is it doesn't show any of them. I'm using firefox and I installed both gnash and gnash-plugin.  There's no error messages of any kind.

---

### Post by juah on 2006-06-16
[QUOTE=CyberAngel]Nice to hear that it works :)

As for the scissors I have used them myself just for editing. Not for deleting something but when you go with the mouse over it, it say edit/delete :P :P
[/QUOTE]

It say doesn't it? But that's as far as it goes when it comes to deletion.8-[ 
Anyway - let's forget that one. The thing is  I'm really glad  for you excellent advice with RealPlayer. Ashtonishing for me was it worked out simply like that. I thought it'd be much harder because it's not included in repos for amd64 architecture.:o - still it is there for i386

---

### Post by CyberAngel on 2006-06-17
[QUOTE=juah]Has anybody else been trying gnash out. For me it's a big disappointment. Installation runs smoothly but that's about it. It is moderate to say it doesn't show all the flashes, while the truth is it doesn't show any of them. I'm using firefox and I installed both gnash and gnash-plugin.  There's no error messages of any kind.[/QUOTE]

I am using Firefox 64bit with gnash plugin for overall web browsing and I have opera 32bit installed too (with 32bit flash plugin) just for listening music to [pandora]("http://www.pandora.com") that unfortunately using a flash thing that it does not loading with gnash :)

---

### Post by juah on 2006-06-17
I've got macromedia flash with firefox32 running in chroot. [Pandora]("http://www.pandora.com") works fine with that. But with firefox64 and gnash - no way. My gnash doesn't work at all. It's a mystery.

As a matter of fact GPL Flash (libflash-mozplugin) seem to work far better with firefox 64, Mostly it works fine; on the other hand it cannot play the Pandora site.

Edit:

Later on I noticed my xserver-xorg configurations had been changed during the latest upgrade.  So 'sudo dpkg-reconfigure xserver-xorg' and choosing the proprietary driver for ATI (fglrx) encouraged me to try Gnash one more time.  Actually Gnash IS working now!  Maybe even better than GPL-flashO:)  so I think I'll stick with this for a while.

---

### Post by Princey on 2006-06-17
[QUOTE=CyberAngel]Have you installed all the ia32 libraries??

Do an "apt-cache search ia32" and apt-get install all the packages that it will find. For me it is six packages

```
# apt-cache search ia32
ia32-libs-kde - KDE ia32 shared libraries for with OpenOffice.org
ia32-libs-openoffice.org - ia32 shared libraries for with OpenOffice.org
ia32-libs - ia32 shared libraries for use on amd64 and ia64 systems
ia32-libs-gtk - gtk+ ia32 shared libraries for with OpenOffice.org
ia32-libs-sdl - ia32 shared libraries of sdl related packages for use on amd64 and ia64 systems
ia32-sun-java5-bin - Sun Java(TM) Runtime Environment (JRE) 5.0 (32-bit)

```[/QUOTE]

Thanks cyberangel. The only one that wasn't listed was the sun java one as I don't have the 32 java installed as yet. I will though as I need to have Opera running. Opera won't run without it. Going to attempt that one now.

---

### Post by zarathustra on 2006-06-18
I would advise against using Gnash. I installed it, and found that it oddly caused not just Firefox to crash, but all the applications I was running at the time.

---

### Post by steabert on 2006-06-18
Hi,

today I tried out xcdroast (one of my favourite programs :lol: )
I first ran it as root to setup the thing ok (like normal)
When I then opened xcdroast as myself (=user) and pressed on
setup button, I got a segfault.

Can anyone comfirm this?

this is on dapper latest upgrade


EDIT: I ran xcdroast through gdb, but the damn thing wouldn't crash, and
since then I couldn't get it to crash again, is this possible???

---

### Post by John Jason Jordan on 2006-06-20
[QUOTE=JoWilly][B]
**Adobe reader newer version 7.0.5** deb is availlable in the marillat repos, direct link here : [ftp://ftp.nerim.net/debian-marillat/pool/main/a/acroread]("ftp://ftp.nerim.net/debian-marillat/pool/main/a/acroread")[/QUOTE]
I tried that, but the URL is wrong.

I used the Ubuntu URL  [ftp://ftp.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread_7.0.1-0.0.ubuntu1_i386.deb](ftp://ftp.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread_7.0.1-0.0.ubuntu1_i386.deb)
and using the force architecture trick it installed perfectly. Oh, and you have to be sure you have libstdc++5 installed, which you can do with plain apt-get.

While it works great, I can't print from it because of the lame print user interface. Someone told me that he had 7.05 and that was fixed. The latest on Adobe's site is 7.08, but it's a tar.gz-something and I'm too new at this to figure out how to get the .deb file out of it. (I uncompressed it, but there's no .deb file -- it has a script you're supposed to run.)

Anyone know where I can get a .deb of at least 7.05?

---

### Post by Princey on 2006-06-20
[QUOTE=John Jason Jordan]I tried that, but the URL is wrong.

I used the Ubuntu URL  [ftp://ftp.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread_7.0.1-0.0.ubuntu1_i386.deb](ftp://ftp.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread_7.0.1-0.0.ubuntu1_i386.deb)
and using the force architecture trick it installed perfectly. Oh, and you have to be sure you have libstdc++5 installed, which you can do with plain apt-get.

While it works great, I can't print from it because of the lame print user interface. Someone told me that he had 7.05 and that was fixed. The latest on Adobe's site is 7.08, but it's a tar.gz-something and I'm too new at this to figure out how to get the .deb file out of it. (I uncompressed it, but there's no .deb file -- it has a script you're supposed to run.)

Anyone know where I can get a .deb of at least 7.05?[/QUOTE]

One method I find and I've used that works perfectly well is to copy and paste. The link to the 7.05 acroread is [ftp://ftp.nerim.net/debian-marillat/pool/main/a/acroread/acroread_7.0.5-0.3_i386.deb]("ftp://ftp.nerim.net/debian-marillat/pool/main/a/acroread/acroread_7.0.5-0.3_i386.deb")

If you find that link it too long to type, try this. After performing the first step in stalling libstdc++5, do the following:

1. Copy the entire url/link that I provided.

2. Open the terminal and type ```
cd temp
``` followed by ```
wget
``` press the spacebar once then hold down the SHIFT key and press the 'Insert' or 'Ins' key on your keyboard. (some have insert, others have ins. It's found together with the home/end keys)

3. Just hit the enter key and it will download acroread. Continue with the rest of the steps outlined in the post/howto you were following. 

This should save you a lot of time from trying to type long urls in the future.

---

### Post by John Jason Jordan on 2006-06-20
[QUOTE=Princey]One method I find and I've used that works perfectly well is to copy and paste. The link to the 7.05 acroread is [ftp://ftp.nerim.net/debian-marillat/pool/main/a/acroread/acroread_7.0.5-0.3_i386.deb]("ftp://ftp.nerim.net/debian-marillat/pool/main/a/acroread/acroread_7.0.5-0.3_i386.deb")

If you find that link it too long to type, try this. After performing the first step in stalling libstdc++5, do the following:

1. Copy the entire url/link that I provided.

2. Open the terminal and type ```
cd temp
``` followed by ```
wget
``` press the spacebar once then hold down the SHIFT key and press the 'Insert' or 'Ins' key on your keyboard. (some have insert, others have ins. It's found together with the home/end keys)

3. Just hit the enter key and it will download acroread. Continue with the rest of the steps outlined in the post/howto you were following. 

This should save you a lot of time from trying to type long urls in the future.[/QUOTE]
Thanks. However, it still doesn't work. First, I guess I don't have a temp folder. But I recall from when I installed the 7.01 deb with force-architecture yesterday that it was done from /tmp, so that is what I used. The following is what happened:

jjj@Devil5:~$ cd /tmp
jjj@Devil5:/tmp$ wget [ftp://ftp.nerim.net/debian-marillat/...5-0.3_i386.deb](ftp://ftp.nerim.net/debian-marillat/...5-0.3_i386.deb)
--09:04:22--  [ftp://ftp.nerim.net/debian-marillat/...5-0.3_i386.deb](ftp://ftp.nerim.net/debian-marillat/...5-0.3_i386.deb)
           => `...5-0.3_i386.deb'
Resolving ftp.nerim.net... 62.4.17.14, 2001:7a8:1:5::14
Connecting to ftp.nerim.net|62.4.17.14|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /debian-marillat ...
No such directory `debian-marillat'.

So evidently something is still wrong. :(

I just tried the URL in a new Firefox tab and it said "prohibited filename in URL." Is it the "..." that is causing the problem?

---

### Post by jon_gunnar on 2006-06-20
[QUOTE=realruntime]Well, Firefox behaves absolutely weird on Dapper-64bit. Sometime it hangs up completely. Then it trys to download PHP-Files - after hitting reload the php works.

Then it sends bad requests to the server (several servers giving me a "bad request" error). After hitting reload it works again.

This is a little bit disappointing. How can a good piece of software (have Firefox on Ubuntu Dapper 32-bit on an other computer - works excellent) become so awful by being compiled with a 64bit compiler?

Mozilla/5.0 (X11; U; Linux x86_64; de; rv:1.8.0.4) Gecko/20060608 Ubuntu/dapper-security Firefox/1.5.0.4[/QUOTE]

I would strongly belive that the problem is on you're setup.Firefox is no problem for most users on Ubuntu,be it 32 or 64 versions.

---

### Post by Princey on 2006-06-20
[QUOTE=John Jason Jordan]Thanks. However, it still doesn't work. First, I guess I don't have a temp folder. But I recall from when I installed the 7.01 deb with force-architecture yesterday that it was done from /tmp, so that is what I used. The following is what happened:

jjj@Devil5:~$ cd /tmp
jjj@Devil5:/tmp$ wget [ftp://ftp.nerim.net/debian-marillat/...5-0.3_i386.deb](ftp://ftp.nerim.net/debian-marillat/...5-0.3_i386.deb)
--09:04:22--  [ftp://ftp.nerim.net/debian-marillat/...5-0.3_i386.deb](ftp://ftp.nerim.net/debian-marillat/...5-0.3_i386.deb)
           => `...5-0.3_i386.deb'
Resolving ftp.nerim.net... 62.4.17.14, 2001:7a8:1:5::14
Connecting to ftp.nerim.net|62.4.17.14|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /debian-marillat ...
No such directory `debian-marillat'.

So evidently something is still wrong. :(

I just tried the URL in a new Firefox tab and it said "prohibited filename in URL." Is it the "..." that is causing the problem?[/QUOTE]

Actually, I tested, the server is down at the moment.

Edit:
Just found a mirror through Google that works. Tested it out for myself. [http://www.tomasek.cz/software/debarch/deb/ftp.nerim.net/debian-marillat/pool/main/a/acroread/acroread_7.0.5-0.3_i386.deb]("http://www.tomasek.cz/software/debarch/deb/ftp.nerim.net/debian-marillat/pool/main/a/acroread/acroread_7.0.5-0.3_i386.deb")

---

### Post by JoWilly on 2006-06-20
FYI, the _**macromedia 32bit flash plugin works perfectly with firefox64**_ using   [nspluginwrapper]("http://www.gibix.net/dokuwiki/en:projects:nspluginwrapper")

Howto here : [http://ubuntuforums.org/showthread.php?t=160318]("http://ubuntuforums.org/showthread.php?t=160318")

More information/solutions/fixes here: [http://ubuntuforums.org/showthread.php?t=193893&page=2]("http://ubuntuforums.org/showthread.php?t=193893&page=2")

EDIT: realplayer and adobe reader plugins should be working too acording to the nspluginwrapper web page, but I have not tried them. Will try later when I get the time.

---

### Post by Kilz on 2006-06-24
In case someone wants to just install 32 bit firefox with flash and java.
[http://www.ubuntuforums.org/showthread.php?t=202537](http://www.ubuntuforums.org/showthread.php?t=202537)

Edit: Added Real Player and Adobe Acrobat plugins.

---

### Post by John Jason Jordan on 2006-06-24
[QUOTE=Princey]Actually, I tested, the server is down at the moment.
Edit:
Just found a mirror through Google that works. Tested it out for myself. [http://www.tomasek.cz/software/debarch/deb/ftp.nerim.net/debian-marillat/pool/main/a/acroread/acroread_7.0.5-0.3_i386.deb]("http://www.tomasek.cz/software/debarch/deb/ftp.nerim.net/debian-marillat/pool/main/a/acroread/acroread_7.0.5-0.3_i386.deb")[/QUOTE]
I had to go to Mexico for a few days but now I'm back. Just tried the above and got:

jjj@Devil5:/tmp$ wget [http://www.tomasek.cz/software/debar...5-0.3_i386.deb](http://www.tomasek.cz/software/debar...5-0.3_i386.deb)
--08:46:46--  [http://www.tomasek.cz/software/debar...5-0.3_i386.deb](http://www.tomasek.cz/software/debar...5-0.3_i386.deb)
           => `debar...5-0.3_i386.deb'
Resolving [www.tomasek.cz](www.tomasek.cz)... 195.113.187.6
Connecting to www.tomasek.cz|195.113.187.6|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
08:46:46 ERROR 404: Not Found.

So evidently I am too late. That site is also down now. Anyone know of any other places to get the 7.05 or later .deb file? (The latest on Adobe's site is 7.08.)

---

### Post by Kilz on 2006-06-24
[QUOTE=John Jason Jordan]I had to go to Mexico for a few days but now I'm back. Just tried the above and got:

jjj@Devil5:/tmp$ wget [http://www.tomasek.cz/software/debar...5-0.3_i386.deb](http://www.tomasek.cz/software/debar...5-0.3_i386.deb)
--08:46:46--  [http://www.tomasek.cz/software/debar...5-0.3_i386.deb](http://www.tomasek.cz/software/debar...5-0.3_i386.deb)
           => `debar...5-0.3_i386.deb'
Resolving [www.tomasek.cz](www.tomasek.cz)... 195.113.187.6
Connecting to www.tomasek.cz|195.113.187.6|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
08:46:46 ERROR 404: Not Found.

So evidently I am too late. That site is also down now. Anyone know of any other places to get the 7.05 or later .deb file? (The latest on Adobe's site is 7.08.)[/QUOTE]

Get the installer from Adobe, its easy to use and works. It installs the program and plugin. I just added the acrobat to my 32 bit firefox install howto.

---

### Post by John Jason Jordan on 2006-06-24
[QUOTE=Kilz]Get the installer from Adobe, its easy to use and works. It installs the program and plugin. I just added the acrobat to my 32 bit firefox install howto.[/QUOTE]
I have Adobe Reader 7.01 properly installed. I don't care about the plugin (well, I do, but will tackle that later.) What I want to do now is upgrade my 7.01 to 7.05 or later.

While stumbling around I discovered that I had the 7.05 deb. It was in ~/Desktop, which is my default download locate for Firefox. So evidently I had found it somewhere and downloaded it before leaving a few days ago, then forgot I had it.

I installed it with 
```
sudo dpkg -i --force-architecture /home/jjj//Desktop/acroread_7.0.5-0.3_i386.deb

```
The script found that I had 7.01 and said things like "upgrading 7.01 to 7.05." It runs fine. The Help > About window says it is 7.05 now. 

However, now I have a worse problem. The whole reason for doing this was to get a better user interface for the Print dialog box, which I have been told was upgraded by Adobe. So the first thing I did was open a PDF and try to print it. Just clicking on File > Print crashes Adobe Reader now. It just disappears from the screen. I tried it with about a dozen PDFs, some from government agencies and corporations, some I created myself. Same results every time.

Anyone have any idea what could be wrong?

---

### Post by Kilz on 2006-06-24
[QUOTE=John Jason Jordan]I have Adobe Reader 7.01 properly installed. I don't care about the plugin (well, I do, but will tackle that later.) What I want to do now is upgrade my 7.01 to 7.05 or later.

While stumbling around I discovered that I had the 7.05 deb. It was in ~/Desktop, which is my default download locate for Firefox. So evidently I had found it somewhere and downloaded it before leaving a few days ago, then forgot I had it.

I installed it with 
```
sudo dpkg -i --force-architecture /home/jjj//Desktop/acroread_7.0.5-0.3_i386.deb

```
The script found that I had 7.01 and said things like "upgrading 7.01 to 7.05." It runs fine. The Help > About window says it is 7.05 now. 

However, now I have a worse problem. The whole reason for doing this was to get a better user interface for the Print dialog box, which I have been told was upgraded by Adobe. So the first thing I did was open a PDF and try to print it. Just clicking on File > Print crashes Adobe Reader now. It just disappears from the screen. I tried it with about a dozen PDFs, some from government agencies and corporations, some I created myself. Same results every time.

Anyone have any idea what could be wrong?[/QUOTE]

Could it be possible that .version in the .deb had problems to? Do yourself a favor get the 7.08 installer from adobe. It should overwrite and install the latest version, strait from the creators. All you have to do is untar the archive, navigate to the folder it makes in the terminal. Then type in sudo ./INSTALL  The pulgin install is just an added bonus, the installer is for the program itself.

---

### Post by John Jason Jordan on 2006-06-24
[QUOTE=Kilz]Could it be possible that .version in the .deb had problems to? Do yourself a favor get the 7.08 installer from adobe. It should overwrite and install the latest version, strait from the creators. All you have to do is untar the archive, navigate to the folder it makes in the terminal. Then type in sudo ./INSTALL  The pulgin install is just an added bonus, the installer is for the program itself.[/QUOTE]
Thanks. I'm making progress!

OK, I did as you suggested, and it worked. That is, I now have Adobe Reader 7.08. And when I click on File > Print it no longer crashes. So far, so good.

However, the problem I was trying to resolve that I had with 7.01 was that the Print dialog box does not recognize printers installed in Cups. All it gives me is a line where I have to enter the print syntax. We are now six years into the third millennium. That is totally lame. Just about every other application sees the printers I have installed, lists the one designated as the default, and gives me a spin button to select the others. I should not have to be reading man pages and crusing the web for wikis and forums just to print a PDF file.

I was hoping that this had been fixed in the later versions, but whoever told me that it was fixed evidently lied. It still just shows default syntax of "lpr-something." :(

While running the script I also told it to install the browser plugin, but that isn't working either. While launching either Adobe Reader or Firefox now I get:

"There was an error while loading the plug-in 'PPKLite.api.' The plug-in failed to initialize."

So it tried to install it, but evidently botched the job. I searched the whole filesystem, but didn't find any file "PPKLite."

I appreciate your help. :)

Edit: I get the error message only when launching Adobe Reader, not Firefox.

---

### Post by Kilz on 2006-06-24
[QUOTE=John Jason Jordan]Thanks. I'm making progress!

OK, I did as you suggested, and it worked. That is, I now have Adobe Reader 7.08. And when I click on File > Print it no longer crashes. So far, so good.

However, the problem I was trying to resolve that I had with 7.01 was that the Print dialog box does not recognize printers installed in Cups. All it gives me is a line where I have to enter the print syntax. We are now six years into the third millennium. That is totally lame. Just about every other application sees the printers I have installed, lists the one designated as the default, and gives me a spin button to select the others. I should not have to be reading man pages and crusing the web for wikis and forums just to print a PDF file.

I was hoping that this had been fixed in the later versions, but whoever told me that it was fixed evidently lied. It still just shows default syntax of "lpr-something." :(

While running the script I also told it to install the browser plugin, but that isn't working either. While launching either Adobe Reader or Firefox now I get:

"There was an error while loading the plug-in 'PPKLite.api.' The plug-in failed to initialize."

So it tried to install it, but evidently botched the job. I searched the whole filesystem, but didn't find any file "PPKLite."

I appreciate your help. :)[/QUOTE]

I got the "PPKlite" error the first time I started it up in firefox , but it then went to the EULA, I agreed and Acrobat loaded in firefox. The error hasnt come back.
If it you are still getting that error, are you using the 64 bit firefox that comes installed with Ubuntu amd64? The plugin is 32 bit and may not work with the 64 bit firefox. 
If you are using the nsplugin wrapper and running 64 bit firefox the plugin needs to [be converted.]("http://ubuntuforums.org/showpost.php?p=1160551&postcount=16") If you cant get the nspluginwrapper to work you can [install 32 bit Firefox on amd64]("http://www.ubuntuforums.org/showthread.php?p=1174435#post1174435")
If you already have 32 bit firefox installed try this just change the <username> to your username.
```
sudo cp -r -p /usr/local/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so /usr/local/firefox32/plugins/
sudo chown -R <username>:users /usr/local/firefox32/plugins/nppdf.so
```

Edit: Found the problem, the file PPKLight.api is causing the errors. The page I found says its a useless file and just delete it , the problem will vanish.
```
sudo rm /usr/local/Adobe/Acrobat7.0/Reader/intellinux/plug_ins/PPKLite.api
```

---

### Post by JoWilly on 2006-06-24
[quote=Kilz]Could it be possible that .version in the .deb had problems to? Do yourself a favor get the 7.08 installer from adobe. It should overwrite and install the latest version, strait from the creators. All you have to do is untar the archive, navigate to the folder it makes in the terminal. Then type in sudo ./INSTALL  The pulgin install is just an added bonus, the installer is for the program itself.[/quote] 
FYI the acroread 7.08 deb package is in the marillat repos and installs nicely with "dpkg -i --force-architecture" (much better for system consistency and to uninstall apps):

[http://www.debian-multimedia.org/pool/main/a/acroread/acroread_7.0.8-0.0_i386.deb]("http://www.debian-multimedia.org/pool/main/a/acroread/acroread_7.0.8-0.0_i386.deb")

---

### Post by JoWilly on 2006-06-24
FYI macromedia flash 32bit and realplayer 32bit plugins work fine in firefox64 using nspluginwrapper.

Check [this thread]("http://ubuntuforums.org/showthread.php?t=193893&page=3") on page 3 to get easy steps to get it to work.

[U][B]Could the author of this sticky thread please update the first post, so that people can find the information easily without searching for hours. Thanks.


[/B][/U]Edit: the realplayer deb is also in the marillat repo here:
[http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb ]("http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb")

---

### Post by Kilz on 2006-06-25
[QUOTE=JoWilly]FYI macromedia flash 32bit and realplayer 32bit plugins work fine in firefox64 using nspluginwrapper.

Check [this thread]("http://ubuntuforums.org/showthread.php?t=193893&page=3") on page 3 to get easy steps to get it to work.

[U][B]Could the author of this sticky thread please update the first post, so that people can find the information easily without searching for hours. Thanks.


[/B][/U]Edit: the realplayer deb is also in the marillat repo here:
[http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb ]("http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb")[/QUOTE]
IMHO a sticky should be edited by a mod , or be created by someone with 100 beans or more. Any less and there is a greater chance the person may lose intrest, or change distro's and then the info isnt updated.

---

### Post by Hendrik van den Boogaard on 2006-06-26
As listed in the end of the post on the first page I'm currently busy with some exams for my study. I will start updating this post on 30 june 2006.

I am actually using Ubuntu since Hoary came out, and I changed my running Debian Unstable to hoary. I started updating the Ubuntu distributions and now my server is running Dapper32 and my own machine is running Dapper64. I agree that I haven't posted much on this forum, but I am very willing to make my new AMD64x2 to run with as many applications as possible. Therefore I won't lose interest in this topic and I will try as many suggestions as are given in this topic and other topics as well. But till the end of this week I simply don't have time to update (and I'm about 100 miles away from my AMD64x2 ;))

Further, I still think (also regarding the numbre of views to this post and the number of downloads I get for dvdrip and rar) that this thread is still valuable for people running Dapper64.

About the NSplugin; the link refered to the second page of the same topic, but I'll change it to the 3rd and I will add the 'Howto Install 32 bit Firefox with Flash w/sound and Java for AMD64' from Kilz to the opening post.

---

### Post by JoWilly on 2006-06-26
[quote=Hendrik van den Boogaard]As listed in the end of the post on the first page I'm currently busy with some exams for my study. I will start updating this post on 30 june 2006.

I am actually using Ubuntu since Hoary came out, and I changed my running Debian Unstable to hoary. I started updating the Ubuntu distributions and now my server is running Dapper32 and my own machine is running Dapper64. I agree that I haven't posted much on this forum, but I am very willing to make my new AMD64x2 to run with as many applications as possible. Therefore I won't lose interest in this topic and I will try as many suggestions as are given in this topic and other topics as well. But till the end of this week I simply don't have time to update (and I'm about 100 miles away from my AMD64x2 ;))

Further, I still think (also regarding the numbre of views to this post and the number of downloads I get for dvdrip and rar) that this thread is still valuable for people running Dapper64.

About the NSplugin; the link refered to the second page of the same topic, but I'll change it to the 3rd and I will add the 'Howto Install 32 bit Firefox with Flash w/sound and Java for AMD64' from Kilz to the opening post.[/quote]

Thanks for the feedback.

Best wishes for your exams.

---

### Post by Kilz on 2006-06-26
[QUOTE=Hendrik van den Boogaard]As listed in the end of the post on the first page I'm currently busy with some exams for my study. I will start updating this post on 30 june 2006.

I am actually using Ubuntu since Hoary came out, and I changed my running Debian Unstable to hoary. I started updating the Ubuntu distributions and now my server is running Dapper32 and my own machine is running Dapper64. I agree that I haven't posted much on this forum, but I am very willing to make my new AMD64x2 to run with as many applications as possible. Therefore I won't lose interest in this topic and I will try as many suggestions as are given in this topic and other topics as well. But till the end of this week I simply don't have time to update (and I'm about 100 miles away from my AMD64x2 ;))

Further, I still think (also regarding the numbre of views to this post and the number of downloads I get for dvdrip and rar) that this thread is still valuable for people running Dapper64.

About the NSplugin; the link refered to the second page of the same topic, but I'll change it to the 3rd and I will add the 'Howto Install 32 bit Firefox with Flash w/sound and Java for AMD64' from Kilz to the opening post.[/QUOTE]

Cool, my post wasnt an attack on you, its just some things come up  in life. People with more beans/posts have just proven they have stayed around, and good luck on the exams

---

### Post by hajk on 2006-06-26
[QUOTE=Hendrik van den Boogaard]

[LIST]
[*][SIZE="4"]*Opera*[/SIZE] - Opera is not available in Dapper64. Here's a thread that might help, it mainly says that you need a statically copiled 32bit version of opera: [http://ubuntuforums.org/showthread.php?t=75940](http://ubuntuforums.org/showthread.php?t=75940)
[/LIST]

[/SIZE][/QUOTE]

The new Opera 9.0 works fine with the AMD64 kernel, provided that you download
the "Other/Static DEB" package, and install with
```

sudo dpkg -i --force-architecture opera-static_9.0-20060616.1-qt_en_i386.deb

``` 
The --force-architecture option is needed because this package is compiled for i386; the keyword here is "static"... it does not rely on system libraries.

(Note: While writing this message logged in with Opera, I note that the little icons for CODE etc don't have descriptive labels... not sure whether this is caused by Opera and whether this requires further configuration.)

---

### Post by IbeeX on 2006-06-28
Hi

if somebady want to install nxclient the he need sto do 
1. get deb from ther web
nxclient_1.5.0-141_i386.deb
2. get from [http://packages.ubuntu.com](http://packages.ubuntu.com) libstdc++2.10-glibc2.2
libstdc++2.10-glibc2.2_2.95.4-24_i386.deb
3. sudo dpkg -i --force-architecture libstdc++2.10-glibc2.2_2.95.4-24_i386.deb
4. sudo dpkg -i --force-architecture nxclient_1.5.0-141_i386.deb
5. sudo ln -s /usr/NX/bin/nxclient /usr/local/bin/

this is it

---

### Post by John Jason Jordan on 2006-06-28
[QUOTE=hajk]The new Opera 9.0 works fine with the AMD64 kernel, provided that you download
the "Other/Static DEB" package, and install with
```

sudo dpkg -i --force-architecture opera-static_9.0-20060616.1-qt_en_i386.deb

``` 
The --force-architecture option is needed because this package is compiled for i386; the keyword here is "static"... it does not rely on system libraries.[/QUOTE]
Awesome!!!

I've been wanting Opera for ages! Finally!! Dude, you rock!

---

### Post by plewisfdx on 2006-06-30
[QUOTE=hajk]The new Opera 9.0 works fine with the AMD64 kernel, provided that you download
the "Other/Static DEB" package, and install with
```

sudo dpkg -i --force-architecture opera-static_9.0-20060616.1-qt_en_i386.deb

``` 
The --force-architecture option is needed because this package is compiled for i386; the keyword here is "static"... it does not rely on system libraries.[/QUOTE]

I get this error msg when trying to start opera:
```
/usr/bin/opera: line 263: /usr/lib/opera/9.0-20060616.1/opera: No such file or directory
/usr/bin/opera: line 263: /usr/lib/opera/9.0-20060616.1/opera: Success
```

I d/l'ed the static DEB package, and did the 'force-arch', but it doesn't load.

---

### Post by Jigme Senge on 2006-07-01
Skype  seems that needs a workaround since it gives me the same error as Opera Error: wrong archtecture 'i386' 

If someone can provide me guidance I would appreciate it, I have migrated most of my applications from XP to Ubuntu for amd64 but I need skype otherwise I will have to go back to windows until I can get a fix.

---

### Post by fabertawe on 2006-07-02
[QUOTE=Jigme Senge]Skype  seems that needs a workaround since it gives me the same error as Opera Error: wrong archtecture 'i386' 

If someone can provide me guidance I would appreciate it, I have migrated most of my applications from XP to Ubuntu for amd64 but I need skype otherwise I will have to go back to windows until I can get a fix.[/QUOTE]

Firstly, if you don't have linux32 installed then this will install it and the packages required to use it...
```
sudo apt-get install ia32-libs ia32-libs-gtk gsfonts gsfonts-x11 linux32
```

Download the static 1.3 Beta (skype-beta_staticQT-1.3.0.30.tar.bz) from
[http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/)
Extract the contents from within Nautilus (right click -> extract to...). Then right click on the desktop and create a launcher. In 'Command' put 'linux32 /<path to skype folder>/skype'. My path is 'linux32 /opt/skype/skype', for example.

It works! Hope that helped.

---

### Post by Princey on 2006-07-02
[QUOTE=plewisfdx]I get this error msg when trying to start opera:
```
/usr/bin/opera: line 263: /usr/lib/opera/9.0-20060616.1/opera: No such file or directory
/usr/bin/opera: line 263: /usr/lib/opera/9.0-20060616.1/opera: Success
```

I d/l'ed the static DEB package, and did the 'force-arch', but it doesn't load.[/QUOTE]

I'm not sure but I've never tried the static version. I use the shared version as stated earlier in this post and have mine running. That's what I'm using to post right at this minute and all my plugins work perfectly well including flash.

---

### Post by Adam4491 on 2006-07-05
Wine 32bit - Wine can give you some troubles. Here's a HowTo that might help: [http://ubuntuforums.org/newreply.php...te=1&p=1122806](http://ubuntuforums.org/newreply.php...te=1&p=1122806)


leads to making a new thread? noguide?

---

### Post by Kilz on 2006-07-05
[QUOTE=Adam4491]Wine 32bit - Wine can give you some troubles. Here's a HowTo that might help: [http://ubuntuforums.org/newreply.php...te=1&p=1122806](http://ubuntuforums.org/newreply.php...te=1&p=1122806)


leads to making a new thread? noguide?[/QUOTE]
I have a wine howto a lof of people have used. [Click here to visit the howto.]("http://www.ubuntuforums.org/showthread.php?t=185557")

---

### Post by Hendrik van den Boogaard on 2006-07-06
[QUOTE=Kilz]I have a wine howto a lof of people have used. [Click here to visit the howto.]("http://www.ubuntuforums.org/showthread.php?t=185557")[/QUOTE]

Oops, my mistake. I changed it in the first post.

---

### Post by Kilz on 2006-07-06
[QUOTE=Hendrik van den Boogaard]Oops, my mistake. I changed it in the first post.[/QUOTE]
Mistakes happen, we are all human.  :D  This sticky is a good thing that has helped a lot of people. I noticed you redid the first post, looks good.

---

### Post by Kilz on 2006-07-06
This is just a question/observation/suggestion 
I have noticed the 64bit section gets some "should I install 64bit, whats missing" posts. It seems that the title of this thread has [scared at least one person into questioning that things are not available]("http://www.ubuntuforums.org/showpost.php?p=1222259&postcount=5") at all in the 64bit OS. So they want to install the 32bit one. 
Do we really want to scare people away from installing the 64bit OS? The more people using it and asking for improvements may be a good thing.
I know that if they read the thread it would prove that isn't the case, but not everyone wants to read a thread that is 8 pages long.  The first post has changed from whats not available, to what are the howto's to make the 64bit OS better. Maybe the title needs to be edited a little? :-k After all its a sticky, and I know the first thing I look at in a forum is the sticky's. But its up to Hendrik in the end, its his thread.

---

### Post by Kilz on 2006-07-11
I have updated my Firefox32 howto to include some automatic setup scripts.

---

### Post by JoWilly on 2006-07-11
> **Kilz said:**
>   The first post has changed from whats not available, to what are the howto's to make the 64bit OS better. Maybe the title needs to be edited a little? :-k After all its a sticky, and I know the first thing I look at in a forum is the sticky's. But its up to Hendrik in the end, its his thread.

**BUMP**

---

### Post by themoebius on 2006-07-12
Does the program icon work for anyone else with 32bit firefox? In the task bar, the icon next to it is a generic icon - how can I get the firefox logo there?

---

### Post by Kilz on 2006-07-12
> **themoebius said:**
> Does the program icon work for anyone else with 32bit firefox? In the task bar, the icon next to it is a generic icon - how can I get the firefox logo there?
Right clicked on firefox in the taskbar. Selected properties. Click on the ugly icon in the box that pops up, click browse in the icon menu, browse over to the icon you want, highlight it, click open.
If you need a nice icon, [I use this one]("http://www.deviantart.com/deviation/5176277/"). Just right click on it and save as.

---

### Post by themoebius on 2006-07-12
> **Kilz said:**
> Right clicked on firefox in the taskbar. Selected properties. Click on the ugly icon in the box that pops up, click browse in the icon menu, browse over to the icon you want, highlight it, click open.
If you need a nice icon, [I use this one]("http://www.deviantart.com/deviation/5176277/"). Just right click on it and save as.

hmm in Gnome there's no properties when you right click on the item in the task bar. Maybe you're using KDE or you're talking about the application launcher? I want to change the actual icon of the program which is representing Firefox on the task bar when its actually running and in the top left corner of the title bar on the firefox window.

---

### Post by sYs^ on 2006-07-12
I hope I dont say any stupid thing but it seems like the link is wrong in the first post for the FireFox tutorial (for me at least).

The correct link is: 
[http://www.ubuntuforums.org/showthread.php?t=202537](http://www.ubuntuforums.org/showthread.php?t=202537)

---

### Post by Kilz on 2006-07-12
> **sYs^ said:**
> I hope I dont say any stupid thing but it seems like the link is wrong in the first post for the FireFox tutorial (for me at least).

The correct link is: 
[http://www.ubuntuforums.org/showthread.php?t=202537](http://www.ubuntuforums.org/showthread.php?t=202537)
Thats strange, I thought that was fixed.

---

### Post by Kilz on 2006-07-12
> **themoebius]hmm in Gnome there's no properties when you right click on the item in the task bar. Maybe you're using KDE or you're talking about the application launcher? I want to change the actual icon of the program which is representing Firefox on the task bar when its actually running and in the top left corner of the title bar on the firefox window.[/quote]
Nope, Im a huge Gnome fan. Sorry, thought you ment the launcher up top. I persoanly hate the blue globe that is the default launcher icon for Firefox.

[QUOTE=sYs^ said:**
> I hope I dont say any stupid thing but it seems like the link is wrong in the first post for the FireFox tutorial (for me at least).

The correct link is: 
[http://www.ubuntuforums.org/showthread.php?t=202537](http://www.ubuntuforums.org/showthread.php?t=202537)
Thats strange, I thought that was fixed.

---

### Post by themoebius on 2006-07-12
> **Kilz said:**
> Nope, Im a huge Gnome fan. Sorry, thought you ment the launcher up top. I persoanly hate the blue globe that is the default launcher icon for Firefox.

Me too, but thats the easy part. Here's a little screen cap that demonstrates the problem. Is anyone else having this problem? [http://personal.zacwittedesign.com/firefoxproblem.png](http://personal.zacwittedesign.com/firefoxproblem.png)

---

### Post by sYs^ on 2006-07-13
This is what I see:

> *Kilz* set up a nice [Howto]("http://ubuntuforums.org/showthread.php?t=191205") about running Firefox 32bit in Dapper64 with 32bit plugins. 
HOWTO = [http://ubuntuforums.org/showthread.php?t=191205](http://ubuntuforums.org/showthread.php?t=191205)

But that is the current topic not your howto, imho.

---

### Post by Kilz on 2006-07-13
> **sYs^ said:**
> This is what I see:

 
HOWTO = [http://ubuntuforums.org/showthread.php?t=191205](http://ubuntuforums.org/showthread.php?t=191205)

But that is the current topic not your howto, imho.
Just use the link in my signature. If you go back to page 8 you will see that Hendrik fixed the link before, dont know why its isnt working again. He pops in every so often, Im sure he will fix it when he dose.

---

### Post by themoebius on 2006-07-13
> **themoebius said:**
> Me too, but thats the easy part. Here's a little screen cap that demonstrates the problem. Is anyone else having this problem? [http://personal.zacwittedesign.com/firefoxproblem.png](http://personal.zacwittedesign.com/firefoxproblem.png)

Hmmm I think the reason why we're not getting the correct program icon for firefox is because we're not launching firefox directly - we're launching that script which launches the linux32 wrapper and firefox inside of it, so we're getting the icon associated with the linux32 wrapper.

Is there anyway to force the icon that the program uses?

---

### Post by acidjames on 2006-07-14
> **hajk said:**
> The new Opera 9.0 works fine with the AMD64 kernel, provided that you download
the "Other/Static DEB" package, and install with
```

sudo dpkg -i --force-architecture opera-static_9.0-20060616.1-qt_en_i386.deb

``` 
The --force-architecture option is needed because this package is compiled for i386; the keyword here is "static"... it does not rely on system libraries.

(Note: While writing this message logged in with Opera, I note that the little icons for CODE etc don't have descriptive labels... not sure whether this is caused by Opera and whether this requires further configuration.)


i'm using ubuntu amd64 and in "Add/Remove programs" i have Opera web listed, but yet, i can't install it, it tells me that the dapper commercial is not enabled (and it is listed in my sources.list)

Don't you think it's strange that it is listed but it is not available for amd64 ?

The programs listed in "Add/Remove programs" should be platform dependant

---

### Post by CyberAngel on 2006-07-14
It should be nice to have the availiable (Unofficial) amd64 repositories on the first post of this thread so new (and old) users can find them easily.

e.g. RAOF`s of Janvitus repos, or any other you may know.

---

### Post by norv on 2006-07-14
**Gem**
I would like to install gem, the Graphics Environment for Multimedia. It is available for Ubuntu Dapper AMD64 but some dependencies are not, eg:
#

[dep] libquicktime1 (>= 0.9.3) [amd64]
    Package not available
#

[dep] xlibmesa-gl [amd64]
    Package not available
or libgl1
    Virtual package

#

[dep] xlibmesa-glu [amd64]
    Package not available
or libglu1
    Virtual package 

libquicktime1 is available for Debian AMD64, should I use that? Or install gem in my 32-bit chroot?

---

### Post by fabertawe on 2006-07-15
> **CyberAngel said:**
> It should be nice to have the availiable (Unofficial) amd64 repositories on the first post of this thread so new (and old) users can find them easily.

e.g. RAOF`s of Janvitus repos, or any other you may know.

This is a good idea. These guys are doing a fantastic job!

Maybe it could be possible to have a "community" repository for us 64bit users, so everything is in one place? Then if anyone other than those guys manages to compile something there'd be a place to submit it to.

A question for the more knowledgeable... how difficult is it to compile something written for 32bit as 64bit? Is it more than changing a few lines in a header file(s)? Also, is it difficult to compile something as 32bit 'static' so it can easily be run with linux32?

Cheers ... Paul

---

### Post by RAOF on 2006-07-15
> **fabertawe said:**
> ...
Maybe it could be possible to have a "community" repository for us 64bit users, so everything is in one place? Then if anyone other than those guys manages to compile something there'd be a place to submit it to.

A question for the more knowledgeable... how difficult is it to compile something written for 32bit as 64bit? Is it more than changing a few lines in a header file(s)? Also, is it difficult to compile something as 32bit 'static' so it can easily be run with linux32?
...

1) I'd be perfectly happy to upload my stuff to a Community repository, should someone be able to provide it.  Good idea, if anyone should be able to volunteer.

2) (Good) Programs aren't written for a specific wordsize, either 32bit or 64bit, so in general building a 64 bit program is as simple as using a version of gcc that outputs 64bit code.  For less-well-written programs, sometimes the programmers do something stupid, like use a pointer (memory reference) as an integer, or an integer as a pointer.  This introduces annoying and or subtle bugs into a 64bit build, becuase integers are not the same size as pointers, whereas they are (generally) the same size on 32bit architectures.

3) The difficulty of compiling static binaries probably depends on the buildsystem.  I'd imagine that with autotools (what most programs are built with) it should be fairly simple, but I've never tried :)

---

### Post by drsdinesh on 2006-07-15
hi,
  am new to linux. installed the 64bit version of ubuntu on my system - AMD64 3500+, 512 MB, 2 80Gb Hard disks , nVidia 3D graphics card - without any hitches. i have a working broadband connection from BSNL using a UTStarcom UT-300R2 ADSL Modem connected to the system by ethernet LAN. works like a dream in windows xp but inspite of help from Kagashe on this forum, i'm unable to connect to the net from ubuntu.
dinesh.

---

### Post by sYs^ on 2006-07-15
> **Kilz said:**
> Just use the link in my signature. If you go back to page 8 you will see that Hendrik fixed the link before, dont know why its isnt working again. He pops in every so often, Im sure he will fix it when he dose.


I didn't say it because I can't find the howto just for the "order" :p

---

### Post by fabertawe on 2006-07-15
> **RAOF said:**
> 1) I'd be perfectly happy to upload my stuff to a Community repository, should someone be able to provide it.  Good idea, if anyone should be able to volunteer.

2) (Good) Programs aren't written for a specific wordsize, either 32bit or 64bit, so in general building a 64 bit program is as simple as using a version of gcc that outputs 64bit code.  For less-well-written programs, sometimes the programmers do something stupid, like use a pointer (memory reference) as an integer, or an integer as a pointer.  This introduces annoying and or subtle bugs into a 64bit build, becuase integers are not the same size as pointers, whereas they are (generally) the same size on 32bit architectures.

3) The difficulty of compiling static binaries probably depends on the buildsystem.  I'd imagine that with autotools (what most programs are built with) it should be fairly simple, but I've never tried :)

Very interesting, thanks RAOF. So if everyone could compile a static version at the same time as their normal 32bit version we'd all be sorted ;-)

I'm new to Linux and I've been trying to compile Gyachi (see [this thread]("http://ubuntuforums.org/showthread.php?t=190900")). I actually got it to compile before my desktop crashed and burned. Now I've reinstalled I can't get past the make errors posted in that thread ](*,) Suffice to say I haven't got much of a clue as to what I'm doing! #-o It's the only messenger software I've been able to use my cam with and it's really bugging me now :-k

Anyway... keep up the good work :) 

Cheers ... Paul

---

### Post by Mickey Mouse on 2006-07-15
Here are some more suggestions:

Digital Mars D compiler (or DGC, its GNU version).
XnView (image viewer - manipulator).
Opera + plugins
Tor

Thank you.

---

### Post by Kilz on 2006-07-16
> **Mickey Mouse said:**
> Here are some more suggestions:

Digital Mars D compiler (or DGC, its GNU version).
XnView (image viewer - manipulator).
Opera + plugins
Tor

Thank you.
Tor is in synaptic
Opera is avaiable from the opera web site and can be forced in.
Xnview has an install script from the author that works.
You may want to setup a chroot for programing languages.

---

### Post by svaiyapu on 2006-07-16
This is regarding Oracle 10gR2 support on Ubuntu Dapper AMD64

Please see 

[http://oande.blogspot.com/2006/07/oracle-10gr2-on-ubuntu-dapper-amd64.html](http://oande.blogspot.com/2006/07/oracle-10gr2-on-ubuntu-dapper-amd64.html)

Best Regards,
-senthil

---

### Post by sacksank on 2006-07-17
> **RAOF said:**
> Actually, if anyone wants a program packaged for AMD64, I'd be happy to extend my repository to include it.  When I have time ;)

I really love to have wine that works the current win app such as photoshop and gyachI in the repo.. :oops:

---

### Post by fabertawe on 2006-07-17
> **sacksank said:**
> I really love to have wine that works the current win app such as photoshop and gyachI in the repo.. :oops:

I compiled Wine yesterday from [their own instructions]("http://wiki.winehq.org/WineOn64bit"). I had some missing dependencies and needed to create the symlinks indicated (including libz.so). I would recommend [Kilz's HOWTO]("http://ubuntuforums.org/showthread.php?t=185557&highlight=wine+64bit") as it's easier ;) 

Paul

---

### Post by Kilz on 2006-07-17
> **fabertawe said:**
> I compiled Wine yesterday from [their own instructions]("http://wiki.winehq.org/WineOn64bit"). I had some missing dependencies and needed to create the symlinks indicated (including libz.so). I would recommend [Kilz's HOWTO]("http://ubuntuforums.org/showthread.php?t=185557&highlight=wine+64bit") as it's easier ;) 

Paul

As I understand it, while you can compile wine to run on a 64bit system. It is still a 32bit application. Can you confirm this?

---

### Post by fabertawe on 2006-07-17
> **Kilz said:**
> As I understand it, while you can compile wine to run on a 64bit system. It is still a 32bit application. Can you confirm this?

Please bare in mind I'm fumbling in the dark with this but as configuring involves this -
```
LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32"  ./configure
```
I suspect you're right ;) 

The only difference I've noticed to installing it from your instructions is I now have a very slight corruption of text on dialogue boxes which can usually be fixed by moving the box. Another plus for your HOWTO!

Have you tried [WineTools]("http://www.von-thadden.de/Joachim/WineTools/index.html") ?

Cheers ... Paul

---

### Post by Kilz on 2006-07-17
> **fabertawe said:**
> Please bare in mind I'm fumbling in the dark with this but as configuring involves this -
```
LDFLAGS="-L/lib32 -L/usr/lib32 -Wl,-rpath,/lib32 -Wl,-rpath,/usr/lib32"  ./configure
```
I suspect you're right ;) 

The only difference I've noticed to installing it from your instructions is I now have a very slight corruption of text on dialogue boxes which can usually be fixed by moving the box. Another plus for your HOWTO!

Have you tried [WineTools]("http://www.von-thadden.de/Joachim/WineTools/index.html") ?

Cheers ... Paul

I perfer [sidenet]("http://www.google.com/url?sa=t&ct=res&cd=3&url=http%3A%2F%2Fsidenet.ddo.jp%2Fwinetips%2Fconfig.html&ei=3BK8RJyVDJuuoQKmjIWGDg&sig2=JKlbehp8bkZtnBc6S140Pg") for setting up wine.

---

### Post by fabertawe on 2006-07-18
> **Kilz said:**
> I perfer [sidenet]("http://www.google.com/url?sa=t&ct=res&cd=3&url=http%3A%2F%2Fsidenet.ddo.jp%2Fwinetips%2Fconfig.html&ei=3BK8RJyVDJuuoQKmjIWGDg&sig2=JKlbehp8bkZtnBc6S140Pg") for setting up wine.

I've only used sidenet myself (your HOWTO recommendation ;)) but was wondering what the differences are?

Cheers ... Paul

---

### Post by Kilz on 2006-07-18
> **fabertawe said:**
> I've only used sidenet myself (your HOWTO recommendation ;)) but was wondering what the differences are?

Cheers ... Paul

Im not 100% sure as its been awhile since I tested it. But I do know winetools gives you a little config gui. For the most part I use the winecfg when I need to make adjust things. The other claim to fame is that it can install ie. I use [ies4linux]("http://www.tatanka.com.br/ies4linux/index-en.html") for that. Sidenet from the sidenet website can install IE but only on wine versions 9.9.0 and lower. I link to an edited install that removes the messed up IE install and just sets up the wine drives, adds fonts, codecs, and sets up the dlls in the wine cfg.

---

### Post by skylark on 2006-07-21
RE: rar support

It is worth mentioning that if you are only interested in decompressing rar archives then it is possible to do this with "unrar" from the multiverse repo:

sudo aptitude install unrar

When installed you can view/extract rar archives in the standard way via file-roller. Or from the command line: "unrar x file.rar"

The main advantage over "rar" is that is easier to install on AMD64, and unrar is compiled from freely available source-code. If you look at the source for "rar" it is a wrapper around a i386 binary! 

There also exists an "unrar-free" which is GPL I believe. Unfortunately unrar-free can't handle some rar archives. "unrar" handles everything I've thrown at it so far. It is non-free because it includes a clause about reverse engineering the rar format to enable compression to a rar archive (see file:///usr/share/doc/unrar/copyright for the details in the license after unrar is installed).

---

### Post by IbeeX on 2006-07-21
I hawe Canon PIXMA IP4200 printer
and if somebady how to install it and that it can work well and print color it would be great !!!

:KS :KS :KS

---

### Post by Hendrik van den Boogaard on 2006-07-29
Hi all, I'm back from my vacation and when I'm home near my own AMD64X2 I will start reading and updating this thread. :)

---

### Post by Kilz on 2006-07-29
> **Hendrik van den Boogaard said:**
> Hi all, I'm back from my vacation and when I'm home near my own AMD64X2 I will start reading and updating this thread. :)

Please change the title of this post. I think its giving the impression that lots of things are missing from the 64bit version.

---

### Post by calvinthomas on 2006-07-31
I don't think Maple 9.5 works in AMD64

---

### Post by Hendrik van den Boogaard on 2006-08-03
I've changed a couple of things in the opening post, but I will yet have to look through all the new replies in this thread. Some strange this I noticed when browsing this topic; 2 references (Wine and Firefox) directed to the wrong addresses. I am sure I already changed these URL's (somewhere om page 8 I tell you this) but now there were wrong again, so I changed them to the right URL.

I will add some info about the new 64 bit repositories later. I myself am a bit 'scared' to use 3rd party repositories for all stuff that is just 'newer'. For example; I don't really trust the Janvitus (do I spell this correclty?) update for 'Revelation' (password manager). I don't think he has included a backdoor, but I think it is only necessary to patch a broken version in Dapper itself and not to install a completely new version (at least; for me). If a security update is there, Ubuntu will notice me about this, but does Janvitus check the Revelation source so often that he will maintain a secure version? Same goes for other programs.

About the title, I agree on changing this. At first stepping to 64bit was confusing but now there is a lot of info out there, where this topic points to. Does anyone has a better suggestion than what I made of it? ;)

Update: I changed the title, but on the main page it is still wrong. If you open the topic, both titles are visible, the old on top, the new a bit below :(

---

### Post by bmcage on 2006-08-04
You can install Maple 9.5 on amd64. 
 See my reply in thread [http://ubuntuforums.org/showthread.php?p=1337016](http://ubuntuforums.org/showthread.php?p=1337016)

Other people needed to do the same workaround for Maple 10, and other Java based programms on amd64.

---

### Post by tymek666 on 2006-08-04
Thx a lot for Skype 1.30 HowTo. Works great :)

---

### Post by Carl H on 2006-08-05
> **Kilz said:**
> I think its giving the impression that lots of things are missing from the 64bit version.

That is what I took it to mean.

---

### Post by Kilz on 2006-08-05
> **Carl H said:**
> That is what I took it to mean.

There isnt, this post is more or less a link to the howtos for the amd64 version to get some programs working. But at this point I'm not sure it can be changed without a mod's help.

---

### Post by Hendrik van den Boogaard on 2006-08-05
It doesn't look like it. The thread is still listed as 'Programs that do not work/are not available under Dapper Drake 64-bit edition', where above my opening post the topic has changed...

Perhaps a can ask a mod to change it. Does anyone has a better title than 'How to get specific programs to run under Dapper Drake 64-bit edition'?

---

### Post by Kilz on 2006-08-05
> **Hendrik van den Boogaard said:**
> It doesn't look like it. The thread is still listed as 'Programs that do not work/are not available under Dapper Drake 64-bit edition', where above my opening post the topic has changed...

Perhaps a can ask a mod to change it. Does anyone has a better title than 'How to get specific programs to run under Dapper Drake 64-bit edition'?

I posted a question on the forums section asking them to change it when I noticed you tried to change it but couldnt.

---

### Post by fabertawe on 2006-08-06
> **Hendrik van den Boogaard said:**
> Does anyone has a better title than 'How to get specific programs to run under Dapper Drake 64-bit edition'?

What about something like "Enabling missing/misbehaving programs under Dapper Drake 64-bit" or "Enhancing the Dapper Drake 64-bit software experience" ;)

Paul

---

### Post by Kilz on 2006-08-06
> **fabertawe said:**
> What about something like "Enabling missing/misbehaving programs under Dapper Drake 64-bit" or "Enhancing the Dapper Drake 64-bit software experience" ;)

Paul

I think we should stay away from anything that gives the impression things are missing.

---

### Post by Hendrik van den Boogaard on 2006-08-07
Too late for suggestions :), the title has changed into my suggestion ;). I hope it will help not to scare people away from 64bit.

---

### Post by Kilz on 2006-08-07
> **Hendrik van den Boogaard said:**
> Too late for suggestions :), the title has changed into my suggestion ;). I hope it will help not to scare people away from 64bit.

I think its a good replacement. The title fits the subject and should stop the "Whats missing" posts.

---

### Post by oldroger on 2006-08-14
If you still have this problem, try to link .aMule to another (local) directory which you have user access to - that worked pretty fine for me!

cya

> **Hendrik van den Boogaard said:**
> I have no idea what causes the problem with aMule in my case. Perhaps it has to do with the fact that my homedir is mounted over NFS. If I unmount the nfs share amule will start correctly. If I mount it again and delete the .aMule dir, it won't start anymore. However, if I make a symlink ~/.aMule which points to /tmp/aMule (an empty dir created by me) it works fine again.

It would be strange though if aMule had problems with NFS, because on Dapper32 this all seemed to work fine.

---

### Post by tomdkat on 2006-08-14
I see Sun is offering [Linux AMD64 native JDK/JRE downloads](https://sdlc1d.sun.com/ECom/EComActionServlet;jsessionid=1459F36AD40394D26B425D81C172D470) for the 1.5.0_08 Java environment.  Can those be used instead of the 32-bit  environments?

If you click the link, scroll down to see the download.

Peace...

---

### Post by Kilz on 2006-08-14
[I have a new ATI driver installer script.]("http://ubuntuforums.org/showthread.php?p=1372283#post1372283") in case anyone would like to use it.

---

### Post by Aikurn on 2006-08-16
I've just installed unrar (non-free version) and it's in the repositories, no need of 32 bits packages :D

---

### Post by BatteryCell on 2006-08-18
> **tomdkat said:**
> I see Sun is offering [Linux AMD64 native JDK/JRE downloads](https://sdlc1d.sun.com/ECom/EComActionServlet;jsessionid=1459F36AD40394D26B425D81C172D470) for the 1.5.0_08 Java environment.  Can those be used instead of the 32-bit  environments?

If you click the link, scroll down to see the download.

Peace...

The links broken for me, asks me to login.

---

### Post by MysticAurora on 2006-08-20
Hi. I'm new to the boards. When I altered my /etc/apt/sources.list to include RAOF's repository (for GNash) and performed an 'apt-get update', I get the following error when apt-get gets to ROAF's repo:

> Err [http://raof.dyndns.org](http://raof.dyndns.org) dapper Release.gpg                                  
  Could not connect to raof.dyndns.org:80 (202.63.35.99), connection timed out
Fetched 15.8kB in 2m0s (132B/s)                   
Failed to fetch [http://raof.dyndns.org/falcon/dists/dapper/Release.gpg](http://raof.dyndns.org/falcon/dists/dapper/Release.gpg)  Could not connect to raof.dyndns.org:80 (202.63.35.99), connection timed out
Reading package lists... Done
W: GPG error: [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC0A1CC62F306651
W: You may want to run apt-get update to correct these problems
W: Some index files failed to download, they have been ignored, or old ones used instead.

I've visited the Gnash project page before and attempted to compile it as well, but I get the following error when I input "./configure":

> checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether make sets $(MAKE)... (cached) yes
checking for pkg-config... yes
checking for kde-config... /usr/bin/kde-config
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for style of include used by make... GNU
checking for g++... no
checking for c++... no
checking for gpp... gpp
checking for C++ compiler default output file name... b.out
checking whether the C++ compiler works... configure: error: cannot run C++ comp
iled programs.
If you meant to cross compile, use `--host'.

I'm running Xubuntu 6.06 (Dapper) AMD64. Is there anything I can do to make this work? I really miss watching Youtube and Google Video..

---

### Post by BatteryCell on 2006-08-20
If you want to get flash video and java to work check out this easy howto:
[http://www.ubuntuforums.org/showthread.php?t=202537&page=15&highlight=firefox+real+player](http://www.ubuntuforums.org/showthread.php?t=202537&page=15&highlight=firefox+real+player)

It eliminates the need for gnash.

---

### Post by RAOF on 2006-08-21
> **MysticAurora said:**
> Hi. I'm new to the boards. When I altered my /etc/apt/sources.list to include RAOF's repository (for GNash) and performed an 'apt-get update', I get the following error when apt-get gets to ROAF's repo:
...

The first problem is because raof.dyndns.org is my home box; it is not on 24/7.  Also, it's got a very poor uplink speed.  I recommend using one of the mirrors instead :).

The second problem is a warning, not an error.  You can fix that by following the instructions on the repository web-page:
```

wget http://ubuntu.moshen.de/2F306651.gpg -O- | sudo apt-key add -

```

---

### Post by kleeman on 2006-08-30
Some specific feedback on an em64t dual xeon system:

First the system with an amd64-xeon kernel works very well and gnome appears very significantly faster (subjectively maybe twice as fast as with a 686-smp kernel and 32 bit setup). smp works well and there are four virtual cpus all of which are loaded.

Failures: linux32 and aoss appear flakey as does the 64bit blackdown java plugin for firefox.

Successes:

Freenx: Works perfectly both as a server and client. Installed from seveas repository but had to use the devscripts utility deb-reversion to change the architecture of several packages and also had to force the client to install 

Realplayer: Version 10.0.8 works without issue in an alsa system despite it being an OSS application. I had two soundcards with the desired one assigned slot 1 rather than slot 0. I had to force the boot to swap these by editing /etc/modprobe.d and adding the undesired sound card's module to the bottom of /etc/modprobe.d/alsa-base (options snd-intel8x0 index=-2). This stops that card being assigned slot 0. After this OSS works flawlessly in alsa.

Acroread: works flawlessly with the latest download from adobe and without using linux32.

Firefox media plugins. Installed the script from kilz for flash, java and mplayer. firefox32 then works as well as the version on the 32 bit kernel set up. java, falsh and most media work once win32 codecs are installed.

Sound and video: Audigy 2 with alsa works great with surround sound. nvidia geforce 7950 GX2 works nicely with 3d acceleration even though it is not listed as supported on the nvidia release notes.

Final Failure: Cube Sauerbraten fps game does not work with linux32 or from the commandline.

Edit: I had later problems with acroread 7.05. In particular one plugin did not load and printing failed. I solved the printing problem by installing version 7.0.8. The plugin problem I solved by the following:

cd INSTALLPATH/intellinux/lib  (INSTALLPATH being where you put your acroread install)
rm libldap.so
ln -s /usr/lib32/libldap_r.so.2.0.130 libldap.so
rm liblber.so
ln -s /usr/lib32/liblber.so.2.0.130 liblber.so

The plugin needed 32bit libraries not 64bit ones....

Further edit: Funny how you find out things don't work after using them for a while. My video card stopped working (hard lockups) which forced me to install the latest beta nvidia driver (9625). No lockups after that plus sauerbraten and googleearth both work perfectly.

---

### Post by donz on 2006-09-07
Hi!

I posted this on the main part of this list too, but it seems to belong here also.

I am having a problem with g++ [g++ (GCC) 4.0.3 (Ubuntu 4.0.3-1ubuntu5) ] On the 64-bit version of Dapper.

It is very hard to find typos and other errors with error messages like this:

big_file_test.cpp: In function â:
big_file_test.cpp:64: error: invalid conversion from â to â
big_file_test.cpp:64: error: initializing argument 1 of â
big_file_test.cpp:64: error: â was not declared in this scope
/usr/include/stdlib.h:640: error: too few arguments to function â
big_file_test.cpp:69: error: at this point in file
/usr/include/stdlib.h:640: error: too few arguments to function â
big_file_test.cpp:74: error: at this point in file
big_file_test.cpp:77: error: â was not declared in this scope
/usr/include/stdlib.h:640: error: too few arguments to function â
big_file_test.cpp:80: error: at this point in file


I have tried re-installing gcc, but that doesn't help.

The problem only seems to occur with c++ code. It works fine with straight c code.

Has anyone encountered this (and hopefully fixed it)?

Thanks

Donz

P.S.  I have no problems with g++ on a different 32-bit machine, also running DapperDrake.

---

### Post by siiib on 2006-09-25
international charachter set??:-k

---

### Post by kuja on 2006-09-26
With special regards to Skype, copying the qt related files out of that is NOT neccessary in Dapper!

I've done a little bit of testing, with Opera (shared QT), and found that all of those same files you're copying are provided by ia32-libs-kde. This should go for Skype as well. Just thought I'd letcha know.

---

### Post by sarmadzhiev on 2006-09-28
This url for skype is not working (the site seems to be down).

[http://bombazyn.mine.nu/Ubuntu/asound32-qtmt32.tar.bz2]("http://bombazyn.mine.nu/Ubuntu/asound32-qtmt32.tar.bz2")

Any ideas were I can find it?

Thx
Nikolay

---

### Post by kuja on 2006-10-08
That's because the URL for skype is out of date. The link was to the beta, but the final version was released this week.

Edit: Wait a bit, I think I misread something. Then again, why do you need that link anyway? what does it have to do with skype exactly? I don't recall needing such a file when I installed skype anway.

---

### Post by Hendrik van den Boogaard on 2006-10-15
The bombazyn site is up now, it's my home site so I cannot guarantee 24/7 :). I also changed the info about Skype to the final version.

---

### Post by radiobuzzer on 2006-10-25
> **Hendrik van den Boogaard said:**
> [*][SIZE="4"]*Mplayer W32codecs*[/SIZE] - Mplayer works fine, but to use the W32codecs which include WMV9 support, you need to use a 32bit Mplayer with 32bit libraries. A guide how to do this is found in this thread: '[http://www.ubuntuforums.org/showthread.php?t=188974]("http://www.ubuntuforums.org/showthread.php?t=188974")'


A good patch for including Windows Media Video 9 (wmv9) format on 64bit systems (working for Mplayer and VLC) can be found here:

[http://ubuntuforums.org/showthread.php?t=1a0565&highlight=wmv+9+amd64](http://ubuntuforums.org/showthread.php?t=1a0565&highlight=wmv+9+amd64)

if any good guy would consider making a package and spreading it through a repository would be great...

---

### Post by Cynical on 2006-10-26
You don't need to do that anymore. It's built into FFmpeg, so Mplayer and VLC should be able to play it by default now :D

[http://www.mplayerhq.hu/design7/news.html](http://www.mplayerhq.hu/design7/news.html)

---

### Post by kuja on 2006-10-26
The MPlayer in both the Edgy and Dapper repositories, as far as I know, can't handle them. I've heard the VLC in Edgy does though. Sooooooooooo, anyhow, I guess we won't see this problem "fixed" until Feisty eh?

---

### Post by Cynical on 2006-10-26
Just because the packages aren't in the ubuntu repositories does not mean that they haven't been "fixed". :P

---

### Post by kuja on 2006-10-26
I'm aware of this cynical, in fact, I've been running Mplayer from SVN for weeks now.

---

### Post by stevecullen on 2006-11-05
I've been trying to build a MythTV on FC5 but gave up as I couldn't get the TV card (a DVICO Dual DVB) to work. I now have Dapper Drake installed on AMD64 & love it but have a problem when trying to build the drivers. I get the following output from make:
make -C /home/steve/v4l-dvb-rounding/v4l
make[1]: Entering directory `/home/steve/v4l-dvb-rounding/v4l'
scripts/make_makefile.pl /lib/modules/2.6.15-26-amd64-generic/build
File not found: /lib/modules/2.6.15-26-amd64-generic/build/include/linux/autoconf.h at ./scripts/make_kconfig.pl line 27.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/home/steve/v4l-dvb-rounding/v4l'
make: *** [all] Error 2
 
I'm not very unix literate but have verified that the /lib/modules/2.6.15-26-amd64-generic directory doesn't exist. 
My uname output is as follows:
 lizard 2.6.15-26-amd64-generic #1 SMP PREEMPT Thu Aug 3 02:52:35 UTC 2006 x86_64 GNU/Linux

Any help is greatly appreciated.

---

### Post by kleeman on 2006-11-05
Try installing the linux-headers package corresponding to your kernel which looks like 2.6.15-26-amd64-generic. Use synaptic to do it if you are a noob. You may need to reboot as well.

---

### Post by stevecullen on 2006-11-06
Thanks Kleeman, that did it! The card is now visible in dmesg & appears stable in the OS. On FC5 the usb tuner in the DVICO Dual sent the OS crazy, generating bulk 110 messages & generally soaking up the CPU. Thanks again I really appreciate it.

---

### Post by imageburn on 2006-11-15
Hey there, got a simple question, maybe already answered but I sure can't find it. . . I've got edgy installed on my own laptop, Pentium, works like a dream. Setting up Ubuntu here for another person who's AMD64 had a windows registry that was just out of control, and I just don't know anything about *that*. 
So, I ran Kilz' firefox2 install script and everything went great.
But, uhhh, what's the terminal command to run Firefox32? Cuz Firefox64 still runs by default of course.

---

### Post by RFScheer on 2006-11-15
On my setup, just typing 

```
firefox32
```

in the terminal does the trick.  That's launching a script, /usr/local/bin/firefox32, which basically sets up for a firefox session and launches /usr/local/firefox32/firefox.  

Hope it helps.

---

### Post by Kilz on 2006-11-16
> **imageburn said:**
> Hey there, got a simple question, maybe already answered but I sure can't find it. . . I've got edgy installed on my own laptop, Pentium, works like a dream. Setting up Ubuntu here for another person who's AMD64 had a windows registry that was just out of control, and I just don't know anything about *that*. 
So, I ran Kilz' firefox2 install script and everything went great.
But, uhhh, what's the terminal command to run Firefox32? Cuz Firefox64 still runs by default of course.

There should also be a launcher in the menu for Firefox32. Also be aware, that if you have either the 32bit, or the 64bit version open. If you try to launch the other, it will just open a window with the version already running.

---

### Post by bmcage on 2006-11-20
> **imageburn said:**
> Hey there, got a simple question, maybe already answered but I sure can't find it. . . I've got edgy installed on my own laptop, Pentium, works like a dream. Setting up Ubuntu here for another person who's AMD64 had a windows registry that was just out of control, and I just don't know anything about *that*. 
So, I ran Kilz' firefox2 install script and everything went great.
But, uhhh, what's the terminal command to run Firefox32? Cuz Firefox64 still runs by default of course.

DO NOT INSTALL THE AMD64 VERSION!!
If your friend is from the windows world, install the 32bit normal Ubuntu version for him. His windows also was 32bit, and AMD64 runs the old bitcode perfectly.
AMD64 version is ok for people who want to max out their PC, but let's face it, there is still many not supported stuff, especially in the drivers, proprietary things. 
If your friend is not a linux freak, do him a favor, and install the more stable 32 bit version. He will so much more happy that everything just works.

---

### Post by crgutierrez on 2006-11-26
> **Hendrik van den Boogaard said:**
> [SIZE="5"][COLOR="Red"]How to get specific programs to run under Dapper Drake 64-bit edition.[/COLOR][/SIZE]

[SIZE="4"]**Why this thread?**[/SIZE]
Upgrading to a 64-bit Operating System is not an easy process. Things that were 'normal' or 'common' in the 32-bit world are different when using a 64-bit processor and their equivalent 64-bit applications. You might run into some troubles, as we all did :). This thread is here to help you overcome most common problems when switching to Ubuntu 64-bit.

[B][SIZE="3"][COLOR="Navy"]Feel free to add programs, solutions or workarounds.
Since the thread is sticky I will do my best to think of solutions and include all solutions suggested by 64bit pioneers like you![/COLOR][/SIZE][/B]

[SIZE="4"]**Things you might try first**[/SIZE]
When switching to a 64-bit operating system, there are still programs that are not natively compiled for the AMD64 architecture. The first thing you can try, if there is a i386 version available, is to force the program to install using the i386 architecture. For other architectures this does not work (when you for instance try to force to install a SPARC compiled application) but luckily the AMD64 architecture is backwards compatible with i386, so these 32bit applications should run fine. The downside of this is that some calls to libraries might not work and need their 32-bit version as well. If you omit the 'force architecture' option dpkg will tell you:

[I]dpkg: error processing packagename_i386.deb (--install):
 package architecture (i386) does not match system (amd64)[/I]

You can do a forced i386 installation like this:
```

sudo dpkg -i --force-architecture *packagename_i386.deb*

```

Another thing you might try if you already installed an application which does not run, is 'linux32'. This program does not really do anything, except for the fact that if you use it as a wrapper for a program, this program will think the machine type is a i686.

An example of this:
```

hendrik@hendrik:~$ *uname -a*
Linux hendrik 2.6.15-25-amd64-k8 #1 SMP PREEMPT Wed Jun 14 11:39:18 UTC 2006 **x86_64** GNU/Linux
hendrik@hendrik:~$ *linux32 uname -a*
Linux hendrik 2.6.15-25-amd64-k8 #1 SMP PREEMPT Wed Jun 14 11:39:18 UTC 2006 **i686** GNU/Linux


```

[SIZE="4"]**'Native' compiled 64-bit programs that do not seem to work from standard repositories**[/SIZE]
[LIST]
[*][SIZE="4"]*PartImage*[/SIZE] - Partimage thinks a DWORD must be 32bit long, so it fails to start and tells me: '*Error: sizeof(DWORD) != 4 (8)*'. If you try the i386 version it will give an error about libslang.so.2.
[INDENT]**Solution:** Install the standard Ubuntu package and then replace the binary with the statically built version from the PartImage website (so installing the package is only for getting all documentation and other stuff, it's not necessary to get partimage running, therefore you may skip the 'apt-get' line):

```

sudo apt-get install partimage
cd /tmp
wget http://switch.dl.sourceforge.net/sourceforge/partimage/partimage-0.6.4-static.tar.bz2
tar xjf partimage-0.6.4-static.tar.bz2
sudo mv partimage /usr/sbin/

```[/INDENT]
[*][SIZE="4"]*dvd::rip*[/SIZE] - Altough all depenencies are found and installed, dvd::rip keeps on complaining that *all* dependencies are missing. It cannot find transcode and imagemagick, although both were installed automatically with 'apt-get install dvdrip'.
[INDENT]**Solution:** I made the changes to the sourcecode as harro0209 pointed me to in his post in this thread. Made a new ubuntu package with a changed version number so the 'old' Ubuntu version won't overwrite it.
```

sudo apt-get install dvdrip
cd /tmp
wget http://bombazyn.mine.nu/Ubuntu/dvdrip_0.52.5-0.1_amd64.deb
sudo dpkg -i dvdrip_0.52.5-0.1_amd64.deb
rm ~/.dvdriprc &> /dev/null
rm ~/.dvdrip/tc_filter_list &> /dev/null

```[/INDENT]
[/LIST]

[SIZE="4"]**Programs that are not available under Dapper Drakte 64-bit**[/SIZE]
[LIST]
[*][SIZE="4"]*Firefox with plugins like Flash/Java/Realplayer*[/SIZE] - Many 64bit plugins are not available. *Kilz* set up a nice [Howto]("http://www.ubuntuforums.org/showthread.php?t=202537") about running Firefox 32bit in Dapper64 with 32bit plugins.
[INDENT][SIZE="3"]**You might wanna give this a try instead of the stuff listed below (gnash, nspluginwrapper etc)**[/SIZE][/INDENT]
[*][SIZE="4"]*Adobe Acrobat Reader 7*[/SIZE] - There does not seem to be a 64 bit edition of Acrobat Reader at all. Trying to apt-get the package will tell you '*E: Package acroread has no installation candidate*'. [INDENT]**Solution:** get the i386 package and do a forced-architecture installation:
```

sudo apt-get install libstdc++5
cd /tmp
wget ftp://ftp.ubuntu.com/ubuntu/pool/multiverse/a/acroread/acroread_7.0.1-0.0.ubuntu1_i386.deb
sudo dpkg -i --force-architecture acroread_7.0.1-0.0.ubuntu1_i386.deb

```
or use the 'Debianized' version in the Marillat repository, which has a newer version (AcrobatReader 7.0.5) : [ftp://ftp.nerim.net/debian-marillat/pool/main/a/acroread/](ftp://ftp.nerim.net/debian-marillat/pool/main/a/acroread/)
[/INDENT]
[*][SIZE="4"]*Realplayer*[/SIZE] - Only RealPlayer 8 is in the standard Dapper 32 repositories. Installing RealPlayer 10 from the Real website however seems to run fine in Dapper 64. I have not really tested this (if a movie needs RealPlayer, it's probably not worth checking it out ;)). You can download the binary installer from: [http://www.real.com/linux](http://www.real.com/linux)
[*][SIZE="4"]*Java 5.0*[/SIZE] - I haven't tried this myself, there seem to be repositories available and you can download Java 5 from Sun's website, but the mozilla plugin is not available (yet?). You can however stick with 'j2re1.4 - Blackdown Java(TM) 2 Runtime Environment, Standard Edition'. That works fine. 
[*][SIZE="4"]*Flashplayer*[/SIZE] - There is no 64bit version of the flash player available. You can use a 32bit firefox from 'getfirefox.com' and there is a howto available in the Ubuntu Wiki (anyone has a good direct link or howto at hand?).
[INDENT]**Workaround 1:** Try to use the *nspluginwrapper* which makes it possible to use the Macromedia 32bit flash version in 64bit Dapper. 
Follow the [howto]("http://ubuntuforums.org/showthread.php?t=193893&page=3") or see [this thread]("http://ubuntuforums.org/showthread.php?t=160318") for more information.
[/INDENT]

[INDENT]**Workaround 2:** You can use 'gnash' from the RAOF repositories (add these lines to you /etc/apt/sources.list):
```

deb http://ubuntu.moshen.de/ dapper all
deb http://raof.dyndns.org/falcon/ dapper eyecandy flash multimedia mythtv all

```
then do a
```

sudo apt-get install gnash gnash-plugin

```
Note: Gnash cannot handle all Flash movies properly yet and the plugin seems to be enabled in firefox only. If you use the mozilla-suite (like I do) it won't work (has to do with the 'plugins.ini' file, haven't figured out how to solve it yet)
[/INDENT]
[*][SIZE="4"]*Mplayer W32codecs*[/SIZE] - Mplayer works fine, but to use the W32codecs which include WMV9 support, you need to use a 32bit Mplayer with 32bit libraries. A guide how to do this is found in this thread: '[http://www.ubuntuforums.org/showthread.php?t=188974]("http://www.ubuntuforums.org/showthread.php?t=188974")'
[*][SIZE="4"]*Rar*[/SIZE] - There is no AMD64 package available in the standard repositories
[INDENT]**Solution:** Either try my first 'experimental' package (All I did was add 'amd64' to the 'architecture' types in the DEBIAN/control file)
```

sudo apt-get install libstdc++5
cd /tmp
wget http://bombazyn.mine.nu/Ubuntu/rar_3.30-2ubuntu2_amd64.deb
sudo dpkg -i rar_3.30-2ubuntu2_amd64.deb

```
Or use the i386 version:
```

sudo apt-get install libstdc++5
cd /tmp
wget ftp://ftp.ubuntu.com/ubuntu/pool/multiverse/r/rar/rar_3.30-2ubuntu2_i386.deb
sudo dpkg -i --force-architecture rar_3.30-2ubuntu2_i386.deb

```[/INDENT]
[*][SIZE="4"]*Opera*[/SIZE] - Opera is not available in Dapper64. Here's a thread that might help, it mainly says that you need a statically copiled 32bit version of opera: [http://ubuntuforums.org/showthread.php?t=75940](http://ubuntuforums.org/showthread.php?t=75940)
[*][SIZE="4"]*Wine*[/SIZE] - Wine can give you some troubles. Here's a HowTo that might help: [http://www.ubuntuforums.org/showthread.php?t=185557](http://www.ubuntuforums.org/showthread.php?t=185557)
[*][SIZE="4"]*Listen*[/SIZE] - You can use the AMD64 package from the 'Janvitus' repository. More info: [http://ubuntuforums.org/showthread.php?t=196093](http://ubuntuforums.org/showthread.php?t=196093).
[*][SIZE="4"]*Bonfire*[/SIZE] - This package is also in the 'Janvitus' repository.
[*][SIZE="4"]*Matlab 7.0*[/SIZE] - Matlab does not understand the AMD64 architecture. It might tell you: '*matlab: No MATLAB bin directory for this machine architecture. ARCH = glnxa64*'
[INDENT]**Solution:**Use the linux32 wrapper to start Matlab. In my case this looks like this
```

linux32 /usr/local/Matlab7/bin/matlab

```[/INDENT]
[*][SIZE="4"]*Wengophone*[/SIZE] - Users have reported problems with this VOIP application, see [http://ubuntuforums.org/showthread.php?p=1137372](http://ubuntuforums.org/showthread.php?p=1137372) for more info
[*][SIZE="4"]*Skype 1.3*[/SIZE] - You can get the Debian package for skype 1.3 (which can use ALSA) from [this]("http://skype.com/go/getskype-linux-deb") website. When you try to run skype, it may complain about *libasound.so.2* and/or *libqt-mt.so.3*. The trick is to download these libraries and put them in the /usr/lib32 dir. Or just copy the codelines below :). The archive on my site is just a tar.bz2 which includes the actual i386 library files that you need to run Skype. I initially had a problem with my microphone input, but someone else already posted a [strange but working solution]("http://ubuntuforums.org/showthread.php?t=214273").
[INDENT]
```

cd /tmp
wget http://skype.com/go/getskype-linux-deb
sudo dpkg -i --force-architecture skype_debian-1.3.0.53-1_i386.deb
wget http://bombazyn.mine.nu/Ubuntu/asound32-qtmt32.tar.bz2
cd /usr/lib32
sudo tar xjvf /tmp/asound32-qtmt32.tar.bz2

```[/INDENT]
[*][SIZE="4"]*Wine*[/SIZE] - I had this info here before, but somehow it got lost. The link to the Wine HowTo is: [http://www.ubuntuforums.org/showthread.php?t=185557](http://www.ubuntuforums.org/showthread.php?t=185557)
[/LIST]

[SIZE="4"]**Things that do not seem to work when you upgrade from Dapper 32bit to Dapper 64bit**[/SIZE]
[LIST]
[*]Upgrading to [SIZE="4"]*Thunderbird*[/SIZE] in my case made my thunderbird crash upon start. Just setting it up again (with my IMAP mailboxes) works fine.
[*]When using [SIZE="4"]*Mozilla calendar plugin*[/SIZE] (by pressing ctrl-8 in mozilla-suite) it crashes mozilla completely. Removing calendar settings makes the calendar-plugin start again, but after added a caldav calendar it crashes again.
[*]When installing [SIZE="4"]*Revelation,*[/SIZE] it does not seem to work directly. Please re-start X and that seems to solve the problem.
[/LIST]

---
[SIZE="1"](cr)edits:
12 june 2006 - Included info how to get Adobe acrobat running, thanks Conq
12 june 2006 - Thread is sticky now :), will try to maintain the thread with all latest info
12 june 2006 - Added 'Kilz' howto for Wine
12 june 2006 - Found a way to get partimage running
12 june 2006 - JoWilly gave some more helpful insights, added to this topic
13 june 2006 - Added RAR and made AMD64 package for RAR
14 june 2006 - Changed Calendar plugin and Listen information
14 june 2006 - Made new AMD64 package with fix and install instructions, thanks harro0209 for the info
18 june 2006 - Added link to Wine32 Howto, thanks Kilz
21 june 2006 - Added nswrapper info, thanks JoWilly
26 june 2006 - Added Kilz 'Firefox32' howto
05 july 2006 - Traced down the *aMule* and *Listen* problems. I needed nfs-common to support proper file-locking over NFS!
06 july 2006 - Refreshed topic
04 aug 2006 - Added Skype, changed Firefox link (again :S), added Wine (also: again :S)
15 oct 2006 - Long time no see... Changed info about Skype 1.3 beta to Skype 1.3 Final[/SIZE]
I found in 

[http://plugindoc.mozdev.org/linux-amd64.html#nswrapper-install-deb](http://plugindoc.mozdev.org/linux-amd64.html#nswrapper-install-deb)

and want to know if it is true?????

" Note:  nspluginwrapper is apparently included with Ubuntu 6.10 (Edgy Eft), but not installed by default. You can install it using apt-get or synaptic."

---

### Post by LaoLiulaoliu on 2006-11-29
How about ubuntu6.10;)

---

### Post by CyberAngel on 2006-11-29
> **LaoLiulaoliu said:**
> How about ubuntu6.10;)

Everything on this post will work even on edgy ;)

If not, post your problem and someone probably will help help you :D

---

### Post by istrebitjel on 2006-12-04
Thanks for that very helpful thread, Hendrik! :cool: 

A couple of these programs, can also be easily installed using Automatix2
[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu)

Maybe you want to add this note :)

---

### Post by jkroto on 2006-12-08
Don't know if this fits into your how-to, but I did manage to find a way to get Citrix ICA client working on 64-bit Edgy.  I wrote up how I did it [here](http://www.ubuntuforums.org/showthread.php?p=1860514#post1860514).

---

### Post by Unterseeboot_234 on 2006-12-09
I've spent hours going back and forth through the File System heirachy -- /usr/lib --- /opt/ --- on and on trying to get the JAVA_HOME and classpath. The problem is: Sun only makes a 32-bit for half of the SDK; the 32-Bit Swiftfox wants its own java; Synaptic will only install 1.5.0._06. I've got a Symlink to java in _06; javac links to _09 (thank goodness!); webstart, I don't know about, but it works 32-bit. NetBeans works because it slams the whole path to _10 every time it compiles.

Then, I would Synaptic packages that would say they were installed, but either nothing happens or the software was half functional. Yeah, Synaptic says Debian Menu was there, but it wasn't.

So, I tried my hand at "building" from tarballs and .gz. That process would lead me to open up all the repositories on Synaptic. I was downloading C++, pearl, C, more packages, more libraries and getting NOWHERE. There is a wall between connecting much of the stuff out there with GNOME, at least the Ubuntu GNOME. That is where most of the builds fail.

I had un-installed Synaptic Kino because it was missing sound after any edit and tried to build it. Removed the build effort, reinstalled Synaptic Kino and ... WHAT!!!! Debian is working and has added hundreds of Menus. All of the libraries have added a lot of new add-ons. Kino works now (the Synaptic version). My network got totally reconfigured -- I think Samba got added.

Which leads me to opinion. I don't see how any source CAN be built on ubuntu. Drake has a "modern" perl. To build takes RedHat because it has a bunch of legacy libraries (in my opinion).

I couldn't replicate my Kino install if you offered me a million euros.

I think I'll stick with the java JRE :roll: 

But, you know what? I wouldn't have it any other way. 64-bit to a scsi is like a nitro-fueled Porsche.

---

### Post by slicker on 2006-12-09
> **Unterseeboot_234 said:**
> I've spent hours going back and forth through the File System heirachy -- /usr/lib --- /opt/ --- on and on trying to get the JAVA_HOME and classpath. The problem is: Sun only makes a 32-bit for half of the SDK; the 32-Bit Swiftfox wants its own java; Synaptic will only install 1.5.0._06. I've got a Symlink to java in _06; javac links to _09 (thank goodness!); webstart, I don't know about, but it works 32-bit. NetBeans works because it slams the whole path to _10 every time it compiles.


Get rid of the non-free Swiftfox. Install the 32bit Firefox that is on the first page of this thread.

---

### Post by TSP on 2006-12-16
I am thinking install edgy 64 bits all this howto's work on edgy to right? or better go for dapper 64?
BTW what a great post! thanks for all the info : )

---

### Post by CyberAngel on 2006-12-16
> **TSP said:**
> I am thinking install edgy 64 bits all this howto's work on edgy to right? or better go for dapper 64?
BTW what a great post! thanks for all the info : )

Most of these indeed work on edgy too so don`t worry :)
Go on edgy and if you have any problem ask for it and someone will help you ;)

---

### Post by Pinoy915 on 2006-12-18
I installed using the Kilz How-To script and Firefox32bit. Flash Player works but I can't seem to get Java to work. It crashes everytime I go to a Java enabled site. I'm on Edgy AMD64.
Gives me this error: 

carlo@carlo-desktop:~$ firefox32 
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
esd: no process killed
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(firefox-bin:7796): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(firefox-bin:7796): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
(QFA)Talkback error: Can't initialize.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/libpangohack.so.0' from LD_PRELOAD cannot be preloaded: ignored.
current locale is not supported in X11, locale is set to CX locale modifiers are not supported, using defaultINTERNAL ERROR on Browser End: SendRequest: Read of ack failed: 0

System error?:: Success

---

### Post by istrebitjel on 2007-01-15
I'd be interested in getting [VirtualBox]("http://www.virtualbox.org/") to run on 64bit.
Can somebody please tell me if it's possible to run 32bit kernel modules?


```
%sudo dpkg -i --force-architecture VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb 
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 108166 files and directories currently installed.)
Preparing to replace virtualbox 1.3.2-20070114_Ubuntu_edgy (using VirtualBox_1.3.2_Ubuntu_Edgy_x86.deb) ...
Unpacking replacement virtualbox ...
Setting up virtualbox (1.3.2-20070114_Ubuntu_edgy) ...
-e 
Creating group 'vboxusers'. VM users must be member of that group!

Starting VirtualBox kernel moduleFATAL: Error inserting vboxdrv (/lib/modules/2.6.17-10-generic/misc/vboxdrv.ko): Invalid module format
(modprobe vboxdrv failed)...fail!
invoke-rc.d: initscript virtualbox, action "start" failed.
dpkg: error processing virtualbox (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 virtualbox

```

---

### Post by alinuxfan on 2007-01-15
I was reading on vitualbox's website that they are in the process of making 64bit versions for both linux and Windows
Hopefully sooner rather than later...

---

### Post by RAOF on 2007-01-15
> **istrebitjel said:**
> I'd be interested in getting [VirtualBox]("http://www.virtualbox.org/") to run on 64bit.
Can somebody please tell me if it's possible to run 32bit kernel modules?
...

No, it isn't.  The 32/64 bit compatibility layer is way above the kernel-module layer.

---

### Post by pickarooney on 2007-01-18
Any news on a working 32-bit mplayer for Edgy and a corresponding mozilla mplayer plugin so I can view streaming avi/realmedia/quicktime files in Firefox 32 bit?

---

### Post by Unoone on 2007-01-28
It would be nice if there was an extra repository just for 64bit applications.:D

Then we could add it to our sources.list

---

### Post by CyberAngel on 2007-01-28
> **Unoone said:**
> It would be nice if there was an extra repository just for 64bit applications.:D

Then we could add it to our sources.list

There are a few but of course unsupported :)

```
deb http://janvitus.cabspace.com/ubuntu/ edgy-janvitus main-amd64
deb http://ubuntu.moshen.de/ edgy misc multimedia

```

---

### Post by Unoone on 2007-01-28
> **CyberAngel said:**
> There are a few but of course unsupported :)

```
deb http://janvitus.cabspace.com/ubuntu/ edgy-janvitus main-amd64
deb http://ubuntu.moshen.de/ edgy misc multimedia

```

Thanks for posting these!:D

---

### Post by Conq on 2007-01-31
> **pickarooney said:**
> Any news on a working 32-bit mplayer for Edgy and a corresponding mozilla mplayer plugin so I can view streaming avi/realmedia/quicktime files in Firefox 32 bit?

Yes, I have just updated the howto with this package. Enjoy!

---

### Post by adza on 2007-02-04
Hendrick,

     Thanks... great thread! I am a rank n00b @ linux and was having a really bad day trying to get skype working on my first ever install...... not only have i got the program running (thanks to your post), i've actually learnt a little about dependencies and the like while at it... i'm quite excited right now...   :)

---

### Post by babwe on 2007-02-06
anyone know a workaround howto get xchat to work with fish on a 64 pc, running Dapper Drake

---

### Post by CyberAngel on 2007-02-06
> **babwe said:**
> anyone know a workaround howto get xchat to work with fish on a 64 pc, running Dapper Drake

What fish has to do with xchat or other graphical application???
Fish is a protocol for secure file sharing over ssh (Like an scp frontend it seems to me :) )

---

### Post by LostAndFound on 2007-02-08
Hi Hendrick,

Thanks for your valuable post. I just had a question in relation to:
"The downside of this is that some calls to libraries might not work and need their 32-bit version as well."

However, I cannot figure out how to install a specific 32-bit library (I've installed all the ones available). Specifically I wanted to install 'libgtkhtml-2' as I am trying to install 'gyachi' which seems to be available only in 32 bit.

Many thanks for any help

---

### Post by Kilz on 2007-02-08
> **LostAndFound said:**
> Hi Hendrick,

Thanks for your valuable post. I just had a question in relation to:
"The downside of this is that some calls to libraries might not work and need their 32-bit version as well."

However, I cannot figure out how to install a specific 32-bit library (I've installed all the ones available). Specifically I wanted to install 'libgtkhtml-2' as I am trying to install 'gyachi' which seems to be available only in 32 bit.

Many thanks for any help

Here is a link to a page that explains how to install the needed lib's and where they should go. [http://tghc.org/32biton64bit.php](http://tghc.org/32biton64bit.php)

---

### Post by fabertawe on 2007-02-08
> **LostAndFound said:**
> [snip] Specifically I wanted to install 'libgtkhtml-2' as I am trying to install 'gyachi' which seems to be available only in 32 bit.

I made a 64bit Edgy deb of Gyachi which you can get [**here**]("http://www.dpb.org.uk/ubuntu/edgy_6.10/"). There is no chat room voice component or plugins but everything else works (cam, audibles etc).

Paul

---

### Post by Joey French on 2007-02-08
Hello all, need some help.
I have successfully installed Acrobat 7 via the Adobe website, and it views fine. However, I am using firefox32 under Kubuntu edgy 64, and firefox does not open pdfs in mozilla-acroread. The biggest problem is that I cannot print from the new acroread. The print dialog does not show my printer, and even if I add lpr -P or kprinter or anything else, it just hangs. The printer prints fine otherwise. Anyone got any idea how to get acroread to print for me? If not, how do I install a printing acroread under edgy 64?

Thanks, 
Joey French

---

### Post by John Jason Jordan on 2007-02-08
> **Joey French said:**
> Hello all, need some help.
I have successfully installed Acrobat 7 via the Adobe website, and it views fine. However, I am using firefox32 under Kubuntu edgy 64, and firefox does not open pdfs in mozilla-acroread. The biggest problem is that I cannot print from the new acroread. The print dialog does not show my printer, and even if I add lpr -P or kprinter or anything else, it just hangs. The printer prints fine otherwise. Anyone got any idea how to get acroread to print for me? If not, how do I install a printing acroread under edgy 64?
I originally installed Adobe Reader 7.08 for Linux when I had Dapper, and after upgrading to Edgy it still works the same. I don't have any problem printing, except that (as you noted) the print dialog box is not CUPS-aware. Since it doesn't know about CUPS, you have to enter a command line statement. What is weird is that some of the other features on the print dialog box do work; it's just that you have to select the printer with the command.

The only thing that I can think of is that somehow you have the command wrong. For one thing, you must state the name of the printer according to what it is called in CUPS. As an example, one of my printers is named "Laserjet-5Si-(Postscript)" in CUPS. Therefore, to print to it the command is:

lpr -P Laserjet-5Si-(Postscript)
or
lp -d Laserjet-5Si-(Postscript)

You can add optional print parameters at the end of the command if you wish (see man lp or man lpr). The important thing is to name the printer exactly as it is called in CUPS. If even one letter is off nothing will happen. Note, however, that you do not append the filename because Adobe Reader's print function will do that.

---

### Post by Joey French on 2007-02-09
Solved...
I needed to reboot apparently, don't ask me why, as it has been weeks since I last rebooted. Maybe some update caused this to stop working. Any way, for those who have a similiar problem in the future:

Under Kubuntu Edgy, you can install Acrobat per their website installer (7.0.8?) with firefox32. I did "system-wide" and "browser-specific", as well as copied the .so from the Acrobat /intellinux install location to my /firefox32 install folder, just to be SURE. Then, I directed firefox to open in acroread, and in the top right corner (printer) I inserted "kprinter". This kicks me to KJobsviewer, where I just hit "print". There you go- Edgy 64amd with newest Acrobat from Adobe, newest prining options dialog and functional printing (with the default printer).

Beautiful. The only thing better would be a native 64 bit Acrobat in a 64 bit Firefox. Oh well, some day.

Joey French

---

### Post by JoeSchmoe1971 on 2007-02-09
I know people have really been trying here, but the skype problem (call failed, etc) isnt getting any in spite of the install mentioned at the beginning of the post. I'm very much a newbiesothingslike tarball and bash are not much help. I can cut and paste with the best of them, though. Is there a solution by now thats easy enough for simpletons like me?
THanks

---

### Post by Snookered on 2007-02-19
wrong thread, sorry.

---

### Post by John Jason Jordan on 2007-02-26
> **Joey French said:**
> Solved...
Under Kubuntu Edgy, you can install Acrobat per their website installer (7.0.8?) 
There is a website installer? Looked all over, all I can find is an option to download 7.09 tar.gz.

I downloaded AdobeReader_enu-7.0.9-1.i386.tar.gz, unpacked it, and did ./INSTALL from the command line. It seemed to install, but it won't run. All I get is:

jjj@Devil5:~$ acroread
/usr/local/Adobe/Acrobat7.0/Reader/intellinux/bin/acroread: error while loading shared libraries: libgdk_pixbuf_xlib-2.0.so.0: wrong ELF class: ELFCLASS64

I wish there was a .deb file somewhere.

---

### Post by kleeman on 2007-02-27
Get the 386 deb from multiverse and install with

sudo dpkg -i --force-architecture ********.deb

works for me.

---

### Post by John Jason Jordan on 2007-02-27
> **kleeman said:**
> Get the 386 deb from multiverse and install with
sudo dpkg -i --force-architecture ********.deb
works for me.
I already found the .deb here:
[http://ftp.osuosl.org/pub/ubuntu/poo...se/a/acroread/](http://ftp.osuosl.org/pub/ubuntu/poo...se/a/acroread/)
And I installed it with --force-architecture as you said. But when I try to launch it from the menu item nothing happens. Trying from a command line reveals why:

jjj@Devil5:~$ acroread
/usr/lib/Adobe/Acrobat7.0/Reader/intellinux/bin/acroread: error while loading shared libraries: libgdk_pixbuf_xlib-2.0.so.0: wrong ELF class: ELFCLASS64

I also tried using the INSTALL script that came with the 7.09 version from Adobe, and also the 7.08 and 7.01 version. Nothing makes any difference. I still get the libgdk-pixbuf-xlib-2.0.so.0 error message.

I have googled on libgdk-pixbuf and on wrong ELF class. Google finds hundreds of pages referring to these -- a week's worth of reading at least. So far all I have gleaned from them is that "wrong ELF class" has something to do with running 32-bit in a 64-bit OS. And gdk-pixbuf has to do with Gnome. 

I really need Adobe Reader 7.08 or 7.09 because earlier versions cannot handle editable PDF files. I had 7.08 working fine under Dapper amd64. It just broke after upgrading to Edgy.

---

### Post by kleeman on 2007-02-27
do you have libgdk-xbuf like packages installed on your system? I don't. Maybe they are interacting with acroread on your system in a weird way.....

Edit: Actually that library comes from libgtk2.0-0 on my system. Do you have that package installed?

Further edit: I notice that my system has both a 64bit and a 32bit version of that library installed. The 64bit version is in the package I mentioned while the 32bit version (presumably the one needed by acroread) is actually in the package ia32-libs-gtk. Try installing this and see if it helps.....

---

### Post by John Jason Jordan on 2007-02-27
> **kleeman said:**
> do you have libgdk-xbuf like packages installed on your system? I don't. Maybe they are interacting with acroread on your system in a weird way.....

Edit: Actually that library comes from libgtk2.0-0 on my system. Do you have that package installed?

Further edit: I notice that my system has both a 64bit and a 32bit version of that library installed. The 64bit version is in the package I mentioned while the 32bit version (presumably the one needed by acroread) is actually in the package ia32-libs-gtk. Try installing this and see if it helps.....
Hey! That fixed it! I needed ia32-libs-gtk. After I installed it, Acroread opens normally!

Dude, I owe you serious beer!

---

### Post by kleeman on 2007-02-28
> **John Jason Jordan said:**
> Hey! That fixed it! I needed ia32-libs-gtk. After I installed it, Acroread opens normally!

Dude, I owe you serious beer!
No worries mate. Just send Heineken (j/k) :guitar:

---

### Post by geakMonkey on 2007-02-28
I downloaded and installed the Ubuntu 6.06 LTS 64 Bit. How can I tell which packages are for 64 bit and which are for 32 bit? I mean, are there packages for both in the install? How can I tell?

---

### Post by Kilz on 2007-02-28
> **geakMonkey said:**
> I downloaded and installed the Ubuntu 6.06 LTS 64 Bit. How can I tell which packages are for 64 bit and which are for 32 bit? I mean, are there packages for both in the install? How can I tell?

You wont be able to tell. The 32bit applications that are in the repositories (OpenOffice is 32bit in Dapper) are not listed as such. But you may find the need to install some 32bit versions for functionality when dealing with proprietary formats. That isnt done during the install or with synaptic, but manualy by terminal most of the time.

---

### Post by John Jason Jordan on 2007-02-28
> **Kilz said:**
> OpenOffice is 32bit in Dapper)
I did not realize that. Do I assume correctly that the OpenOffice 2.0.4 in the Edgy repositories is 64-bit? Wait ... there is no 64-bit OOo, right?

OOo 2.0.2 worked fine for me on Dapper amd64. After upgradng to Edgy and 2.0.4 I have a raft of problems. I'd like either to go back to 2.0.2 or up to 2.1. I did find amd64 .debs for 2.1 and installed it, but it was even worse than 2.0.4. However, the .debs were not official. Might it be possible to use the Feisty repositories on Edgy in order to get OOo 2.1? Or vice-versa, could I use the Dapper repositories to get 2.0.2?

---

### Post by Kilz on 2007-02-28
> **John Jason Jordan said:**
> I did not realize that. Do I assume correctly that the OpenOffice 2.0.4 in the Edgy repositories is 64-bit? Wait ... there is no 64-bit OOo, right?

OOo 2.0.2 worked fine for me on Dapper amd64. After upgradng to Edgy and 2.0.4 I have a raft of problems. I'd like either to go back to 2.0.2 or up to 2.1. I did find amd64 .debs for 2.1 and installed it, but it was even worse than 2.0.4. However, the .debs were not official. Might it be possible to use the Feisty repositories on Edgy in order to get OOo 2.1? Or vice-versa, could I use the Dapper repositories to get 2.0.2?

Yes the Open office in Edgy is 64bit. Personally I still use Dapper for most things. I recently had to reinstall and didnt even consider Edgy. I have a Feisty partition to test it. But I find that Dapper is very stable, I like Feisty, but its not stable enough for me yet. There is also about 2 years more of patch support left Dapper. Sometimes in Linux its not always best to run the latest thing.

---

### Post by geakMonkey on 2007-03-07
> **Kilz said:**
> You wont be able to tell. The 32bit applications that are in the repositories (OpenOffice is 32bit in Dapper) are not listed as such. But you may find the need to install some 32bit versions for functionality when dealing with proprietary formats. That isnt done during the install or with synaptic, but manualy by terminal most of the time.

From what I can tell from [http://tghc.org/32firefox.php]("http://tghc.org/32firefox.php") the firefox32 is invoked as its own process with its own lib/source/etc? And, that ppl who are using are using it conjunction with firefox for 64bit. Is that what is happening?

Is Ice Weasel a program that can be used instead of Firefox?

---

### Post by geakMonkey on 2007-03-07
BTW Kilz;

It tried out my Java on the [link]("http://www.wildsnake.com/webgame/sso/") from your page. Here is what I got on the Java Console:

Java Plug-in 1.6.0
Using JRE version 1.6.0 Java HotSpot(TM) Client VM
User home directory = /home/myself
network: Loading user-defined proxy configuration ...
network: Done.
network: Loading proxy configuration from Netscape Navigator ...
network: Error reading registry file: /home/myself/.mozilla/appreg
network: Done.
network: Loading browser proxy configuration ...
network: Done.
network: Proxy Configuration: Browser Proxy Configuration


----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
p:   reload proxy configuration
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------

basic: New window ID: 2818fb6
basic: Value of xembed: 1
basic: setWindow: call before applet exists:2818fb6
basic: Referencing classloader: sun.plugin.ClassLoaderInfo@176c74b, refcount=1
basic: Added progress listener: sun.plugin.util.GrayBoxPainter@2808b3
basic: Loading applet ...
basic: Initializing applet ...
basic: Starting applet ...
basic: completed perf rollup
network: Cache entry not found [url: http://www.wildsnake.com/webgame/sso/pinball.jar, version: null]
network: Connecting http://www.wildsnake.com/webgame/sso/pinball.jar with proxy=DIRECT
network: Connecting http://www.wildsnake.com/webgame/sso/pinball.jar with cookie "__utma=22861757.740558625.1173302159.1173302159.1173302159.1; __utmb=22861757; __utmc=22861757; __utmz=22861757.1173302159.1.1.utmccn=(referral)|utmcsr=tghc.org|utmcct=/32firefox.php|utmcmd=referral"
network: Downloading resource: http://www.wildsnake.com/webgame/sso/pinball.jar
	Content-Length: 85,590
	Content-Encoding: null
network: Wrote URL http://www.wildsnake.com/webgame/sso/pinball.jar to File /home/myself/.java/deployment/cache/6.0/39/6a7e8667-24b73b28-temp
network: No certificate info for unsigned JAR file: http://www.wildsnake.com/webgame/sso/pinball.jar
network: Cache entry found [url: http://www.wildsnake.com/webgame/sso/pinball.jar, version: null]
network: No certificate info for unsigned JAR file: http://www.wildsnake.com/webgame/sso/pinball.jar
liveconnect: JavaScript: UniversalBrowserRead enabled
liveconnect: JavaScript: UniversalJavaPermission enabled
liveconnect: JavaScript: UniversalBrowserRead enabled
liveconnect: JavaScript: UniversalJavaPermission enabled
liveconnect: JavaScript: UniversalBrowserRead enabled
liveconnect: JavaScript: UniversalJavaPermission enabled
liveconnect: JavaScript: UniversalBrowserRead enabled
liveconnect: JavaScript: UniversalJavaPermission enabled
liveconnect: JavaScript: UniversalBrowserRead enabled
liveconnect: JavaScript: UniversalJavaPermission enabled
liveconnect: JavaScript: UniversalBrowserRead enabled
liveconnect: JavaScript: UniversalJavaPermission enabled
liveconnect: JavaScript: UniversalBrowserRead enabled
liveconnect: JavaScript: UniversalJavaPermission enabled
network: Cache entry not found [url: http://www.wildsnake.com/webgame/sso/data/pindata.zip, version: null]
network: Connecting http://www.wildsnake.com/webgame/sso/data/pindata.zip with proxy=DIRECT
network: Connecting http://www.wildsnake.com/webgame/sso/data/pindata.zip with cookie "__utma=22861757.740558625.1173302159.1173302159.1173302159.1; __utmb=22861757; __utmc=22861757; __utmz=22861757.1173302159.1.1.utmccn=(referral)|utmcsr=tghc.org|utmcct=/32firefox.php|utmcmd=referral"
network: Downloading resource: http://www.wildsnake.com/webgame/sso/data/pindata.zip
	Content-Length: 488,666
	Content-Encoding: null
network: Wrote URL http://www.wildsnake.com/webgame/sso/data/pindata.zip to File /home/myself/.java/deployment/cache/6.0/0/71c4edc0-23198997-temp
network: Cache entry not found [url: http://www.wildsnake.com/webgame/sso/audio/ball1.au, version: null]
network: Connecting http://www.wildsnake.com/webgame/sso/audio/ball1.au with proxy=DIRECT
network: Connecting http://www.wildsnake.com/webgame/sso/audio/ball1.au with cookie "__utma=22861757.740558625.1173302159.1173302159.1173302159.1; __utmb=22861757; __utmc=22861757; __utmz=22861757.1173302159.1.1.utmccn=(referral)|utmcsr=tghc.org|utmcct=/32firefox.php|utmcmd=referral"
network: Downloading resource: http://www.wildsnake.com/webgame/sso/audio/ball1.au
	Content-Length: 1,581
	Content-Encoding: null
network: Wrote URL http://www.wildsnake.com/webgame/sso/audio/ball1.au to File /home/myself/.java/deployment/cache/6.0/25/4b613559-11c5d5d5-temp
basic: Loaded audio clip: http://www.wildsnake.com/webgame/sso/audio/ball1.au
network: Cache entry not found [url: http://www.wildsnake.com/webgame/sso/audio/ball.au, version: null]
network: Connecting http://www.wildsnake.com/webgame/sso/audio/ball.au with proxy=DIRECT
network: Connecting http://www.wildsnake.com/webgame/sso/audio/ball.au with cookie "__utma=22861757.740558625.1173302159.1173302159.1173302159.1; __utmb=22861757; __utmc=22861757; __utmz=22861757.1173302159.1.1.utmccn=(referral)|utmcsr=tghc.org|utmcct=/32firefox.php|utmcmd=referral"
network: Downloading resource: http://www.wildsnake.com/webgame/sso/audio/ball.au
	Content-Length: 1,942
	Content-Encoding: null
network: Wrote URL http://www.wildsnake.com/webgame/sso/audio/ball.au to File /home/myself/.java/deployment/cache/6.0/16/6e4b46d0-754242e0-temp
basic: Loaded audio clip: http://www.wildsnake.com/webgame/sso/audio/ball.au
network: Cache entry not found [url: http://www.wildsnake.com/webgame/sso/audio/ss007.au, version: null]
network: Connecting http://www.wildsnake.com/webgame/sso/audio/ss007.au with proxy=DIRECT
network: Connecting http://www.wildsnake.com/webgame/sso/audio/ss007.au with cookie "__utma=22861757.740558625.1173302159.1173302159.1173302159.1; __utmb=22861757; __utmc=22861757; __utmz=22861757.1173302159.1.1.utmccn=(referral)|utmcsr=tghc.org|utmcct=/32firefox.php|utmcmd=referral"
network: Downloading resource: http://www.wildsnake.com/webgame/sso/audio/ss007.au
	Content-Length: 1,115
	Content-Encoding: null
network: Wrote URL http://www.wildsnake.com/webgame/sso/audio/ss007.au to File /home/myself/.java/deployment/cache/6.0/56/6e85778-51ed48cd-temp
basic: Loaded audio clip: http://www.wildsnake.com/webgame/sso/audio/ss007.au
network: Cache entry not found [url: http://www.wildsnake.com/webgame/sso/audio/ss008.au, version: null]
network: Connecting http://www.wildsnake.com/webgame/sso/audio/ss008.au with proxy=DIRECT
network: Connecting http://www.wildsnake.com/webgame/sso/audio/ss008.au with cookie "__utma=22861757.740558625.1173302159.1173302159.1173302159.1; __utmb=22861757; __utmc=22861757; __utmz=22861757.1173302159.1.1.utmccn=(referral)|utmcsr=tghc.org|utmcct=/32firefox.php|utmcmd=referral"
network: Downloading resource: http://www.wildsnake.com/webgame/sso/audio/ss008.au
	Content-Length: 1,258
	Content-Encoding: null
network: Wrote URL http://www.wildsnake.com/webgame/sso/audio/ss008.au to File /home/myself/.java/deployment/cache/6.0/30/7740229e-44df34c9-temp
basic: Loaded audio clip: http://www.wildsnake.com/webgame/sso/audio/ss008.au
network: Cache entry not found [url: http://www.wildsnake.com/webgame/sso/audio/ss005.au, version: null]
network: Connecting http://www.wildsnake.com/webgame/sso/audio/ss005.au with proxy=DIRECT
network: Connecting http://www.wildsnake.com/webgame/sso/audio/ss005.au with cookie "__utma=22861757.740558625.1173302159.1173302159.1173302159.1; __utmb=22861757; __utmc=22861757; __utmz=22861757.1173302159.1.1.utmccn=(referral)|utmcsr=tghc.org|utmcct=/32firefox.php|utmcmd=referral"
network: Downloading resource: http://www.wildsnake.com/webgame/sso/audio/ss005.au
	Content-Length: 2,001
	Content-Encoding: null
network: Wrote URL http://www.wildsnake.com/webgame/sso/audio/ss005.au to File /home/myself/.java/deployment/cache/6.0/34/25a9efa2-1c837171-temp
basic: Loaded audio clip: http://www.wildsnake.com/webgame/sso/audio/ss005.au
network: Cache entry not found [url: http://www.wildsnake.com/webgame/sso/audio/ss001.au, version: null]
network: Connecting http://www.wildsnake.com/webgame/sso/audio/ss001.au with proxy=DIRECT
network: Connecting http://www.wildsnake.com/webgame/sso/audio/ss001.au with cookie "__utma=22861757.740558625.1173302159.1173302159.1173302159.1; __utmb=22861757; __utmc=22861757; __utmz=22861757.1173302159.1.1.utmccn=(referral)|utmcsr=tghc.org|utmcct=/32firefox.php|utmcmd=referral"
network: Downloading resource: http://www.wildsnake.com/webgame/sso/audio/ss001.au
	Content-Length: 687
	Content-Encoding: null
network: Wrote URL http://www.wildsnake.com/webgame/sso/audio/ss001.au to File /home/myself/.java/deployment/cache/6.0/30/63a1dcde-1f454835-temp
basic: Loaded audio clip: http://www.wildsnake.com/webgame/sso/audio/ss001.au
network: Cache entry not found [url: http://www.wildsnake.com/webgame/sso/audio/whistle1.au, version: null]
network: Connecting http://www.wildsnake.com/webgame/sso/audio/whistle1.au with proxy=DIRECT
network: Connecting http://www.wildsnake.com/webgame/sso/audio/whistle1.au with cookie "__utma=22861757.740558625.1173302159.1173302159.1173302159.1; __utmb=22861757; __utmc=22861757; __utmz=22861757.1173302159.1.1.utmccn=(referral)|utmcsr=tghc.org|utmcct=/32firefox.php|utmcmd=referral"
network: Downloading resource: http://www.wildsnake.com/webgame/sso/audio/whistle1.au
	Content-Length: 1,278
	Content-Encoding: null
network: Wrote URL http://www.wildsnake.com/webgame/sso/audio/whistle1.au to File /home/myself/.java/deployment/cache/6.0/30/5638f65e-1babfe73-temp
basic: Loaded audio clip: http://www.wildsnake.com/webgame/sso/audio/whistle1.au
network: Cache entry not found [url: http://www.wildsnake.com/webgame/sso/audio/whistle_long.au, version: null]
network: Connecting http://www.wildsnake.com/webgame/sso/audio/whistle_long.au with proxy=DIRECT
network: Connecting http://www.wildsnake.com/webgame/sso/audio/whistle_long.au with cookie "__utma=22861757.740558625.1173302159.1173302159.1173302159.1; __utmb=22861757; __utmc=22861757; __utmz=22861757.1173302159.1.1.utmccn=(referral)|utmcsr=tghc.org|utmcct=/32firefox.php|utmcmd=referral"
network: Downloading resource: http://www.wildsnake.com/webgame/sso/audio/whistle_long.au
	Content-Length: 8,418
	Content-Encoding: null
network: Wrote URL http://www.wildsnake.com/webgame/sso/audio/whistle_long.au to File /home/myself/.java/deployment/cache/6.0/50/63059932-7cb6e259-temp
basic: Loaded audio clip: http://www.wildsnake.com/webgame/sso/audio/whistle_long.au
network: Cache entry not found [url: http://www.wildsnake.com/webgame/sso/audio/whistletripple.au, version: null]
network: Connecting http://www.wildsnake.com/webgame/sso/audio/whistletripple.au with proxy=DIRECT
network: Connecting http://www.wildsnake.com/webgame/sso/audio/whistletripple.au with cookie "__utma=22861757.740558625.1173302159.1173302159.1173302159.1; __utmb=22861757; __utmc=22861757; __utmz=22861757.1173302159.1.1.utmccn=(referral)|utmcsr=tghc.org|utmcct=/32firefox.php|utmcmd=referral"
network: Downloading resource: http://www.wildsnake.com/webgame/sso/audio/whistletripple.au
	Content-Length: 3,879
	Content-Encoding: null
network: Wrote URL http://www.wildsnake.com/webgame/sso/audio/whistletripple.au to File /home/myself/.java/deployment/cache/6.0/24/4df73e58-2d813862-temp
basic: Loaded audio clip: http://www.wildsnake.com/webgame/sso/audio/whistletripple.au
network: Cache entry not found [url: http://www.wildsnake.com/webgame/sso/audio/crowd_1.au, version: null]
network: Connecting http://www.wildsnake.com/webgame/sso/audio/crowd_1.au with proxy=DIRECT
network: Connecting http://www.wildsnake.com/webgame/sso/audio/crowd_1.au with cookie "__utma=22861757.740558625.1173302159.1173302159.1173302159.1; __utmb=22861757; __utmc=22861757; __utmz=22861757.1173302159.1.1.utmccn=(referral)|utmcsr=tghc.org|utmcct=/32firefox.php|utmcmd=referral"
network: Downloading resource: http://www.wildsnake.com/webgame/sso/audio/crowd_1.au
	Content-Length: 26,448
	Content-Encoding: null
network: Wrote URL http://www.wildsnake.com/webgame/sso/audio/crowd_1.au to File /home/myself/.java/deployment/cache/6.0/2/2fa54d82-31090f01-temp
basic: Loaded audio clip: http://www.wildsnake.com/webgame/sso/audio/crowd_1.au
network: Cache entry not found [url: http://www.wildsnake.com/webgame/sso/audio/sp032a.au, version: null]
network: Connecting http://www.wildsnake.com/webgame/sso/audio/sp032a.au with proxy=DIRECT
network: Connecting http://www.wildsnake.com/webgame/sso/audio/sp032a.au with cookie "__utma=22861757.740558625.1173302159.1173302159.1173302159.1; __utmb=22861757; __utmc=22861757; __utmz=22861757.1173302159.1.1.utmccn=(referral)|utmcsr=tghc.org|utmcct=/32firefox.php|utmcmd=referral"
network: Downloading resource: http://www.wildsnake.com/webgame/sso/audio/sp032a.au
	Content-Length: 13,073
	Content-Encoding: null
network: Wrote URL http://www.wildsnake.com/webgame/sso/audio/sp032a.au to File /home/myself/.java/deployment/cache/6.0/13/140d20d-21803585-temp
basic: Loaded audio clip: http://www.wildsnake.com/webgame/sso/audio/sp032a.au
Loading masks 0
Loading masks 2
ReadZBall()
ReadZBuffer()
ReadZSBuffers()
Game Init OK
basic: Stopping applet ...
basic: New window ID: 0
basic: Removed progress listener: sun.plugin.util.GrayBoxPainter@2808b3
basic: Finding information ...
basic: Releasing classloader: sun.plugin.ClassLoaderInfo@176c74b, refcount=0
basic: Caching classloader: sun.plugin.ClassLoaderInfo@176c74b
basic: Current classloader cache size: 1
basic: Done ...
basic: Joining applet thread ...
basic: Destroying applet ...
network: Cache entry not found [url: http://www.wildsnake.com:80/webgame/log.php?gid=sso&t=0&g=0&ms=0&ml=0&data=rounds_0;gOur_0;gOpp_0, version: null]
basic: Disposing applet ...
basic: Quiting applet ...
basic: Joined applet thread ...
network: Connecting http://www.wildsnake.com:80/webgame/log.php?gid=sso&t=0&g=0&ms=0&ml=0&data=rounds_0;gOur_0;gOpp_0 with proxy=DIRECT
Cookie service is not available - use cache to determine "Cookie"
WriteStatistics() OK
Exception in thread "Thread-7" java.lang.NullPointerException
	at pinball.DrawRules(pinball.java:1011)
	at pinball.paint(pinball.java:1307)
	at pinball.repaintQuick(pinball.java:649)
	at pinball.run(pinball.java:2613)
	at java.lang.Thread.run(Thread.java:619)
basic: New window ID: 2829840
basic: Value of xembed: 1
basic: setWindow: call before applet exists:2829840
basic: Referencing classloader: sun.plugin.ClassLoaderInfo@176c74b, refcount=1
basic: Added progress listener: sun.plugin.util.GrayBoxPainter@5d391d
basic: Loading applet ...
basic: Initializing applet ...
basic: Starting applet ...
basic: completed perf rollup
basic: Loaded audio clip: http://www.wildsnake.com/webgame/sso/audio/ball1.au
basic: Loaded audio clip: http://www.wildsnake.com/webgame/sso/audio/ball.au
basic: Loaded audio clip: http://www.wildsnake.com/webgame/sso/audio/ss007.au
basic: Loaded audio clip: http://www.wildsnake.com/webgame/sso/audio/ss008.au
basic: Loaded audio clip: http://www.wildsnake.com/webgame/sso/audio/ss005.au
basic: Loaded audio clip: http://www.wildsnake.com/webgame/sso/audio/ss001.au
basic: Loaded audio clip: http://www.wildsnake.com/webgame/sso/audio/whistle1.au
basic: Loaded audio clip: http://www.wildsnake.com/webgame/sso/audio/whistle_long.au
basic: Loaded audio clip: http://www.wildsnake.com/webgame/sso/audio/whistletripple.au
basic: Loaded audio clip: http://www.wildsnake.com/webgame/sso/audio/crowd_1.au
basic: Loaded audio clip: http://www.wildsnake.com/webgame/sso/audio/sp032a.au
Loading masks 0
Loading masks 2
ReadZBall()
ReadZBuffer()
ReadZSBuffers()
liveconnect: JavaScript: UniversalBrowserRead enabled
liveconnect: JavaScript: UniversalJavaPermission enabled
liveconnect: JavaScript: UniversalBrowserRead enabled
liveconnect: JavaScript: UniversalJavaPermission enabled
Game Init OK

As you can see, the Game Init is OK yet there is an Exception:

Exception in thread "Thread-7" java.lang.NullPointerException
	at pinball.DrawRules(pinball.java:1011)
	at pinball.paint(pinball.java:1307)
	at pinball.repaintQuick(pinball.java:649)
	at pinball.run(pinball.java:2613)
	at java.lang.Thread.run(Thread.java:619)

What is the output supposed to look for Java running correctly?

---

### Post by Kilz on 2007-03-08
> **geakMonkey said:**
> BTW Kilz;

It tried out my Java on the [link]("http://www.wildsnake.com/webgame/sso/") from your page. Here is what I got on the Java Console:

Java Plug-in 1.6.0
Using JRE version 1.6.0 Java HotSpot(TM) Client VM
User home directory = /home/myself
network: Loading user-defined proxy configuration ...
network: Done.
network: Loading proxy configuration from Netscape Navigator ...
network: Error reading registry file: /home/myself/.mozilla/appreg
network: Done.
network: Loading browser proxy configuration ...
network: Done.
network: Proxy Configuration: Browser Proxy Configuration

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~`

What is the output supposed to look for Java running correctly?

Im not really sure, I have never looked at the java console. But my howto uses java 1.5.0, because 1.6.0 is really buggy.

---

### Post by Doctor J on 2007-03-16
> **geakMonkey said:**
> From what I can tell from [http://tghc.org/32firefox.php]("http://tghc.org/32firefox.php") the firefox32 is invoked as its own process with its own lib/source/etc? And, that ppl who are using are using it conjunction with firefox for 64bit. Is that what is happening?

Is Ice Weasel a program that can be used instead of Firefox?

firefox32 is, indeed, its own install wi/ separate libraries.  You will then have different executables for 'firefox' - the 64 bit version, and 'firefox32'.  However, most folks won't ever use the 64 bit version after they have all the 32 bit plugins set up.  Some go so far as to delete the 64 bit version.

iceweasel is another browser built from the firefox source tree.  It doesn't offer any benefits over firefox - the difference is that it has a new license that is considered less restrictive.  firefox is still better supported.

---

### Post by Kilz on 2007-03-16
> **Doctor J said:**
> 
iceweasel is another browser built from the firefox source tree.  It doesn't offer any benefits over firefox - the difference is that it has a new license that is considered less restrictive.  firefox is still better supported.

Yes, and Iceweasel takes out a little bit of proprietary code/graphics that are in Firefox. IMHO its also faster. All extensions that I have tried work for both.

---

### Post by Kernel_Krunch on 2007-04-07
Here is an alternative update for flash install via nspluginwrapper.

```
#versions 04/06/07
wget -v http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-0.9.91.2-1.x86_64.rpm
wget -v http://gwenole.beauchesne.info/projects/nspluginwrapper/files/nspluginwrapper-i386-0.9.91.2-1.x86_64.rpm
wget -v http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
tar -xvf install_flash_player_9_linux.tar.gz
sudo su
```
password
```
apt-get -y install linux32 ia32-libs lib32asound2 ia32-libs-gtk alien
alien -v nspluginwrapper-0.9.91.2-1.x86_64.rpm
alien -v nspluginwrapper-i386-0.9.91.2-1.x86_64.rpm
dpkg -i nspluginwrapper_0.9.91.2-2_amd64.deb
dpkg -i nspluginwrapper-i386_0.9.91.2-2_amd64.deb
nspluginwrapper -i ./install_flash_player_9_linux/libflashplayer.so
rm -dvr install_flash_player_9_linux
rm -v install_flash_player_9_linux.tar.gz
rm -v nspluginwrapper-0.9.91.2-1.x86_64.rpm
rm -v nspluginwrapper-i386-0.9.91.2-1.x86_64.rpm
rm -v nspluginwrapper_0.9.91.2-2_amd64.deb
rm -v nspluginwrapper-i386_0.9.91.2-2_amd64.deb
exit


```

This suddenly became necessary after a reinstall
```
sudo ln -s /usr/lib/mozilla/plugins/npwrapper.so /usr/lib/mozilla-firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla-firefox/plugins/
```
After the reinstall apt-get told me that 'ia32-lib-gtk' was not in the repository and i had to get it from another source...
i swear i just copied the commands to this post after it worked on youtube. sorry for all the edits.

---

### Post by eznet on 2007-04-07
> **Hendrik van den Boogaard said:**
> [SIZE="4"]*PartImage*[/SIZE] - Partimage thinks a DWORD must be 32bit long, so it fails to start and tells me: '*Error: sizeof(DWORD) != 4 (8)*'. If you try the i386 version it will give an error about libslang.so.2.
[INDENT]**Solution:** Install the standard Ubuntu package and then replace the binary with the statically built version from the PartImage website (so installing the package is only for getting all documentation and other stuff, it's not necessary to get partimage running, therefore you may skip the 'apt-get' line):

```

sudo apt-get install partimage
cd /tmp
wget http://switch.dl.sourceforge.net/sourceforge/partimage/partimage-0.6.4-static.tar.bz2
tar xjf partimage-0.6.4-static.tar.bz2
sudo mv partimage /usr/sbin/

```[/INDENT]


Thank you so much for this.  I am running Feisty Fawn 64 bit on my DV6000T (2GHZ Core2Duo) and this worked like a charm!

---

### Post by bow on 2007-04-08
I'm a novice in ubuntu and linux.I don't know whats goin on but can any one help me how to play mp3 , Avi and other common media formats?
I couldn't install essential programs because they were for 32 bit
plz hlp me
:(

---

### Post by tomygun56 on 2007-04-09
Just use Rhythmbox, it comes with gnome.  Applications, Sound&Video.
If you need additional codex, sometimes you do look at this site:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Multimedia_Players_.26_Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Multimedia_Players_.26_Browser_Plug-ins)

---

### Post by Kilz on 2007-04-09
> **bow said:**
> I'm a novice in ubuntu and linux.I don't know whats goin on but can any one help me how to play mp3 , Avi and other common media formats?
I couldn't install essential programs because they were for 32 bit
plz hlp me
:(

Exactly what programs, how did you try and install them, and are they listed on the first post of this topic?

---

### Post by jhouse5266534 on 2007-04-22
running "sudo apt-get install ia32-libs" fixed all my problems.

It's so easy, I recommend trying this when no .deb is available.  

I don't know if it was a dependency of ia32-libs that fixed the problem, but it worked.  I believe that many 32 bit applications will need the ia32 libraries anyway, so just do it first :)

---

### Post by Enverex on 2007-04-25
You have Wine listed twice in the first post and it links to a depreciated and very unsupported method of installing/setting up Wine.

---

### Post by Kilz on 2007-04-25
> **Enverex said:**
> You have Wine listed twice in the first post and it links to a depreciated and very unsupported method of installing/setting up Wine.

If you look at the page it links to, and read and follow the instructions it is still a good method. Since there is no wine deb in the 64bit Ubuntu repositories , any methods are unsupported as the only supported way is with the repositories. But the deb you can download and install is linked to on the wine projects pages.
Let me also add that when the method was found, back when Dapper Drake was released. There was no method to install wine on 64bit

---

### Post by Enverex on 2007-04-25
> **Kilz said:**
> If you look at the page it links to, and read and follow the instructions it is still a good method. Since there is no wine deb in the 64bit Ubuntu repositories , any methods are unsupported as the only supported way is with the repositories. But the deb you can download and install is linked to on the wine projects pages.
Let me also add that when the method was found, back when Dapper Drake was released. There was no method to install wine on 64bit

By unsupported I mean by Wine. Any bug reports, AppDB test data entries or other issues will be invalid (the method I was looking at was the one using old versions of Wine and Sidenet).

---

### Post by Kilz on 2007-04-25
> **Enverex said:**
> By unsupported I mean by Wine. Any bug reports, AppDB test data entries or other issues will be invalid (the method I was looking at was the one using old versions of Wine and Sidenet).

That may be, but the method works for the most part. In fact I just updated it a little today. Exactly what makes it invalid?

---

### Post by Enverex on 2007-04-25
Use of external scripts for installing things and other outside factors such as ies4linux and winetools (as well as Loki installers) makes Wine "impure" so to speak so to cut down on chances of issues being because of these external factors, they are excluded. Tests and bugs are only to be filed with "vanilla" Wine. It "works" for getting it installed but it's still modified from what it should be by default.

Wine either needs to be compiled from source or installed cleanly with a prebuilt package, no third party methods or scripts.

Think of it like Wine is Debian and Ubuntu would be ies4linux. One is based on and heavily uses the other, but there are still key modifications which could, and do cause differences and/or problems.

The supported methods for installing Wine are documented on the WineHQ site anyway in walkthrough format.

---

### Post by Kilz on 2007-04-25
> **Enverex said:**
> Use of external scripts for installing things and other outside factors such as ies4linux and winetools (as well as Loki installers) makes Wine "impure" so to speak so to cut down on chances of issues being because of these external factors, they are excluded. Tests and bugs are only to be filed with "vanilla" Wine. It "works" for getting it installed but it's still modified from what it should be by default.

Wine either needs to be compiled from source or installed cleanly with a prebuilt package, no third party methods or scripts.

Think of it like Wine is Debian and Ubuntu would be ies4linux. One is based on and heavily uses the other, but there are still key modifications which could, and do cause differences and/or problems.

The supported methods for installing Wine are documented on the WineHQ site anyway in walkthrough format.

But the problem is that the [Wine HQ uses an older form]("http://wiki.winehq.org/UbuntuAMD64") of my howto. That they admit [that wine is only for i386.]("http://www.winehq.org/site/download-deb")
Sadly the Ubuntu developers cant even make it work, there is no wine package in the Ubuntu amd64 repo's. 
The older version of the howto no longer works. You will have problems setting it up. Try the "official" page yourself.
At least I am offering a work around to get functionality for 64bit Ubuntu users. When the winehq offers a Ubuntu 64bit .deb file. I will be glad to point the howto directly to it.

---

### Post by Enverex on 2007-04-25
Wine compiled and installed fine for me (Feisty x86_64). So if I can do it I'm pretty sure the packagers can.
That howto you linked to isn't the one that it referred to in general (the WineOn64 is).

Anyway, I'm not saying your method using things doesn't help people (actually a force-arch of the 386 package would be perfectly acceptable, it's using other external things that makes it non-pure) but it's no use to the devs and AppDB/Bugs.

Maybe I should try packaging it, I don't have much time atm though and packaging for Ubuntu/Debian is messy if you're not used to it.

---

### Post by Kilz on 2007-04-25
> **Enverex said:**
> Wine compiled and installed fine for me (Feisty x86_64). So if I can do it I'm pretty sure the packagers can.
That howto you linked to isn't the one that it referred to in general (the WineOn64 is).

Anyway, I'm not saying your method using things doesn't help people (actually a force-arch of the 386 package would be perfectly acceptable, it's using other external things that makes it non-pure) but it's no use to the devs and AppDB/Bugs.

Maybe I should try packaging it, I don't have much time atm though and packaging for Ubuntu/Debian is messy if you're not used to it.

Ill try it to, cant hurt.

---

### Post by dfreer on 2007-04-27
pSX and ZSNES 32-bit programs should work very well in AMD64, .debs can be found in my sig. Might be useful to add to front page.

---

### Post by illbashu on 2007-11-08
i am running gusty and when i try this command i get this 
```
dpkg: requested operation requires superuser privilege
```

can someone plz help me...

---

### Post by CyberAngel on 2007-11-09
> **illbashu said:**
> i am running gusty and when i try this command i get this 
```
dpkg: requested operation requires superuser privilege
```

can someone plz help me...

First of all what is the command are you running?
Probably of the error status you need to run your command using sudo.

Second, why are you posting on that thread and you are not creating a new one?
This one is for specific problems on the 64bit dapper version.

---

### Post by vgrisham on 2007-12-23
[quote=JoWilly;1178397]FYI the acroread 7.08 deb package is in the marillat repos and installs nicely with "dpkg -i --force-architecture" (much better for system consistency and to uninstall apps):

I've just installed Adobe Reader 8, and after reading the license agreement, my computer feels violated and dirty. I'd tried to uninstall using the command "sudo dpkg -r --force-architecture AdobeReader_enu-8.1.1-1.i386.deb", but I get the error message: "dpkg: you must specify packages by their own names, not by quoting the names of the files they come in"

I tried dropping the force architecture part of the command, but I get the same error. 

What is the command to use to remove a program once one has installed via force architecture?

Thanks,
Vaughn

---

### Post by CyberAngel on 2007-12-23
try this one: ```
sudo dpkg -r acroread
```

---

### Post by JoWilly on 2007-12-25
> **vgrisham said:**
> 

I've just installed Adobe Reader 8, and after reading the license agreement, my computer feels violated and dirty. I'd tried to uninstall using the command "sudo dpkg -r --force-architecture AdobeReader_enu-8.1.1-1.i386.deb", but I get the error message: "dpkg: you must specify packages by their own names, not by quoting the names of the files they come in"

I tried dropping the force architecture part of the command, but I get the same error. 

What is the command to use to remove a program once one has installed via force architecture?


Just use the package name, not the file name.

For this package it would be something like "sudo dpkg -r AdobeReader_enu"

---

### Post by radi0j0hn on 2008-01-01
I am frightfully new at this, even though I have been in the DOS/Windows world for 20 years.  I understand the concept of "sudo dpkg -i --force-architecture packagename_i386.deb" where I put in the name of the program to be installed.
 
In my case, I want  kompozer-0.7.10-i386.deb.  The package is on my desktop.  How do I tell  the OS WHERE it is?  I get the error:  error processing kompozer-0.7.10-i386.deb (--install):
 cannot access archive: No such file or directory

Where should I put the package sop it can be found?

TIA

John

---

### Post by ~LoKe on 2008-01-01
> **radi0j0hn said:**
> Where should I put the package sop it can be found?

Put it in your /home/username folder (/home/john, or simply ~/).  That way, you'll open up your terminal and you'll already be in that directory.  Then you can do...
```
sudo dpkg -i --force-architecture kompozer-0.7.10-i386.deb
```
Or, if the file is on your desktop...
```
cd ~/Desktop && sudo dpkg -i --force-architecture kompozer-0.7.10-i386.deb
```
or...
```
sudo dpkg -i --force-architecture ~/Desktop/kompozer-0.7.10-i386.deb
```

---

### Post by Kilz on 2008-01-01
> **radi0j0hn said:**
> I am frightfully new at this, even though I have been in the DOS/Windows world for 20 years.  I understand the concept of "sudo dpkg -i --force-architecture packagename_i386.deb" where I put in the name of the program to be installed.
 
In my case, I want  kompozer-0.7.10-i386.deb.  The package is on my desktop.  How do I tell  the OS WHERE it is?  I get the error:  error processing kompozer-0.7.10-i386.deb (--install):
 cannot access archive: No such file or directory

Where should I put the package sop it can be found?

TIA

John

What version of Ubuntu are you running? Kompozer is in the repos for Feisty, Gutsy, and Hardy. If you are running any of those ```
sudo apt-get install kompozer
``` will install the 64bit version. It will alos recieve automatic updates if there are aly.

---

### Post by vgrisham on 2008-01-01
> **radi0j0hn said:**
> I am frightfully new at this, even though I have been in the DOS/Windows world for 20 years.  I understand the concept of "sudo dpkg -i --force-architecture packagename_i386.deb" where I put in the name of the program to be installed.
 
In my case, I want  kompozer-0.7.10-i386.deb.  The package is on my desktop.  How do I tell  the OS WHERE it is?  I get the error:  error processing kompozer-0.7.10-i386.deb (--install):
 cannot access archive: No such file or directory

Where should I put the package sop it can be found?

TIA

John

John,

Welcome to Ubuntu. If I were you, I'd follow the previous advice to install the 64-bit version from the repositories. In addition to using apt-get from the terminal, Synaptic is another, easier way to go. Go to System>Administration>Synaptic Package Manager. Once there, simply search for Komposer, and you will be able to select and install it easily. Synaptic will then keep track of updates for the package for you.

---

### Post by popatopalous on 2008-03-06
Should this maybe be updated to Gutsy? I'd be real interested in how to get RealPlayer to work in Kubuntu Gutsy x86_64.

---

### Post by Kilz on 2008-03-07
> **popatopalous said:**
> Should this maybe be updated to Gutsy? I'd be real interested in how to get RealPlayer to work in Kubuntu Gutsy x86_64.

The thing is, most of the info including realplayer is still good even for Gutsy. Go download the installer from real.

---

### Post by popatopalous on 2008-03-07
> **Kilz said:**
> The thing is, most of the info including realplayer is still good even for Gutsy. Go download the installer from real.

Thanks. Didn't realize. Perhaps could be better titled? No big deal though. Just good to know.

---

### Post by factotum218 on 2008-03-22
Many thanks for your information. People like you make the 64-bit Linux desktop a bit less of a pain in the **** at the beginning.

---

### Post by yulester on 2008-04-15
""""Nvidia drivers aren't a problem, they are in the repository and more recent versions are downloadable from Nvidia. You do have to install them though, the open-source nv drivers are installed by default."""

I tried that today, but it said It needed to download some kernel items before it did could proceed.

So what do I need to actually get this done?

---

### Post by Sef on 2008-04-26
> I tried that today, but it said It needed to download some kernel items before it did could proceed.

What kernel items need to be downloaded?

---

