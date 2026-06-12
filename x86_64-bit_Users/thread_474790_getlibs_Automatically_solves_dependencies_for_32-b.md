---
title: "getlibs: Automatically solves dependencies for 32-bit programs on 64-bit"
date: 2007-06-15
forum: x86 64-bit Users
---

### Post by Cappy on 2007-06-15
[B]On 64-bit systems it downloads and installs libraries needed for 32-bit programs and 64-bit programs.
On 32-bit systems it downloads and installs libraries needed for 32-bit programs.[/B]
Newest version: 2.06 released on [March 1st, 2008]

Thank you to the following bug reporters: marararam ViRMiN Cabal elanthis BogusJoe NullHead mooball
Thank you to the following Beta Testers: Kilz BogusJoe NullHead
Special thanks to: RavanH

[SIZE="3"]**To install or upgrade:**[/SIZE]

Download getlibs-all from 
[http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/)


[SIZE="3"]**getlibs works on:**[/SIZE]
[LIST][*]All Ubuntu and Debian systems
[*]Debian or Ubuntu based distributions (best to use the package name)
[/LIST]


Tip: To install a 32-bit debian package for a program (not a library!) use 
```
sudo dpkg -i --force-all package_name.deb
```

[SIZE="3"]**Usage Examples:**[/SIZE]

getlibs on a program to download all missing libraries:
```
getlibs /usr/bin/skype
```
-----

Use getlibs to install a 32-bit library using the library name:
```
getlibs -l libogg.so.0 libSDL-1.2.so.0
```
-----

Use getlibs to install a 32-bit library using the package name:
```
getlibs -p libqt4-core libqt4-gui
```
-----

Install a 32-bit library file (.deb):
```
getlibs -i ~/i386_library_1.deb
```
-----

Download and install a 32-bit library file (.deb):
```
getlibs -w http://mirrors.kernel.org/ubuntu/pool/main/s/sdl-image1.2/libsdl-image1.2_1.2.5-3_i386.deb
```
-----

[SIZE="3"]**Other options:**[/SIZE]

--apt-file : Uses apt-file to find the packagenames for libraries. The default uses packages.ubuntu.com. This is especially useful for non-ubuntu users.

--build : converts a 32-bit package to a 64-bit package and installs it. This will only install libraries from a 32-bit package into the correct place! This will not install any binaries from that package! This is very beta.

--savebuild : use with --build. Saves new 64-bit package to /home/$USER

--mirror or -m : Use the specified mirror to download from if one is not specified for package

--verbose : Extra output

--ldconfig  : Runs ldconfig on directories where new libraries are installed

-64 : Will let apt-get install 64-bit packages for a 64-bit system

-32 : Left only for compatibility with getlibs v1. 32-bit library installation is the default for all systems.

--distro : can set as either Ubuntu or Debian. Ubuntu installs to /usr/lib32 and/or /lib32. Debian installs to /emul/ia32-linux/

--release : can set as hardy gutsy feisty edgy or dapper. Determines what web interface release is used in search.

---

### Post by fabertawe on 2007-06-15
> **Cappy said:**
> **What do you guys think? Is this script helpful enough I should improve it?**

Hi Cappy,

sounds like a great idea and something that could be very useful for installing 32bit apps. I just wish I had something to try it out with! I'm sure you'll get some good feedback for this :D

Paul

---

### Post by Kilz on 2007-06-15
A very interesting project. Sounds like something that would make multiarch a reality before the Ubuntu developers do it. For i386 binaries, it installs the 32bit libraries in the correct place? This might stop some new users fubaring their installs by forcing libraries.

---

### Post by ©TriMoon® on 2007-06-15
> **Cappy said:**
> **What do you guys think? Is this script helpful enough that I should improve it?**

Always handy to have support scripts to ease things.
Some tips for change:
1) Dont demand install as root.
2) Rename the script to have .sh extension, only real binaries should have names without extensions.
3) Use sudo and the like to visually ask the user for administrative rights when really needed.

---

### Post by gbesso on 2007-06-15
This is great, Thank you so much!

---

### Post by Cappy on 2007-06-15
> **Kilz said:**
> For i386 binaries, it installs the 32bit libraries in the correct place?

Yes, it does! I commented my code if you would like to take a look.

---

### Post by Cappy on 2007-06-21
I've updated this to version 1.01
New features:
*Built-in support for handling multiple missing libraries
*Cleaned code up, cleaned regex's up
*Added new feature: install libraries using the name
Example:
```

**$ getlibs -64 libogg.so.0 libSDL-1.2.so.0**
Matched library libogg.so.0 to libogg0
Matched library libSDL-1.2.so.0 to libsdl1.2debian-all
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libogg0 is already the newest version.
The following NEW packages will be installed:
  libsdl1.2debian-all
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 213kB of archives.
After unpacking 20.5kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```
This new feature supports non arch downloading, just like the binary (original/main) function.

---

### Post by jusmurph on 2007-06-21
very nice project!

---

### Post by RavanH on 2007-06-23
Thanks, Cappy, for this GREAT script!

I wanted to test the latest Skype and it was not available through Simple64 yet. Searching the forums, I stumbled upon your promising post. And it worked!

FYI: 
After installing getlibs (following your instructions) and downloading the [Skype 1.4.0.74 deb package]("http://skype.com/go/getskype-linux-ubuntu") to my home directory, I installed the latest Skype (32bit architecture) on my AMD64 Ubuntu Feisty by opening a terminal emulation screen and entering ```
sudo dpkg -i --force-architecture skype*.deb
```

Then I entered the command ```
skype
``` which returned the error ```
skype: error while loading shared libraries: libQtDBus.so.4: cannot open shared object file: No such file or directory
```

Then I entered ```
getlibs /usr/bin/skype
``` which returned ```
Matched library libQtCore.so.4 to /feisty/libs/libqt4-core
Matched library libQtDBus.so.4 to /feisty/libs/libqt4-core
Matched library libQtGui.so.4 to /feisty/libs/libqt4-gui
Matched library libQtNetwork.so.4 to /feisty/libs/libqt4-core
Matched library libsigc-2.0.so.0 to /feisty/libs/libsigc++-2.0-0c2a
Libraries have been installed.
```

Then I tried again the command ```
skype
``` which this time returned ```
skype: error while loading shared libraries: libdbus-1.so.3: cannot open shared object file: No such file or directory
```

So again, I ran ```
getlibs /usr/bin/skype
``` which this time returned ```
Matched library libdbus-1.so.3 to /feisty/libs/libdbus-1-3
Libraries have been installed.
```

And for sure, this time the command ```
skype
``` resulted in Skype starting up! 
 :popcorn: 

So again: a big THANKS for this great script. IMHO it should be integrated in Ubuntu's 64bit version ASAP!!! 

--ravan

---

### Post by blindarbalest on 2007-06-24
Thank you very much!  I had already forked up my libraries trying to get the 32 bit dependencies for Skype installed -- fortunately apt-get installed what I needed to get Ubuntu working again.  getlibs worked like a charm, and I'm now chatting happily. :)

---

### Post by Cabal on 2007-06-25
I'm using Kubuntu (yes, I'm not in the correct forum), but I've been struggling with Skype for some time now, and getlibs sounded like a good solution, but it does not seem to be working for me.

```
rafael@cobranca:~$ skype
skype: error while loading shared libraries: libQtDBus.so.4: cannot open shared object file: No such file or directory
rafael@cobranca:~$ getlibs /usr/bin/skype
No match found for libQtCore.so.4
No match found for libQtDBus.so.4
No match found for libQtGui.so.4
No match found for libQtNetwork.so.4
No match found for libsigc-2.0.so.0
```

Am I missing something?

---

### Post by zsouthboy on 2007-06-25
This script should be integrated into all debian based distros, if you are willing to manage that project. It would help linux newbies even more than now!

---

### Post by RavanH on 2007-06-25
> **zsouthboy said:**
> This script should be integrated into all debian based distros, if you are willing to manage that project. It would help linux newbies even more than now!
Hear-hear!

---

### Post by Cappy on 2007-06-25
In the meantime, here is the install for skype: [http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

---

### Post by jw5801 on 2007-06-26
Great script! I've been trying to run ePSXe for a while now, but couldn't find the required 32-bit libraries it needed. The script told me that it "...isn't missing any dependancies!" but when I got it to find the libs that ePSXe told me it was missing it worked like a charm! (I'd copy the error messages here for you, but it's working now so I can't replicate them).

This really should be shipped with the 64-bit distro! It solves alot of hassle.

---

### Post by Cabal on 2007-06-26
Cappy, here's the output:

```
rafael@cobranca:~/Programas$ sh -x /usr/bin/getlibs /usr/bin/skype
+ [ 1 -lt 1 ]
+ [ 1 -gt 1 ]
+ [ 1 -eq 1 ]
+ binaryfile=/usr/bin/skype
+ file /usr/bin/skype
+ grep -c 32-bit
+ isit32bit=1
+ arch
+ architecture=x86_64
+ [ x86_64 = x86_64 ]
+ [ 1 -eq 1 ]
+ download=1
+ ldd /usr/bin/skype
+ grep not found
+ awk {print $1}
+ grep -v ./
+ sed s/+/%2B/g
+ dependencylist=libQtDBus.so.4
libQtGui.so.4
libQtNetwork.so.4
libQtCore.so.4
libsigc-2.0.so.0
+ echo libQtDBus.so.4 libQtGui.so.4 libQtNetwork.so.4 libQtCore.so.4 libsigc-2.0.so.0
+ awk {print $1}
+ libraryneeded=libQtDBus.so.4
+ [ libQtDBus.so.4 =  ]
+ cd /tmp
+ [ -d /tmp/getlibs ]
+ mkdir -m 700 getlibs
+ cd /tmp/getlibs
+ echo libQtDBus.so.4
libQtGui.so.4
libQtNetwork.so.4
libQtCore.so.4
libsigc-2.0.so.0
+ sort liblist.tmp
+ uniq
+ libraries=libQtCore.so.4
libQtDBus.so.4
libQtGui.so.4
libQtNetwork.so.4
libsigc-2.0.so.0
+ rm liblist.tmp
+ libraryneeded=
+ [ 1 -eq 1 ]
+ wget -q -O- http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libQtCore.so.4&searchmode=searchfiles&case=insensiti
ve&version=feisty&arch=i386
+ grep usr/lib/[^/]*[s]*<
+ grep -o "[^<]*"
+ grep -v color:
+ sed s/"//g
+ linktopage2=
+ echo
+ awk {print $1}
+ packagename=
+ [  =  ]
+ echo No match found for libQtCore.so.4
No match found for libQtCore.so.4
+ [ 1 -eq 2 ]
+ [ 1 -eq 1 ]
+ wget -q -O- http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libQtDBus.so.4&searchmode=searchfiles&case=insensiti
ve&version=feisty&arch=i386
+ grep usr/lib/[^/]*[s]*<
+ grep -o "[^<]*"
+ grep -v color:
+ sed s/"//g
+ linktopage2=
+ echo
+ awk {print $1}
+ packagename=
+ [  =  ]
+ echo No match found for libQtDBus.so.4
No match found for libQtDBus.so.4
+ [ 1 -eq 2 ]
+ [ 1 -eq 1 ]
+ wget -q -O- http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libQtGui.so.4&searchmode=searchfiles&case=insensitiv
e&version=feisty&arch=i386
+ grep usr/lib/[^/]*[s]*<
+ grep -o "[^<]*"
+ grep -v color:
+ sed s/"//g
+ linktopage2=
+ echo
+ awk {print $1}
+ packagename=
+ [  =  ]
+ echo No match found for libQtGui.so.4
No match found for libQtGui.so.4
+ [ 1 -eq 2 ]
+ [ 1 -eq 1 ]
+ wget -q -O- http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libQtNetwork.so.4&searchmode=searchfiles&case=insens                                                      itive&version=feisty&arch=i386
+ grep usr/lib/[^/]*[s]*<
+ grep -o "[^<]*"
+ grep -v color:
+ sed s/"//g
+ linktopage2=
+ echo
+ awk {print $1}
+ packagename=
+ [  =  ]
+ echo No match found for libQtNetwork.so.4
No match found for libQtNetwork.so.4
+ [ 1 -eq 2 ]
+ [ 1 -eq 1 ]
+ wget -q -O- http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libsigc-2.0.so.0&searchmode=searchfiles&case=insensi                                                      tive&version=feisty&arch=i386
+ grep usr/lib/[^/]*[s]*<
+ grep -o "[^<]*"
+ grep -v color:
+ sed s/"//g
+ linktopage2=
+ echo
+ awk {print $1}
+ packagename=
+ [  =  ]
+ echo No match found for libsigc-2.0.so.0
No match found for libsigc-2.0.so.0
+ [ 1 -eq 2 ]
+ [ -d /tmp/getlibs/extracted/usr/lib/ ]
+ [  !=  ]
+ sudo rm -rf /tmp/getlibs
```

Oh, maybe I should mention that I couldn't download your script with wget, for some weird reason... and I noticed the command more than once on the script. I'm also behind a proxy here (--proxy-user and --proxy-password did not help me also)

---

### Post by Cabal on 2007-06-26
Ohh great, now it just works, for no special reason at all  :P

Dunno what happened yesterday.

But as a sugestion, maybe you could update your script by adding a prompt for proxy user and password for some users behind proxys, who have no idea how do edit wgetrc and stuff like that.

Not that I'm linux wiz or anything, but it took me a long time to figure out these details when installing Firefox 2.

---

### Post by Cappy on 2007-06-26
I found this too:
```
export http_proxy="http://username:password@proxy.example.com:8080"
```
which can be run before the script to correct the problem.

---

Version 1.02 is now released which includes several bug fixes. 
*There is now a message that says you are running getlibs on a non-binary instead of displaying the "no missing dependancies!" message.

Known remaining bugs:
*Check if there are new dependencies after running.
*Proxy
*It will not solve dependencies that need to be moved to the binary's folder. Such dependencies error out like this: "error while loading shared libraries: **_./_**libraryname.so" (it's the "./" in the front of the library name). The reason that the script doesn't solve this yet is because ldd will always show that library, even if it is actually in the folder. You must find the library - /usr/lib32 if it is a 32-bit binary on a 64-bit system and otherwise in /usr/lib and copy it to the folder with the binary. It may also be necessary to chown $USER:$USER it and/or chmod 755 it.
*Downloads files multiple times in a few packages like the qt

---

### Post by Sockerdrickan on 2007-07-11
Great script.

---

### Post by marararam on 2007-07-13
Hi Cappy,
some remarks on your script:
1) 'give_error' does not give any error message but provides usage info, so it would better be called 'print_usage' or 'usage_info' or something similar
2) construction of $templist could be done in one line without a loop by use of $* or $@ respectively
3) repeated line: architecute=`arch`
4) there is no need to 'sudo' the dpkg -x, works perfectly as normal user
5) all 'rm -rf' can be done without sudo then, too. 
6) maybe 'mktemp' would be of use to create a temporary directory (ensures a unique name)
7) some cleanup on abortion misses, can be done with 'trap' and a function. Somewhere near top of script insert:
--->8---
cleanup () {
	rm -rf $tmp # your temporary dir
}

croak () {
	echo "some error occured" 
	exit 13
}

trap "cleanup" 0 2 3 15

trap "croak" ERR
---8<---

8) great script, got skype 1.4 working.

---

### Post by Cappy on 2007-07-13
1) changed, thanks
2) loop is for some error handling which is in the next version
3) changed, thanks
4/5) changed, thanks
6) changed, thanks didn't know about this command
7) will do -especially needed now with the mktemp, thanks much

---

### Post by Cappy on 2007-07-16
The size of the script more than doubled from the last update. It's grown about three times the size of the first version which was released almost exactly a month ago (June 17th).

Version 1.03:

getlibs will now work with the correct repositories with:
[LIST][*]All Ubuntu: Gutsy, Feisty, Edgy, Dapper, Breezy, Hoary, Warty
[*]All Debian: Sid (unstable), Lenny (testing), Etch (stable), Sarge (oldstable)
[*]Mepis (Using the ubuntu repos)
[*]All debian or ubuntu based 32-bit systems
[*]Probably on other 64-bit debian based systems
[/LIST]

*Fixed every known bug including the "skype" bug where getlibs must be run twice on skype to solve the dependencies.
*Error Handling - Validates ALL user input. Before it would say "All dependencies satisfied" even if you didn't point it at an existing file. Lots and lots of added error handling. Didn't build it in earlier so there could be at least a working program.
*If a library is missing in the folder of the binary getlibs will now tell you.

I wish I had a spicy shrimp ramen bowl; I need to go buy some.

---

### Post by RavanH on 2007-07-16
I've got your previous version running, and very happy with it :)

So do I update to the latest by way of ```
cd /tmp
wget -q http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs
chmod +x getlibs
sudo mv getlibs /usr/bin
cd ~
``` as if it is a new install? Or will that break anything?

---

### Post by Cappy on 2007-07-16
Good question. Yes, if you run that code again you will upgrade getlibs. I'll change the first page to say this; Thanks.

Thanks for mentioning getlibs on the skype forums too. A few people seem to have gotten help from that.

---

### Post by RavanH on 2007-07-16
> **Cappy said:**
> Thanks for mentioning getlibs on the skype forums too. A few people seem to have gotten help from that.
No, thank *you* for such an excellent script. Good scripts that are not in the repositories yet deserve word-of-mouth promotion :)

---

