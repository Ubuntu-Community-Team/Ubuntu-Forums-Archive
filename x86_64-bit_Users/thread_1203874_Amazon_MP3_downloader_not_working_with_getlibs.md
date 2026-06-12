---
title: "Amazon MP3 downloader not working with getlibs"
date: 2009-07-03
forum: x86 64-bit Users
---

### Post by par129 on 2009-07-03
Befor I post any of my problems here, I thoroughly search the web for the solution. Unfortunately I have not been able to find a solution to installing the amazon mp3 down-loader onto my 64 bit version of 9.04. I've tried several on the posts using the getlibs but am still getting error messages. I've followed the following post

[http://ubuntuforums.org/showthread.php?t=692590](http://ubuntuforums.org/showthread.php?t=692590)

and gotten the following in terminal

par@par-desktop:~$ sudo dpkg --install --force-architecture amazonmp3.deb
dpkg: error processing amazonmp3.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 amazonmp3.deb
par@par-desktop:~$ sudo getlibs /usr/bin/amazonmp3
The file "/usr/bin/amazonmp3" does not exist
Usage: getlibs /path/to/binary
       getlibs -l i386librarytoinstall.so
       getlibs -p i386packagename
       getlibs -w [www.website.com/i386package.deb](www.website.com/i386package.deb)
       getlibs -i /home/root/i386package.deb
       See 'man getlibs' for more commands
par@par-desktop:~$ 

not sure what the post means by running the libs a few times, any help, thanks...

---

### Post by jocko on 2009-07-04
> **par129 said:**
> par@par-desktop:~$ sudo dpkg --install --force-architecture amazonmp3.deb
dpkg: error processing amazonmp3.deb (--install):
 cannot access archive: [COLOR=Red]No such file or directory[/COLOR]
There's your problem. You are not in the correct directory.
Where did you save the .deb file? If it's on your desktop, the command would be:
```
cd ~/Desktop
sudo dpkg --install --force-architecture amazonmp3.deb
```
Or:
```
sudo dpkg --install --force-architecture ~/Desktop/amazonmp3.deb
```

---

### Post by oldos2er on 2009-07-04
Try this software instead of Amazon's: [http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)

---

### Post by par129 on 2009-07-05
Thanks for the reply, tried installing from desktop with both commands and got the following:

par@par-desktop:~$ cd ~/Desktop
par@par-desktop:~/Desktop$ sudo dpkg --install --force-architecture amazonmp3.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 175148 files and directories currently installed.)
Preparing to replace amazonmp3 1.0.3-1 (using amazonmp3.deb) ...
Unpacking replacement amazonmp3 ...
dpkg: dependency problems prevent configuration of amazonmp3:
 amazonmp3 depends on libboost-thread1.34.1; however:
  Package libboost-thread1.34.1 is not installed.
 amazonmp3 depends on libboost-iostreams1.34.1; however:
  Package libboost-iostreams1.34.1 is not installed.
 amazonmp3 depends on libboost-signals1.34.1; however:
  Package libboost-signals1.34.1 is not installed.
 amazonmp3 depends on libboost-date-time1.34.1; however:
  Package libboost-date-time1.34.1 is not installed.
 amazonmp3 depends on libcurl3; however:
  Package libcurl3 is not installed.
dpkg: error processing amazonmp3 (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info ...
Errors were encountered while processing:
 amazonmp3
par@par-desktop:~/Desktop$ sudo dpkg --install --force-architecture ~/Desktop/amazonmp3.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 175148 files and directories currently installed.)
Preparing to replace amazonmp3 1.0.3-1 (using .../home/par/Desktop/amazonmp3.deb) ...
Unpacking replacement amazonmp3 ...
dpkg: dependency problems prevent configuration of amazonmp3:
 amazonmp3 depends on libboost-thread1.34.1; however:
  Package libboost-thread1.34.1 is not installed.
 amazonmp3 depends on libboost-iostreams1.34.1; however:
  Package libboost-iostreams1.34.1 is not installed.
 amazonmp3 depends on libboost-signals1.34.1; however:
  Package libboost-signals1.34.1 is not installed.
 amazonmp3 depends on libboost-date-time1.34.1; however:
  Package libboost-date-time1.34.1 is not installed.
 amazonmp3 depends on libcurl3; however:
  Package libcurl3 is not installed.
