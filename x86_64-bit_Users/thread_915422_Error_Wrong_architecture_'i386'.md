---
title: "Error: Wrong architecture 'i386'"
date: 2008-09-09
forum: x86 64-bit Users
---

### Post by jdorenbush on 2008-09-09
I have some .deb files on my desktop that I am trying to install and I keep getting the following error: Error: Wrong architecture 'i386'

To be honest, I didn't even know I was running a 64 bit install. Is there any way to run as 32 bit, or is there significant benefits to running 64 bit.

I am just really annoyed with this because I have had problems installing several things due to this error.

---

### Post by kjohansen on 2008-09-09
You can run a 32 bit operating system on a 64 bit system, but you would have to reinstall.

---

### Post by jdorenbush on 2008-09-09
Reinstalling sounds like no fun.

Whats the best workaround for installing apps where I run into this problem?

---

### Post by kjohansen on 2008-09-09
Here is a pseudo guide:

[http://www.unixtutorial.org/2008/03/install-32-bit-deb-packages-on-64-bit/](http://www.unixtutorial.org/2008/03/install-32-bit-deb-packages-on-64-bit/)

It is specifically for Skype, buy it includes the basics for forcing the architecture.

---

### Post by Jouke74 on 2008-09-10
I have no clue what you are trying to install, but I suggest you first check Synaptic to see if the program is not there yet. If you really want a deb then go to the Ubuntu repository site.

If not, then try to find the AMD64 debian file from the original sites or sites like Getdeb. Note that you are taking a (small) security risk here. 

If all fails you can download a i386 deb file and use above link (I assume force architecture). However, if there are no debs at all for AMD64 it usually better (though more difficult) to compile the source yourself. Of course this is possible only if the software is free.

---

### Post by bford16 on 2008-09-10
> **jdorenbush said:**
> I have some .deb files on my desktop that I am trying to install and I keep getting the following error: Error: Wrong architecture 'i386'

To be honest, I didn't even know I was running a 64 bit install. Is there any way to run as 32 bit, or is there significant benefits to running 64 bit.

I am just really annoyed with this because I have had problems installing several things due to this error.

I think it is possible to install and run 32-bit software on Ubuntu, but you have to do some special workaround. Search the forum for "32-bit Firefox" for examples.

---

### Post by etnlIcarus on 2008-09-10
[Hope this helps](http://www.linux.com/feature/142075).

---

### Post by Yellow Pasque on 2008-09-10
> or are there significant benefits to running 64 bit.
Read the sticky in this forum.

---

### Post by graben3 on 2008-09-10
There is a small command you probably already have :

linux32

In a terminal type :

linux32 yourcommandhere

That tries to run programs in 32 bits mode...

Works sometimes but not everytime. Loki (games) installers are specially tricky and most of the time wont work on 64 bits.

32 bits software runs most of the time fine under ubuntu...

I currently use Thunderbird as my mail client and there is no 64 bits version. It runs OK thought I had some problems on the first run (the one that creates the user profiles)

I'm not sure why but I installed Ubuntu 8.04 32 bits version on most of my friends computers and I installed 64bits version on my computer and found out that the 64bits is less stable than the 32 bits... some weird things happenned when I was setting up this 64 bits version... I fixed them but still...many unexplicable bugs appeared during the process of creating my perfect setup / preferences.

---

### Post by graben3 on 2008-09-10
> or are there significant benefits to running 64 bit. 

You know what... not that much.

**64 bits advantages :**

- Faster video compression, maths with large data are good in 64 bits
- 4GB or more ram  : possible

**64 bits Disadvantages :** 
- Not that much software for 64bits yet
- Sometimes more problems with 43 bits apps

32 bits advantages :

- most software is 32 bits
- well tested, less problems

32 Bits disadvantages :
- The opposite of the 64 bits advantages mostly !

---

### Post by Yellow Pasque on 2008-09-10
> 32 bits advantages :
- most software is 32 bits
- well tested, less problems

Huh? You seem to be under the misconception that software has to be written/coded specifically for 64-bit. With the exception of device drivers, it usually doesn't (there are some other exceptions with poorly written, non-portable code); it just has to be compiled/built for 64-bit. Most of the software packages in the 32-bit repo are available in the 64-bit repo.

Closed-source apps with no 64-bit version are a pain, but we work around that (nspluginwrapper, --force-architecture, etc.) 64-bit instructions speeds up more than video compression, although that is one example where it excels.

---

### Post by jespdj on 2008-09-10
> **graben3 said:**
> **64 bits Disadvantages :** 
- Not that much software for 64bits yet
Nonsense. In the Ubuntu repository, all the software that is available for the 32-bit version is also available for the 64-bit version. And 32-bit software also runs on the 64-bit version.
> **graben3 said:**
> 32 bits advantages :

- most software is 32 bits
- well tested, less problems
As above, everything in the 32-bit Ubuntu repo is also in the 64-bit Ubuntu repo. And the 64-bit version is just as well tested as the 32-bit version.

---

### Post by Sef on 2008-09-10
>  In the Ubuntu repository, all the software that is available for the 32-bit version is also available for the 64-bit version.

If it is supported software that is true.  However, Universe and Multiverse repositories may have software that is only 32-bit versions exist for.  Even there almost all software is made for both 32 and 64-bit.

---

### Post by Kilz on 2008-09-10
> **Sef said:**
> If it is supported software that is true.  However, Universe and Multiverse repositories may have software that is only 32-bit versions exist for.  Even there almost all software is made for both 32 and 64-bit.

Other than proprietary things like the flash and java plugins can you give an example or two of an application that is in the repositories and only 32bit?

---

### Post by Sef on 2008-09-10
Had a problem with a couple of games.  Otherwise all is fine.

---

### Post by anandbabu20 on 2008-09-11
One software that is not available in 64bit is Adobe Reader.

---

### Post by apyorik on 2009-04-15
I've been setting up my Ubuntu installation for about two months, and I've gotten several "wrong architecture" messages. In addition to the Adobe plugins I can remember seeing one for FreeAVG antivirus. (Yes, I know about clamAV, but my XPx64 machine is using AVG and while learning everything about ubuntu is on my list, the startup ramp is somewhat steep, and clamAV isn't an install-and-go program, at least for me.)

---

### Post by jespdj on 2009-04-15
You can install a 32-bit package on a 64-bit system by using the --force-architecture switch on dpkg:
```
sudo dpkg -i --force-architecture filename.deb
```
You might need to install the necessary 32-bit libraries to make your 32-bit software work. The [getlibs](http://ubuntuforums.org/showthread.php?t=474790) script can do that automatically for you.

@apyorik: Unless you have a special reason, you don't need anti-virus software on your Ubuntu computer. Ubuntu is not like Windows, where anti-virus software is more or less mandatory.

---

### Post by presence1960 on 2009-04-16
> **apyorik said:**
> I've been setting up my Ubuntu installation for about two months, and I've gotten several "wrong architecture" messages. In addition to the Adobe plugins I can remember seeing one for FreeAVG antivirus. (Yes, I know about clamAV, but my XPx64 machine is using AVG and while learning everything about ubuntu is on my list, the startup ramp is somewhat steep, and clamAV isn't an install-and-go program, at least for me.)

for security including AV in Ubuntu read this: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by webgrunt on 2009-05-17
> **jespdj said:**
> You can install a 32-bit package on a 64-bit system by using the --force-architecture switch on dpkg:
```
sudo dpkg -i --force-architecture filename.deb
```You might need to install the necessary 32-bit libraries to make your 32-bit software work. The [getlibs]("http://ubuntuforums.org/showthread.php?t=474790") script can do that automatically for you.

I successfully installed getlibs, but when I run the command 
```
sudo dpkg -i --force-architecture install_flash_player_10_linux.deb
```it tells me 
```
dpkg: error processing install_flash_player_10_linux.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 install_flash_player_10_linux.deb
```Any ideas?

---

### Post by pixel :-) on 2009-05-17
flash isn't stand alone, its a plugin, it has to be used buy 64 bit browzer, use the pakage that is alredy in the repozitories, it installs automatically a wrapper

sudo apt-get install flashplugin-installer, if you have too much trouble with the wraper, just install the 32 bit browzer, then install for it the plugin manually

As extra:

if theres is a conflict with what is alredy in ia32-libs, you can overide the lib with.

/lib/ld-linux.so.2 --library-path PATH EXECUTABLE

or a little wraper(renamed as your program)

 #!/bin/sh
  export LD_LIBRARY_PATH=YOUR_LIB_PATH:$LD_LIBRARY_PATH
  exec /usr/bin/my_program.orig $*

---

### Post by oldos2er on 2009-05-17
> **webgrunt said:**
> I successfully installed getlibs, but when I run the command 
```
sudo dpkg -i --force-architecture install_flash_player_10_linux.deb
```it tells me 
```
dpkg: error processing install_flash_player_10_linux.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 install_flash_player_10_linux.deb
```Any ideas?

 You need to run
```
sudo dpkg -i --force-architecture install_flash_player_10_linux.deb
```
in the same directory where install_flash_player_10_linux.deb is.

---

### Post by pixel :-) on 2009-05-17
per oldos2er, you had a space "r _" in the name, but if it's flash you install, don't, it's not going to work, a 64bit browser needs 64bit plugging, just apt get the package that is in the official repositories, for this.

For helix player, follow my advice above.

---