### Post by SpikeLee on 2007-07-17
Erreurs étranges...
Lorsque je lance le script, j'ai un affichage mal formaté et rien ne marche :
```

~$ getlibs /usr/bin/skype
Matched library libQtCore.so.4 to http://packages.debian.org/unstable/libs/libqt4-core
Matched library libQtDBus.so.4 to http://packages.debian.org/unstable/libs/libqt4-core
Matched library libQtGui.so.4 to http://packages.debian.org/unstable/libs/libqt4-gui
Matched library libQtNetwork.so.4 to http://packages.debian.org/unstable/libs/libqt4-core
Matched library libsigc-2.0.so.0 to http://packages.debian.org/unstable/libs/libsigc++-2.0-0c2a
The following i386 libraries will be installed:\nhttp://packages.debian.org/unstable/libs/libqt4-core\nhttp://packages.debian.org/unstable/libs/libqt4-core\nhttp://packages.debian.org/unstable/libs/libqt4-gui\nhttp://packages.debian.org/unstable/libs/libqt4-core\nhttp://packages.debian.org/unstable/libs/libsigc++-2.0-0c2a
Continue? (y/n) y
Downloading.dpkg-deb: impossible de lire l'archive « /tmp/getlibs.JaCSc29007/\n\n\n\n\n »: Aucun fichier ou répertoire de ce type
Installing libraries ...
cp: ne peut évaluer `/tmp/getlibs.JaCSc29007/extracted/*': Aucun fichier ou répertoire de ce type
New depedencies have been detected:
libQtDBus.so.4
Matched library libQtDBus.so.4 to http://packages.debian.org/unstable/libs/libqt4-core
The following i386 libraries will be installed:\nhttp://packages.debian.org/unstable/libs/libqt4-core
Continue? (y/n)

```

Le problème d'affichage se résouds en remplaçant les *echo* par des *echo -e*, mais par contre, cela ne fonctionne toujours pas :

```
Continue? (y/n) y
DownloadingInstalling libraries ...
cp: ne peut évaluer `/tmp/getlibs.VMXUk14751/extracted/*': Aucun fichier ou répertoire de ce type
New depedencies have been detected:
libQtDBus.so.4

```

Une idée ?

---

### Post by Cappy on 2007-07-17
Hi, the error was mine because the packages.debian.org had a little different syntax on the packages.ubuntu.com. For instance, "i386" shows up once on an ubuntu package but debian also has a "hurt i386". Try with the new script. 
As for the echo -e, the "sh" shell the program is running in does not have the "echo -e" function and is automatically set to do so. It may be different on your sh shell but it doesn't look like it is disrupting the script.

---
[http://www.google.com/language_tools](http://www.google.com/language_tools)

	Bonjour, l'erreur était la mienne parce que packages.debian.org a eu une peu de syntaxe différente sur packages.ubuntu.com. Par exemple, « i386 » apparaît une fois sur un paquet d'ubuntu mais debian a également « un i386 blessé ». Essai avec le nouveau manuscrit. 
Quant à l'écho - e, la coquille « SH » que le programme fonctionne dedans n'a pas « écho - la fonction d'e » et est automatiquement placé pour faire ainsi. Elle peut être différente sur votre coquille SH mais elle ne regarde pas comme elle perturbe le manuscrit.

---

### Post by SpikeLee on 2007-07-18
Hi ! 

Fisrt of all, sorry for speaking French, I was on French forums before, and I forgot to switch in English :oops:

Secondly, thank you very much, this script works perfectly. However, I had to replace again all the "echo" by "echo -e".  The shell I use is shell bash
I think you can leave it like that, it doesn't matter for the other shell. and it shouldn't give an error.

Nice job cappy:wink:

---

### Post by Cappy on 2007-07-18
Iif you are running debian the script now sets
```
shopt -s xpg_echo
```
which makes echo recognize special characters. For a second there I was worried that I was going to have to go through and replace the lines with echo with something else.
I just tested this on a virtualbox debian and it looks like it is working well =)

I also noticed that debian can't use sudo by default? I guess that means that most people will be using getlibs as root on debian.

---

### Post by SpikeLee on 2007-07-18
Thanx for the tips ;)

Indeed, I'm running a debian distribution, and I had to run this scrpit as root even if I have sudo on  my machine. Don't know why. It should have worked, but...
Anyway, everything is working good now ;)

---

### Post by mrpurple on 2007-08-01
hi thank You for the script. it resolve all my problem.
now i'm asking what i have to do for an update as soon there is a new version of skype ?
thank to help  a really newby.

---

### Post by Cappy on 2007-08-01
You will just need to re-install skype -
download the new ubuntu skype .deb file and if you are running 64-bit
```
sudo dpkg -i --force-architecture skype-*.deb
```
Just like you did the first time. You probably won't need to use getlibs again after re-installing unless they add a new 32-bit library (you will get an error when you launch "skype" from the terminal if you do)

---

### Post by Cappy on 2007-08-02
New version 1.04:
No new features.
Some bug fixes and added flexibility when parsing the webpages so that it will work on situation where my preferred mirror, mirrors.kernel.org, is not available.
Some more error messages, for instance, if someone tries to install libGL.so.1 which can only be installed by the right video drivers.

The code is now released under the "DO WHAT THE **** YOU WANT TO PUBLIC LICENSE" which allows you to basically do anything you want with the code including copy parts of it for your own scripts, modify it, sell it, etc.

---

### Post by nickdjones on 2007-08-04
first up, thanks, this thread has provided the most progress out of anything I've come across, when coupled with your other thread on installing Skype [http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295). These 2 threads should be promoted top/foremost on skype and other forums as THE ones to watch.

Now for my issues .. I made it almost all the way to the end of your AMD64 Skype install instructions on a fresh install of Ubuntu 7.04 Feisty .. but failed at this 2nd to last one:
```

sudo dpkg -i --force-architecture skype-*.deb
```
which looked like this when run:

```
sudo dpkg -i --force-architecture skype-*.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 105121 files and directories currently installed.)
Preparing to replace skype 1.4.0.94-1 (using skype-debian_1.4.0.94-1_i386.deb) ...
Unpacking replacement skype ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqt4-core (>= 4.2.1); however:
  Package libqt4-core is not installed.
 skype depends on libqt4-gui (>= 4.2.1); however:
  Package libqt4-gui is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype

```

which is when I found the wonderful getlibs script, installed it, and ran it, with the following output:

```
getlibs /usr/bin/skype
This application isn't missing any dependencies

```

so, how bout installing each .so manually, thinking I'm pretty smart i proceeded to run:

```
getlibs -32 libQTCore.so.4
Matched library libQTCore.so.4 to /feisty/libs/libqt4-core
The following i386 libraries will be installed:
/feisty/libs/libqt4-core
Continue? (y/n) y
Downloading. Installing libraries ...

```
for each of
```

libQtCore.so.4
libQtDBus.so.4
libQtGui.so.4
libQtNetwork.so.4
libsigc-2.0.so.0
```
thinking I was pretty smart! Taking a browser around (which I did later, but is worth noting here), these libs seemed to have been istalled within the skype install directory, which is perhaps the issue I need to resolve, but I haven't found any info telling me whereelse to put them.. any advice on this one appreciated:

```
~/skypebetainstall/libqt/
```

Now, I thought, back to that 2nd to last line and get back on track.. 

```
 sudo dpkg -i --force-architecture skype-*.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 105121 files and directories currently installed.)
Preparing to replace skype 1.4.0.94-1 (using skype-debian_1.4.0.94-1_i386.deb) ...
Unpacking replacement skype ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqt4-core (>= 4.2.1); however:
  Package libqt4-core is not installed.
 skype depends on libqt4-gui (>= 4.2.1); however:
  Package libqt4-gui is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype
```

hmmm... perhaps not.. and for good measure (really desperate not sure what to do actions of a lost man!).. 

```
getlibs /usr/bin/skype
This application isn't missing any dependencies
```

so. what next.. ah, your post here [http://ubuntuforums.org/showpost.php?p=2912896&postcount=14](http://ubuntuforums.org/showpost.php?p=2912896&postcount=14) talks about getting some debug information from your install script.. nice touch btw. so here it is:

```
sh -x /usr/bin/getlibs /usr/bin/skype
+ trap clean_up_err 1 2 3 13 15
+ trap clean_up 0
+ PATH=/usr/bin:/bin:/sbin:/usr/sbin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
+ export PATH
+ mktemp -d /tmp/getlibs.XXXXXXXXXX
+ clean_up_err
+ rm -rf
+ exit 1
+ tempdir=/tmp/getlibs.cFQFXP4403
+ [ 1 -lt 1 ]
+ echo x
+ grep x
+ [ x ]
+ debugon=1
+ arch
+ architecture=x86_64
+ lsb_release -c
+ grep -o [[:alnum:]]*$
+ releaseinput=feisty
+ distroname=feisty
+ set_site_ubuntu
+ sitetouse=http://packages.ubuntu.com
+ [ http://packages.ubuntu.com = http://packages.debian.org ]
+ [ x86_64 = x86_64 ]
+ [ http://packages.ubuntu.com = http://packages.debian.org ]
+ [ x86_64 = x86_64 ]
+ [ http://packages.ubuntu.com = http://packages.ubuntu.com ]
+ [ ! -e /usr/lib32/libGLU.so.1 ]
+ [ 1 -gt 1 ]
+ binaryfile=/usr/bin/skype
+ [ ! -f /usr/bin/skype ]
+ [ ! -r /usr/bin/skype ]
+ file /usr/bin/skype
+ grep ELF
+ [ -z /usr/bin/skype: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.4.1, dynamically linked (uses shared libs), stripped ]
+ file /usr/bin/skype
+ grep 32-bit
+ isit32bit=/usr/bin/skype: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.4.1, dynamically linked (uses shared libs), stripped
+ file /usr/bin/skype
+ grep 64-bit
+ isit64bit=
+ [ x86_64 = x86_64 ]
+ [ /usr/bin/skype: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.4.1, dynamically linked (uses shared libs), stripped ]
+ nativedownload=0
+ dirname /usr/bin/skype
+ clean_up_err
+ rm -rf /tmp/getlibs.cFQFXP4403
+ exit 1
+ cd /usr/bin
+ basename /usr/bin/skype
+ binaryfile=skype
+ ldd skype
+ grep not found
+ awk {print $1}
+ sed s/+/%2B/g
+ dependencylist=
+ echo 
+ grep \./
+ sed s/\.\///g
+ neededlocallibraries=
+ [  ]
+ echo 
+ grep -v ./
+ dependencylist=
+ echo 
+ grep [[:alpha:]]
+ [ -z  ]
+ echo This application isn't missing any dependencies
This application isn't missing any dependencies
+ exit
+ clean_up
+ rm -rf /tmp/getlibs.cFQFXP4403

```

and thats it.. as far as i've come so far. I think I might need to move my QT4 files somewhere, and then complete your install script.. but just not sure where to.. any help appreciated!

---

### Post by Cappy on 2007-08-04
Hi, try
```
sudo dpkg -i --force-all skype-*.deb
```
and it will install.
If it doesn't run THEN use getlibs:
```
sudo getlibs /usr/bin/skype
```

(you are running getlibs on your old skype install)
I can see how that is confusing, I'll see about making that clear somewhere.

---

### Post by nickdjones on 2007-08-04
Thanks Cappy, I found the other packages script here [http://ubuntuforums.org/showthread.php?t=449551](http://ubuntuforums.org/showthread.php?t=449551) which seems to have worked, albeit it gave me some confusing output while going through the install, which I've noted here [http://ubuntuforums.org/showthread.php?p=3135060#post3135060](http://ubuntuforums.org/showthread.php?p=3135060#post3135060).

I haven't run your suggestions since Skype is now working, so sorry if I can't report whether they finally worked for me.

thanks ! Nick

---

### Post by Ran.Rutenberg on 2007-08-13
Keep on the good work...

This script solved all the problems I had with Skype on my machine.

Thanks,
Ran Rutenberg

---

### Post by mrpurple on 2007-08-17
dear upgrading to the last skype versione i obtaing this error :

 sudo dpkg -i --force-all skype-*.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 135873 files and directories currently installed.)
Preparing to replace skype 1.4.0.94-1 (using skype-debian_1.4.0.99-1_i386.deb) ...
Unpacking replacement skype ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing skype-debian_1.4.0.99-1_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/skype/sounds/CallRingingOut.wav')
Errors were encountered while processing:
 skype-debian_1.4.0.99-1_i386.deb

so do You have a solution for that ?

---

### Post by Cappy on 2007-08-17
That means you need to redownload the .deb file because it did not finish downloading.

Also ... I just uploaded 1.05. Not much in it. Fixed an error I came across today where getlibs wouldn't extract a debian under weird circumstances. Fixed a parsing problem for non-english users.

---

### Post by TechZilla on 2007-08-28
was going to do all the 32-bit dependancy crap for skype, but this script did that whore for me....HUGE appreciation man. now this process is even easier :KS

HUGE PROPS on a well done. highly usfull script

---

### Post by tekhawk on 2007-09-03
:guitar: thank you ive been using opensuse for past year just moving to ubuntu but these forums and stuff like this app are making it easy

---

### Post by ViRMiN on 2007-09-12
Cappy

Thanks for sharing your script.  Having battled this afternoon trying to get Skype up and running on my new x64 machine with a fresh install of Feisty and then upgraded to Gutsy, I've found a change required:

Line 122: architecture = `uname -m`

The /bin/arch binary is not there, and has been "replaced" with 'uname -a'; or so I read.  Either way, making that one change to your script got Skype up and running!!!  Cheers!!!

---

### Post by Cappy on 2007-09-12
Thank you for the information. I will make the change asap (aka when I'm done with my CS project that is due tonight).

---

### Post by jeskuruvilla on 2007-09-12
Hi folks,

I cant seem to get skype installed on my intel centrino duo  processor. I am forced to accept amd64 as the architecture. while trying to install skype I get

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ia32-libs: Depends: lib32stdc++6 but it is not going to be installed
             Depends: lib32gcc1 but it is not going to be installed
             Depends: lib32z1 but it is not going to be installed
             Depends: libc6-i386 but it is not going to be installed
E: Broken packages

All of this started with an attempt to install pidgin and the command that caused the removal of the above libs was $ sudo apt-get install -f
How can this be undone? The usr folder shows the presence of both lib32 and lib64 folders.
Forcing the architecture on the 32 bit programs does not help. Any pointers would be appreciated.

---

### Post by martsie on 2007-09-13
This has worked perfectly for me. 

(K)Ubuntu 7.04

[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

---

### Post by terry98 on 2007-09-13
OMG... i'm using Ubuntu Feisty 64bit and i tried installing acetoneiso for gnome but it failed on a library that i already had, but then i ran the getlibs script and it downloades again what it needed and worked normally... 

Great job on "getlibs"......


Another step to making Linux more user friendly....:grin:

---

### Post by malachias on 2007-09-22
I love you Cappy and I want you to know that.

---

### Post by RavanH on 2007-09-24
> **ViRMiN said:**
> Cappy

Thanks for sharing your script.  Having battled this afternoon trying to get Skype up and running on my new x64 machine with a fresh install of Feisty and then upgraded to Gutsy, I've found a change required:

Line 122: architecture = `uname -m`

The /bin/arch binary is not there, and has been "replaced" with 'uname -a'; or so I read.  Either way, making that one change to your script got Skype up and running!!!  Cheers!!!

On a fresh Gutsy install, this did indeed make getlibs work... 
1. in terminal: sudo gedit /usr/bin/getlibs
2. Search > Go to > line 122
3. replace 'arch' with 'uname -m'

Thanks ViRMiN and Cappy!

---

### Post by Cappy on 2007-09-24
Getlibs has been updated now, thanks.

---

### Post by GSF1200S on 2007-09-28
Oh my god, dude.. you dont know how much easier youve made my KDE life. It sucks having to find each dependency with apt because a deb package is made for (gnome) ubuntu. Good stuff..

---

### Post by bouncingmolar on 2007-09-30
I know this isn't a debian forum, but I have a problem using it on debian sid amd64 (i think thats what i've got). What am I missing?

```

# getlibs /usr/bin/skype
No match found for package libQtCore.so.4
No match found for package libQtDBus.so.4
No match found for package libQtGui.so.4
No match found for package libQtNetwork.so.4
No match found for package libsigc-2.0.so.0
No libraries to download. 
```

and

```
getlibs -32 libQtCore.so.4
No match found for package libQtCore.so.4
No libraries to download.
```
:confused:

---

### Post by Cappy on 2007-09-30
I just looked and debian changed their web package interface so that is why getlibs isn't working on it. The script worked for debian because both the ubuntu and debian used the same interface. 

Also they changed the template so a grep won't work so I would need to write a multi-line awk regex to find what package to download. I won't be able to update the script for the new interface for at least a week.

There is a guide on how to do it manually on debian here:
[http://www.debian-administration.org/articles/531](http://www.debian-administration.org/articles/531)

Alternatively, you can change getlibs to think you are a Debian Gutsy but of course you would be installing ubuntu libraries.

---

### Post by plutino on 2007-10-02
great script, it saved me from abandon my old plotting software which requires 32-bit tcl/tk.  Thank you.

---

### Post by Luciferion on 2007-10-08
This is really great and useful tool. Thank You for that !!

---

### Post by DaveTheAve on 2007-10-09
> david@Devlon:~$ skype
skype: error while loading shared libraries: libQtDBus.so.4: cannot open shared object file: No such file or directory
david@Devlon:~$ whereis skype
skype: /usr/bin/skype /usr/X11R6/bin/skype /usr/bin/X11/skype /usr/share/skype

david@Devlon:~$ getlibs /usr/bin/skype
Matched library libQtCore.so.4 to /feisty/libs/libqt4-core
Matched library libQtDBus.so.4 to /feisty/libs/libqt4-core
Matched library libQtGui.so.4 to /feisty/libs/libqt4-gui
Matched library libQtNetwork.so.4 to /feisty/libs/libqt4-core
Matched library libsigc-2.0.so.0 to /feisty/libs/libsigc++-2.0-0c2a
The following i386 libraries will be installed:
/feisty/libs/libqt4-core
/feisty/libs/libqt4-gui
/feisty/libs/libsigc++-2.0-0c2a
Continue? (y/n) y
Downloading... Installing libraries ...
New depedencies have been detected:
libdbus-1.so.3
Matched library libdbus-1.so.3 to /feisty/libs/libdbus-1-3
The following i386 libraries will be installed:
/feisty/libs/libdbus-1-3
Continue? (y/n) y
Downloading. Installing libraries ...

david@Devlon:~$ skype
(Skype works!)


One thing I would change however is when i pressed enter without pressing Y (assuming it would default), it aborted the program and why the need to ask to continue twice? I understand it needs more dependancys but I already gave the program my permission.

++$happyUbuntuUser;

---

### Post by esdaniel on 2007-10-10
Thank you, great work!

---

### Post by tonywhelan on 2007-10-19
Cappy, have just installed getlibs and Skype on my new Ubuntu Gutsy installation, your script was very helpful!

---

### Post by Cappy on 2007-10-19
> **DaveTheAve said:**
> One thing I would change however is when i pressed enter without pressing Y (assuming it would default), it aborted the program and why the need to ask to continue twice? I understand it needs more dependancys but I already gave the program my permission.

++$happyUbuntuUser;

Thank you for the UI suggestions Dave.

---

### Post by malachias on 2007-10-21
If you use this wonderful script you'll probably notice it stops working in Gusty, giving an error for 'arch' on line 119. Actually the problem's on line 122: `arch` is no longer a valid command. The quick fix for this is to manually set the value of architecture in the script. I run 64 bit Ubuntu, so I just changed the line to read:
architecture="x86_64";

If you use a powerpc, set it to "ppc". If you use 32 bit ubuntu, as far as I can tell you should just set it to any value that isn't "x86_64" or "ppc" (i.e. "i386", or even "omghi" should work).

---

### Post by Cappy on 2007-10-21
I fixed that Gutsy bug a few weeks ago (thanks to ViRMiN!). Just as proof I'm running Gutsy and it works:
```

$ sudo getlibs /usr/bin/skype
Matched library libdbus-1.so.3 to /gutsy/libs/libdbus-1-3
The following i386 libraries will be installed:
/gutsy/libs/libdbus-1-3
Continue? (y/n) y
Downloading. Installing libraries ...

```
Please update to the newest version.

As for a ppc .. getlibs would try to apt-get install the missing libraries (Just saying it doesn't add much functionality).

---

### Post by drtvasudevan on 2007-10-25
another word of appreciation from here!
thanks a million!
tv
ubuntu 7.10 intel dual core duo

---

### Post by jaybombalous on 2007-10-27
Hands down one of the best and most useful scripts for a 64 bit arch system yet. Of course, ironically this had to be one of the first things I installed and it worked so well for me to get skype up and running.

I can see it being a lot more useful, I vote for this to make it into the official supported software repos. Its works just that good...

---

### Post by paulmac on 2007-10-27
Thank you for the link that installed this program.  seems like 90% of the time when I cut and paste in terminal it does not work.  thank you for the sane and easy install of the program.

---

### Post by RavanH on 2007-10-27
Has anyone tested getlibs on [cairo-dock]("https://developer.berlios.de/projects/cairo-dock/") yet?

I recently installed [cairo-dock 32bit version 1.3.8]("https://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=13619") with "dpkg -i --force-architecture" and then did all the missing dependancies manually (see [https://developer.berlios.de/forum/message.php?msg_id=40418](https://developer.berlios.de/forum/message.php?msg_id=40418)). 

Now I see that the new getlibs works on Gutsy, but am hesitant to remove all the manually installed libs from my system to go and test getlibs on /usr/bin/cairo-dock ...

Anyone willing to test? If it works, installation of cairo-dock will have become very easy on AMD64... and a lot of people will have a very nice and functional piece of eye candy at their disposal :)

--ravan

---

### Post by Cappy on 2007-10-27
Getlibs will be able to but I'm not able to download the 32-bit deb file.
[http://prdownload.berlios.de/cairo-dock/cairo-dock_v1.3.8.1_i686-32bits.deb](http://prdownload.berlios.de/cairo-dock/cairo-dock_v1.3.8.1_i686-32bits.deb)
The link is broken.

If running getlibs on the binary doesn't work then you can always use the getlibs -32 way.

---

### Post by Vesa Paatero on 2007-10-30
Thanks, Cappy, the script worked great!

When I tried to install missing 32-bit libraries for Skype myself, the 32-bit libs seemed to overwrite the corresponding 64-bit ones (for libsigc++, at least), but your script puts them in a dedicated place to avoid that.

I'm glad I found your script before trying to make a 32-bit chroot area or implement some other complicated scheme. :-)

Vesa

---

### Post by Cappy on 2007-10-30
Cairo-dock works fine for me.

Here is it working:
```

**~/Desktop$ sudo dpkg --force-all -i cairo-dock_v1.3.8.1_i686-32bits.deb **
[sudo] password for cappy:
Selecting previously deselected package cairo-dock.
(Reading database ... 162800 files and directories currently installed.)
Unpacking cairo-dock (from cairo-dock_v1.3.8.1_i686-32bits.deb) ...
dpkg: cairo-dock: dependency problems, but configuring anyway as you request:
 cairo-dock depends on libglitz-glx1; however:
  Package libglitz-glx1 is not installed.
Setting up cairo-dock (1.3.8) ...
**cappy:~/Desktop$ whereis cairo-dock**
cairo-dock: /usr/bin/cairo-dock /usr/share/cairo-dock
**cappy:~/Desktop$ sudo getlibs /usr/bin/cairo-dock**
Matched library libglitz-glx.so.1 to /gutsy/libs/libglitz-glx1
Matched library libglitz.so.1 to /gutsy/libs/libglitz1
Matched library librsvg-2.so.2 to /gutsy/libs/librsvg2-2
The following i386 libraries will be installed:
/gutsy/libs/libglitz1
/gutsy/libs/libglitz-glx1
/gutsy/libs/librsvg2-2
Continue? (y/n) y
Downloading... Installing libraries ...
New depedencies have been detected:
libgsf-1.so.114
libcroco-0.6.so.3
Matched library libcroco-0.6.so.3 to /gutsy/libs/libcroco3
Matched library libgsf-1.so.114 to /gutsy/libs/libgsf-1-114
The following i386 libraries will be installed:
/gutsy/libs/libcroco3
/gutsy/libs/libgsf-1-114
Continue? (y/n) y
Downloading.. Installing libraries ...

```

I get some errors below but the program runs perfectly:
```

cappy@cappy-chan:~$ cairo-dock
Attention : Error opening directory '/usr/share/cairo-dock/plug-in': No such file or directory
  no module will be available
(cairo-dock:15561): Gtk-WARNING **: Error loading theme icon 'gtk-cancel' for stock: Unable to load image-loading module: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: cannot open shared object file: No such file or directory

(cairo-dock:15561): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -2 and height 71

(cairo-dock:15561): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -2 and height 71

(cairo-dock:15561): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -2 and height 71

(cairo-dock:15561): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -2 and height 71

(cairo-dock:15561): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -2 and height 71
rm -rf /home/cappy/.cairo-dock/current_theme/*
/bin/cp -r /usr/share/cairo-dock/themes/_Ubuntu_/* /home/cappy/.cairo-dock/current_theme
 -> cConfFileLanguage : fr
Attention : Key file does not have key 'main dock view'
Attention : Key file does not have key 'sub-dock view'
  res_name : gaim; res_class : Gaim
  pas de _NET_WM_ICON, mais un pixmap
_cairo_dock_get_pixbuf_from_pixmap (56623122) : 48x42x24 pixels (0;0)
_cairo_dock_get_pixbuf_from_pixmap (56623123) : 48x42x1 pixels (0;0)
  res_name : opera; res_class : Opera
  res_name : nautilus; res_class : Nautilus
  res_name : nautilus; res_class : Nautilus
  res_name : gnome-terminal; res_class : Gnome-terminal
  res_name : gnome-terminal; res_class : Gnome-terminal
cairo_dock_update_dock_size ()
cairo_dock_update_dock_size ()
cairo_dock_replace_key_values (0)
Attention : Key file does not have key 'frame1'
Attention : Key file does not have key 'frame3'

```

Edit:
The package manager didn't like the force-all and it said I had a broken package
```

 sudo apt-get -f install
The following NEW packages will be installed:
  libglitz-glx1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 31.2kB of archives.
After unpacking 111kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 ftp://ftp.gtlib.gatech.edu gutsy/main libglitz-glx1 0.5.6-1 [31.2kB]
Fetched 31.2kB in 0s (174kB/s)  
Selecting previously deselected package libglitz-glx1.
(Reading database ... 163069 files and directories currently installed.)
Unpacking libglitz-glx1 (from .../libglitz-glx1_0.5.6-1_amd64.deb) ...
Setting up libglitz-glx1 (0.5.6-1) ...

```
so I had to resolve that.

---

### Post by RavanH on 2007-11-01
> **Cappy said:**
> Cairo-dock works fine for me.

Here is it working:
```

**~/Desktop$ sudo dpkg --force-all -i cairo-dock_v1.3.8.1_i686-32bits.deb **
[sudo] password for cappy:
Selecting previously deselected package cairo-dock.
(Reading database ... 162800 files and directories currently installed.)
Unpacking cairo-dock (from cairo-dock_v1.3.8.1_i686-32bits.deb) ...
dpkg: cairo-dock: dependency problems, but configuring anyway as you request:
 cairo-dock depends on libglitz-glx1; however:
  Package libglitz-glx1 is not installed.
Setting up cairo-dock (1.3.8) ...
**cappy:~/Desktop$ whereis cairo-dock**
cairo-dock: /usr/bin/cairo-dock /usr/share/cairo-dock
**cappy:~/Desktop$ sudo getlibs /usr/bin/cairo-dock**
Matched library libglitz-glx.so.1 to /gutsy/libs/libglitz-glx1
Matched library libglitz.so.1 to /gutsy/libs/libglitz1
Matched library librsvg-2.so.2 to /gutsy/libs/librsvg2-2
The following i386 libraries will be installed:
/gutsy/libs/libglitz1
/gutsy/libs/libglitz-glx1
/gutsy/libs/librsvg2-2
Continue? (y/n) y
Downloading... Installing libraries ...
New depedencies have been detected:
libgsf-1.so.114
libcroco-0.6.so.3
Matched library libcroco-0.6.so.3 to /gutsy/libs/libcroco3
Matched library libgsf-1.so.114 to /gutsy/libs/libgsf-1-114
The following i386 libraries will be installed:
/gutsy/libs/libcroco3
/gutsy/libs/libgsf-1-114
Continue? (y/n) y
Downloading.. Installing libraries ...

```

I get some errors below but the program runs perfectly:
```

cappy@cappy-chan:~$ cairo-dock
Attention : Error opening directory '/usr/share/cairo-dock/plug-in': No such file or directory
  no module will be available
(cairo-dock:15561): Gtk-WARNING **: Error loading theme icon 'gtk-cancel' for stock: Unable to load image-loading module: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: /usr/lib32/gtk-2.0/2.10.0/loaders/svg_loader.so: cannot open shared object file: No such file or directory

(cairo-dock:15561): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -2 and height 71

(cairo-dock:15561): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -2 and height 71

(cairo-dock:15561): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -2 and height 71

(cairo-dock:15561): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -2 and height 71

(cairo-dock:15561): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -2 and height 71
rm -rf /home/cappy/.cairo-dock/current_theme/*
/bin/cp -r /usr/share/cairo-dock/themes/_Ubuntu_/* /home/cappy/.cairo-dock/current_theme
 -> cConfFileLanguage : fr
Attention : Key file does not have key 'main dock view'
Attention : Key file does not have key 'sub-dock view'
  res_name : gaim; res_class : Gaim
  pas de _NET_WM_ICON, mais un pixmap
_cairo_dock_get_pixbuf_from_pixmap (56623122) : 48x42x24 pixels (0;0)
_cairo_dock_get_pixbuf_from_pixmap (56623123) : 48x42x1 pixels (0;0)
  res_name : opera; res_class : Opera
  res_name : nautilus; res_class : Nautilus
  res_name : nautilus; res_class : Nautilus
  res_name : gnome-terminal; res_class : Gnome-terminal
  res_name : gnome-terminal; res_class : Gnome-terminal
cairo_dock_update_dock_size ()
cairo_dock_update_dock_size ()
cairo_dock_replace_key_values (0)
Attention : Key file does not have key 'frame1'
Attention : Key file does not have key 'frame3'

```

Edit:
The package manager didn't like the force-all and it said I had a broken package
```

 sudo apt-get -f install
The following NEW packages will be installed:
  libglitz-glx1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 31.2kB of archives.
After unpacking 111kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 ftp://ftp.gtlib.gatech.edu gutsy/main libglitz-glx1 0.5.6-1 [31.2kB]
Fetched 31.2kB in 0s (174kB/s)  
Selecting previously deselected package libglitz-glx1.
(Reading database ... 163069 files and directories currently installed.)
Unpacking libglitz-glx1 (from .../libglitz-glx1_0.5.6-1_amd64.deb) ...
Setting up libglitz-glx1 (0.5.6-1) ...

```
so I had to resolve that.

Hi Cappy, thrilled to hear GETLIBS does the trick again!!!

It really :guitar:

Did you have to use --force-all? I only used --force-architecture and did not run into the broken package issue...

The errors you get when running cairo-dock from terminal are related to the theme the cairo-dock is using. If you can see the dock on your screen, then right-click on it (anywhere) and choose Cairo-Dock>Configure>All to open up configuration screen. Select the english language on the tab Cairo-Dock. Close and restart the dock to get everything in english. Then right-click again and choose Cairo-Dock>Manage Themes to select a nicer theme :)

---

### Post by salariua on 2007-11-02
You've got to love Ubuntu and all the things that came with it, the community, forum, magazines etc. 

You guys are my heroes.... Keep up the good work  !

---

### Post by joelpedersen on 2007-11-02
:KS Sweet Script!  That was easy as pie!

---

### Post by PriceChild on 2007-11-07
poke

---

### Post by xtonix on 2007-11-07
Isn't easyer to use 
```
lsb_release -i
Distributor ID: Debian

``` to determinate the distribution and 
```
lsb_release -r
Release:        testing

``` for release?

Now it's in the code:
```

#Select the correct site to download/search on                                                                                                               
releaseinput=`lsb_release -c | grep -o [[:alnum:]]*$` #grep last word in the distro's codename                                                               
case $releaseinput in                                                                                                                                        
#Ubuntu                                                                                                                                                      
heron) distroname="heron"; set_site_ubuntu;;                                                                                                                 
gutsy) distroname="gutsy"; set_site_ubuntu;;                                                                                                                 
feisty) distroname="feisty"; set_site_ubuntu;;                                                                                                               
edgy) distroname="edgy"; set_site_ubuntu;;                                                                                                                   
dapper) distroname="dapper"; set_site_ubuntu;;                                                                                                               
#Debian                                                                                                                                                      
sid) distroname="unstable"; set_site_debian;;                                                                                                                
lenny) distroname="testing"; set_site_debian;;                                                                                                               
etch) distroname="stable"; set_site_debian;;                                                                                                                 
sarge) distroname="oldstable"; set_site_debian;;                                                                                                             
#Old Ubuntu                                                                                                                                                  
breezy) distroname="breezy"; set_site_ubuntu;;                                                                                                               
hoary) distroname="hoary"; set_site_ubuntu;;                                                                                                                 
warty) distroname="warty"; set_site_ubuntu;;                                                                                                                 
#Unknown                                                                                                                                                     
*) echo "Unknown distro, using Debian Unstable (sid) settings"; distroname="unstable"; set_site_debian;;      
esac

```

---

### Post by Cappy on 2007-11-07
If I had known the lsb_release -r output that information for debian I probably would have used what you suggested. This was the first shell script I wrote and some things are done in an around-the-bout way. I take and will credit any contributions/changes if you would like to make any.

---

### Post by NullHead on 2007-11-15
Cappy 

When getlibs installs a lib for you does it cache the libs that it installs?

---

### Post by Cappy on 2007-11-15
No, it doesn't. The libs are saved to /tmp/ and then those libraries are moved directly to the lib folder.

---

### Post by NullHead on 2007-11-15
Does it make a log with the library filename in it?

---

### Post by Cappy on 2007-11-15
It doesn't. The only thing it does is download and move the needed libraries to /usr/lib32.

---

### Post by NullHead on 2007-11-15
Alright thanks for the help.

---

### Post by drtvasudevan on 2007-11-17
should we lock the files after installing with getlibs?
recently skype wont start. after thinking for time i thought the original dependency files might have changed and the 32 bit versions have not been installed.
i ran getlibs again and sure there two files that needed changing.
redownloaded and now it works fine.
tv

---

### Post by supersonicdarky on 2007-11-19
Server seems to be down. Any mirrors?

(if it's just me, then can someone please download and attach)

---

### Post by Momba on 2007-11-19
No... It's not you. Same problem here. BUT: Google Cache still can give you the source.
But as I have been a proud Ubuntu user for the second day now, I haven't the slightest clue what to do with it. :)
 If you know please let me know.

---

### Post by Cappy on 2007-11-19
My server was down for a little bit - sorry.

&#31169;&#12418;&#12450;&#12491;&#12513;&#12364;&#22909;&#12365;&#12290;

---

### Post by svtfmook on 2007-11-19
how do you reverse this?  i no longer can play flash video w/ sound after this

---

### Post by Cappy on 2007-11-19
> **svtfmook said:**
> how do you reverse this?  i no longer can play flash video w/ sound after this

What did you use getlibs on?

What output do you get in the terminal when you run
```
firefox
```
from the terminal and try to watch a flash video?

---

### Post by elanthis on 2007-11-20
svtfmook:

Upgrading to pulseaudio will break sound in Flash, so check to see if that's the problem.

32-bit flash uses 32-bit ALSA, which requires a 32-bit Pulseaudio plugin, which doesn't exist in the 64-bit packages at all.  I tried using getlibs to fix this, but it doesn't work (and its error output looks broken, too):

elanthis@stargrazer:~$ getlibs -32 /usr/lib/alsa-lib/libasound_module_pcm_pulse.so 
No match found for package /uslialsa-lilibasound_module_pcm_pulse.so
No libraries to download.

Killing pulseaudio will also fix the problem, but long term obviously Ubuntu needs to fix this and offer a 32-bit version of the ALSA Pulse plugin for those stupid 32-bit apps.

---

### Post by Momba on 2007-11-20
Installed it and it worked great. Just wanted to say thank you!

---

### Post by RavanH on 2007-11-21
And Getlibs comes to the rescue again!

I downloaded the new Skype beta 2.0 on [http://www.skype.com/intl/en/download/skype/linux/beta/](http://www.skype.com/intl/en/download/skype/linux/beta/) (supposedly has video support at last) but after installing it

```
~$ sudo dpgk -i --force-architecture skype*.deb
....
~$ skype
skype: error while loading shared libraries: libXss.so.1: cannot open shared object file: No such file or directory
```

clearly has more dependencies:

```
:~$ getlibs /usr/bin/skype
Matched library libXss.so.1 to /gutsy/libs/libxss1
The following i386 libraries will be installed:
/gutsy/libs/libxss1
Continue? (y/n) y
Downloading. Installing libraries ...
```

:)

---

### Post by Winawer on 2007-11-24
This script saved my bacon with a few programs - thank you so much! :KS

---

### Post by loosetoned on 2007-11-25
Just wanted to say thank you,  this script saves hours,  it's fantastic.  Good work!

---

### Post by malathion on 2007-11-26
sorry, double post!

---

### Post by malathion on 2007-11-26
> **zsouthboy said:**
> This script should be integrated into all debian based distros, if you are willing to manage that project. It would help linux newbies even more than now!

Indeed. This is amazing.

This thread really must be stickied in the amd64 forum... you just saved me endless headaches installing 32 bit apps on my 64 bit gusty. Thank you!!

---

### Post by Cappy on 2007-12-08
I am going to do a complete rewrite of getlibs.

New features should include:
[LIST]
[*]Logging
[*]Downloading libraries from your local selected mirror instead of just kernel.org
[*]Option to install libraries by package name
[*]Option to install local libraries
[*]Option to install a library using a link to the package
[*]Ability to remove or upgrade installed 32-bit libraries (at least remove)
[*]Much faster runtime
[/LIST]

I was learning shell scripting as I wrote getlibs so it will be easier for me to rewrite getlibs than trying to make the current getlibs do new tricks.
The main goal of the new version will be to allow a user multiple ways to install a library.

I may end up releasing just a few of the possible features in the first 2.0 release so tell me what feature you would like to see first. Now is the time to mention any feature that I haven't listed if you would like to see it in the next getlibs.

---

### Post by NullHead on 2007-12-08
> **Cappy said:**
> I am going to do a complete rewrite of getlibs.

New features should include:
[LIST]
[*]Logging
[*]Downloading libraries from your local selected mirror instead of just kernel.org
[*]Option to install libraries by package name
[*]Option to install local libraries
[*]Option to install a library using a link to the package
[*]Ability to remove or upgrade installed 32-bit libraries (at least remove)
[*]Much faster runtime
[/LIST]

I was learning shell scripting as I wrote getlibs so it will be easier for me to rewrite getlibs than trying to make the current getlibs do new tricks.
The main goal of the new version will be to allow a user multiple ways to install a library.

I may end up releasing just a few of the possible features in the first 2.0 release so tell me what feature you would like to see first. Now is the time to mention any feature that I haven't listed if you would like to see it in the next getlibs.

I would like logging and ability to remove or upgrade installed 32-bt libraries. :D I'm over joyed to hear you're going to make a newer version! Maybe you could add a gui too? lol It's too much to ask! it's already such a wonderful application anyways! :cool:

---

### Post by Brando569 on 2007-12-12
wow this seems like an awesome script, i saw a link to it in one of the 64 bit stickies i was reading and decided to check it out. ill test this baby out later on lm-sensors v3 that i was trying to compile earlier and it wouldnt work because of dependancy errors.

---

### Post by Kilz on 2007-12-12
> **Brando569 said:**
> wow this seems like an awesome script, i saw a link to it in one of the 64 bit stickies i was reading and decided to check it out. ill test this baby out later on lm-sensors v3 that i was trying to compile earlier and it wouldnt work because of dependancy errors.

As I understand it, the script doesnt install dependencies for things you want to compile , but for 32bit applications you force install.

---

### Post by Cappy on 2007-12-12
You just need to sudo apt-get install the required packages. Getlibs is for use with pre-compiled binaries (programs).

According the project you need the following required packages:
```
sudo apt-get install build-essential bison gcc flex sysfsutils perl libsysfs-dev
```

---

### Post by Kilz on 2007-12-12
> **Cappy said:**
> You just need to sudo apt-get install the required packages. Getlibs is for use with pre-compiled binaries (programs).


I thought so. Thanks for clarifying that for us Cappy, getlibs is an awesome script.

---

### Post by Cappy on 2007-12-22
Getlibs v2.00 is done. If you are willing to help try it out for me!
Install:
[http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-2.00-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-2.00-all.deb)
Source:
[http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-2.00.sh](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-2.00.sh)

I've been using the following to test getlibs:
```
sudo rm /usr/lib32/libQtCore* /usr/lib32/libQtDBus* /usr/lib32/libQtGui* /usr/lib32/libQtNetwork* /usr/lib32/libdbus-*
sudo getlibs /usr/bin/skype

```
but you may try something I haven't thought of. I've left debugging messages in for testing. A good command to test is
```
libpng.so.3
```
let me know if there are any errors/problems (or if it works perfectly in everything you try!)

Here are some of the most important options:
--file "filename" or -f "filename here" will install a .deb library you have locally on your computer correctly.
--link 'link here' or -w 'link here' will download and install a .deb library given a link
--ldconfig will make sure the newly installed libraries are linked. Skipped otherwise.
--mirror 'mirror address' or -m mirror 'mirror address' will download from the mirror of your choice. Default is the one specified in /etc/apt/sources.list and the backup is [http://mirrors.kernel.org/ubuntu/](http://mirrors.kernel.org/ubuntu/)

> 
Logging (NOT YET - depends on everything else)
Downloading libraries from your local selected mirror instead of just kernel.org (CHECK)
Option to install libraries by package name (CHECK)
Option to install local libraries (CHECK)
Option to install a library using a link to the package (CHECK)
Ability to remove or upgrade installed 32-bit libraries (at least remove) (NOT YET - depends on logging)
Much faster runtime (CHECK)


sudo getlibs library/binary/packagename now works. On 64-bit it will install 32-bit packages unless you specify -64.
This means ```
sudo getlibs /usr/bin/skype
sudo getlibs libQtGui.so.4 libQtCore.so.4
sudo getlibs -32 libQtGui.so.4 libQtCore.so.4
sudo getlibs libqt4-core libqt4-gui
sudo getlibs -32 libqt4-core libqt4-gui

```
will all do the same thing (using the binary path is always better). I'm not sure if this is a good idea. I'm wondering if instead the syntax for packages should only be
```

sudo getlibs -p libqt4-core libqt4-gui
sudo getlibs --package libqt4-core libqt4-gui

```
The problem is that getlibs checks to see if there is a file "X" and if it doesn't exist it assumes it is a package. I put a message in when this happens.
```

$ sudo getlibs abcdef
abcdef is not a file. Assuming this is a package name.

The following i386 packages will be installed: abcdef
Continue [Y/n]? n

```

---

### Post by wingnux on 2007-12-29
AWESOME!!!

Thank you! It solved my problem with epsxe! =)

---

### Post by BogusJoe on 2007-12-31
Hello Cappy,
adding my Thanks along with the others.  I am by no mean an expert at Ubuntu, but have been playing with Linux (as a user) for several years and have always been plauged by Libs not found.
Fantastic Work!

Downloaded your latest version 2.00
Currently using Hardy Heron 8.04 64 bit

Goal: to get Enenmy Territory Quake Wars to work with HH 8.04  Yes ETQW is a 32bit app.

User Puccaso has helped me with the video driver and it works great, so far. Even though it is a test driver. Compiz does not work. Video card is a HD3870. Went through the installation of ETQW, but it needs a lib file.  I tried "getlibs ver. 2.00" 

```

bogusjoe@uby64-HH:~/etqw$ ./etqw
./etqw.x86: error while loading shared libraries: libdirectfb-0.9.so.25: cannot open shared object file: No such file or directory

bogusjoe@uby64-HH:~/etqw$ getlibs etqw
Cannot determine the dependencies required by this program, it may be a script:
If this program needs a 32-bit library use:
getlibs -32 i386librarytoinstall.so
If this program needs a 64-bit library use:
getlibs -64 amd64librarytoinstall.so

bogusjoe@uby64-HH:~/etqw$ getlibs -32 etqw.x86
Looking up libdirectfb-0.9.so.25 on web interface: 
No match
Looking up libfusion-0.9.so.25 on web interface: 
No match
Looking up libdirect-0.9.so.25 on web interface: 
No match
Using mirror http://us.archive.ubuntu.com/ubuntu/
bogusjoe@uby64-HH:~/etqw$

```

I have not tried:

```

~$ sudo dpgk -i --force-architecture etqw*.deb

```

Since the actual installer for Quake Wars is "ETQW-client-1.2-full.r5.x86.run" Didn't know if this would work or not?  Can you or someone help please?

---

### Post by Cappy on 2007-12-31
Hi, thanks for the post. I now see that hardy is not listed on the web interface so you will need to use the --release option.

This should be ```
getlibs --release gutsy ~/etqw/etqw.x86
```

If that still isn't working correctly use
```
getlibs -p libdirectfb-0.9-25 libdirectfb-0.9-25 libdirectfb-0.9-25
```

---

### Post by BogusJoe on 2007-12-31
> **Cappy said:**
> Hi, thanks for the post. I now see that hardy is not listed on the web interface so you will need to use the --release option.

This should be ```
getlibs --release gutsy ~/etqw/etqw.x86
```

If that still isn't working correctly use
```
getlibs -p libdirectfb-0.9-25 libdirectfb-0.9-25 libdirectfb-0.9-25
```

Thanks Cappy.  The first command worked! 
ETQW is trying to run now, but SDL_ListModes ignored.  I think I have seen this before and will search more on this.

You and some others on the forums have made the holidays a worthwhile vacation time!

Happy New Year! and Be Safe!

---

### Post by Jinouchi on 2008-01-02
I'm having trouble installing skype on debian. Here's what I get:

```

# getlibs skype
No match found for package libQtCore.so.4
No match found for package libQtDBus.so.4
No match found for package libQtGui.so.4
No match found for package libQtNetwork.so.4
No libraries to download.

```

Why won't it work?

---

### Post by Gavla on 2008-01-02
Champion! Now I can play Alien Arena!

---

### Post by Cappy on 2008-01-02
> **Jinouchi said:**
> I'm having trouble installing skype on debian. Here's what I get:

```

# getlibs skype
No match found for package libQtCore.so.4
No match found for package libQtDBus.so.4
No match found for package libQtGui.so.4
No match found for package libQtNetwork.so.4
No libraries to download.

```

Why won't it work?

Use the new getlibs v2 on the front post

---

### Post by Cappy on 2008-01-03
getlibs is now v2.01

Let me know if you have any problems with it.

---

### Post by ~LoKe on 2008-01-03
I used the previous version and it works nicely (unfortunately it wasn't the solution I was looking for).  It's a great app and I'm definitely keeping it installed.

Thanks!

---

### Post by Anubis on 2008-01-03
:confused: I don't get why not just run the 32bit *buntu and be done with it?:confused:

But, nice work helping the noobs get there jobs done.

Just an opinion.:cool::cool:

---

### Post by ~LoKe on 2008-01-03
> **Anubis said:**
> :confused: I don't get why not just run the 32bit *buntu and be done with it?:confused:

Because there are advantages to the 64bit release and it's worth the trouble for a couple 32bit apps.

---

### Post by NullHead on 2008-01-03
> **Anubis said:**
> :confused: I don't get why not just run the 32bit *buntu and be done with it?:confused:

But, nice work helping the noobs get there jobs done.

Just an opinion.:cool::cool:

If everyone is still using the older, slower and more developed 32-bit architecture then why would you need a new hardware or newer faster software? Where there is satisfaction there is no innovation. There is huge performance benefits for using 64bit. Using 64bit also  shows there is a want for newer faster computers.

---

### Post by chemist109 on 2008-01-09
> **Anubis said:**
> :confused: I don't get why not just run the 32bit *buntu and be done with it?:confused:

But, nice work helping the noobs get there jobs done.

Just an opinion.:cool::cool:

At my work, there are scientists that use 64 bit Linux apps for number crunching and they don't want to have to use an entirely different machine for the more mundane tasks.  (Like browsing the web while a simulation is running).

---

### Post by clumsySmurf on 2008-01-17
Please note that on my system (Debian sid) the package lsb-release was not installed. Should be put in the package as a dependency imho.

---

### Post by mtwa on 2008-01-18
Just a quick thank you!
I was attempting to run MeVisLab, a medical image processing application on my Kubuntu 7.10 64bit system. After running your script and updating my video drivers I am in business. Thanks for helping this noob! Cheers, Michael

---

### Post by curdegn on 2008-01-20
Helllo,
I have the following troubles trying to install the missing library Libcurl3 for Zattoo:
----
user@computer:~$ sudo getlibs /usr/bin/zattoo_player
libcurl.so.3: libcurl3
The following i386 packages will be installed:
libcurl3
Continue [Y/n]?
Downloading ...
Failed to download file from [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) for [http://archive.ubuntu.com/ubuntu/./libcurl3_7.16.4-2ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/./libcurl3_7.16.4-2ubuntu1_i386.deb)
The mirrors do not have the requested file or there is no internet connection
File downloaded successfully from [http://mirrors.kernel.org/ubuntu/](http://mirrors.kernel.org/ubuntu/)
ls: /tmp/getlibs.yjuPYW7462/*.deb: No such file or directory
Installing libraries ...
linuxmce@dcerouter:~$     
-----
I checked the mentioned ubuntu archive, the required file is there.What is going on? Any advise ?

---

### Post by Cappy on 2008-01-21
getlibs v2.02:
----
Tons of bug fixes

If libGL.so.1 is missing but there is a libGL.so.* library getlibs will link it.

Build options:
--build: Will convert a 32-bit package to a 64-bit package and install it instead of extracting it. Probably the new future default option. Hopefully will fix the "disappearing library" problem. Also will allow packages to be removed.

--savebuild: Saves the built packages to /home/$USER

---

### Post by RavanH on 2008-01-22
Hi Cappy,

Trying Getlibs to get Gizmo (SIP client, see gizmoproject.com) working on Gutsy64, I ran into an error:

```
getlibs /usr/bin/gizmo
No match for libsipphoneapi.so.1.7.07.73
No packages to install
```

I tried ```
getlibs -l libsipphoneapi.so
``` but with similar result...

Any ideas?

--ravan

*Very* small improvement suggestion: make command options 'getlibs -h' and 'getlibs --help' return the little help text that 'getlibs' does?

---

### Post by Cappy on 2008-01-22
> **RavanH said:**
> 
*Very* small improvement suggestion: make command options 'getlibs -h' and 'getlibs --help' return the little help text that 'getlibs' does?

I'll do that =)


libsipphoneapi.so.1.7.07.73 is only available inside the gizmo package. I downloaded [http://download.gizmoproject.com/GizmoDownload/gizmo-project_3.1.0.79_libstdc++6_i386.deb](http://download.gizmoproject.com/GizmoDownload/gizmo-project_3.1.0.79_libstdc++6_i386.deb) and saw it inside to be installed to /usr/lib/libsipphoneapi.so.1.7.07.73
so you should be able to 
```
sudo cp /usr/lib/libsipphoneapi.so.1.7.07.73 /usr/lib32/libsipphoneapi.so.1.7.07.73
```

or you can try out the beta getlibs feature --build and do
```
getlibs --build --savebuild -i gizmo-project_3.1.0.79_libstdc++6_i386.deb
```
which will create a package with just /usr/lib32/libsipphoneapi.so.1.7.07.73 and install it.

---

### Post by RavanH on 2008-01-22
> **Cappy said:**
> ```
sudo cp /usr/lib/libsipphoneapi.so.1.7.07.73 /usr/lib32/libsipphoneapi.so.1.7.07.73
```

or you can try out the beta getlibs feature --build and do
```
getlibs --build --savebuild -i gizmo-project_3.1.0.79_libstdc++6_i386.deb
```
which will create a package with just /usr/lib32/libsipphoneapi.so.1.7.07.73 and install it.
Thanks Cappy,

Once again, you saved my day :)

---

### Post by RavanH on 2008-01-22
> **Cappy said:**
> or you can try out the beta getlibs feature --build and do
```
getlibs --build --savebuild -i gizmo-project_3.1.0.79_libstdc++6_i386.deb
```
which will create a package with just /usr/lib32/libsipphoneapi.so.1.7.07.73 and install it.
So what happens here exactly? Getlibs 'converts' the 32bit package to fit the 64bit filestructure? In that way the proper dir gets used when installing 32bit libs? ---- NEAT!!!

Would it be possible to have Getlibs look in /usr/lib/ for any 32bit libraries it cannot find? So that ```
getlibs /usr/bin/gizmo
``` would result in the libsipphoneapi (if not found for download but found in /usr/lib/) to be copied to /usr/lib32/ ? 

Sort of the --build procedure but then afterwards ;)


Anyway, I cannot emphasize enough: Getlibs :guitar:
--ravan

---

### Post by largosblade on 2008-01-23
Worked just the way you said... Thanks

---

### Post by mastergunner on 2008-01-27
subscribed

---

### Post by mooball on 2008-01-31
Ive been trying to use getlibs on skype and pixel with no luck for a while and finally figured out why - getlibs is finding the wrong URLs for the libs. for instance this is the output from  
getlibs pixel

```
:~/bin/Pixel$ getlibs pixel
libaspell.so.15: libaspell15
The following i386 packages will be installed:
libaspell15
Continue [Y/n]? y
Downloading ...
Failed to download file from  for http://mirrors.kernel.org/ubuntu/debpool/main/a/aspell/libaspell15_0.60.5-1ubuntu1_i386.deb
The mirrors do not have the requested file or there is no internet connection
No packages to install
```

I finally noticed that the URL is wrong, it has the path /ubuntu/**debpool**/main.... when it looks to me like it should be /ubuntu/**pool**/main....