dpkg: error processing amazonmp3 (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info ...
Errors were encountered while processing:
 amazonmp3


The app is listed in the internet menu but when i click, i see an attempt to start on the lower bar but nothing ever opens.

---

### Post by jocko on 2009-07-05
> **par129 said:**
> Thanks for the reply, tried installing from desktop with both commands and got the following:

par@par-desktop:~$ cd ~/Desktop
par@par-desktop:~/Desktop$ sudo dpkg --install --force-architecture amazonmp3.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 175148 files and directories currently installed.)
Preparing to replace amazonmp3 1.0.3-1 (using amazonmp3.deb) ...
Unpacking replacement amazonmp3 ...
dpkg: dependency problems prevent configuration of amazonmp3:
 [COLOR=Red]amazonmp3 depends on libboost-thread1.34.1; however:
  Package[/COLOR][COLOR=Red] libboost-thread1.34.1 is not installed.
 amazonmp3 depends on libboost-iostreams1.34.1; however:
  Package[/COLOR][COLOR=Red] libboost-iostreams1.34.1 is not installed.
 amazonmp3 depends on libboost-signals1.34.1; however:
  Package [/COLOR][COLOR=Red]libboost-signals1.34.1 is not installed.
 amazonmp3 depends on libboost-date-time1.34.1; however:
  Package [/COLOR][COLOR=Red]libboost-date-time1.34.1 is not installed.
 amazonmp3 depends on libcurl3; however:
  Package [/COLOR][COLOR=Red]libcurl3 is not installed.[/COLOR]
dpkg: error processing amazonmp3 (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info ...
Errors were encountered while processing:
 amazonmp3

The answer is right there in the red text (didn't you read the text before you posted it?)... Just install the missing packages:
```
sudo apt-get update
sudo apt-get install libboost-thread1.34.1 libboost-iostreams1.34.1 libboost-signals1.34.1 libboost-date-time1.34.1 libcurl3
```And after that you will probably have to run the second command from your first post:
```
sudo getlibs /usr/bin/amazonmp3
```

---

### Post by par129 on 2009-07-05
Thanks for the reply, i'm pretty sure there were no problems with what you sent, but it attempts to start but nothing happens, based on my "bean count" i wouldnt have been able to figure how to install the missing packages even if i read it. i am going to try to completley uninstall if i can figure out how and try again, thanks again for your post

---

### Post by jocko on 2009-07-06
> **par129 said:**
> ... based on my "bean count" i wouldnt have been able to figure how to install the missing packages even if i read it.
Welcome to ubuntu. To install a package if you know it's name (which you do if you get an error message telling you that package "[COLOR=Red]packagename[/COLOR]" is not installed), either install it from a terminal:
```
sudo apt-get install[COLOR=Red] packagename[/COLOR]
```
Or open up synaptic (System-->Administration-->Synaptic package manager) and search for the package.

---

### Post by par129 on 2009-07-11
how do i install the clamz?

---

### Post by oldos2er on 2009-07-11
> **par129 said:**
> how do i install the clamz?

 Extract the folder somewhere in your $HOME directory, then read the README. You'll need to install build-essential if you haven't already.

---

### Post by par129 on 2009-07-19
Still can get Amazon MP3 downloader working

this is what i get when i try to uninstall or remove, I would like to start fresh with some of these instructions

par@par-desktop:~$ sudo aptitude remove amazonmp3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "amazonmp3"
Couldn't find any package whose name or description matched "amazonmp3"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

---

### Post by par129 on 2009-07-19
Tried installing using the following command along with the error message

par@par-desktop:~$ sudo dpkg -i --force-architecture amazonmp3.deb

dpkg: error processing amazonmp3.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 amazonmp3.deb
par@par-desktop:~$

---

