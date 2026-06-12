---
title: "Glibc-2.0 on linux x86_64"
date: 2008-10-21
forum: x86 64-bit Users
---

### Post by pooyaplus on 2008-10-21
Hi,

I was trying to install my LDOCE dictionary on my hardy 64 but the bash installer returns this error message:
```

This installation does not support glibc-2.0 on Linux / x86_64
returned error code (1)
Press return to close the window

```

Does that mean I can not have my dictionary on my 64bit ubuntu?

---

### Post by jespdj on 2008-10-21
How did you install that software, what steps did you take exactly? From the Ubuntu repository, or from somewhere else? Did you compile it from source, or do you have a binary package? Is it a 32-bit or a 64-bit program? If it is 32-bit, then is there also a 64-bit version of it available?

---

### Post by pooyaplus on 2008-10-21
Actually, this is a CD within my longman dictionary, it has a folder for linux installation. I could install it on my other laptop (32 bit) with no trouble. 

It is a .sh file and that was the output.

---

### Post by pooyaplus on 2008-10-22
Bump!

---

### Post by jespdj on 2008-10-22
Maybe you need the 32-bit version of the library glibc-2.0. Try installing ia32-libs:
```
sudo apt-get install ia32-libs
```
Then run the installation script again. If it still complains, try running it with "linux32":
```
linux32 installscript.sh
```
This will fool the script so that it will "think" it runs on 32-bit Linux.

---

### Post by pooyaplus on 2008-10-24
Will give it a shot, and post back the results. Thanks.

---

### Post by pooyaplus on 2008-10-26
Hi, I had the "ia32-libs" installed, but when I attempted the linux 32 command it says I need some other packages. 

uml-utilities and user-mode-linux; which both seems to be  deprecated for hardy! Or maybe there is a temporary problem with my Internet connection that prevents the fetching the archives of the ubuntu repositories.

---

### Post by pooyaplus on 2008-11-01
Hi again.
I installed the linux32 and it did the trick of installing the application. But it won't run:
```

sh ./ldoce
./ldoce4-bin: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```

---

### Post by pooyaplus on 2008-11-05
Bump!:confused:

---

### Post by Yellow Pasque on 2008-11-05
Use getlibs to obtain the necessary 32-bit libs.
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by tomdkat on 2008-11-05
You're missing this library:

libgtk-1.2.so.0

That isn't part of glibc but is an outdated GTK 1.2 library.  See if you can find a newer version of the software you are trying to run.  I don't know if you will be able to install the correct GTK 1.2 library without much pain and agony since it's just so old.

Peace...

---

### Post by pooyaplus on 2008-11-05
That is right, it is an outdated GTK library.
> **tomdkat said:**
> See if you can find a newer version of the software you are trying to run.
I am not sure if they have released another version or they have considered the 64-bit libs in that release.
I will try getlibs as suggested in the previous posts and see if that does the trick for me or not.

Cheers

---

### Post by pooyaplus on 2008-11-08
> **Temüjin said:**
> Use getlibs to obtain the necessary 32-bit libs.
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Hi, what I understand from the thread you just recommended is that, getlibs will fetch the unmet dependencies and libraries of 32-bit arch for the 64-bits machines. 
So that would only apply for .deb packages right?

---

### Post by Yellow Pasque on 2008-11-08
> So that would only apply for .deb packages right?
No... it will place the 32-bit libraries in /usr/lib32 for any app to use. getibs is a really slick script

---

### Post by Elliander on 2008-11-19
I also seem to be missing "libgtk-1.2.so.0" but I have all of my 32bit libraries installed that I could find in the Synaptic Package Manager. And also installed this here: 
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

I can't seem to find where to find it. I know the game is old, but it's not THAT old. Why would anyone with half a brain cut out needed files from availability?

> elliander@elliander-ubuntu:~$ sudo linux32 /usr/local/games/creatures3/creatures3
Welcome to Creatures 3!
Querying language
/usr/local/games/creatures3/langpick: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
elliander@elliander-ubuntu:~$ 


---

### Post by Yellow Pasque on 2008-11-19
> I also seem to be missing "libgtk-1.2.so.0" but I have all of my 32bit libraries installed that I could find in the Synaptic Package Manager. And also installed (getlibs)
You have to use the getlibs program that you installed to "get the libs" :P
```
sudo getlibs -l libgtk-1.2.so.0
```

> I know the game is old, but it's not THAT old. Why would anyone with half a brain cut out needed files from availability?
You're running a 64-bit distro, so the 64-bit versions of the libraries are available in Synaptic. Only the most common 32-bit libraries have official "lib32" packages. That's why users of this very forum wrote/tested the getlibs script.