So why is it getting the address wrong?

Im using version 2.03

---

### Post by Cappy on 2008-01-31
Please give me the output of 
```
getlibs --verbose -p libaspell15
```

The file /etc/apt/sources.list using
```
cat /etc/apt/sources.list
```

and finally
```
apt-cache policy libaspell15
```

Copy and paste each from the terminal into CODE blocks please! Thanks!

---

### Post by lamadredelsapo on 2008-01-31
Great! I was looking for something easy to solve this.

---

### Post by mooball on 2008-01-31
in response to your request for outputs....


```
$ getlibs --verbose -p libaspell15
The following i386 packages will be installed: libaspell15
Continue [Y/n]? y
queue: debpool/main/a/aspell/libaspell15_0.60.5-1ubuntu1_amd64.deb
Downloading ...
Downloading http://mirrors.kernel.org/ubuntu/debpool/main/a/aspell/libaspell15_0.60.5-1ubuntu1_i386.deb
Failed to download file from  for http://mirrors.kernel.org/ubuntu/debpool/main/a/aspell/libaspell15_0.60.5-1ubuntu1_i386.deb
The mirrors do not have the requested file or there is no internet connection
No packages to install
```


```
$ cat /etc/apt/sources.list

.. commented lines removed ..

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

.. commented lines removed ..

# Line commented out by installer because it failed to verify:
deb http://au.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://eric.lavar.de/comp/linux/debian/ unstable/
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://au.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb http://eric.lavar.de/comp/linux/debian/ ubuntu/
```



