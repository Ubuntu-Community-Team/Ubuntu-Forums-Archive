---
title: "How do i Install it?????"
date: 2008-02-14
forum: Wine
---

### Post by Patrekeosully88 on 2008-02-14
I don't mean to sound like an uber noob but i just got linux yestorday and i was trying to import some EXE files. I tired to and it said i couldn't basically so i got wine and i tired to install it but i have no idea how to install wine or anything on linux. I've been a windows user all my life so i guess im used to cushy installs ;) 

Any one who could help me with installing it and how to use wine, or point me in the direction of how to, would be greatly appreated. :D

---

### Post by tcpip4lyfe on 2008-02-14
open a terminal and type

sudo apt-get install wine


What are you trying to do?

---

### Post by Patrekeosully88 on 2008-02-14
I am trying to get some games on this computer. Its from steam, if u know what that is. 

But i tried what u said and i got

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
USER@USER-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libasound2 (> 1.0.12) but 1.0.10-2ubuntu4 is to be installed
        Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is to be installed
        Depends: libgphoto2-2 (>= 2.3.0) but 2.1.6-5.2ubuntu8 is to be installed        Depends: libgphoto2-port0 (>= 2.3.0) but 2.1.6-5.2ubuntu8 is to be installed
        Depends: libxml2 (>= 2.6.27) but 2.6.24.dfsg-1ubuntu1.1 is to be installed
        Depends: libxslt1.1 (>= 1.1.20) but 1.1.15-1ubuntu1 is to be installed
E: Broken packages

```

Soo..... what now?:confused:

---

### Post by blackdragon1157 on 2008-02-14
Follow the instructions [here]("http://winehq.org/site/download-deb") to add the repository to your sources.  After that, try ```
sudo apt-get install wine
``` again.

As far as Steam goes, It's a pretty easy install.  Just follow the instructions in the [AppDB entry]("http://appdb.winehq.org/appview.php?iVersionId=1554").

---

### Post by maxehhh on 2008-02-14
i read [this](http://ubuntuforums.org/showthread.php?t=624644) guide from here, and i get this error:

> root@bl1zzard:/home/bl1zzard/Desktop# sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: ia32-libs (>= 1.6) but it is not going to be installed
        Depends: lib32asound2 (> 1.0.14) but it is not going to be installed
        Depends: libc6-i386 (>= 2.6-1) but it is not going to be installed
E: Broken packages


---

### Post by blackdragon1157 on 2008-02-14
What Ubuntu version?   Have you tried installing Wine through Synaptic?  If those missing libraries are available, they'll be installed that way.

---

### Post by tcpip4lyfe on 2008-02-14
First off you have another synaptic package manager open or something else that is locking apt-get so close down everything and reboot just so we have a clean slate.

Now do:

sudo apt-get update
sudo apt-get install wine
sudo apt-get install -f


That should install it.

Just so you know this isn't an easy thing to do.  I remember the first time I used wine and it took me 3 weeks until I could actually play a game.

Here is more info on steam:

[http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)


Bookmark winehq.org  It will be your life line to getting this working.  It's going to be rough but stick with it and you'll get it.  The  good news is that steam actually works on linux fairly well but that doesn't mean you'll be able to play games with it. Some games work awesome.  WOW and the half-lifes worked great for me.  But the majority don't though without some SERIOUS tweeking and other just plain won't work.  

 If you want to game, windows is still your best bet. Dual booting is what I do. Games in windows, everything else in linux.

---

### Post by maxehhh on 2008-02-14
Well sorry for posting my problem in someone else's thread, i have Gutsy and when i try to install it throught synaptic i get the same error.

---