---

### Post by Elliander on 2008-11-19
Now what...
> 
elliander@elliander-ubuntu:~$ sudo getlibs -l libgtk-1.2.so.0
libgtk-1.2.so.0: libgtk1.2
The following i386 packages will be installed:
libgtk1.2
Continue [Y/n]? y
Downloading ...
Installing libraries ...
elliander@elliander-ubuntu:~$ sudo /usr/local/games/creatures3/creatures3
Welcome to Creatures 3!
Querying language
/usr/local/games/creatures3/langpick: error while loading shared libraries: libgmodule-1.2.so.0: cannot open shared object file: No such file or directory
elliander@elliander-ubuntu:~$ 



I have every GTK I could find installed. All lib32 I could find. 

I also tried installing this: 
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

I tried this:

> elliander@elliander-ubuntu:~$ sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree
Reading state information... Done
libgtk1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
elliander@elliander-ubuntu:~$

I tried this: (which just gave me a different error)

> elliander@elliander-ubuntu:~$ export LD_ASSUME_KERNEL=2.2.5
elliander@elliander-ubuntu:~$ sudo linux32 /usr/local/games/creatures3/creatures3
sudo: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory

I tried this:
> 
elliander@elliander-ubuntu:~$ sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree
Reading state information... Done
libgtk1.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
elliander@elliander-ubuntu:~$

---

### Post by Yellow Pasque on 2008-11-19
You have to keep using the getlibs script to get the 32-bit libraries the program asks for.
> error while loading shared libraries: libgmodule-1.2.so.0
So;
```
sudo getlibs -l libgmodule-1.2.so.0
```
Use ldd to make sure the prgram's requirements are satisfied:
```
ldd /usr/local/games/creatures3/creatures3
sudo getlibs /usr/local/games/creatures3/creatures3
```
Use getlibs for libraries that aren't found. Keep using getlibs for whatever library file the program asks for until it runs without asking for any more shared libraries.

---

### Post by Elliander on 2008-11-19
Well this is what happened:

> elliander@elliander-ubuntu:~$ sudo /usr/local/games/creatures3/creatures3
Welcome to Creatures 3!
Querying language
/usr/local/games/creatures3/langpick: error while loading shared libraries: libgmodule-1.2.so.0: cannot open shared object file: No such file or directory
elliander@elliander-ubuntu:~$ sudo getlibs -l libgmodule-1.2.so.0
[sudo] password for elliander: 
libgmodule-1.2.so.0: libglib1.2
The following i386 packages will be installed:
libglib1.2
Continue [Y/n]? y
libglib1.2 was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install
elliander@elliander-ubuntu:~$ ldd /usr/local/games/creatures3/creatures3
	not a dynamic executable
elliander@elliander-ubuntu:~$ sudo getlibs /usr/local/games/creatures3/creatures3
Cannot determine the dependencies required by this program, it may be a script:
If this program needs a 32-bit library use:
getlibs -l i386librarytoinstall.so
If this program needs a 64-bit library use:
getlibs -64l amd64librarytoinstall.so
elliander@elliander-ubuntu:~$ sudo getlibs -\ i386librarytoinstall.so
Usage: getlibs /path/to/binary
       getlibs -l i386librarytoinstall.so
       getlibs -p i386packagename
       getlibs -w [www.website.com/i386package.deb](www.website.com/i386package.deb)
       getlibs -i /home/root/i386package.deb
       See 'man getlibs' for more commands
elliander@elliander-ubuntu:~$ 


It didn't really do anything. And error persists.

---

### Post by Elliander on 2008-11-19
aha! I got to thinking that since it gets stuck when it tries to use langpick, I would use that command on that.

> 
elliander@elliander-ubuntu:~$ sudo getlibs /usr/local/games/creatures3/langpick
libgmodule-1.2.so.0: libglib1.2
libglib-1.2.so.0: libglib1.2ldbl
libgmodule-1.2.so.0: libglib1.2
libglib-1.2.so.0: libglib1.2ldbl
libgmodule-1.2.so.0: libglib1.2
libglib-1.2.so.0: libglib1.2ldbl
The following i386 packages will be installed:
libglib1.2
libglib1.2ldbl
Continue [Y/n]? y
libglib1.2 was not found in your repositories
Make sure you have all repositories enabled and updated
Downloading ...
Installing libraries ...
elliander@elliander-ubuntu:~$ sudo /usr/local/games/creatures3/creatures3
Welcome to Creatures 3!
Querying language