```
$ apt-cache policy libaspell15
libaspell15:
  Installed: 0.60.5-1ubuntu1
  Candidate: 0.60.5-1ubuntu1
  Version table:
 *** 0.60.5-1ubuntu1 0
        500 http://au.archive.ubuntu.com gutsy/main Packages
        100 /var/lib/dpkg/status

```

I should note that the problem happens with all libs, not just aspell, Ive not yet been able to download a single lib.

---

### Post by Cappy on 2008-01-31
Thank you mooball,
I've corrected this bug. I'm uploading it shortly after this is posted. Just install the new version from the first post in this thread.

---

### Post by mooball on 2008-02-01
Yippie, it works, thanks for that.

Tom

---

### Post by crjackson on 2008-02-09
Thanks Cappy, just used getlibs to help install amazonmp3 downlolader.  I don't know how to make it grab all the libs at once, but it got them for me one at a time until the app was installed.

---

### Post by wraund on 2008-02-18
Thank you for showing me this :)

It has revolutionized my installation of 32 programs on to 64 :)

---

### Post by Cappy on 2008-02-20
The packages.ubuntu.com web interface changed. Unfortunately this week is completely busy with tests and projects due to the midterm. I probably won't be able to fix the problem until Saturday. Common installs such as Skype will still work.

This only affects library lookups that are not listed in getlibs. I recommend you use the package name manually ```
sudo getlibs -p packagename1 packagename2
```
or install and configure apt-file and use the --apt-file option.

On the plus side, packages.ubuntu.com now includes Hardy!

---

### Post by Cappy on 2008-02-25
Okay, the new getlibs is uploaded. It has support for the new packages.ubuntu. **Everyone who has getlibs should upgrade or else you will get messages about "No match found"** if the library isn't one I specifically put in an internal list with getlibs.

I also made some minor changes to getlibs to improve the compatibility with other languages. Also added support for mirrors that don't end with / (which they should), and mirrors that are www. or https: addresses.

---

### Post by crgutierrez on 2008-02-25
Would this allow me to install and run i386.deb iscan drivers*** in my 7.10 64 bit Ubuntu????(****epson V350 PHOTO scanner driver). Gracias!

---

### Post by Cappy on 2008-02-25
Some people have had success doing that. I suggest you start a new thread if you have problems though.

---

### Post by Cappy on 2008-03-01
Getlibs 2.06 released. Fixes a problem where files will report as being in the "BinaryfileXmatches" package. That's actually "Binary file X matches" without the spaces and it was caused by some text that wasn't in parenthesis =(

---

### Post by Omnios on 2008-03-01
Hi how does this work? I have a Dell SPS 1530 with a core 2 duo 2.2ghz. What I am wondering is would I be able to install Kubuntu 64bit and still use 32bit programs with this? I really would like to try 64bit but from what I read so far is 64bit is not totally ready yet and will that resolve these issues?

---

### Post by crjackson on 2008-03-02
> **Omnios said:**
>  What I am wondering is would I be able to install Kubuntu 64bit and still use 32bit programs with this? 

Yes.  It's one of the most aswsome scripts you will find.  Actually, you can do that anyway, but getlibs makes it much easier and more automated.

64bit IS ready to rock/roll already.  Don't wait any longer.

---

### Post by vijaym on 2008-03-04
Hey Cappy
thanks for the good script. works perfectly for me.

vijay

---

### Post by rmtatum on 2008-03-10
I used getlibs to install Gizmo.  The programs loads and is able to receive calls.  However the interface is broken and missing images.  Also the dialpad tab does not show the dialpad.

Below is some of the error output from the program: 

(gizmo:8338): Gtk-CRITICAL **: gtk_icon_set_new_from_pixbuf: assertion `pixbuf != NULL' failed

(gizmo:8338): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gizmo:8338): Gtk-CRITICAL **: gtk_icon_factory_add: assertion `icon_set != NULL' failed

(gizmo:8338): Gtk-CRITICAL **: gtk_icon_set_unref: assertion `icon_set != NULL' failed

(gizmo:8338): Gtk-CRITICAL **: gtk_icon_set_new_from_pixbuf: assertion `pixbuf != NULL' failed

(gizmo:8338): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gizmo:8338): Gtk-CRITICAL **: gtk_icon_factory_add: assertion `icon_set != NULL' failed

(gizmo:8338): Gtk-CRITICAL **: gtk_icon_set_unref: assertion `icon_set != NULL' failed

---

### Post by Cappy on 2008-03-11
Try ```
sudo apt-get install libgtk2.0-0 gconf2 libstdc++6 libasound2 zlib1g
```

---

### Post by rmtatum on 2008-03-11
I have the afore mentioned packages installed already.

---

### Post by rmtatum on 2008-03-11
I'm running Kubuntu Hardy (with Ubuntu-desktop installed).

---

### Post by soxs on 2008-03-11
you might need gtk2-engines-pixbuf or libgdk-pixbuf2

---

### Post by rmtatum on 2008-03-11
I had gtk2-engines-pixbuf installed already, and I installed libgdk-pixbuf2 and libgdk-pixbuf-gnome2.  I still have the error.

---

### Post by lynx shadow on 2008-03-11
i've been trying to get openproj and opera 9.5 to run on my intel core2 duo notebook, installed with ubuntu 7.10 gutsy, for about 2 weeks now. i'm new with linux and i've tried loading all libs, jre6, and anything else i can get my hands on that i read about in different forums.

i still haven't got openproj installed, but i was able to install opera 9.50. the problem is when i run it, it crashes after 5 seconds or so.

this thread tells me that there's something wrong per se with jave. i'd like to try out the commands suggested, but i'm not sure whether i can just type 'opera' or 'openproj' instead of 'skype', because that would be the way i'd go.

can you tell me if you thing the suggested commands would solve my problem?

i would really appreciate any suggestions you may have.

thanks

---

### Post by soxs on 2008-03-11
> **rmtatum said:**
> I had gtk2-engines-pixbuf installed already, and I installed libgdk-pixbuf2 and libgdk-pixbuf-gnome2.  I still have the error.
what about gob2? If it will still not run, I have no clue what is missing.

---

### Post by rmtatum on 2008-03-11
I installed gob2 but that didn't fix the error.

---

### Post by soxs on 2008-03-12
I suggest you to start another thread. This seems to get somewhat more difficult to fix.

---

### Post by Rogers on 2008-03-12
This should become part of the 64bit distro, it solves all 64bit issues.

---

### Post by Repgahroll on 2008-03-13
Oh, man!

This just saved my life :D (my fingers at least)

No more 32-bit chroot! Now it's possible to install any 32-bit package without issues!

THANKYAU VARIE MUCHE!!!

---

### Post by Cappy on 2008-03-13
> **lynx shadow said:**
> 
this thread tells me that there's something wrong per se with jave. i'd like to try out the commands suggested, but i'm not sure whether i can just type 'opera' or 'openproj' instead of 'skype', because that would be the way i'd go.


It will if the problem is a missing library. You have to run "opera" on the command line to see what the problem is. 

/usr/bin/opera is actually a script that runs the actual opera binary that is elsewhere though. It's still not hard though.

```
grep 'BINARYDIR=/' /usr/bin/opera
```

will tell you. Or just looking in the file.
Or
```
getlibs `grep 'BINARYDIR=/' /usr/bin/opera | grep -o '/.*'`/opera
```
to make it easy

---

### Post by curdegn on 2008-03-16
Hello,

Having some problems using getlibs to install the necessary 32bit libraries for the zatto player on  the ubuntu based LinuxMCE system;
```

sudo getlibs /usr/bin/zattoo_player
.......
.......
Downloading ...
Failed to download file http://archive.ubuntu.com/ubuntu/./libcurl3_7.16.4-2ubuntu1_i386.deb
The mirrors do not have the requested file or there is no internet connection.


```
Well I do have an internet connection......
Has anybody an idea where the problem is?

Following my source.list:
```

deb file:/usr/pluto/deb-cache/ ./
deb http://archive.ubuntu.com/ubuntu/ gutsy  main restricted multiverse universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-security  main restricted multiverse universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates  main restricted multiverse universe
deb http://linuxmce.com/ubuntu/ ./
deb http://deb.linuxmce.com/ubuntu/ 20dev_ubuntu  main
deb http://deb.linuxmce.com/ubuntu/ replacements_ubuntu  main

```

Thanks a lot

---

### Post by Cappy on 2008-03-16
It may be a change your distro made.
```
apt-cache show libcurl3 | grep '\.deb'
```
may show the problem.

That first lines in your sources may also be the problem. The Filename: field may be pointing at your local disk (which would explain the './').

You can use the getlibs -w option. For instance,
```
getlibs -w http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/pool/main/c/curl/libcurl3_7.16.4-2ubuntu1_i386.deb
```

---

### Post by curdegn on 2008-03-16
Dear Cappy,

Thanks for the answer. The getlibs -w option worked fine and zattoo is not missing any library any more.
```
sudo getlibs /usr/bin/zattoo_player
This application isn't missing any dependencies

```

But unfortunately the zatoo_player does still not start but end in a "Segmentation fault".

Is there a way to find out what the problem is?

Thanks again and regards
Curdegn

---

### Post by Cappy on 2008-03-17
strace can tell you why/where it is crashing but segmentation faults can be hard to debug sometimes.

---

