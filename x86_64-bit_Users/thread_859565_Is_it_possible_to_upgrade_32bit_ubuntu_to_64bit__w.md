---
title: "Is it possible to upgrade 32bit ubuntu to 64bit  without reinstalling?"
date: 2008-07-14
forum: x86 64-bit Users
---

### Post by crazyrk on 2008-07-14
Hi people, I was wondering if it's possible to upgrade my 32bit ubuntu that's already installed to a 64bit one? If yes, what happens with the programs already installed? Is there any way to make flash works in 64bit? I can spend some time to make my system work :)
Sorry for so many questions, but some search made me more confuse than before :(
Thanks!

---

### Post by logos34 on 2008-07-14
Can't upgrade across architectures.  You'll have to do a fresh install.  Yes flash works on x64 (flashplugin-nonfree is the easiest).  Check out the stickies over in the x86_64 forum

---

### Post by steveneddy on 2008-07-17
Backup you /home folder, reinstall, enable the backports repos and install Flash 10 from the repos.

64 bit rocks.

---

### Post by TimothyLuke on 2008-07-17
Disclaimer: Have no idea HOW to do what I am suggesting below but with some googling and patience i know I have seen the information about on how to do it.


Process:
[LIST]
[*]Extract list of currently installed applications  *
[*]Backup /home and /etc 
[*]Install 64bit version of Ubuntu
[*]Reinstall the packages from step 1  *
[*]Restore /home and /etc
[/LIST]

* There is a way of doing this in Aptitude but I have no idea how.


I have seen comments on being able to do a chunk of this via a live CD but do now know the details. 

(I know this is not the most helpful of posts but hopefully it will be a start)

---

### Post by logos34 on 2008-07-17
> **TimothyLuke said:**
> Disclaimer: Have no idea HOW to do what I am suggesting below but with some googling and patience i know I have seen the information about on how to do it.

Process:
[LIST]
[*]Extract list of currently installed applications  *
[*]Backup /home and /etc
[*]Install 64bit version of Ubuntu
[*]Reinstall the packages from step 1  *
[*]Restore /home and /etc
[/LIST]

* There is a way of doing this in Aptitude but I have no idea how.


Here's good, concise guide:
[https://help.ubuntu.com/community/FeistyUpgradesFreshInstall](https://help.ubuntu.com/community/FeistyUpgradesFreshInstall)

Basically you just save your currently installed packages list to file, do fresh install specifying [separate /home]("http://www.psychocats.net/ubuntu/separatehome") mountpoint (**but do NOT check the 'format' box**), then plug the list back in afterward and install--it will grab the x64 versions of all the debs 

Or if you don't have (and don't want) separate /home, you could just backup (to usb hard disk, dvd, etc) with tar (gzip) or **cp -a**:

sudo tar -czvpf /path/to/mybackup.tgz /home/user 

or 

sudo cp -a /home/user /destination


Here's another variation of the dpkg selections routine:

>  **[3.4.9 Record/copy system configuration]("http://www.debian.org/doc/manuals/quick-reference/ch-package.en.html#s-record")**

    To make a local copy of the package selection states: 
        **# dpkg --get-selections "*" > myselections**   # or use \*
     # debconf-get-selections > debconfsel.txt     "*" makes myselections include package entries for "purge" too. 
    You can transfer this file to another computer, and install it there with: 
        **# dselect update**
     # debconf-set-selections < debconfsel.txt
     **# dpkg --set-selections < myselections**
     **# apt-get -u dselect-upgrade**    # or dselect install 

Another link:
[http://www.debian-administration.org/articles/282](http://www.debian-administration.org/articles/282)

Hope that helps

---

