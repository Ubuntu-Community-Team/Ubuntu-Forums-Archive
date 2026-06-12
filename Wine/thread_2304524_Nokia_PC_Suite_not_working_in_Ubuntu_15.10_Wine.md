---
title: "Nokia PC Suite not working in Ubuntu 15.10 Wine"
date: 2015-11-27
forum: Wine
---

### Post by Manoj_Arun_Kumar on 2015-11-27
Hi,

I am using Ubuntu 15.10 & i have installed wine1.7 and installed nokia pc suite using wine loader .

Nokia PC Suite installation was successfully, but i am unable to connection my nokia c2-00 device in any possible connection.

I am getting the following error :

There is no available connection type and therefore connection to phone cannot be established. The wizard will exit.

Question :

1) How can make my bluetooth device visible in wine1.7 which is already enable in Ubuntu system.

Thanks
MAK

---

### Post by r2rX on 2015-12-06
Unfortunately, as far as I know, I don't think it is possible (if anyone knows otherwise, feel free to correct :) ).

[http://wiki.winehq.org/USB](http://wiki.winehq.org/USB)

You may want to consider looking into Virtualization software (i.e. VirtualBox or VMWare) with a VM of Windows.

---

### Post by coldraven on 2015-12-06
I once installed the Nokia suite in Windows, it took up about 2 GB of disc space! I only needed it for one tiny function and it failed at doing that :(
Anyway, what do you want to do with your phone?
If you just want to back-up your contacts use gammu. (only 3 MB disc space!) Gammu is in the Software Centre but is a command line tool. Once you have created a config file for it it's an easy one line command to quickly backup or restore to your phone.
If you look at the second part of my post below you can see that a backup is as easy as this:
```
gammu --backup my_contacts.lmb
```

The gammu config file is a hidden file called .gammurc in your home folder (the dot in front makes it hidden). 
You can create it with Gedit and it will look something like this (You have to get the port and channel from your computer). Don't forget to save the file with a dot (period) in front of gammurc.

```

#######################
[gammu]
port = D8:2A:7E:C2:51:83
model = NAUTO
connection = bluephonet
channel = 1
synchronizetime = yes
logfile = 
logformat = nothing
use_locking = 
gammuloc=

```

Gammu can also do a lot of other things but I'm trying to keep this  simple. There is a GUI front end called Wammu but I never got it to  work. That was years ago so maybe it has improved since then.
[http://wammu.eu/gammu/](http://wammu.eu/gammu/)


My original post:
[http://ubuntuforums.org/showthread.php?t=1737148&highlight=nokia](http://ubuntuforums.org/showthread.php?t=1737148&highlight=nokia)

---