### Post by rmtatum on 2008-03-20
I think one of the packages in Ubuntu Hardy has a bug.  I did a fresh install of Kubuntu Hardy Alpha 5 KDE4 in a virtual machine and then installed ia32-libs and gconf2.  I then installed gizmo and getlibs.  I still had the error.

However, following the same procedure as mentioned above with Kubuntu Gutsy produced no error.

---

### Post by tatojo on 2008-03-20
I just installed Acrobat Reader 8 in a hardy-server-amd64 alpha 6 with
```
sudo dpkg -i --force-all AdobeReader_enu-8.1.2-1.i386.deb
```

After asked for sudo password, had this output:
```
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package adobereader-enu.
(Reading database ... 194505 files and directories currently installed.)
Unpacking adobereader-enu (from AdobeReader_enu-8.1.2-1.i386.deb) ...
Setting up adobereader-enu (8.1.2) ...
```

and it's working!!
Is that all???

Have to say that I enter:
```
getlibs /usr/bin/acroread
Cannot determine the dependencies required by this program, it may be a script:
If this program needs a 32-bit library use:
getlibs -l i386librarytoinstall.so
If this program needs a 64-bit library use:
getlibs -64l amd64librarytoinstall.so
```

So, I typed:
```
getlibs -l i386librarytoinstall.so
No match for i386librarytoinstall.so
No packages to install
```

I want to understand if it was enough to install getlibs, and everything was setup automatically!

---

### Post by jiyosub on 2008-03-26
I'm having the exact same problem.  I still have no solution too.  :(


> **rmtatum said:**
> I think one of the packages in Ubuntu Hardy has a bug.  I did a fresh install of Kubuntu Hardy Alpha 5 KDE4 in a virtual machine and then installed ia32-libs and gconf2.  I then installed gizmo and getlibs.  I still had the error.

However, following the same procedure as mentioned above with Kubuntu Gutsy produced no error.

---

### Post by crgutierrez on 2008-03-31
Thnaks. You would like to know that I could get **[COLOR="black"]VariCad Viewer (i386)[/COLOR]** to work in my 64 bit 7.10 with the getlibs. Not so much luck with iscan for my epson scanner

---

### Post by MasterSushi on 2008-04-03
I can't seem to figure out how to use the --build or --savebuild commands. I would like to convert a 32bit .deb to a 64bit .deb using these commands but I keep getting the following output.

```

MasterSushi@Ubuntu:~$ getlibs -l --build --savebuild gizmo-project_3.1.0.79_libstdc++6_i386.deb
basename: invalid option -- -
Try `basename --help' for more information.
No match for 
No match for gizmo-project_3.1.0.79_libstdc++6_i386.deb
No packages to install