And hey! Something actually happens without an error!


err.. spoke too soon. The following error occurred after I selected the language. But I guess it's progress.

> /home/elliander/.creatures3
Bootstrap for world switcher
/usr/local/games/creatures3/creatures3: line 99: 19510 Segmentation fault      "$C3_MAIN"/lc2e
elliander@elliander-ubuntu:~$ 


So now when I try to run the program I instead get this each time:

> elliander@elliander-ubuntu:~$ sudo /usr/local/games/creatures3/creatures3
Welcome to Creatures 3!
/usr/local/games/creatures3/creatures3: line 99: 19529 Segmentation fault      "$C3_MAIN"/lc2e
elliander@elliander-ubuntu:~$ 


---

### Post by Elliander on 2008-11-19
I tried this:
> 


elliander@elliander-ubuntu:~$ export LD_ASSUME_KERNEL=2.2.5
elliander@elliander-ubuntu:~$ sudo linux32 /usr/local/games/creatures3/creatures3
sudo: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
elliander@elliander-ubuntu:~$ sudo getlibs -l libdl.so.2
sudo: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
elliander@elliander-ubuntu:~$ 

Then I tried closing the terminal, opening the terminal again, and I was able to do this:

> elliander@elliander-ubuntu:~$ sudo getlibs -l libdl.so.2
libdl.so.2: libc6
The following i386 packages will be installed:
libc6
Continue [Y/n]? y
Downloading ...
Installing libraries ...

Then I got this new error:

> elliander@elliander-ubuntu:~$ sudo linux32 /usr/local/games/creatures3/creatures3
Welcome to Creatures 3!
/usr/local/games/creatures3/lc2e: error while loading shared libraries: libgtk-1.2.so.0: wrong ELF class: ELFCLASS64


So I tried this:

> elliander@elliander-ubuntu:~$ export LD_ASSUME_KERNEL=2.2.5
elliander@elliander-ubuntu:~$ sudo linux32 /usr/local/games/creatures3/creatures3
sudo: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
elliander@elliander-ubuntu:~$ 

back to square one. Sorta.

> 
Welcome to Creatures 3!
/usr/local/games/creatures3/lc2e: error while loading shared libraries: libgtk-1.2.so.0: wrong ELF class: ELFCLASS64
elliander@elliander-ubuntu:~$ 



---

### Post by Elliander on 2008-11-19
I followed this guide here:

