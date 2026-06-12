---
title: "cannot install flashplayer on AMD64 (after lots of trying!)"
date: 2008-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by stevieP on 2008-01-20
This is my first post, I'll try to be clear as to what I tried.

I have an amd64 system:
$ uname -a
Linux jayz 2.6.15-28-amd64-generic #1 SMP PREEMPT Tue Mar 13 20:51:52 UTC 2007 x86_64 GNU/Linux

which I believe is running dapper drake:
$ cat /etc/issue
Ubuntu 6.06.1 LTS \n \l

or System > About Ubuntu gives:
"Thank you for your interest in Ubuntu 6.06 LTS - the Dapper Drake - released in June 2006."

I tried following the directions on this thread:
[http://ubuntuforums.org/archive/index.php/t-495090.html](http://ubuntuforums.org/archive/index.php/t-495090.html)

$ wget [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

$ tar -zxf install_flash_player_9_linux.tar.gz
$ cd install_flash_player_9_linux/
$ mv *flashplayer* ~/.mozilla/plugins

This all worked fine:
$ cd ~/.mozilla/plugins/ ; ls *flash*
flashplayer-installer*  flashplayer.xpt  libflashplayer.so*

However I was not able to install the nspluginwrapper using:
$ sudo aptitude install nspluginwrapper

which gave output including:

(gobbledegook..)
Couldn't find any package whose name or description matched "nspluginwrapper"

(more gobbledegook..)
0 packages upgraded, 0 newly installed, 0 to remove and 147 not upgraded.

$ locate nspluginwrapper

(gave no results)

Then I searched around and was able to find a nswrapper file here:
[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)
which is supposed to be a Nspluginwrapper Install Script for Dapper-Gutsy

after unpacking it:
$ tar -xzvf oldflash-0.1.1.tar.gz

I tried to install it with:
$ sudo ./GetFlash

I selected install option 1 for dapper drake:
Install option (1-3)? :1

It went through several processes and gave a lot of output. I'm not sure it all ran successfully, for example some disturbing output (to me) was:

ln: creating symbolic link `/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so' to `/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so': File exists

(maybe this isn't a problem)

Then it said: " The plugin and files should now be installed .
 But we need to set the ownership of the files to you
 Please type in your login name and hit enter.  The terminal will then close and everything will be setup. Make sure to restart your browser for all
 changes to take effect."

I typed my username, hit enter, and it said:

chown: cannot access `/usr/lib/nspluginwrapper/plugins': No such file or directory

 Everything has been installed

If I look in `/usr/lib/nspluginwrapper/plugins' indeed there is no such directory:
$ cd /usr/lib/nspluginwrapper/;ls
i386/  noarch/  x86_64/
$ cd x86_64/;ls
linux/
cd linux/;ls
npconfig*  npwrapper.so*

i.e. I think the relevant files are in /usr/lib/nspluginwrapper/plugins/x86_64/linux/

I'm not sure what symbolic link I should create or what files I should chown. When I open a window on firefox and type 'about:plugins' in the address bar, I get:

No plug-ins are installed
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org. 

So I'm at a loss! Any suggestions, please?

StevieP

---

### Post by Kilz on 2008-01-20
I would recommend , that when asking help about a howto or script, to post in the thread for that howto or script first. I would also recommend posting [in the 64bit section ]("http://ubuntuforums.org/forumdisplay.php?f=134")if you are running the amd64 bit version. Experienced users of that version will help you. This section mainly has 32bit users.

Thanks for the info you are reporting. It looks like the nsplugiwrapper package wasn't installed. That you had a file already may mean that you tried other methods that failed before the script.

[Here is the latest version]("http://home.comcast.net/~ubuntume/oldflash-0.1.2.tar.gz"), try it, dont close the script when its done. Try a flash enabled site. If you still have problems copy the text in the terminal and paste it to a reply here.

---

### Post by stevieP on 2008-01-21
OK Kilz, I will make sure to post in those forums from now on with issues on my amd64 system (Its also fine with me if a mod wants to move my thread over there),

I downloaded the newest script that you posted and tried it on a flash enabled site (eg youtube). It did not run and gave a message to the effect " Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player."

So, here is the output of the script:
-------------------------------------------------------------------------------
$ sudo ./GetFlash

 This script is used to setup Flash and nspluginwrapper
 for use in 64bit Firefox or other mozilla based browsers

 Please select the version of the Ubuntu you are installing to.
 Install options are :

 1. Dapper Drake v6.06 or Edgy Eft 6.10
 2. Feisty Fawn v 7.04
 3. Gutsy Gibbon

Install option (1-3)? :1
Dapper Drake 6.06 or Edgy Eft 6.10
Reading package lists... Done
Building dependency tree... Done
Note, selecting nspluginwrapper for regex 'nspluginwrapper*'
Note, selecting nspluginwrapper-i386 for regex 'nspluginwrapper*'
The following packages will be REMOVED:
  nspluginwrapper nspluginwrapper-i386
0 upgraded, 0 newly installed, 2 to remove and 147 not upgraded.
Need to get 0B of archives.
After unpacking, 360kB disk space will be freed.
(Reading database ... 111826 files and directories currently installed.)
Removing nspluginwrapper ...
dpkg - warning: while removing nspluginwrapper, directory `/usr/lib64/mozilla/plugins' not empty so not removed.
dpkg - warning: while removing nspluginwrapper, directory `/usr/lib64/mozilla' not empty so not removed.
Removing nspluginwrapper-i386 ...
Reading package lists... Done
Building dependency tree... Done
Package flashplugin-nonfree is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 147 not upgraded.
Reading package lists... Done
Building dependency tree... Done
Package libflash-mozplugin is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 147 not upgraded.
Reading package lists... Done
Building dependency tree... Done
Package libflash0c2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 147 not upgraded.
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gnash
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mozilla-plugin-gnash
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package swfdec-mozilla
Reading package lists... Done
Building dependency tree... Done
Note, selecting libswfdec-dev for regex 'libswfdec*'
Note, selecting libswfdec0.3-dev instead of libswfdec-dev
Note, selecting libswfdec0.3-dev for regex 'libswfdec*'
Note, selecting libswfdec0.3 for regex 'libswfdec*'
E: Couldn't find package libswfdec*
Reading package lists... Done
Building dependency tree... Done
ia32-libs is already the newest version.
ia32-libs-gtk is already the newest version.
linux32 is already the newest version.
lib32asound2 is already the newest version.
alien is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 147 not upgraded.
--22:27:00--  [http://home.comcast.net/~ubuntume/nspluginwrapper-0.9.91.4-1.x86_64.rpm](http://home.comcast.net/~ubuntume/nspluginwrapper-0.9.91.4-1.x86_64.rpm)
           => `nspluginwrapper-0.9.91.4-1.x86_64.rpm'
Resolving home.comcast.net... 216.87.188.20
Connecting to home.comcast.net|216.87.188.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 54,389 (53K) [text/plain]

100%[===============================================>] 54,389       131.39K/s

22:27:06 (130.85 KB/s) - `nspluginwrapper-0.9.91.4-1.x86_64.rpm' saved [54389/54389]

--22:27:06--  [http://home.comcast.net/~ubuntume/nspluginwrapper-i386-0.9.91.4-1.x86_64.rpm](http://home.comcast.net/~ubuntume/nspluginwrapper-i386-0.9.91.4-1.x86_64.rpm)
           => `nspluginwrapper-i386-0.9.91.4-1.x86_64.rpm'
Resolving home.comcast.net... 216.87.188.20
Connecting to home.comcast.net|216.87.188.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 51,010 (50K) [text/plain]

100%[===============================================>] 51,010        97.99K/s

22:27:06 (97.90 KB/s) - `nspluginwrapper-i386-0.9.91.4-1.x86_64.rpm' saved [51010/51010]

Warning: Skipping conversion of scripts in package nspluginwrapper: postinst prerm
Warning: Use the --scripts parameter to include the scripts.
nspluginwrapper_0.9.91.4-2_amd64.deb generated
nspluginwrapper-i386_0.9.91.4-2_amd64.deb generated
Selecting previously deselected package nspluginwrapper.
(Reading database ... 111800 files and directories currently installed.)
Unpacking nspluginwrapper (from nspluginwrapper_0.9.91.4-2_amd64.deb) ...
Selecting previously deselected package nspluginwrapper-i386.
Unpacking nspluginwrapper-i386 (from nspluginwrapper-i386_0.9.91.4-2_amd64.deb) ...
Setting up nspluginwrapper (0.9.91.4-2) ...
Setting up nspluginwrapper-i386 (0.9.91.4-2) ...
--22:27:11--  [http://home.comcast.net/~ubuntume/flash.tar.gz](http://home.comcast.net/~ubuntume/flash.tar.gz)
           => `flash.tar.gz'
Resolving home.comcast.net... 216.87.188.20
Connecting to home.comcast.net|216.87.188.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,604,967 (2.5M) [application/x-tar]

100%[===============================================>] 2,604,967    219.91K/s    ETA 00:00

22:27:22 (226.10 KB/s) - `flash.tar.gz' saved [2604967/2604967]

libflashplayer.so
ln: creating symbolic link `/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so' to `/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so': File exists




 The plugin and files should now be installed .
 But we need to set the ownership of the files to you
 Please type in your login name and hit enter.  The terminal will then close and everything will be setup. Make sure to restart your browser for all
 changes to take effect.
steve
chown: cannot access `/usr/lib/nspluginwrapper/plugins': No such file or directory




 Everything has been installed
 Once you read this you can close this terminal
 window. If you have a browser running you
 will need to restart it.
-------------------------------------------------------------------------------------------------

I'm confused about which error message(s) is the one I should do something about.  
are these 'error' messages significant?:
E: Couldn't find package gnash
E: Couldn't find package mozilla-plugin-gnash
E: Couldn't find package swfdec-mozilla
E: Couldn't find package libswfdec*
dpkg - warning: while removing nspluginwrapper, directory `/usr/lib64/mozilla/plugins' not empty so not removed.

is this message significant?:
chown: cannot access `/usr/lib/nspluginwrapper/plugins': No such file or directory

Like I mentioned above the relevant files seem to be in a subdirectory of '/usr/lib/nspluginwrapper/plugins'

I can see several lines in the GetFlash script that are referring to that directory, e.g.
sudo chown -R "$refstr":users /usr/lib/nspluginwrapper/plugins

but there is no directory with that name there on my system:
$ du -m /usr/lib/nspluginwrapper*
1       /usr/lib/nspluginwrapper/noarch
1       /usr/lib/nspluginwrapper/x86_64/linux
1       /usr/lib/nspluginwrapper/x86_64
1       /usr/lib/nspluginwrapper/i386/linux
1       /usr/lib/nspluginwrapper/i386
1       /usr/lib/nspluginwrapper


Thanks for any help,
StevieP

---

### Post by misfitpierce on 2008-01-21
Can just get the tar.gz and do this

nspluginwrapper -i /file/location/libflash.so

itll install it into nspluginwrapper... just dont erase file from whereever you put it. Does not matter where... just dont remove it.

---

### Post by Perfect Storm on 2008-01-21
> OK Kilz, I will make sure to post in those forums from now on with issues on my amd64 system (Its also fine with me if a mod wants to move my thread over there),


Done.

---

### Post by Kilz on 2008-01-21
> **stevieP said:**
> 

I'm confused about which error message(s) is the one I should do something about.  
are these 'error' messages significant?:
E: Couldn't find package gnash
E: Couldn't find package mozilla-plugin-gnash
E: Couldn't find package swfdec-mozilla
E: Couldn't find package libswfdec*
dpkg - warning: while removing nspluginwrapper, directory `/usr/lib64/mozilla/plugins' not empty so not removed.
No these messages are there because the script attempts to clean out all old flash installs that may conflict with the flash plugin it installs. Old failed attempts were and are the number one cause of failure of the flash plugin.

> **stevieP said:**
> is this message significant?:
chown: cannot access `/usr/lib/nspluginwrapper/plugins': No such file or directory

Like I mentioned above the relevant files seem to be in a subdirectory of '/usr/lib/nspluginwrapper/plugins'

I can see several lines in the GetFlash script that are referring to that directory, e.g.
sudo chown -R "$refstr":users /usr/lib/nspluginwrapper/plugins

but there is no directory with that name there on my system:
$ du -m /usr/lib/nspluginwrapper*
1       /usr/lib/nspluginwrapper/noarch
1       /usr/lib/nspluginwrapper/x86_64/linux
1       /usr/lib/nspluginwrapper/x86_64
1       /usr/lib/nspluginwrapper/i386/linux
1       /usr/lib/nspluginwrapper/i386
1       /usr/lib/nspluginwrapper


Thanks for any help,
StevieP

It looks like nspluginwrapper is installed, but its not making the plugin wrapper.  Can you please give me the results of
```
ls -al /usr/lib/mozilla/plugins
```

---

### Post by jasper-two on 2008-01-21
KILZ or any body that  can help

Can you help with this one
I downloaded the NSPLUGINWRAPPER  to get the flashplayer and all I get is loads of errors
I have read all the help forums you have writen  and removed all the other flashplayer
so Iam at a loss


 This script is used to setup Flash and nspluginwrapper 
 for use in 64bit Firefox or other mozilla based browsers 

 Please select the version of the Ubuntu you are installing to. 
 Install options are : 

 1. Dapper Drake v6.06 or Edgy Eft 6.10 
 2. Feisty Fawn v 7.04 
 3. Gutsy Gibbon 

Install option (1-3)? :3
 Gutsy Gibbon 
[sudo] password for jasper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libswscale1d libboost-date-time1.34.1 libqt4-core libqt4-gui libept0
  libboost-thread1.34.1 libxapian15 debtags
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  flashplugin-nonfree nspluginwrapper
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 537kB disk space will be freed.
(Reading database ... 135696 files and directories currently installed.)
Removing flashplugin-nonfree ...
Removing nspluginwrapper ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libswscale1d libboost-date-time1.34.1 libqt4-core libqt4-gui libept0
  libboost-thread1.34.1 libxapian15 debtags
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nspluginwrapper is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libswscale1d libboost-date-time1.34.1 libqt4-core libqt4-gui libept0
  libboost-thread1.34.1 libxapian15 debtags
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libswscale1d libboost-date-time1.34.1 libqt4-core libqt4-gui libept0
  libboost-thread1.34.1 libxapian15 debtags
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflash-mozplugin is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libswscale1d libboost-date-time1.34.1 libqt4-core libqt4-gui libept0
  libboost-thread1.34.1 libxapian15 debtags
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflash0c2 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libswscale1d libboost-date-time1.34.1 libqt4-core libqt4-gui libept0
  libboost-thread1.34.1 libxapian15 debtags
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libswscale1d libboost-date-time1.34.1 libqt4-core libqt4-gui libept0
  libboost-thread1.34.1 libxapian15 debtags
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mozilla-plugin-gnash is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libswscale1d libboost-date-time1.34.1 libqt4-core libqt4-gui libept0
  libboost-thread1.34.1 libxapian15 debtags
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libswscale1d libboost-date-time1.34.1 libqt4-core libqt4-gui libept0
  libboost-thread1.34.1 libxapian15 debtags
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libswfdec0.4-dbg for regex ‘libswfdec*’
Note, selecting libswfdec0.4-dev for regex ‘libswfdec*’
Note, selecting libswfdec0.5-dev for regex ‘libswfdec*’
Note, selecting libswfdec-dev for regex ‘libswfdec*’
Note, selecting libswfdec0.3-dev for regex ‘libswfdec*’
Note, selecting libswfdec0.3 for regex ‘libswfdec*’
Note, selecting libswfdec0.4 for regex ‘libswfdec*’
Note, selecting libswfdec0.5-1 for regex ‘libswfdec*’
Note, selecting libswfdec0.5-1-dbg for regex ‘libswfdec*’
E: Couldn't find package libswfdec*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
The following packages were automatically installed and are no longer required:
  libswscale1d libboost-date-time1.34.1 libqt4-core libqt4-gui libept0
  libboost-thread1.34.1 libxapian15 debtags
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
tar: install_flash_player_9_linux.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mv: cannot stat `/tmp/nsplugwrapper/install_flash_player_9_linux/libflashplayer.so': No such file or directory
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
sudo: nspluginwrapper: command not found




 The plugin and files should now be installed .
 But we need to set the ownership of the files to you 
 Please type in your login name and hit enter.  The terminal will then close and everything
 will be setup. Make sure to restart your browser for all 
 changes to take effect.
jasper

---

### Post by Kilz on 2008-01-21
> **jasper-two said:**
> 
Error parsing proxy URL [**http://:8080/:**](**http://:8080/:**) Invalid host name.

jasper

It looks like you have some kind of proxy server running. This is stopping the script from downloading the nspluginwrapper and flash plugin.

---

### Post by stevieP on 2008-01-21
OK Kilz, here is the output of 
$ ls -al /usr/lib/mozilla/plugins
total 6976
drwxr-xr-x 2 steve users    4096 2008-01-20 22:27 ./
drwxr-xr-x 3 root  root     4096 2006-07-18 15:19 ../
-rwxr-xr-x 1 steve users 7040036 2007-06-19 17:31 libflashplayer.so*
lrwxrwxrwx 1 steve users      50 2006-07-18 15:19 nppdf.so -> ../../Adobe/Acrobat7.0/Browser/intellinux/nppdf.so
-rwxr-xr-x 1 steve users   69696 2008-01-20 22:27 npwrapper.libflashplayer.so*
lrwxrwxrwx 1 steve users      61 2008-01-20 22:27 npwrapper.so -> ../../../../usr/lib/nspluginwrapper/x86_64/linux/npwrapper.so*


If npwrapper is the relevant executable, it looks like the chown is correct, and the link is corrrect:

$ cd /usr/lib/mozilla/plugins/
$ ls ../../../../usr/lib/nspluginwrapper/x86_64/linux/
npconfig*  npwrapper.so*

Can't figure out what's wrong here.

nspluginwrapper does seem to be installed:
$ whereis nspluginwrapper
nspluginwrapper: /usr/bin/nspluginwrapper /usr/lib/nspluginwrapper /usr/bin/X11/nspluginwrapper

But I still get "no plugins are installed" when I type "about:plugins" in the address bar. I wonder if there is a problem with my mozilla installation?...

---

### Post by Kilz on 2008-01-21
> **stevieP said:**
> OK Kilz, here is the output of 
$ ls -al /usr/lib/mozilla/plugins
total 6976
drwxr-xr-x 2 steve users    4096 2008-01-20 22:27 ./
drwxr-xr-x 3 root  root     4096 2006-07-18 15:19 ../
-rwxr-xr-x 1 steve users 7040036 2007-06-19 17:31 libflashplayer.so*
lrwxrwxrwx 1 steve users      50 2006-07-18 15:19 nppdf.so -> ../../Adobe/Acrobat7.0/Browser/intellinux/nppdf.so
-rwxr-xr-x 1 steve users   69696 2008-01-20 22:27 npwrapper.libflashplayer.so*
lrwxrwxrwx 1 steve users      61 2008-01-20 22:27 npwrapper.so -> ../../../../usr/lib/nspluginwrapper/x86_64/linux/npwrapper.so*


If npwrapper is the relevant executable, it looks like the chown is correct, and the link is corrrect:



$ cd /usr/lib/mozilla/plugins/
$ ls ../../../../usr/lib/nspluginwrapper/x86_64/linux/
npconfig*  npwrapper.so*

Can't figure out what's wrong here.

nspluginwrapper does seem to be installed:
$ whereis nspluginwrapper
nspluginwrapper: /usr/bin/nspluginwrapper /usr/lib/nspluginwrapper /usr/bin/X11/nspluginwrapper

But I still get "no plugins are installed" when I type "about:plugins" in the address bar. I wonder if there is a problem with my mozilla installation?...

Lets try this. Delete these files.

```
-rwxr-xr-x 1 steve users   69696 2008-01-20 22:27 npwrapper.libflashplayer.so*
lrwxrwxrwx 1 steve users      61 2008-01-20 22:27 npwrapper.so -> ../../../../usr/lib/nspluginwrapper/x86_64/linux/npwrapper.so*
```

If this file has a * on the end , remove it
```
-rwxr-xr-x 1 steve users 7040036 2007-06-19 17:31 libflashplayer.so*
```

Then enter this 
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflash.so

If this doesnt work, we will look at the firefox directory next.
ls -al /usr/lib/firefox/plugins

---

### Post by stevieP on 2008-01-21
OK here are the results:

$ ls
libflashplayer.so*  nppdf.so@  npwrapper.libflashplayer.so*  npwrapper.so@

$ sudo rm npwrapper.libflashplayer.so
$ sudo rm npwrapper.so
$ ls
libflashplayer.so*  nppdf.so@

$ sudo rm libflashplayer.so
$ sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflash.so
nspluginwrapper: /usr/lib/mozilla/plugins/libflash.so is not a valid NPAPI plugin

I think this was also misfitpierce's suggestion, but I don't have libflash.so installed:
$ whereis libflash.so
libflash:
$ locate libflash.so
$

(nothing, its not installed anywhere... Don't I need to download it and install it before including it in the "nspluginwrapper -i /usr/lib/mozilla/plugins/libflash.so" command? Should I do that?) 

In any event, here is the output to:
$ ls -al /usr/lib/firefox/plugins/
total 20
drwxr-xr-x 2 root root  4096 2008-01-20 22:12 ./
drwxr-xr-x 5 root root  4096 2007-05-18 11:41 ../
-rw-r--r-- 1 root root 11600 2007-03-26 18:25 libunixprintplugin.so
lrwxrwxrwx 1 root root    50 2006-07-18 15:19 nppdf.so -> ../../Adobe/Acrobat7.0/Browser/intellinux/nppdf.so

(nothing about flashplayers...)

StevieP

---

### Post by Kilz on 2008-01-22
My bad, I wanted for you to rename the libflashplayer.so, but I see I wrote remove. But not a problem. [Just download this one]("http://home.comcast.net/~ubuntume/flash.tar.gz"), extract it,  and copy it into /usr/lib/mozilla/plugins/ Then run

```
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```

---

### Post by stevieP on 2008-01-23
OK, I downloaded the file and copied it to /usr/lib/mozilla/plugins/ :

$ ls /usr/lib/mozilla/plugins
libflashplayer.so*  nppdf.so@

should I be renaming it? I did not. Instead I ran nspluginwrapper to include it as you suggested:

$ sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
Password:
$ ls -Ft
npwrapper.libflashplayer.so*  libflashplayer.so*  nppdf.so@

so nspluginwrapper built an executable "npwrapper.libflashplayer.so"

I think flashplayer is still not working. 
Here for example are some websites that seem to require flash:

when I go to
[http://www.youtube.com/watch?v=aQUAxN9Sxdo](http://www.youtube.com/watch?v=aQUAxN9Sxdo)

I get "Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player."

When I go to
[http://www.rockefellercenter.com/home.html](http://www.rockefellercenter.com/home.html)

I get "Additional plugins are required to display all the media on this page" and a button to "Install missing plugins". Clicking on this gives "No suitable plugins were installed" and a button for "manual install". Clicking on this button takes me back over to Adobe flash player:
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

When I type about:plugins in the browser address bar, I still get:
"No plug-ins are installed
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org."

Not sure what to do next. I'd appreciate any suggestions though. 

Could it be a problem with my firefox version? I am using Firefox version 1.5.011 
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.0.11) Gecko/20070327
Ubuntu/dapper-security Firefox/1.5.011


StevieP

---

### Post by Kilz on 2008-01-23
Is there some reason all your flash plugins have a * at the end? This is not the way they should be and not the way I archived them. What version of Ubuntu are you running? Are you running Ubuntu, Xubuntu, Kubuntu?

---

### Post by Yellow Pasque on 2008-01-24
> **Kilz said:**
> Is there some reason all your flash plugins have a * at the end? This is not the way they should be and not the way I archived them. What version of Ubuntu are you running? Are you running Ubuntu, Xubuntu, Kubuntu?

From the ls man page:
> -F, --classify             append indicator (one of */=>@|) to entries

---

### Post by stevieP on 2008-01-24
Right. its just my ls option to show what is an executable and what is a link, directory, etc. I actually had ls aliased to do this automatically. Here it is without:

$ ls --file-type /usr/lib/mozilla/plugins/
libflashplayer.so  nppdf.so  npwrapper.libflashplayer.so


As for my Ubuntu version:

$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"

(I'm not exactly sure if this means Ubuntu rather than Kubuntu or Xubuntu)

---

### Post by Kilz on 2008-01-25
Ok, does this exist
```
/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
```

If not does this exist

```
~/.mozilla/plugins/npwrapper.libflashplayer.so
```

---

### Post by jasper-two on 2008-01-25
> **Kilz said:**
> It looks like you have some kind of proxy server running. This is stopping the script from downloading the nspluginwrapper and flash plugin.

Hi Kilz
Sorry to be a pain but
After you said that it is a proxy server problem I removed my  ADSL wireless connection and connected direct to my adsl modem so I could download the nspluginwrapper but I still get the same error.

I do not no what to do now can you help

Jasper

The following packages were automatically installed and are no longer required:
libswscale1d libboost-date-time1.34.1 libqt4-core libqt4-gui libept0
libboost-thread1.34.1 libxapian15 debtags
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
tar: install_flash_player_9_linux.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mv: cannot stat `/tmp/nsplugwrapper/install_flash_player_9_linux/l ibflashplayer.so': No such file or directory
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
dpkg: error processing *.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
*.deb
sudo: nspluginwrapper: command not found

---

### Post by SebMKd on 2008-01-25
I'm on Gusty now, and got some difficulties with the built-in FlashPlugin-nonFree from Adobe and the community supported one.
After a lots of research and reading in various forums I came to understand that an older release of Flash9 was better for AMD64.

So, here is what I did, which works flawlessly (tested on Youtube, Shockwavegame....etc):
- With Synaptic look for "Flash". Remove all the "non-free" plugins.
- Download this version of Flash: [http://launchpadlibrarian.net/10804892/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb](http://launchpadlibrarian.net/10804892/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb)
- Install with Deb package installer.
- Restart.

Maybe this helps. However, I did not test it on Dapper.

Good luck.
Seb

---

### Post by stevieP on 2008-01-29
> **Kilz said:**
> Ok, does this exist
/usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
If not does this exist
~/.mozilla/plugins/npwrapper.libflashplayer.so

Thank you for your suggestion Kilz, as I have mentioned above in post #3, there is no such directory /usr/lib/nspluginwrapper/plugins/ :
> **stevieP said:**
>  is this message significant?:
chown: cannot access `/usr/lib/nspluginwrapper/plugins': No such file or directory

Like I mentioned above the relevant files seem to be in a subdirectory of '/usr/lib/nspluginwrapper/plugins'

I can see several lines in the GetFlash script that are referring to that directory, e.g.
sudo chown -R "$refstr":users /usr/lib/nspluginwrapper/plugins

but there is no directory with that name there on my system:
$ du -m /usr/lib/nspluginwrapper*
1       /usr/lib/nspluginwrapper/noarch
1       /usr/lib/nspluginwrapper/x86_64/linux
1       /usr/lib/nspluginwrapper/x86_64
1       /usr/lib/nspluginwrapper/i386/linux
1       /usr/lib/nspluginwrapper/i386
1       /usr/lib/nspluginwrapper


The only directory in /usr/lib/nspluginwrapper/ where an npwrapper library is located 
is in  /usr/lib/nspluginwrapper/x86_64/linux/:
```
$ ls /usr/lib/nspluginwrapper/x86_64/linux/
npconfig  npwrapper.so
```
The only place where the file npwrapper.libflashplayer.so is located is in /usr/lib/mozilla/plugins/ :
```
 $ locate npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so 
```

Moreover, ~/.mozilla/plugins is an empty directory,  There are no files in it :
```
 $ ls -a ~/.mozilla/plugins/
.  ..

```

> **SebMKd said:**
> I'm on Gusty now, ...
So, here is what I did, which works flawlessly (tested on Youtube, Shockwavegame....etc):
- With Synaptic look for "Flash". Remove all the "non-free" plugins.
- Download this version of Flash: [http://launchpadlibrarian.net/10804892/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb](http://launchpadlibrarian.net/10804892/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb)
- Install with Deb package installer.
- Restart.

Thank you for the suggestion Seb. I will try that method as soon as I can restart my computer. Right now I am running some jobs on it which takes several days- they should be done by tomorrow, and I will post my results then. 

StevieP

---

### Post by Kilz on 2008-01-29
So the nspluginwrapper is installed, but you are unable to generate wrapped plugins, the symlinks to the non existent plugins do not matter.
What is the version of the installed nspluginwrapper, you should be able to find it in synaptic.

---

### Post by stevieP on 2008-01-31
> **Kilz said:**
> What is the version of the installed nspluginwrapper, you should be able to find it in synaptic.
Kilz, so far as I understand the version of nspluginwrapper is the one you gave me in message #2?:
> **Kilz said:**
> Thanks for the info you are reporting. It looks like the nsplugiwrapper package wasn't installed. That you had a file already may mean that you tried other methods that failed before the script.
[Here is the latest version]("http://home.comcast.net/~ubuntume/oldflash-0.1.2.tar.gz"), try it, dont close the script when its done. Try a flash enabled site. If you still have problems copy the text in the terminal and paste it to a reply here.
sp

---

### Post by stevieP on 2008-01-31
> **SebMKd said:**
> 
- With Synaptic look for "Flash". Remove all the "non-free" plugins.
- Download this version of Flash: [http://launchpadlibrarian.net/10804892/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb](http://launchpadlibrarian.net/10804892/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb)
- Install with Deb package installer.
- Restart.

Seb, my installation was unsuccessful. I completely removed the non-free flash plugin, downloaded from the link you provided, and tried to install with the Deb package installer. I received an error message in Deb package installer that read: 
"Error: Dependency is not satisfiable: nspluginwrapper

my ubuntu version in the Details tab in the installer is:
Version: 9.0.115.0ubuntu2

My included files in the installation are:
./
var/
var/cache/
var/cache/flashplugin-nonfree/
var/lib/
var/lib/flashplugin-nonfree/
usr/
usr/lib/
usr/lib/iceape/
usr/lib/iceape/plugins/
usr/lib/xulrunner/
usr/lib/xulrunner/plugins/
usr/lib/midbrowser/
usr/lib/midbrowser/plugins/
usr/lib/mozilla/
usr/lib/mozilla/plugins/
usr/lib/iceweasel/
usr/lib/iceweasel/plugins/
usr/lib/firefox/
usr/lib/firefox/plugins/
usr/lib/flashplugin-nonfree/
usr/share/
usr/share/lintian/
usr/share/lintian/overrides/
usr/share/lintian/overrides/flashplugin-nonfree
usr/share/doc/
usr/share/doc/flashplugin-nonfree/
usr/share/doc/flashplugin-nonfree/changelog.gz
usr/share/doc/flashplugin-nonfree/copyright



I did see a similar error message in the forums here:
[http://ubuntuforums.org/showthread.php?t=668451](http://ubuntuforums.org/showthread.php?t=668451)
but with no resolution. 

I also found the error message here: [http://lox.cl/archivos/2007/07/07/instala-adobe-flash-player-en-ubuntu-para-amd64/](http://lox.cl/archivos/2007/07/07/instala-adobe-flash-player-en-ubuntu-para-amd64/), but not being able to read spanish I don't know what was done to resolve it.

---

### Post by Kilz on 2008-01-31
> **stevieP said:**
> Kilz, so far as I understand the version of nspluginwrapper is the one you gave me in message #2?:


Nope, that was the version of the script, and later the version of flash. Can you please open up Synaptic. Do a search for nsplugiwrapper, and tell me the version from the installed version column.

---

### Post by stevieP on 2008-02-01
> **Kilz said:**
> Do a search for nsplugiwrapper, and tell me the version from the installed version column.
Ah. Interestingly I have 2 versions of nspluginwrapper installed: nspluginwrapper and 
nspluginwrapper-i386. Should I uninstall nspluginwrapper-i386?
Here is the version info on nspluginwrapper that I have installed:
```
Package: nspluginwrapper
Installed version: 0.9.91.4-2
Latest version: 0.9.91.4-2 
```

StevieP

---

### Post by Kilz on 2008-02-01
> **stevieP said:**
> Ah. Interestingly I have 2 versions of nspluginwrapper installed: nspluginwrapper and 
nspluginwrapper-i386. Should I uninstall nspluginwrapper-i386?
Here is the version info on nspluginwrapper that I have installed:
```
Package: nspluginwrapper
Installed version: 0.9.91.4-2
Latest version: 0.9.91.4-2 
```

StevieP

Good it looks like the correct version is installed.
Open a terminal and type in 
```
nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
```
without sudo

---

### Post by stevieP on 2008-02-01
> Open a terminal and type in  nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so 
OK,  Done:
```
$ nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
$ ls /usr/lib/mozilla/plugins/
libflashplayer.so  nppdf.so  npwrapper.libflashplayer.so
$ ls -l /usr/lib/mozilla/plugins/libflashplayer.so
-rwxr-xr-x 1 stevieP stevieP 7040036 2007-06-19 17:31 /usr/lib/mozilla/plugins/libflashplayer.so

```
I closed firefox and reopened it, still no luck...
Typing "about:plugins" in the address bar gives again:
"No plug-ins are installed
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org."

Please let me know if I should uninstall or reinstall anything.
sp

---

### Post by brucehelp on 2008-02-01
All I can say is I installed the wrapper and the flash player it all works.
AMD64 Ubuntu 7.10 Gutsy.
So it can work hang in there.

---

### Post by Kilz on 2008-02-02
> **stevieP said:**
> OK,  Done:
```
$ nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so


There should now be a wrapped plugin in ~/.mozilla/plugins

[CODE]sudo rm -f /usr/lib/firefox/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
sudo ln -sf ~/.mozilla/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
```


and a restart should have flash working.

---

### Post by stevieP on 2008-02-02
> **Kilz said:**
> There should now be a wrapped plugin in ~/.mozilla/plugins
But there is not:
```
$ ls ~/.mozilla/plugins/
$

```
(i.e. yeilds nothing, the directory is empty)

So should I copy one or more of the files from  /usr/lib/mozilla/plugins/  into my ~/.mozilla/plugins directory? All the command
$ nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
did was to put the npwrapper libraries in /usr/lib/mozilla/plugins/ , not in ~/.mozilla/plugins
as I mentioned above.

Here is where npwrapper files are:
```
$ locate npwrapper
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/nspluginwrapper/x86_64/linux/npwrapper.so 
```
Here is where libflashplayer files are:
```
$ locate libflashplayer
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so 
```

---

### Post by Kilz on 2008-02-03
> **stevieP said:**
> But there is not:
```
$ ls ~/.mozilla/plugins/
$

```
(i.e. yeilds nothing, the directory is empty)

So should I copy one or more of the files from  /usr/lib/mozilla/plugins/  into my ~/.mozilla/plugins directory? All the command
$ nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
did was to put the npwrapper libraries in /usr/lib/mozilla/plugins/ , not in ~/.mozilla/plugins
as I mentioned above.

Here is where npwrapper files are:
```
$ locate npwrapper
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/nspluginwrapper/x86_64/linux/npwrapper.so 
```
Here is where libflashplayer files are:
```
$ locate libflashplayer
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so 
```

Im not sure why the nspluginwrapper is refusing to make wrapped plugins, but thats what is happening. You may be better off [installing firefox32]("http://ubuntuforums.org/showthread.php?t=202537") and having a functional browser.

---

### Post by Yellow Pasque on 2008-02-03
Try the file attached to this post.  It's for Flash r115 and was made with nspluginwrapper 0.9.91.5
gunzip it to /usr/lib/nspluginwrapper/plugins, then:
```
cd /usr/lib/firefox/plugins
sudo ln -s /usr/lib/nspluginwrapper/npwrapper.libflashplayer.so
```
(make sure libflashplayer.so is in that directory too)

---

### Post by stevieP on 2008-02-04
> **Temüjin said:**
> Try the file attached to this post.  It's for Flash r115 and was made with nspluginwrapper 0.9.91.5 gunzip it to /usr/lib/nspluginwrapper/plugins,
OK done: I'm assuming you mean the directory  /usr/lib/nspluginwrapper/ ? There is no directory /usr/lib/nspluginwrapper/plugins  that you mentioned above, and the symbolic link you are creating below is to the directory /usr/lib/nspluginwrapper
So, before doing anything:
```
$ ls -F /usr/lib/nspluginwrapper/
i386/  noarch/  x86_64/ 
```
(there are only directories in that folder. Moreover libflashplayer.so is not in that directory. Nor is it in /usr/lib/firefox/plugins/ . I mentioned above where libflashplayer.so is located on my computer with the "locate" command. 
>  (make sure libflashplayer.so is in that directory too)
I didn't know what specific directory you were referring to here, so I copied it to both:
```
$ sudo cp /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox/plugins/
$  sudo cp /usr/lib/firefox/plugins/libflashplayer.so /usr/lib/nspluginwrapper/

```
after copying the gzip file over to the /usr/lib/nspluginwrapper/ directory and unzipping it):
```
$ ls -F /usr/lib/nspluginwrapper/
i386/  libflashplayer.so*  noarch/  npwrapper.libflashplayer.so  x86_64/
$ 
```
 then:
```
$ cd /usr/lib/firefox/plugins
$ sudo ln -s /usr/lib/nspluginwrapper/npwrapper.libflashplayer.so
$ ls -F
libflashplayer.so*  libunixprintplugin.so  nppdf.so@  npwrapper.libflashplayer.so@
$ 
```
So the link has been created. 
Do I need to restart my computer? I've restarted firefox, but I STILL don't see anything on youtube or the like. 
I am running some jobs again but can restart my computer tomorrow. If it doesn't work, perhaps I should follow Kilz's suggestion and install another version of firefox....

---