```

I am guessing that I simply don't understand how to use the --build or --savebuild commands. Does anyone know how to do what I am attempting using getlibs?

---

### Post by Cappy on 2008-04-03
Look here:
[http://ubuntuforums.org/showpost.php?p=4185776&postcount=116](http://ubuntuforums.org/showpost.php?p=4185776&postcount=116)

---

### Post by MasterSushi on 2008-04-04
After looking over that post I am guessing that the --build and --savebuild functions do not do what I thought they did.

I thought I would be able to create a .deb file that would allow a 32 bit application to be installed on a 64 bit system using the --build and --savebuild functions. It appears that this extracts libraries from a 32 bit .deb and then places them into a new .deb that can be installed on a 64 bit system, but the binaries are lost in the newly created .deb file.

---

### Post by Cappy on 2008-04-04
32-bit applications can be easily installed with ```
dpkg --force-all -i packagename.deb
```

getlibs helps with the libraries in the process.

---

### Post by MasterSushi on 2008-04-04
I know, and getlibs works great to fix any missing 32 bit libraries. I was hoping to be able to create a .deb file for someone so that they could click on the .deb and install the application. I thought that is what the --build --savebuild commands would do. I misunderstood their purpose.

---

### Post by kuja on 2008-04-15
This package is extremely useful. I'd love if it were in the ubuntu repositories. It's probalby too late for Hardy now, but a lovely script none-the-less Cappy. Maybe you could find someone to help you get the package into the archives in #ubuntu-devel on IRC Cappy?

---

### Post by tpost001 on 2008-04-15
Thanks Cappy.  I followed your suggestions after forcing the i386 version of SKYPE and getting nowhere,  I also added the missing libraries with no luck.  But after clicking on your link and installing getlib and following your advice, I got SKYPE to work on my amd64 machine running Ubuntu 7.10.  Thanks.

---

### Post by rmtatum on 2008-04-22
> **jiyosub said:**
> I'm having the exact same problem.  I still have no solution too.  :(
The latest updates to Ubuntu Hardy have fixed the problems I had with Gizmo.

---

### Post by andrebrait on 2008-04-27
this should be soon included in ubuntu's repos

---

### Post by Asere on 2008-04-30
Hi all,

I've been trying hard to get Skype installed on my Ubuntu 8.04 64 bit system.

When I want to run the > sudo dpkg -i --force-all '/home/*username*/Escritorio/skype-debian_2.0.0.68-1_i386.deb' I get the response> unable to resolve host *hostname*

When running > sudo dpkg -i --force-architecture skype-*.deb the installation starts, but gives the response > wrong architecture 'i386'

I have already installed the two needed libraries.

I run a Intel Dual Core 2 CPU.

Maybe something with the root account messed up? Earlier I already noticed that the OS has difficulties when it's supposed to be prompting for the userpassword while installing something.
Any way to repair this?

Please give detailed instructions - newbie ;) 
thanks

---

### Post by RavanH on 2008-05-02
> **Asere said:**
> Hi all,

I've been trying hard to get Skype installed on my Ubuntu 8.04 64 bit system.

When I want to run the  I get the response

When running  the installation starts, but gives the response 

I have already installed the two needed libraries.

I run a Intel Dual Core 2 CPU.

Maybe something with the root account messed up? Earlier I already noticed that the OS has difficulties when it's supposed to be prompting for the userpassword while installing something.
Any way to repair this?

Please give detailed instructions - newbie ;) 
thanks

That's funny. Just using ```
sudo dpkg -i --force-all skype-*.deb
``` and then ```
getlibs /usr/bin/skype
``` worked fine on my Ubuntu 8.04 64 bit system...

---

### Post by Sef on 2008-05-03
Thank you very much Cappy.  It seems to be working.  I will try it out later.

Update:  Gyachi is up and running. :)

---

### Post by Sarteck on 2008-05-05
Thank you SOOOOOO much!  ^_^

dfreer's site is down, and I've been having trouble getting pSX working.  With getlibs, not a problem!  Yopu're a lifesaver. :3

---

### Post by jfollmann on 2008-05-06
Wow, thanks! I used this to get Amazon MP3 downloader (which only has 32-bit binaries available) working on my 64-bit Hardy installation. I'm not sure I could have done it otherwise.

I can has DRM-free music now!

---

### Post by 8086 on 2008-05-07
Just tried your script on Opera, and it worked great!

---

### Post by RavanH on 2008-05-11
Hi Cappy,

I am trying to make my Cairo Dock how-to a bit more 'effective' by writing instructions for getting all dependencies for the plugins deb package that has to be installed alongside the cairo-dock deb (you probably know what i am talking about). The latest version has all kinds of new dependencies that 

By running the getlibs /usr/bin/cairo-dock all dependencies for the dock itself are adequately solved but the plugins require more... I was hoping that something like ```
getlibs -i cairo-dock-plug-ins_*.deb
``` would do the trick but that it doesn't (should it?).

Is there any way (option) to get getlibs to install all dependencies for any deb package -- be it with or without installing that package?

At this moment I can only think of the following instruction to get all plugin dependencies in place: ```
sudo getlibs -p libgnome2-0 gvfs libgnomevfs2-0 libgnome-keyring0 libavahi-glib1 libavahi-common3 libavahi-client3 libgnomeui-0 libvte9 libbonoboui2-0
``` and for xfce additionally ```
sudo getlibs -p libgamin0 libstartup-notification0 libthunar-vfs-1-2 libexo-0.3-0 libxfce4util4 libhal-storage1
``` (as far as I figured out so far ;) ) 

And these dependencies may change in time, as more plugins get developed ofcource...

But before I go and paste these long commands into the how-to, two questions:
1. any way to use getlibs to do these dependencies automated?
2. does getlibs need **sudo**?

Thanks for all your help,
Ravan

---

### Post by negora on 2008-05-11
I just wanted to thank Cappy for its excellent program. I'm still a  novice on Linux and this thing is helping me a lot to run some necessary 32 bits apps on Kubuntu 64 bits. Thank you!!!

---

### Post by NullHead on 2008-05-11
> **RavanH said:**
> Hi Cappy,

I am trying to make my Cairo Dock how-to a bit more 'effective' by writing instructions for getting all dependencies for the plugins deb package that has to be installed alongside the cairo-dock deb (you probably know what i am talking about). The latest version has all kinds of new dependencies that 

By running the getlibs /usr/bin/cairo-dock all dependencies for the dock itself are adequately solved but the plugins require more... I was hoping that something like ```
getlibs -i cairo-dock-plug-ins_*.deb
``` would do the trick but that it doesn't (should it?).

Is there any way (option) to get getlibs to install all dependencies for any deb package -- be it with or without installing that package?

At this moment I can only think of the following instruction to get all plugin dependencies in place: ```
sudo getlibs -p libgnome2-0 gvfs libgnomevfs2-0 libgnome-keyring0 libavahi-glib1 libavahi-common3 libavahi-client3 libgnomeui-0 libvte9 libbonoboui2-0
``` and for xfce additionally ```
sudo getlibs -p libgamin0 libstartup-notification0 libthunar-vfs-1-2 libexo-0.3-0 libxfce4util4 libhal-storage1
``` (as far as I figured out so far ;) ) 

And these dependencies may change in time, as more plugins get developed ofcource...

But before I go and paste these long commands into the how-to, two questions:
1. any way to use getlibs to do these dependencies automated?
2. does getlibs need **sudo**?

Thanks for all your help,
Ravan

I would think just installing the deb and then using "getlibs /usr/bin/programname would do it easily and more streamline instead of manually listing all the files for each flavor or Ubuntu.

---

### Post by Cappy on 2008-05-12
> **RavanH said:**
> Hi Cappy,

I am trying to make my Cairo Dock how-to a bit more 'effective' by writing instructions for getting all dependencies for the plugins deb package that has to be installed alongside the cairo-dock deb (you probably know what i am talking about). The latest version has all kinds of new dependencies that 

By running the getlibs /usr/bin/cairo-dock all dependencies for the dock itself are adequately solved but the plugins require more... I was hoping that something like ```
getlibs -i cairo-dock-plug-ins_*.deb
``` would do the trick but that it doesn't (should it?).

Is there any way (option) to get getlibs to install all dependencies for any deb package -- be it with or without installing that package?

At this moment I can only think of the following instruction to get all plugin dependencies in place: ```
sudo getlibs -p libgnome2-0 gvfs libgnomevfs2-0 libgnome-keyring0 libavahi-glib1 libavahi-common3 libavahi-client3 libgnomeui-0 libvte9 libbonoboui2-0
``` and for xfce additionally ```
sudo getlibs -p libgamin0 libstartup-notification0 libthunar-vfs-1-2 libexo-0.3-0 libxfce4util4 libhal-storage1
``` (as far as I figured out so far ;) ) 

And these dependencies may change in time, as more plugins get developed ofcource...

But before I go and paste these long commands into the how-to, two questions:
1. any way to use getlibs to do these dependencies automated?

Unfortunately, no, not from a package name. This was actually planned for the next getlibs release though. Now that I think about it, it's a really good idea and I just thought of how to do it really easily. You are a pretty good muse.

You can use getlibs -b (short for binary) to solve for library dependencies though
E.g. ```
getlibs -b /usr/share/cairo-dock/plug-in/libcd-xfce-integration.so
```

Using that command on that library for a xfce user would pull all of the 32-bit xfce libraries they are lacking.

For a gnome user,
```
getlibs -b /usr/share/cairo-dock/plug-in/libcd-gnome-integration.so
```

Without the -b getlibs just sees a library and tries to find the package name. With the -b getlibs ldds it and finds its dependencies.

> 
2. does getlibs need **sudo**?


No. The script calls sudo when it needs it (only when copying the libraries over to the system folder). The script does not need to be run with sudo but it can be.

---

### Post by RavanH on 2008-05-12
> **NullHead said:**
> I would think just installing the deb and then using "getlibs /usr/bin/programname would do it easily and more streamline instead of manually listing all the files for each flavor or Ubuntu.

Well, that is problematic in this case. The deb file i am talking about holds not a program but plugins for a program (called cairo-dock) ... so traditional method does not work... I need to get all dependencies for the plugins to work for my how-to on [http://ubuntuforums.org/showthread.php?t=613087](http://ubuntuforums.org/showthread.php?t=613087)

----

But I have to report another success story: Installing Salasaga ( [http://www.salasaga.org/index.php/download](http://www.salasaga.org/index.php/download) for Flash movie creation) from the 32bit package and using getlibs to do the dependencies worked like a charm :)

Who needs M$ now?

---

### Post by RavanH on 2008-05-12
> **Cappy said:**
> Unfortunately, no, not from a package name. This was actually planned for the next getlibs release though. Now that I think about it, it's a really good idea and I just thought of how to do it really easily. You are a pretty good muse.

You can use getlibs -b (short for binary) to solve for library dependencies though
E.g. ```
getlibs -b /usr/share/cairo-dock/plug-in/libcd-xfce-integration.so
```

Using that command on that library for a xfce user would pull all of the 32-bit xfce libraries they are lacking.

For a gnome user,
```
getlibs -b /usr/share/cairo-dock/plug-in/libcd-gnome-integration.so
```

Without the -b getlibs just sees a library and tries to find the package name. With the -b getlibs ldds it and finds its dependencies.



No. The script calls sudo when it needs it (only when copying the libraries over to the system folder). The script does not need to be run with sudo but it can be.

Excellent ! :) I can work with that... However, I can't wait for that next release to make life even easier ;)

---

### Post by RavanH on 2008-05-13
> **Cappy said:**
> ...You can use getlibs -b (short for binary) to solve for library dependencies though
E.g. ```
getlibs -b /usr/share/cairo-dock/plug-in/libcd-xfce-integration.so
```...

Will getlibs handle wildcard? So would ```
getlibs -b /usr/share/cairo-dock/plug-in/*.so
``` generate any effect? When I try it, I get the response "This application isn't missing any dependencies" but that might not be an indication of success...

---

### Post by RavanH on 2008-05-13
> **Cappy said:**
> ...
Without the -b getlibs just sees a library and tries to find the package name. With the -b getlibs ldds it and finds its dependencies...

Oh, and you might want to put this neat little option in the --help text :)

---

### Post by Cappy on 2008-05-14
> **RavanH said:**
> Will getlibs handle wildcard? So would ```
getlibs -b /usr/share/cairo-dock/plug-in/*.so
``` generate any effect? When I try it, I get the response "This application isn't missing any dependencies" but that might not be an indication of success...

Getlibs ignores subsequent commands after a binary is given so getlibs is really just checking the first match.

You can use
```
for i in /usr/share/cairo-dock/plug-in/*.so; do echo "$i"; getlibs -b "$i"; done;
```
though.

---

### Post by RavanH on 2008-05-14
> **Cappy said:**
> ...```
for i in /usr/share/cairo-dock/plug-in/*.so; do echo "$i"; getlibs -b "$i"; done;
```
...

WHOOOOT ! That works a treat, thanks :)

---

### Post by soxs on 2008-05-18
I am sorry to kill the peace... but strangely it does not work for me, though it worked 6 months ago like a charm.

```
 sudo getlibs -l libpng.so.3

```
```
 sudo getlibs -l i386libpng.so.3

```
does not do anything, atl least I get zer0 output messsages.

I have all repositories enabled (if that is a matter of fact, but I do not think so)

Edit: I allready have a lib called libpng.so.3 ```
/usr/lib/libpng.so.3
``` but I guesss thats 64bit version of what I need/ tipp10 (the program I want to run smoooth) requires.

---

### Post by Cappy on 2008-05-18
getlibs relies on [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and the site is apparently down
You can use the package name though:
```
sudo getlibs -p libpng3
```

There's also an option for apt-file, if you happen to have that installed.

---

### Post by kripz on 2008-05-18
how do i remove files? i accidently installed libqt4-core and libqt4-gui. I dont need them anymore...

---

### Post by ZOMGxuan on 2008-05-31
It would be very helpful if getlibs also installed the dependencies of the library packages that are installed. Otherwise one would have to do it manually.

For example
```
getlibs -p build-essential
```
currently does nothing, instead of installing the 32bit development libraries.

---

### Post by soxs on 2008-05-31
> **kripz said:**
> how do i remove files? i accidently installed libqt4-core and libqt4-gui. I dont need them anymore... Don't care about that, it doesn't hurt at all if you have some additional 32bit libraries, it doesn't hurt at all.

---

### Post by MdaG on 2008-06-01
I just wanted to chip in and says thanks! Thanks to this script I finally won the war on pSX :)
It works and I can finally run my old PSX games in Linux.

Just one question, does getlibs track changes or do I need to keep a mental note on which libraries it has installed? 
In short, is there such a thing as "rmlibs"?

Not that it hurts to have a few additional libs installed...

---

### Post by serpiko.. on 2008-06-13
oh thanks for the great post, it worked just like you mentioned even 1 year after you posted it so a great thanks again
serpiko

---

### Post by ViRMiN on 2008-06-13
Cappy's script's come in useful for a lot of people, he's done a good job to create it.  Well done Cappy! :D

---

### Post by dazzlindonna on 2008-06-19
jfollman, i don't suppose you'd be willing to give exact instructions for a newbie to getting amazon downloader working with this?  assume some of us know little.  :)

---

### Post by Cappy on 2008-06-19
> **dazzlindonna said:**
> jfollman, i don't suppose you'd be willing to give exact instructions for a newbie to getting amazon downloader working with this?  assume some of us know little.  :)

Right here:
[http://ubuntuforums.org/showpost.php?p=5194828&postcount=52](http://ubuntuforums.org/showpost.php?p=5194828&postcount=52)

---

### Post by stinkinrich88 on 2008-06-22
sorry if this was already asked but is there a way to uninstall the 32bit libraries?

---

### Post by Cappy on 2008-06-22
> **stinkinrich88 said:**
> sorry if this was already asked but is there a way to uninstall the 32bit libraries?

No, sorry. That will be in the next version of getlibs.

---

### Post by runekock on 2008-06-28
Thanks for this great script.  By using it, I could easily get Zattoo working on my system (Debian unstable).

I had to add the following lines to the "stored list" in getlibs:
libcares.so.2 libc-ares2
libssh2.so.1 libssh2-1

Zattoo still tries to load the 64-bit version of libpixbufloader-png.so, even with the 32-bit lib installed.  Zattoo also failed to find flash player, until I copied libflashplayer.so to ~/.mozilla/plugins (is that wise?).  Probably out of scope for getlibs to deal with these two problems.


Rune

---

### Post by PaulW89 on 2008-07-02
Hi,
thank you for this script!

I use Ubuntu Hardy AMD64 and I need ld and as for i386 architecture.

But something didn't work:
```
getlibs -p /usr/bin/ld
The following i386 packages will be installed: /usr/bin/ld
Continue [Y/n]? Y
W: Package /usr/bin/ld not found
E: No packages found
/usr/bin/ld was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install

```

How can I install the missing repositories for i386?

Thank you!

Paul

---

### Post by Cappy on 2008-07-02
You don't need the 32-bit version of ld.

I'm guessing you are trying to compile 32-bit programs on a 64-bit computer. There are a few thread on that:
[http://ubuntuforums.org/showthread.php?t=790607&highlight=multilib](http://ubuntuforums.org/showthread.php?t=790607&highlight=multilib)
[http://ubuntuforums.org/showthread.php?t=843887&highlight=multilib](http://ubuntuforums.org/showthread.php?t=843887&highlight=multilib)
[http://ubuntuforums.org/showthread.php?t=779280&highlight=multilib](http://ubuntuforums.org/showthread.php?t=779280&highlight=multilib)

---

### Post by stoodleysnow on 2008-08-01
Thanks very much, I can now play stepmania!:guitar:

---

### Post by nzadLithium on 2008-08-08
Hey

Getlibs has worked for me before, but for some reason it keeps telling me that theres no match for 'libdirect-0.9.so.25'. I'm trying to run unreal tournament 2004 (which worked for me on feisty. Then i upgraded to gutsy and it stopped going, I didnt bother fixing it. Now i decided i want to play (i'm on hardy now :D ).

I have tried using the program on both the 32bit and 64bit binaries but neither worked. I have a more up to date version of 64bit libdirectfb (ver 1. something) already installed, but UT has always had problems following symlinks on this pc :S

I can go through manually and copy all my lib files then rename them to old version names, but thats kind of a pain.

I am wondering why getlibs is not finding the 64bit or 32bit libraries (and also if anyone knows of a way to get ut to follow symlinks).

Help plz :S

---

### Post by Cappy on 2008-08-08
There's no problem with getlibs, libdirect-0.9.so.25 isn't in the Hardy repos.
You can use ```
sudo getlibs -l libdirect-1.0.so.0
```
or
```
sudo getlibs -p libdirectfb-1.0-0
```
to install the 32-bit libdirectfb-1.0-0

---

### Post by ronnieredd on 2008-08-08
Adding my thanks to the growing masses.
Installing ibm5250 terminal emulator Iseries.
Get the latest 
Download the latest version (32bit is the only version with an emulator) RPM package. Use alien to turn it into a deb
```
sudo dpkg -i --force-all /YOURDIRECTORY/iseriesaccess_5.4.0-2.4_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package iseriesaccess.
(Reading database ... 204832 files and directories currently installed.)
Unpacking iseriesaccess (from .../iseriesaccess_5.4.0-2.4_i386.deb) ...
Setting up iseriesaccess (5.4.0-2.4) ...

Configuration file `/opt/ibm/iSeriesAccess/etc/cwb_defaultprefs.ini', does not exist on system.
Installing new config file as you request.
post install processing for iSeriesAccess 1.4...configure
iSeries Access ODBC Driver has been deleted (if it existed at all) because its usage count became zero
odbcinst: Driver installed. Usage count increased to 1. 
    Target directory is /etc
Locale en_US not found ( using locale -a ) this may cause the IBM 5250 emulator to fail.
Generating the locale en_US using locale-gen utility.
Generating locales...
  en_US.ISO-8859-1... done
Generation complete.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
ronnie@yyz:~$ ibm5250 
ibm5250: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
ronnie@yyz:~$ getlibs /usr/bin/ibm5250
Cannot determine the dependencies required by this program, it may be a script:
If this program needs a 32-bit library use:
getlibs -l i386librarytoinstall.so
If this program needs a 64-bit library use:
getlibs -64l amd64librarytoinstall.so
ronnie@yyz:~$ ibm5250 
ibm5250: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
ronnie@yyz:~$ getlibs -l libXm.so.3
libXm.so.3: libmotif3
The following i386 packages will be installed:
libmotif3
Continue [Y/n]? y
Downloading ...
Installing libraries ...
ronnie@yyz:~$ ibm5250 
5250: [ INFORMATIONAL ]: Build Date: September 2006 (1.2).
```
Thank You!
I'm going to try to brave a gdesklet install now.:popcorn:

---

### Post by KrossX on 2008-08-08
Worked like a charm! I love you more than a beer now!

---

### Post by IntuitiveNipple on 2008-08-16
There's a couple of bugs in the script that are quite insidious.

I was trying to use getlibs from within a package *postinst* script to ease the installation of required 32-bit libs and couldn't figure out why the postinst script was failing with an error when calling getlibs because it returned a non-zero result.

I added "set -x" to the start of getlibs and analysed the output. As a result I found:

[list=1]
[*] final exit code depends on an earlier command and doesn't return success/true/0 when it should
[*] mktemp statement is faulty
[/list]

The final "exit" without a return-code means that the exit-code returned to the caller is that of the last executed command. In this case the 
```

if [ -n "$binarypath" ]
```
which returned false (non-zero).

The final exit needs to explictly set the success/true/0 return value:
```

        parameters="$dependencylist"
    else
        exit 0 #No new dependencies
    fi
else
    exit 0
fi
done

```

The creation of the temporary directory causes the execution of clean_up_err():
```

++ mktemp -d /tmp/getlibs.XXXXXXXXXX
++ clean_up_err
++ rm -rf
++ exit 1
+ tempdir=/tmp/getlibs.hspjx28935

```

It is caused by an error in:
```

tempdir=`mktemp -d /tmp/getlibs.XXXXXXXXXX || echo "Unable to create temp directory in /tmp"; clean_up_err`

```
This code doesn't do what is intended since the call to clean_up_err **follows a statement terminator semi-colon** and is therefore always executed. It is luck that it is also inside the child-shell call and therefore $tempdir hasn't got a value.

It should be like this:
```

tempdir=`mktemp -d /tmp/getlibs.XXXXXXXXXX` || `echo "Unable to create temp directory in /tmp"; clean_up_err`

```
I'm still not happy with that logic since the *error* needs to chain two commands - I'd rather split it up:
```

tempdir=`mktemp -d /tmp/getlibs.XXXXXXXXXX`
if [ $? -ne 0 ]; then
	echo "Unable to create temp directory in /tmp"
	clean_up_err`
fi

```

---

### Post by IntuitiveNipple on 2008-08-17
I've packaged getlibs to make it easier to install and maintain. The package uses correct Debian control and configuration and is available from my PPA (Personal Package Archive).

Add my PPA to the sources list:
```

sudo sh -c "echo 'deb http://ppa.launchpad.net/intuitivenipple/ubuntu $(lsb_release -sc) main' >/etc/apt/sources.list.d/intuitivenipple.list"
sudo sh -c "echo 'deb-src http://ppa.launchpad.net/intuitivenipple/ubuntu $(lsb_release -sc) main' >>/etc/apt/sources.list.d/intuitivenipple.list"
sudo apt-get update

```

Install getlibs:
```

sudo apt-get install getlibs

```

---

### Post by snakep on 2008-08-20
I've installed getlibs, and I'm trying to use it to fix devede.  I am running 64-bit Gutsy, and the latest version of devede available for 64-bit is quite old.  I downloaded the deb for devede and installed it by 
```
 sudo dpkg -i --force-all devede_3.10-0~rastersoft1_all.deb
```
However, devede is actually a perl script, so when I run getlibs, I get 
```
Cannot determine the dependencies required by this program, it may be a script:
If this program needs a 32-bit library use:
getlibs -l i386librarytoinstall.so
If this program needs a 64-bit library use:
getlibs -64l amd64librarytoinstall.so

```
There were some problems that were reported when I installed devede.  It needed imagemagick, so I installed that via Synaptic, and then devede worked.  

Here's the problem: Synaptic now thinks that devede is broken and should be removed.  Also, when I open the Update Manager, it says that the software index is broken, and I should run 
```
sudo apt-get install -f
```
When I do that, it asks to remove devede, which is defeats the purpose.  

Is there a way to fix this?  Will getlibs help me?

Thanks in advance,

Jeremiah

---

### Post by jw5801 on 2008-08-20
> **snakep said:**
> I've installed getlibs, and I'm trying to use it to fix devede.  I am running 64-bit Gutsy, and the latest version of devede available for 64-bit is quite old.  I downloaded the deb for devede and installed it by 
```
 sudo dpkg -i --force-all devede_3.10-0~rastersoft1_all.deb
```
However, devede is actually a perl script, so when I run getlibs, I get 
```
Cannot determine the dependencies required by this program, it may be a script:
If this program needs a 32-bit library use:
getlibs -l i386librarytoinstall.so
If this program needs a 64-bit library use:
getlibs -64l amd64librarytoinstall.so

```
There were some problems that were reported when I installed devede.  It needed imagemagick, so I installed that via Synaptic, and then devede worked.  

Here's the problem: Synaptic now thinks that devede is broken and should be removed.  Also, when I open the Update Manager, it says that the software index is broken, and I should run 
```
sudo apt-get install -f
```
When I do that, it asks to remove devede, which is defeats the purpose.  

Is there a way to fix this?  Will getlibs help me?

Thanks in advance,

Jeremiah

Hardy has [version 3.6](http://packages.ubuntu.com/hardy/devede) in its repositories. You may wind up with a bunch of dependencies that you need newer versions of, but it's probably worth a shot. I'd try adding the hardy repository to your repo list and then installing it using apt and seeing what it'll ask you to upgrade and whether it'll break anything. Don't upgrade absolutely everything though, unless you want to upgrade to Hardy.

---

### Post by Felson on 2008-09-03
@Cappy
Thanks for this awesome script! You just removed about 45 lines from my ePSXe how-to. Wish I would have found this when I was doing that the first time.

---

### Post by yoyoq on 2008-09-05
and my thanks as well

(worked for coot binary on 64bit machine,  after trying for
days to compile the damn code)

---

### Post by Felson on 2008-09-16
feature request....
It would be nice to be able to do the following
```

getlibs /path/to/some/local/file.so

```
and have it check for the dependencies for the local file instead of trying to find a source for, and install "file.so".

---

### Post by NullHead on 2008-09-16
Are you still developing getlibs? I remember you saying something about it being included in 8.10s repo, but I can't remember, so I'll ask again. 

Will Getlibs be in the ubuntu repository any time soon?

---

### Post by Cappy on 2008-09-16
> **Felson said:**
> feature request....
It would be nice to be able to do the following
```

getlibs /path/to/some/local/file.so

```
and have it check for the dependencies for the local file instead of trying to find a source for, and install "file.so".

```

getlibs --binary /path/to/some/local/file.so

```

I ended up doing it that way because some people tried using the path + library name instead of just the library name.

> **NullHead said:**
> Are you still developing getlibs? I remember you saying something about it being included in 8.10s repo, but I can't remember, so I'll ask again. 

Will Getlibs be in the ubuntu repository any time soon?

No, I planned to make getlibs compatible with dpkg and add a man page before I submitted. I didn't ever finish when I realized that getlibs would always be reliant on packages.ubuntu.com and thus is not suited for a repository since I handled html "parsing" through bash and changes to packages.ubuntu.com could make getlibs stop functioning at the time of a distro release (when packages.ubuntu.com is updated).
There are some other programs that cache the package lists to make it possible to not use packages.ubuntu.com but they are a bit buggy and extremely slow at building their cache.

---

### Post by Felson on 2008-09-16
@Cappy
LOL Thanks. And thanks for not telling me to RTFM... :p Figures it was already in there.

---

### Post by doorknob60 on 2008-09-20
It's broken in Intrepid, any ideas? [http://ubuntuforums.org/showthread.php?t=924895](http://ubuntuforums.org/showthread.php?t=924895)

EDIT: Fixed it, packages like libqt4-gui in intrepid are just dummy packages, which don't really do anything. manually istalling the real packages with sudo getlibs -p libqtgui4 (for example) is working. :) I guess only testing with Skype isn't the best, but I didn't get any errors (besides the Skype ones of course) so I was really stumped.

---

### Post by grandtxred on 2008-09-23
I was trying to get bomgar rep client for remote support to work without success and this really came in and saved me time and saved my day.  THANK YOU!!

Mike

---

### Post by dj_deef on 2008-10-01
I ran getlibs -l with these arguments:

libwx_gtk2u_core-2.8.so.0
libwx_baseu-2.8.so.0
libavformat.so.1d
libavcodec.so.1d
libavutil.so.1d
libtheora.so.0
libvorbisenc.so.2
libraw1394.so.8
libvorbis.so.0
libswscale.so.1d
libdc1394_control.so.13
libgsm.so.1
libgio.so
libgiogconf.so
libgvfsdbus.so
libgiohal-volume-monitor.so

Now I want to completely remove all the i386 packages installed with this way.
How can I do?

---

### Post by Yellow Pasque on 2008-10-01
Look in your /usr/lib32 directory and remove them?

---

### Post by dj_deef on 2008-10-01
I hoped there was a better and faster way.

---

### Post by Yellow Pasque on 2008-10-01
Heh, it's been 3 hours since you posted. You could have had them removed by now.

Out of curiosity, why do you want to remove them?

---

### Post by dj_deef on 2008-10-01
because every line that's written up implies the removal of more than one file (so they are many files) and I'm afraid to delete something that has not to be deleted

---

### Post by fluffman86 on 2008-10-14
Thanks for this program, Cappy.  I was starting to get pretty ticked (and still kinda am ticked) at Amazon for their mp3 downloader breaking on Ubuntu 8.04.1.  I really didn't want to have to put a call in to them.

Anyway, great program, now I can get music again!

:guitar:

---

### Post by wangmaster on 2008-10-20
Given that getlibs basically fetches the i386 deb package, and pulls out the appropriate library and places them into /lib32|/usr/lib32 tree this is not really suitable for libraries that contain modules built using a fixed libdir location right?  For example, the gnome-vfs and gconf modules generally have a libdir location of /usr/lib/[gnome-vfs|gconf] or something like that.

---

### Post by Cappy on 2008-10-20
> **wangmaster said:**
> Given that getlibs basically fetches the i386 deb package, and pulls out the appropriate library and places them into /lib32|/usr/lib32 tree this is not really suitable for libraries that contain modules built using a fixed libdir location right?  For example, the gnome-vfs and gconf modules generally have a libdir location of /usr/lib/[gnome-vfs|gconf] or something like that.

Right, for those libraries with fixed locations you have to use sed and replace /usr/lib with /usr/l32 (which would be a link to /usr/lib32, keeps same number of bytes).

Example:
[http://ubuntuforums.org/showpost.php?p=4757395&postcount=17](http://ubuntuforums.org/showpost.php?p=4757395&postcount=17)

It can easily be done automatically, if you wanted to add a loop in the script to do it.

---

### Post by wangmaster on 2008-10-20
> **Cappy said:**
> Right, for those libraries with fixed locations you have to use sed and replace /usr/lib with /usr/l32 (which would be a link to /usr/lib32, keeps same number of bytes).

Example:
[http://ubuntuforums.org/showpost.php?p=4757395&postcount=17](http://ubuntuforums.org/showpost.php?p=4757395&postcount=17)

It can easily be done automatically, if you wanted to add a loop in the script to do it.

That works for things that have a loader configuration file, but for example for gnome-vfs where the modules are relative to a libpath built into libgnomevfs-2.so this technique won't work either right?  I haven't had the itch to configure a 32-bit libgnomevfs for freedesktop mime database support on ubuntu yet, but i did so on gentoo and had to build libgnomevfs with LIBDIR set to /usr/lib32 in order for it to work.

I never figured out a trick (LD_LIBRARY_PATH, LD_PRELOAD, etc etc) that got around that, but if you did get around that, I'd love to know how.

---

### Post by Cappy on 2008-10-21
> **wangmaster said:**
> That works for things that have a loader configuration file, but for example for gnome-vfs where the modules are relative to a libpath built into libgnomevfs-2.so this technique won't work either right?  I haven't had the itch to configure a 32-bit libgnomevfs for freedesktop mime database support on ubuntu yet, but i did so on gentoo and had to build libgnomevfs with LIBDIR set to /usr/lib32 in order for it to work.

I never figured out a trick (LD_LIBRARY_PATH, LD_PRELOAD, etc etc) that got around that, but if you did get around that, I'd love to know how.

That technique is for binaries/libraries such as libgnomevfs-2.so. That's why you have to keep the path length the same, so you don't change the offset in the binary.

---

### Post by wangmaster on 2008-10-21
> **Cappy said:**
> That technique is for binaries/libraries such as libgnomevfs-2.so. That's why you have to keep the path length the same, so you don't change the offset in the binary.

I need to read for content better.  I saw the first sed line modifying the loader txt file, but not the second sed line modifying the .so itself.

Neat trick, thanks for the info :)

---

### Post by jairoalejandros on 2008-10-23
OK first thing first, YOU ARE THE MAN, thanks a lot. Done that, I could finally intall skype on my computer, the problem was i have a intel centrino duo 32 and i keep getting the Wrong Architecture 'i386' BS but now its working good. THANKS MAN.

---

### Post by asta on 2008-10-28
```
lrwxrwxrwx 1 root   root        18 Oct 23 17:32 libstdc++.so.6 -> libstdc++.so.6.0.9
drwxr-xr-x 3 root   root      4096 Oct 28 13:38 xulrunner
drwxr-xr-x 2 root   root      4096 Oct 28 13:38 pkgconfig
lrwxrwxrwx 1 root   root        12 Oct 28 13:38 libxul.so -> libxul.so.0d
lrwxrwxrwx 1 root   root        18 Oct 28 13:38 libxpcomglue.so -> libxpcomglue.so.0d
lrwxrwxrwx 1 root   root        14 Oct 28 13:38 libxpcom.so -> libxpcom.so.0d
lrwxrwxrwx 1 root   root        20 Oct 28 13:38 libgtkembedmoz.so -> libgtkembedmoz.so.0d

```

Running Kubunt 8.05 on AMD 64 and I'm trying to fix my firefox32 dependency problem. 

The above is (last part of) the result I get when 'ls -lrt' of /usr/lib32. I installed libxul using:

```
getlibs -l libxul.so

```

So, it creates symlinks but does not install any libs? Getlibs 2.06.

---

### Post by skipperczt on 2008-11-23
Used this to install amazon mp3 downloader, works great!

---

### Post by twisted_steel on 2008-12-07
> **skipperczt said:**
> Used this to install amazon mp3 downloader, works great!

Me too.  Thanks Cappy!

---

### Post by kjb34 on 2009-01-01
I can't get getlibs to work with Amazon mp3 downloader. I typed getlibs -p amazonmp3.deb and it initially works and ask if i want to continue i type yes and it says that it can't find it in my repos

---

### Post by Kilz on 2009-01-01
> **kjb34 said:**
> I can't get getlibs to work with Amazon mp3 downloader. I typed getlibs -p amazonmp3.deb and it initially works and ask if i want to continue i type yes and it says that it can't find it in my repos


Is the file one you downloaded, or is it in the Ubuntu repositories? Getlibs can access 32bit applications in the 32bit repositories. But if its one that you downloaded, getlibs doesn't know what it is or where its at.

---

### Post by kjb34 on 2009-01-02
I downloaded it. I didn't know it was in the Ubuntu repos.

---

### Post by Kilz on 2009-01-02
> **kjb34 said:**
> I downloaded it. I didn't know it was in the Ubuntu repos.

It may not be, but if it isnt , getlibs cant find it with that command.

---

### Post by kjb34 on 2009-01-02
gotcha

---

### Post by oldos2er on 2009-01-02
> **kjb34 said:**
> I can't get getlibs to work with Amazon mp3 downloader. I typed getlibs -p amazonmp3.deb and it initially works and ask if i want to continue i type yes and it says that it can't find it in my repos

 You should try this software instead of Amazon's MP3 downloader: [http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)

---

### Post by Hated On Mostly on 2009-01-14
> **kjb34 said:**
> I can't get getlibs to work with Amazon mp3 downloader. I typed getlibs -p amazonmp3.deb and it initially works and ask if i want to continue i type yes and it says that it can't find it in my repos

[http://www.ensode.net/roller/dheffelfinger/entry/installing_amazon_mp3_downloader_under](http://www.ensode.net/roller/dheffelfinger/entry/installing_amazon_mp3_downloader_under)

Install amazon mp3 downloader

```
sudo dpkg -i --force-architecture amazonmp3.deb
```

Install libraries using getlibs:

```

sudo getlibs /usr/bin/amazonmp3
```

---

### Post by elfprince13 on 2009-01-17
I need to get a copy of the 32bit libGLU.a. I tried reinstalling libgl1-mesa-dev with getlibs, but it's still missing libGLU.a.

[edit]
my bad it should have been libglu1-mesa-dev

---

### Post by kjb34 on 2009-01-18
> **Hated On Mostly said:**
> [http://www.ensode.net/roller/dheffelfinger/entry/installing_amazon_mp3_downloader_under](http://www.ensode.net/roller/dheffelfinger/entry/installing_amazon_mp3_downloader_under)

Install amazon mp3 downloader

```
sudo dpkg -i --force-architecture amazonmp3.deb
```

Install libraries using getlibs:

```

sudo getlibs /usr/bin/amazonmp3
```

That worked like a charm. thanks a bunch

---

### Post by rocketero2008 on 2009-01-28
> **Cappy said:**
> I'll do that =)


libsipphoneapi.so.1.7.07.73 is only available inside the gizmo package. I downloaded [http://download.gizmoproject.com/GizmoDownload/gizmo-project_3.1.0.79_libstdc++6_i386.deb](http://download.gizmoproject.com/GizmoDownload/gizmo-project_3.1.0.79_libstdc++6_i386.deb) and saw it inside to be installed to /usr/lib/libsipphoneapi.so.1.7.07.73
so you should be able to 
```
sudo cp /usr/lib/libsipphoneapi.so.1.7.07.73 /usr/lib32/libsipphoneapi.so.1.7.07.73
```

or you can try out the beta getlibs feature --build and do
```
getlibs --build --savebuild -i gizmo-project_3.1.0.79_libstdc++6_i386.deb
```
which will create a package with just /usr/lib32/libsipphoneapi.so.1.7.07.73 and install it.

Didn't work for me, I can open gizmo but when I click on 'connect' or in 'register new account' I get a popup saying that the connection was lost.

---

### Post by dreamnid on 2009-02-03
I'm having trouble getting getlibs from the URL provided for the past few days. I'm guessing the site is down.

Anybody has a mirror?

Thanks!

---

### Post by davy724 on 2009-02-15
hi dont know if u can help but i just bought an album on amazon mp3 downloader bot it says can't connet. check your  internet connection and retry download. am a complete aateur with computers. cann u help?

---

### Post by Cappy on 2009-02-15
Try installing
```
sudo apt-get install lib32nss-mdns
```

---

### Post by dryder on 2009-02-16
Hi,

As a long shot, would this help installing the 32-bit driver for the Epson 4490 so it will work in 64bit installation?

A lot of people can not get the driver to install in 64 bit and there isn't a 64bit driver.

David

---

### Post by arch0njw on 2009-02-25
> **crjackson said:**
> Thanks Cappy, just used getlibs to help install amazonmp3 downlolader.  I don't know how to make it grab all the libs at once, but it got them for me one at a time until the app was installed.

I second this thanks.  This is working nicely under Kubuntu 8.04.2 64-bit.

---

### Post by oldos2er on 2009-02-25
> **davy724 said:**
> hi dont know if u can help but i just bought an album on amazon mp3 downloader bot it says can't connet. check your  internet connection and retry download. am a complete aateur with computers. cann u help?

 Use this software: [http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)

---

### Post by phillipsrich on 2009-03-05
Citrix Receiver Manager - Help

myid@myhostname:/usr/lib32$ /usr/lib/ICAClient/wfcmgr /usr/lib/ICAClient/wfcmgr: error while loading shared libraries: libXm.so.4: cannot open shared object file: No such file or directory

myid@myhostname:/usr/lib32$ getlibs /usr/lib/ICAClient/wfcmgr 
No match for libXm.so.4
No packages to install

ls -al libX*
lrwxrwxrwx 1 root root     15 2009-03-04 00:54 libX11.so.6 -> libX11.so.6.2.0 -rw-r--r-- 1 root root 971436 2008-10-08 07:59 libX11.so.6.2.0
lrwxrwxrwx 1 root root     15 2009-03-04 00:54 libXau.so.6 -> libXau.so.6.0.0 -rw-r--r-- 1 root root   7408 2008-05-19 03:20 libXau.so.6.0.0
lrwxrwxrwx 1 root root     15 2009-03-04 00:54 libXaw3d.so -> libXaw3d.so.6.1 
lrwxrwxrwx 1 root root     15 2009-03-04 00:54 libXaw3d.so.6 -> libXaw3d.so.6.1 -rw-r--r-- 1 root root 285584 2007-05-15 14:48 libXaw3d.so.6.1
lrwxrwxrwx 1 root root     16 2009-03-04 00:54 libXaw7.so.7 -> libXaw7.so.7.0.0 -rw-r--r-- 1 root root 374152 2008-05-19 03:38 libXaw7.so.7.0.0
lrwxrwxrwx 1 root root     12 2009-03-04 00:54 libXaw.so.7 -> libXaw7.so.7
lrwxrwxrwx 1 root root     22 2009-03-04 00:54 libXcomposite.so.1 -> libXcomposite.so.1.0.0 -rw-r--r-- 1 root root   9452 2008-06-01 06:40 libXcomposite.so.1.0.0
lrwxrwxrwx 1 root root     19 2009-03-04 00:54 libXcursor.so.1 -> libXcursor.so.1.0.2 -rw-r--r-- 1 root root  33152 2007-10-24 00:39 libXcursor.so.1.0.2
lrwxrwxrwx 1 root root     19 2009-03-04 00:54 libXdamage.so.1 -> libXdamage.so.1.1.0 -rw-r--r-- 1 root root   6260 2008-05-19 03:31 libXdamage.so.1.1.0
lrwxrwxrwx 1 root root     17 2009-03-04 00:54 libXdmcp.so.6 -> libXdmcp.so.6.0.0 -rw-r--r-- 1 root root  16628 2008-05-19 02:55 libXdmcp.so.6.0.0
lrwxrwxrwx 1 root root     16 2009-03-04 00:54 libXext.so.6 -> libXext.so.6.4.0 -rw-r--r-- 1 root root  55772 2008-05-02 23:03 libXext.so.6.4.0
lrwxrwxrwx 1 root root     18 2009-03-04 00:54 libXfixes.so.3 -> libXfixes.so.3.1.0 -rw-r--r-- 1 root root  14128 2007-04-27 08:59 libXfixes.so.3.1.0
lrwxrwxrwx 1 root root     15 2009-03-04 00:54 libXft.so.2 -> libXft.so.2.1.2 -rw-r--r-- 1 root root  75700 2008-06-17 01:12 libXft.so.2.1.2
lrwxrwxrwx 1 root root     20 2009-03-04 00:54 libXinerama.so.1 -> libXinerama.so.1.0.0 -rw-r--r-- 1 root root   6528 2008-05-19 06:09 libXinerama.so.1.0.0
lrwxrwxrwx 1 root root     14 2009-03-04 00:54 libXi.so.6 -> libXi.so.6.0.0 -rw-r--r-- 1 root root  34232 2008-10-18 03:08 libXi.so.6.0.0
lrwxrwxrwx 1 root root     15 2009-03-04 00:54 libXmu.so.6 -> libXmu.so.6.2.0 -rw-r--r-- 1 root root  89624 2008-01-23 11:49 libXmu.so.6.2.0
lrwxrwxrwx 1 root root     16 2009-03-04 00:54 libXmuu.so.1 -> libXmuu.so.1.0.0 -rw-r--r-- 1 root root  10432 2008-01-23 11:49 libXmuu.so.1.0.0
lrwxrwxrwx 1 root root     16 2009-03-04 00:54 libXpm.so.4 -> libXpm.so.4.11.0 -rw-r--r-- 1 root root  63624 2007-10-24 01:28 libXpm.so.4.11.0
lrwxrwxrwx 1 root root     14 2009-03-04 00:54 libXp.so.6 -> libXp.so.6.2.0 -rw-r--r-- 1 root root  30356 2008-07-08 03:34 libXp.so.6.2.0 
lrwxrwxrwx 1 root root     18 2009-03-04 00:54 libXrandr.so.2 -> libXrandr.so.2.1.0 -rw-r--r-- 1 root root  25912 2008-08-27 17:47 libXrandr.so.2.1.0
lrwxrwxrwx 1 root root     19 2009-03-04 00:54 libXrender.so.1 -> libXrender.so.1.3.0 -rw-r--r-- 1 root root  34352 2008-06-14 01:36 libXrender.so.1.3.0
lrwxrwxrwx 1 root root     15 2009-03-04 00:54 libXss.so.1 -> libXss.so.1.0.0 -rw-r--r-- 1 root root   9656 2008-05-02 23:56 libXss.so.1.0.0
lrwxrwxrwx 1 root root     17 2009-03-04 00:54 libXTrap.so.6 -> libXTrap.so.6.4.0 -rw-r--r-- 1 root root  31036 2008-06-18 13:37 libXTrap.so.6.4.0
lrwxrwxrwx 1 root root     14 2009-03-04 00:54 libXt.so.6 -> libXt.so.6.0.0 -rw-r--r-- 1 root root 326564 2007-05-21 05:27 libXt.so.6.0.0
lrwxrwxrwx 1 root root     16 2009-03-04 00:54 libXtst.so.6 -> libXtst.so.6.1.0 -rw-r--r-- 1 root root  17500 2007-11-14 04:05 libXtst.so.6.1.0
lrwxrwxrwx 1 root root     14 2009-03-04 00:54 libXv.so.1 -> libXv.so.1.0.0 -rw-r--r-- 1 root root  17848 2008-06-13 02:42 libXv.so.1.0.0
lrwxrwxrwx 1 root root     19 2009-03-04 00:54 libXxf86vm.so.1 -> libXxf86vm.so.1.0.0 -rw-r--r-- 1 root root  17820 2008-08-04 17:29 libXxf86vm.so.1.0.0


Any thoughts?
Rich

---

### Post by arch0njw on 2009-03-05
> **phillipsrich said:**
> Citrix Receiver Manager - Help

myid@myhostname:/usr/lib32$ /usr/lib/ICAClient/wfcmgr /usr/lib/ICAClient/wfcmgr: error while loading shared libraries: libXm.so.4: cannot open shared object file: No such file or directory

myid@myhostname:/usr/lib32$ getlibs /usr/lib/ICAClient/wfcmgr 
No match for libXm.so.4
No packages to install

...SNIP...

Any thoughts?
Rich
*I am running opensuse10*[I].2 x86_64.

To get the citrix client working (it is 32bit ICAClient-[/I] *10.6-1.i386.*[I]rpm) you need to trick it into thinking you have an older version of the motif libraries:
[/I] * 1) you need to install the 32bit openmotif-*[I]libs-32bit.
2) You need to rpm install the citrix RPM with --nodeps
rpm --nodeps -i ICAClient-[/I]*10.6-1.i386.*[I]rpm
3) You need to symlink the libXm.so.4[/I][I] to libXm.so.3
ln -s /usr/lib/l[/I]*ibXm.so.4 /usr/lib/l*[I]ibXm.so.3

Now you can run the client and connection[/I] [I] manager:
/usr/lib/I[/I]*CAClient/wfi*[I]ca
/usr/lib/I[/I]*CAClient/wfc**mgr*

--- which is quoted from this thread here:  [http://forums.citrix.com/thread.jspa?threadID=88558&tstart=-3](http://forums.citrix.com/thread.jspa?threadID=88558&tstart=-3)

That's not me, BTW.  I directly quoted.  Give that a try and see if it works.  Looks like this is one case that it doesn't because the DEBs in question are not in the repositories.

---

### Post by Cappy on 2009-03-05
```
sudo getlibs -p lesstif2; sudo ln -s /usr/lib32/libXm.so.4 /usr/lib32/libXm.so.2
```
will probably work.

---

### Post by afecelis on 2009-03-07
Cappy, I'm getting the following error when trying to compile in Freebasic, which only works in 32 bit systems:
```
fbc -w all "random.bas" (in directory: /media/500G/Exer/IrrlichtWrapper/myprojects/snippets)
ld: skipping incompatible /usr/lib/libXpm.so when searching For -lXpm
ld: skipping incompatible /usr/lib/libXpm.a when searching For -lXpm
ld: cannot find -lXpm
Compilation failed.
```

Is there anything that can be done to fix it with getlibs?  ;)

regards,
Alvaro

---

### Post by Cappy on 2009-03-07
```
sudo getlibs -p libxpm-dev
```
or
```
sudo getlibs -l libXpm.so
```

---

### Post by afecelis on 2009-03-07
Thanks a lot Cappy! :D

I'll try it out immediately and tell you how things go.

regards,

Alvaro

---

### Post by afecelis on 2009-03-07
It fixed the libxpm issue, then it asked for libxrandr (installed fine with getlibs), and then for libxrender (again, no problem) but now the compilation stops when not finding -lncurses, so I try the same command:
```
sudo getlibs -p libncurses-dev
```

but I get the following message:
> libncurses-dev was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install

what's the proper command to install the ncurses library?

a million thanks for your help!  :D
Alvaro

---

### Post by Cappy on 2009-03-07
```
sudo getlibs -p libncurses5-dev
```
which is findable by using [http://packages.ubuntu.com/](http://packages.ubuntu.com/) or apt-file

---

### Post by afecelis on 2009-03-07
you rule!!!  :D

Thanks a lot for the help and the patience.

It's compiling fine now.

Regards,

Alvaro

---

### Post by afecelis on 2009-03-07
I just placed this fix in the Freebasic/Linux forums. In case anyone's interested here's the link:
[http://www.freebasic.net/forum/viewtopic.php?p=117288#117288](http://www.freebasic.net/forum/viewtopic.php?p=117288#117288)

---

### Post by afecelis on 2009-03-07
mmm, although I installed libncurses with the command you told me, on other examples it seems to be looking for another version of this library. I'm getting this other error (only with some examples):
```
ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/../../../../lib32//libncurses.so when searching for -lncurses
```

I think it's looking for it in a different folder from the one I installed. :-k

**EDITED:** It seems to be just a warning, the program still runs.  ;)

---

### Post by dryder on 2009-03-09
Hi,

This is a long thread and I am confused and lacking the technical skills some obviously have here. So please bear with me.

I am trying to use getlibs to install Avasys' i386 driver that I converted to a deb package using alien, for my Epson 4490 scanner to see if I can get it to work in hardy 8.04, amd64, preferably with xsane. (It works like a charm in i386).

The package is: iscan-plugin-gt-x750_1.0.0-2_i386.deb

I have installed glibs 2.06.

But I am lost on the next step. Could anybody suggest what it should be?

Do I need all iscan files/folders removed first (installed trying other methods)? If so, what is the easiest way as iscan does not show up in synaptic?

David

---

### Post by rko618 on 2009-03-18
> **Cappy said:**
> No, sorry. That will be in the next version of getlibs.

How can you not include that functionality? I installed some libs with getlibs by mistake and now I'm not sure how to correctly replace them with their 64 bit versions.

---

### Post by Cappy on 2009-03-18
Because 32-bit libraries will not conflict with 64-bit libraries and are installed in a separate directory.

---

### Post by inphektion on 2009-03-28
why can't I find this anymore in jaunty?  I thought it was in the repo's but I can't find it and my system doesn't have it....:confused:

---

### Post by kforum on 2009-03-29
hey there Cappy, i love your program, but i was wondering... what does getlibs do exactly, when it downloads where does it wget from, and when it 'installs' what commands does it run? 

another weird thing i got libgtk1.2 through getlibs, but somewhow the prob im trying to use(EPSXE) is asking for it again... it wasnt the first time i ran it, so why is it whining?
has it suddenly forgotten that libgtk1.2 is in usr/lib32 and no usr/lib?

im not sure what to do about that, any help appreciated.

honestly im just beginning to understand the ia32 system, but i got everything installed.

thanks for all the great work, and for any response.
cheers

---

### Post by Mars73 on 2009-03-30
Thanks a 1000 times for getlibs!
I must have spend hours and hours on getting a Citrix ICA Client working on a Ubuntu 64 bit machine and the client is 32 bit.
Installing getlibs and then typing in the command:
sudo getlibs /usr/lib/ICAClient/wfcmgr
cured everything.
Wonderful stuff.

---

### Post by RavanH on 2009-03-30
> **Mars73 said:**
> Thanks a 1000 times for getlibs!
I must have spend hours and hours on getting a Citrix ICA Client working on a Ubuntu 64 bit machine and the client is 32 bit.
Installing getlibs and then typing in the command:
sudo getlibs /usr/lib/ICAClient/wfcmgr
cured everything.
Wonderful stuff.

I am trying to do the same and the Citrix ICA client **wfcmgr** runs now only I cannot get the browser plugin **wfica** to work. Is says it is missing libXaw.so.6 but when I do > # getlibs /usr/lib/ICAClient/wfica
No match for libXaw.so.6
No packages to install

There is libXaw.so.7 on my machine so I made a hard link /usr/lib32/libXaw.so.6 to the existing libXaw.so.7 but that gets me a Segmentation Error... I suppose that is because it is a 64bit lib?

I tried ```
# getlibs -l libXaw.so
libXaw.so: libxaw7-dev
The following i386 packages will be installed:
libxaw7-dev
``` but that did not solve anything...

Cappy, is there a way I can use getlibs to find libXaw.so.6 32bit libs ?

=====
EDIT: I found on [http://ubuntuforums.org/showthread.php?t=1026225](http://ubuntuforums.org/showthread.php?t=1026225) about this issue solved for 32bit (I suppose) by linking to libXaw3d.so.6 instead so I tried that and also did ```
# getlibs -l libXaw3d.so
libXaw3d.so: xaw3dg
The following i386 packages will be installed:
xaw3dg
Continue [Y/n]? 
Downloading ...
Installing libraries ...
``` but still the same Segmentation Fault :(

---

### Post by Yellow Pasque on 2009-03-30
RavenH: keep in mind that in the post you linked to is made by a 32-bit user, so if you just copied and pasted that command, it won't help you.

My libXaw files in /usr/lib32 look like so:
```
 ls -la /usr/lib32 | grep libXaw
lrwxrwxrwx  1 root root       15 2008-10-27 14:36 libXaw3d.so -> libXaw3d.so.6.1
lrwxrwxrwx  1 root root       15 2008-10-27 14:36 libXaw3d.so.6 -> libXaw3d.so.6.1
-rw-r--r--  1 root root   285584 2007-05-15 17:48 libXaw3d.so.6.1
lrwxrwxrwx  1 root root       16 2008-10-27 14:36 libXaw7.so.7 -> libXaw7.so.7.0.0
-rw-r--r--  1 root root   374152 2008-05-19 06:38 libXaw7.so.7.0.0
lrwxrwxrwx  1 root root       24 2009-03-30 18:47 libXaw.so.6 -> /usr/lib32/libXaw3d.so.6
lrwxrwxrwx  1 root root       12 2008-10-27 14:36 libXaw.so.7 -> libXaw7.so.7
```

---

### Post by RavanH on 2009-03-30
> **Temüjin said:**
> RavenH: keep in mind that in the post you linked to is made by a 32-bit user, so if you just copied and pasted that command, it won't help you.

I realized that and linked to the lib32 one... So I have the same (or am I mistaken?)

```
 ls -la /usr/lib32 | grep libXaw
lrwxrwxrwx  1 root root       15 2009-03-30 23:41 libXaw3d.so -> libXaw3d.so.6.1
lrwxrwxrwx  1 root root       15 2009-03-30 23:41 libXaw3d.so.6 -> libXaw3d.so.6.1
-rw-r--r--  1 root root   285584 2009-03-30 23:41 libXaw3d.so.6.1
-rw-r--r--  1 root root   490360 2009-03-30 23:32 libXaw7.a
lrwxrwxrwx  1 root root       16 2009-03-30 23:32 libXaw7.so -> libXaw7.so.7.0.0
lrwxrwxrwx  1 root root       16 2009-01-13 21:47 libXaw7.so.7 -> libXaw7.so.7.0.0
-rw-r--r--  1 root root   374152 2008-05-19 12:38 libXaw7.so.7.0.0
lrwxrwxrwx  1 root root       10 2009-03-30 23:32 libXaw.so -> libXaw7.so
lrwxrwxrwx  1 root root       24 2009-03-30 23:51 libXaw.so.6 -> /usr/lib32/libXaw3d.so.6
lrwxrwxrwx  1 root root       12 2009-01-13 21:47 libXaw.so.7 -> libXaw7.so.7
```

---

### Post by Yellow Pasque on 2009-03-31
RavanH: I just noticed that you're trying to run a 32-bit browser plugin. Are you using a 32-bit browser? If not, that could definitely cause your segfault.

---

### Post by RavanH on 2009-03-31
> **Temüjin said:**
> RavanH: I just noticed that you're trying to run a 32-bit browser plugin. Are you using a 32-bit browser? If not, that could definitely cause your segfault.

Temujin, I am not using the plugin /usr/local/lib/netscape/plugins/npica.so itself (which does nothing in either FF or Opera) but I am trying to get -at least- the script /usr/lib/ICAClient/wfica that handles .ica links to work. As soon as that works I can easily configure Opera to be able to use the weblinks for opening the client.

Right now, I have an ica file localy that I want to use with wfica like so ```
/usr/lib/ICAClient/wfica -file /path/to/file.ica
``` and here is where I get the Segfault...

---

### Post by KillerCodeninja on 2009-04-02
Brilliant script!

Thank you =D

---

### Post by deamon_knight on 2009-04-07
I'm trying to get an older game to run. It has a Linux Binary but it says I'm missing libstdc++.so.2.8. Running getlibs on the binary reports "No match for libstdc++.so.2.8". Any suggestions of how to proceed?

---

### Post by LinuxRen on 2009-04-07
great job, thx!

---

### Post by Cappy on 2009-04-08
> **kforum said:**
> hey there Cappy, i love your program, but i was wondering... what does getlibs do exactly, when it downloads where does it wget from, and when it 'installs' what commands does it run? 

another weird thing i got libgtk1.2 through getlibs, but somewhow the prob im trying to use(EPSXE) is asking for it again... it wasnt the first time i ran it, so why is it whining?
has it suddenly forgotten that libgtk1.2 is in usr/lib32 and no usr/lib?

im not sure what to do about that, any help appreciated.

honestly im just beginning to understand the ia32 system, but i got everything installed.

thanks for all the great work, and for any response.
cheers

Getlibs looks up the package name from the library name using packages.ubuntu.com --> looks up the package info on your system using the package name --> finds the 32-bit package in your selected repository --> download --> extract /usr/lib/ in package to temp directory --> repeat all steps for all packages --> move all from temp directory to /usr/lib32


I can't tell you why epsxe is failing without knowing the output from ```
getlibs --verbose /path/to/epsxe/epsxe
```
```
cd /path/to/epsxe/ && ldd epsxe
```
```
cd /usr/lib32 && ls libgtk*
```
```
egrep -U 'usr/lib' /path/to/epsxe/epsxe
```

Other's library problems seem to be because they need old libraries that are not in the repos.

My internet has been down for a week and my cable company tells me "there is no estimated time frame available for when service will be restored"...

---

### Post by tristangrimaux on 2009-04-11
Awesome! Your script did it's magic with Kerio Admin Console, a closed source mail server solution and administration on Intrepid. Thank you VERY MUCH!!! Your script should come default on Ubuntu64.

---

### Post by Radamand on 2009-04-12
sigh, i am getting so very frustrated...

ldd ut2004-bin-linux-amd64
	linux-vdso.so.1 =>  (0x00007fff45dff000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007fc23d999000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007fc23d77d000)
	**./libSDL-1.2.so.0 => not found**
	libstdc++.so.5 => /usr/lib/libstdc++.so.5 (0x00007fc23d4a1000)
	libm.so.6 => /lib/libm.so.6 (0x00007fc23d21c000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007fc23d004000)
	libc.so.6 => /lib/libc.so.6 (0x00007fc23cc92000)
	/lib64/ld-linux-x86-64.so.2 (0x00007fc23db9d000)


me@my-laptop:/usr/local/games/ut2004/System$ getlibs ut2004-bin-linux-amd64
You need to be copy the following libraries to the same directory as the binary:
libSDL-1.2.so.0
This application isn't missing any dependencies

---

### Post by Yellow Pasque on 2009-04-13
Radamand, why are you trying to use getlibs for a 64-bit app? You should have the file in question if you have libsdl1.2debian and one of the backends, like libsdl1.2debian-alsa or libsdl1.2-pulseaudio installed.

---

### Post by Cappy on 2009-04-13
> **Radamand said:**
> 
me@my-laptop:/usr/local/games/ut2004/System$ getlibs ut2004-bin-linux-amd64
You need to be copy the following libraries to the same directory as the binary:
libSDL-1.2.so.0
This application isn't missing any dependencies

Like getlibs says, you need to
```
sudo ln -s /usr/lib/libSDL-1.2.so.0 /usr/local/games/ut2004/System/libSDL-1.2.so.0
```
or copy it

---

### Post by afecelis on 2009-04-15
Cappy, is there a "remove" command to uninstall libraries you got with getlibs? I installed some X11 and gl 32 bits libraries to be able to run blitzmax but now when I try to build blender I get this error (which didn't occur before):
```
/usr/bin/ld: cannot find -lGL
```
So I don't know if my libraries are now conflicting.  :(

thanks in advance for any help.

cheers,
Alvaro

---

### Post by afecelis on 2009-04-15
Problem solved. It seems I was missing the "libgl1-mesa-dev" package.  ;)
More info about it here:
[http://blenderartists.org/forum/showthread.php?t=153564](http://blenderartists.org/forum/showthread.php?t=153564)

---

### Post by kamitsukai on 2009-04-20
I've got a problem with mplayer...

I'm running Linux Mint 6 64 bit which is meant to be compatible with Ubuntu 8.10 64 bit (basically the same...)

When I use getlibs to find the and install MPlayer 32 bit's dependencies I get this:

```
carl@mint-desktop ~/Desktop $ getlibs /usr/bin/mplayer
libXvMC.so.1: libxvmc1
libXvMCW.so.1: libxvmc1
libXxf86dga.so.1: libxxf86dga1
libGL is installed from video drivers, please install or reinstall your video drivers
libggi.so.2: libggi2
libcaca.so.0: libcaca0
libcucul.so.0: libcucul0
libvga.so.1: libsvga1
libfaac.so.0: libfaac0
No match for libx264.so.59
libmp3lame.so.0: liblame0
libsmbclient.so.0: libsmbclient
libgif.so.4: libgif4
libcdda_interface.so.0: libcdparanoia0
libcdda_paranoia.so.0: libcdparanoia0
libfribidi.so.0: libfribidi0
libenca.so.0: libenca0
libmad.so.0: libmad0
libvorbis.so.0: libvorbis0a
libspeex.so.1: libspeex1
libtheora.so.0: libtheora0
libmpcdec.so.3: libmpcdec3
libdv.so.4: libdv4
libxvidcore.so.4: libxvidcore4
liblirc_client.so.0: liblircclient0
libaa.so.1: libaa1
The following i386 packages will be installed:
libaa1
libcaca0
libcdparanoia0
libcucul0
libdv4
libenca0
libfaac0
libfribidi0
libggi2
libgif4
liblame0
liblircclient0
libmad0
libmpcdec3
libsmbclient
libspeex1
libsvga1
libtheora0
libvorbis0a
libxvidcore4
libxvmc1
libxxf86dga1
Continue [Y/n]? y
liblame0 was not found in your repositories
Make sure you have all repositories enabled and updated
Downloading ...
Installing libraries ...

```

and I try to run MPlayer but I get this error:
```
carl@mint-desktop ~/Desktop $ gmplayer
gmplayer: error while loading shared libraries: libXvMC.so.1: cannot open shared object file: No such file or directory

```


Thanks in advance!

also how do you remove 32 bit apps once installed? and remove dependencies...

---

### Post by Cappy on 2009-04-20
getlibs looks up the package names on packages.ubuntu.com but the looked up info will be useless for your system because the package names will be different on Mint. You have to use getlibs -p package_name1 package_name2 for each 32-bit package you want to install.

---

### Post by kamitsukai on 2009-04-20
It uses exactly the same repository as Ubuntu...

says so in there ["About Page"]("http://www.linuxmint.com/about.php")

Ive looked into it a bit more and it appears that the package liblame0 was renamed in intrepid to libmp3lame0?

---

### Post by Vadi on 2009-04-20
Can't get it to work for this one lib:

> vadi@ubuntu:~$ getlibs libgnome-keyring.so
libgnome-keyring.so: libgnome-keyring-dev
The following i386 packages will be installed:
libgnome-keyring-dev
Continue [Y/n]? y
libgnome-keyring-dev was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install
vadi@ubuntu:~$ getlibs --help
Usage: getlibs /path/to/binary
       getlibs -l i386librarytoinstall.so
       getlibs -p i386packagename
       getlibs -w [www.website.com/i386package.deb](www.website.com/i386package.deb)
       getlibs -i /home/vadi/i386package.deb
       See 'man getlibs' for more commands
vadi@ubuntu:~$ getlibs -l libgnome-keyring.so
libgnome-keyring.so: libgnome-keyring-dev
The following i386 packages will be installed:
libgnome-keyring-dev
Continue [Y/n]? y
libgnome-keyring-dev was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install
vadi@ubuntu:~$ getlibs -p libgnome-keyring-dev
The following i386 packages will be installed: libgnome-keyring-dev
Continue [Y/n]? y
libgnome-keyring-dev was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install
vadi@ubuntu:~$ apt-cache search libgnome-keyring-dev
libgnome-keyring-dev - Development files for GNOME keyring service
vadi@ubuntu:~$ 


> vadi@ubuntu:~$ '/opt'/'NowBoarding'/bin/'NowBoarding'
libgnome-keyring.so: cannot open shared object file: No such file or directory


---

### Post by Cappy on 2009-04-20
Ah, I didn't know Mint could use the ubuntu repos.
```
getlibs --distro Ubuntu --release intrepid /usr/bin/mplayer
```
should force getlibs to lookup the correct package names.

---

### Post by Cappy on 2009-04-20
> **Vadi said:**
> Can't get it to work for this one lib:

Curious it is failing on the command
```
linkmirror="`apt-cache policy $pack | grep -m 1 -i -o '\(http:\|www.\|ftp:\|https:\)[^ ]*'`"
```

What is the output from ```
apt-cache policy libgnome-keyring-dev
```
?

You can use
> getlibs -w mirrors.kernel.org/ubuntu/pool/main/g/gnome-keyring/libgnome-keyring-dev_2.20-0ubuntu4_i386.deb
in the meantime.

---

### Post by Vadi on 2009-04-21
> vadi@ubuntu:~$ apt-cache policy libgnome-keyring-dev
libgnome-keyring-dev:
  Installed: 2.26.0-0ubuntu3~iiwkt1
  Candidate: 2.26.0-0ubuntu3~iiwkt1
  Version table:
 *** 2.26.0-0ubuntu3~iiwkt1 0
        100 /var/lib/dpkg/status
     2.24.1-0ubuntu1 0
        500 [http://gpl.savoirfairelinux.net](http://gpl.savoirfairelinux.net) intrepid/main Packages
vadi@ubuntu:~$ 


I think I got my keyring upgraded from the webkit ppa a while back.

---

### Post by Vadi on 2009-04-21
I suspect this one will be a tricky one to solve:

> vadi@ubuntu:~$ getlibs -w mirrors.kernel.org/ubuntu/pool/main/g/gnome-keyring/libgnome-keyring-dev_2.20-0ubuntu4_i386.deb 
Downloading ...
Installing libraries ...
[sudo] password for vadi: 
vadi@ubuntu:~$ '/opt'/'NowBoarding'/bin/'NowBoarding'
libgnome-keyring.so: cannot open shared object file: No such file or directory
^C
vadi@ubuntu:~$ getlibs '/opt'/'NowBoarding'/bin/'NowBoarding'
This application isn't missing any dependencies
vadi@ubuntu:~$ 


Some background info: this is an Adobe AIR app, that thing is 32bit only atm (which worked out great, until some apps needed to store sensitive data, and adobe integrated with the gnome keyring - which is great, but no worky on 64bit - although they did they they're working on a 64bit air). The game I'm trying to get to work is a commercial one, but there are free applications like [Moderator]("http://www.adobe.com/cfusion/marketplace/index.cfm?event=marketplace.offering&offeringID=10225") and [Lita]("http://www.adobe.com/cfusion/marketplace/index.cfm?event=marketplace.offering&offeringID=10386") that require the keyring too.

---

### Post by Cappy on 2009-04-21
Ah, well, I bet you need the non-dev library
```
getlibs -p libgnome-keyring0
```
or
```
getlibs -w http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-keyring/libgnome-keyring0_2.24.1-0ubuntu1_i386.deb
```

If that doesn't work, try this afterwards:
```
sudo rm /usr/lib32/libgnome-keyring.so
sudo ln -s /usr/lib32/libgnome-keyring.so.0 /usr/lib32/libgnome-keyring.so
```

If that still doesn't work, check for a hardcoded link in the binary:
```
egrep -U 'usr/lib' '/opt'/'NowBoarding'/bin/'NowBoarding'
```

---

### Post by Vadi on 2009-04-21
First getlibs didnt work, but second did. Thanks a ton!

---

### Post by kamitsukai on 2009-04-21
> **Cappy said:**
> Ah, I didn't know Mint could use the ubuntu repos.
```
getlibs --distro Ubuntu --release intrepid /usr/bin/mplayer
```
should force getlibs to lookup the correct package names.

Thanks, sorry if my post seemed a bit rude (it did once I re-red it this morning:()

I seem to get a problem from that command:

```
carl@mint-desktop ~ $ getlibs --distro Ubuntu --release intrepid /usr/bin/mplayer
libGL is installed from video drivers, please install or reinstall your video drivers
No match for libglide.so.2
No packages to install

```

---

### Post by kamitsukai on 2009-04-22
bump... =]

---

### Post by Cappy on 2009-04-22
You're missing 32-bit video drivers at ```
/usr/lib32/libGL.*
```
Secondly, you're missing libglide.so.2 but it may be referring to package gtk2-engines's libglide.so
```
sudo getlibs -p gtk2-engines
```
> sudo ln -s /usr/lib32/gtk-2.0/2.10.0/engines/libglide.so /usr/lib32/gtk-2.0/2.10.0/engines/libglide.so.2

---

### Post by Vadi on 2009-04-25
I upgraded to 9.04 and need to get the 32bit keyring again... is *getlibs -w [http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-keyring/libgnome-keyring0_2.24.1-0ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-keyring/libgnome-keyring0_2.24.1-0ubuntu1_i386.deb)* still valid?

---

### Post by arashiko28 on 2009-04-25
I downloaded it and tried it with aMSN but had the same error message about having some tckximage file missing.
Keep up the good work. Perhaps you can solve my problem.

---

### Post by scribe_user on 2009-05-04
A program called Express Scribe, a transcription program, is only comfortable on 32-bit Ubuntu. Getlibs appears to be the way to get Scribe running on my 64-bit setup. Yet I'm baffled how to do this.

Scribe is normally installed as a shell script using the simple command line text,

sudo ./scribe

(once I'm in the correct directory, of course).

How is this procedure adjusted for the use of getlibs?

TIA,
paulb

---

### Post by Vadi on 2009-05-04
Do

> getlibs scribe

To install the 32bit libraries needed by scribe. Then you may launch it as usual.

---

### Post by Cappy on 2009-05-04
> **scribe_user said:**
> 
How is this procedure adjusted for the use of getlibs?


getlibs needs to be pointed at the binary for it find the dependencies. This means it can't be pointed at the install if it's a shell script.

If the install works and the command to run it is simply "scribe" (and that's not a script too) then it may be as easy as
```
sudo getlibs `which scribe`
```

---

### Post by scribe_user on 2009-05-04
According to file properties, the installer (filename: scribe) is a shell script (shell script (application/x-shellscript)). Here's what I saw in the terminal window when I tried a few things while in the directory where the scribe file is located:

paul@paul-desktop:~$ getlibs /home/paul/Desktop/scribe
Cannot determine the dependencies required by this program, it may be a script:
If this program needs a 32-bit library use:
getlibs -l i386librarytoinstall.so
If this program needs a 64-bit library use:
getlibs -64l amd64librarytoinstall.so

paul@paul-desktop:~$ sudo getlibs `which /home/paul/Desktop/scribe`
Cannot determine the dependencies required by this program, it may be a script:
If this program needs a 32-bit library use:
getlibs -l i386librarytoinstall.so
If this program needs a 64-bit library use:
getlibs -64l amd64librarytoinstall.so

paul@paul-desktop:~$ sudo getlibs -l i386librarytoinstall.so
No match for i386librarytoinstall.so
No packages to install

Obviously I don't know what I am doing.

---

### Post by jefelex on 2009-05-04
This looks like a great project!  does it work on hardware libraries and programs?  I'm a total newbie at this, although I've been using Ubuntu since 7.04 was new - I only ever used the 32 bit install, but with the 64 bit, I can't get my webcam to work properly, nor my fax modem (only 32bit .deb packages for those)

Also where can I get the latest update of getlibs?

Thanks in advance!

John

I read through the source code, which answered a lot of questions!  Thanks, Cappy, your code is easy to read, and quite instructional!

Thanks, John

---

### Post by Vadi on 2009-05-05
Can you open the file in the text editor and paste what it says here?

---

### Post by scribe_user on 2009-05-05
Posting the content of the Scribe file seemed like an excellent idea. But strangely, it wouldn't open up using an editor. The best sense I was able to get from it was to open it using the OpenOffice Writer. It opens this way, but everything after the ARCHIVE FOLLOWS line is characters that are untranslatable. So what I've done is, I've (tried to) attached the zipped archive that contains the file. Maybe someone who has more facility with this than I do would be able to experiment. I am just out of my depth, sad to say.

Just an editorial note: I don't know if Scribe has been written elegantly by programming rules, but in terms of utility, it is an amazing program and that it is available for free.... That amazes me.

  	 	 	 	 	 	  #!/bin/sh echo "" echo "Please wait while installer is initialising....."  # create a temp directory to extract to. export WRKDIR=`mktemp -d /tmp/selfextract.XXXXXX`  SKIP=`awk '/^__ARCHIVE_FOLLOWS__/ { print NR + 1; exit 0; }' $0`  # Take the TGZ portion of this file and pipe it to tar. tail -n +$SKIP $0 | tar xz -C $WRKDIR  # execute the installation script  PREV=`pwd` cd $WRKDIR ./install.sh $WRKDIR   # delete the temp files cd $PREV rm -rf $WRKDIR  exit 0  __ARCHIVE_FOLLOWS__

---

### Post by HunterWare on 2009-05-12
Cappy,

Firstly: Let me add another "thank you".  I spent all morning messing with 32/64bit libs and then stumbled across a mention of your script. *poof* Problem solved. Genius.

Secondly: Since this thread stands out so distinctly from beginning to end, I have to say an additional "thank you" for your patience and assistance.  I've never seen a dev so consistently help others.  Not one RTFM, "that's what search is for", or any other non-constructive reply.  Hat's off...

---

### Post by Yellow Pasque on 2009-05-12
For running Scribe Express:
- Download the tar.gz
- Extract the file somewhere (e.g. your home directory)
- Run the script. For example, if it's in your home directory:
```
cd ~/
./scribe
```
- The binary is located at /opt/nch/scribe/bin ; so now you can run getlibs on it:
```
cd /opt/nch/scribe/bin
sudo getlibs scribe
```

---

### Post by Cappy on 2009-05-20
I'm taking down my webserver so getlibs is temporarily located here: [http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/)

---

### Post by Cavillis on 2009-06-11
When attempting to solve my dependency problems, I ran```
getlibs AvConnect
```which resulted in the output:
```
No match for libssl.so.0.9.7
No match for libcrypto.so.0.9.7
```Any solutions?

---

### Post by Yellow Pasque on 2009-06-11
Cavillis:
```
sudo getlibs -w http://security.debian.org/debian-security/pool/updates/main/o/openssl097/libssl0.9.7_0.9.7k-3.1etch3_i386.deb
```

---

### Post by Vadi on 2009-06-23
How about this one:

> vadi@ubuntu-laptop:~$ getlibs '/home/vadi/Desktop/cuby/cuby' 
No match for libopenal.so.0
No packages to install
vadi@ubuntu-laptop:~$ 


---

### Post by Yellow Pasque on 2009-06-23
Vadi:
```
sudo getlibs -w http://ftp.ca.debian.org/debian/pool/main/o/openal/libopenal0a_0.0.8-4_i386.deb
```

---

### Post by Vadi on 2009-06-24
Thanks, that worked.

---

### Post by cacycleworks on 2009-06-27
Thank you!!

I saw this thread when I was having "64 bit problems" a year or so ago, but never used it. Until today. I used it to run the 32 bit installer for [www.xtuple.org](www.xtuple.org) (an open source accounting system that will one day smoke quickbooks).

BTW, I clicked on the links to the server to get the 2 getlibs files, which I then scp'd into my target server. When I saw "getlibs" was a bash script, I just sudo vi /bin/getlibs & pasted it in to install it. Since that worked, I guess it was ok I didn't read any directions.

**Thank you for such a useful and easy to use tool! **
:)

---

### Post by TwosComplement on 2009-08-03
Wow, this seems incredible! I like my 64 bit Ubuntu but that meant sacrificing some of my favorite software... Now it looks like I can run those (and prevent Skype from destroying Gnome when it runs). Speaking of which, has anyone else had that problem?

---

### Post by Sockerdrickan on 2009-08-04
Seriously this should come as default.

---

### Post by RavanH on 2009-08-05
> **TwosComplement said:**
> Wow, this seems incredible! I like my 64 bit Ubuntu but that meant sacrificing some of my favorite software... Now it looks like I can run those (and prevent Skype from destroying Gnome when it runs). Speaking of which, has anyone else had that problem?

Are you not using the 64bit Skype from the Medibuntu repository?

---

### Post by jefelex on 2009-08-05
> **Tux0r said:**
> Seriously this should come as default.

I think you are absolutely right!

John

---

### Post by stolk on 2009-09-09
Hi,

Great script!

But isn't it easier to store the files at launchpad instead of a free hosting site? (it's more save :) )

---

### Post by mac666 on 2009-09-13
i tried everything in here but i still get 
```
mac@turd:~/Downloads/lampp$ sudo ./lampp start 
XAMPP is currently only availably as 32 bit application. Please use a 32 bit compatibility library for your system.

```

any ideas?

---

### Post by nairbv on 2009-09-22
I was trying to get adobe air to work:

$ getlibs Adobe\ AIR\ Application\ Installer
The file "Adobe" does not exist
Usage: getlibs /path/to/binary
       getlibs -l i386librarytoinstall.so
       getlibs -p i386packagename
       getlibs -w [www.website.com/i386package.deb](www.website.com/i386package.deb)
       getlibs -i /home/bvaughan/i386package.deb
       See 'man getlibs' for more commands

looks like it's parsing command line arguments incorrectly.  I tried using quotes and such too which didn't help.

---