[http://whynotwiki.com/GNU/Linux_/_Running_32-bit_applications_on_64-bit_Linux](http://whynotwiki.com/GNU/Linux_/_Running_32-bit_applications_on_64-bit_Linux)

But I already had the files.

Another thread suggested that I go here to solve the ELF problem.

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Which I already installed before, but figured I could reinstall. Didn't help.

Problems persist. I have no idea what to do next. Tried everything I can think of. If it's not one error it's another. Why isn't there some easy package to install to enable  Ubuntu to play without issue both 32-bit and 64-bit programs?


> 

elliander@elliander-ubuntu:~$ sudo linux32 /usr/local/games/creatures3/creatures3
[sudo] password for elliander: 
Welcome to Creatures 3!
/usr/local/games/creatures3/lc2e: error while loading shared libraries: libgtk-1.2.so.0: wrong ELF class: ELFCLASS64
elliander@elliander-ubuntu:~$ 

---

### Post by Cappy on 2008-11-20
It's in the error message: ```
libglib1.2 was not found in your repositories
Make sure you have all repositories enabled and updated
```


You need to follow this guide to enable your universe repositories: [http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html](http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html)

Then use
```
sudo getlibs /usr/local/games/creatures3/lc2e
```
or
```
sudo getlibs -p 'libglib1.2'
```

---

### Post by Elliander on 2008-11-20
oh, that problem only occurred because I was using:

> export LD_ASSUME_KERNEL=2.2.5

I have all repositories enabled. (well, except source code, but I don't plan to mess with that any time soon.)

I only displayed it to show what I got with each and every thing I tried. Now the only problem I have is:
> 
elliander@elliander-ubuntu:~$ /usr/local/games/creatures3/creatures3
Welcome to Creatures 3!
/usr/local/games/creatures3/lc2e: error while loading shared libraries: libgtk-1.2.so.0: wrong ELF class: ELFCLASS64
elliander@elliander-ubuntu:~$ 


I have yet to find anything on google, ask, or on Ubuntu Forums which helps me solve this problem. I have found quite a few articles where this problem came up, but I already tried everything suggested in the articles I so far found.

> elliander@elliander-ubuntu:~$ sudo getlibs /usr/local/games/creatures3/lc2e
[sudo] password for elliander: 
No match for lc2elib.so
No match for libSDLStretch.so
libgtk-1.2.so.0: libgtk1.2
libgdk-1.2.so.0: libgtk1.2
libglib-1.2.so.0: libglib1.2ldbl
No match for libstdc++-libc6.1-2.so.3
The following i386 packages will be installed:
libglib1.2ldbl
libgtk1.2
Continue [Y/n]? y
Downloading ...
Installing libraries ...
elliander@elliander-ubuntu:~$ /usr/local/games/creatures3/creatures3
Welcome to Creatures 3!
/usr/local/games/creatures3/lc2e: error while loading shared libraries: libgtk-1.2.so.0: wrong ELF class: ELFCLASS64
elliander@elliander-ubuntu:~$ 


That didn't work...

> elliander@elliander-ubuntu:~$ sudo getlibs -p 'libglib1.2'
The following i386 packages will be installed: libglib1.2
Continue [Y/n]? y
libglib1.2 was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install
elliander@elliander-ubuntu:~$ /usr/local/games/creatures3/creatures3
Welcome to Creatures 3!
/usr/local/games/creatures3/lc2e: error while loading shared libraries: libgtk-1.2.so.0: wrong ELF class: ELFCLASS64
elliander@elliander-ubuntu:~$ 

Neither did that...

And:
> 
elliander@elliander-ubuntu:~$ export LD_ASSUME_KERNEL=2.2.5
elliander@elliander-ubuntu:~$ /usr/local/games/creatures3/creatures3
/bin/bash: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
elliander@elliander-ubuntu:~$ 


See, I have all the 32 bit libraries installed. Everything I could find. And still nothing is working. It's as if Ubuntu doesn't know where to find lib32 folder.

---

### Post by Yellow Pasque on 2008-11-20
Can you post the output of:
```
cat /etc/apt/sources.list
```

---

### Post by Elliander on 2008-11-20
Ok, this is weird. It says Ubuntu 7.10 but I upgraded to Ubuntu 8.10 a few days ago. And under system monitor it says Ubuntu 8.04 but anyway, here's what it says.

> elliander@elliander-ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
elliander@elliander-ubuntu:~$ 


---

### Post by Yellow Pasque on 2008-11-20
It looks like you're running Ubuntu 8.04 (Hardy) because there's no mention of intrepid in your repo sources file. Did you reallly upgrade to 8.10?

---

### Post by Elliander on 2008-11-20
Yes of course. I used the update manager. And I always keep all my files up to day and recheck often. It says my system is up to date and there are NO updates available.

And btw, I never had 8.4 I started with a burned CD, 7.10 and just a few days ago upgraded from 7.10 to 8.10 - not once was 8.4 on my system at all so I don't understand why it would say that.

---

### Post by Elliander on 2008-11-20
So... any chance that there is a Bug in Ubuntu that causes it to not see lib32 or see it as something else? I know I have the files needed but it isn't working.

---

### Post by Yellow Pasque on 2008-11-20
> and just a few days ago upgraded from 7.10 to 8.10 - not once was 8.4 on my system at all so I don't understand why it would say that
I don't know of any way to upgrade from Gutsy to Intrepid. You can only upgrade one release at a time, so you would have to upgrade to Hardy before you upgrade to Intrepid/

---

### Post by Elliander on 2008-11-20
I don't really understand the difference or why that would prevent me from playing my 32-bit games.

---

### Post by Elliander on 2008-11-20
Again, I have the 32-bit libraries installed. So the type of Ubuntu really shouldn't make a difference. I just want it all to work. I have spent several hours trying.

---

### Post by Elliander on 2008-11-23
I can confirm that my computer using Ubuntu can run 32-bit programs because I got WINE to run a windows version of Creatures. (well, up to a point) but the same game written for Linux won't run at all.

So back up a moment... Ubuntu won't run 32-bit games written for Linux on 64-bit hardware but it will run 32-bit games written for windows?

And this makes sense how?

---

### Post by Elliander on 2008-11-24
um... :confused: ... ](*,) ... still need help. [-o<

---

### Post by pooyaplus on 2009-01-21
Alright, returning to my own problem with the Longman Dictionary! I finally managed to try this amazing getlibs script on a 32-bit machine, to get the libgtk-1.2.so.0 deprecated packages. Andf it worked smoothly. :wink: 

Now I have to find some free time to test the script on my 64-bit machine. Hope this solves the issue.

Will post back the results guys. Thanks for the help.

---

