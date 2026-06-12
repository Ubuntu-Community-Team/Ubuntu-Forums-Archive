---
title: "Opera Installation Script"
date: 2006-04-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by bernardfrancois on 2006-04-05
Hi,

I made a bash script to install Opera in Ubuntu for amd64.

Today I've put the WIP03 (Work-In-Progress) version online. It can be downloaded [here](http://www.evonet.be/~bfran/extern/operaInstall_WIP03.sh).

After downloading, you can run it by executing **sudo bash operaInstall_WIP03.sh**.

Not to loose your bookmarks and other opera settings, you might first execute this:
**cd ; tar -czf .opera.backup.tar.gz .opera**
If you lost your settings and you got opera to work again, you can execute this to recover your previous opera settings:
**cd ; tar -xzvhf .opera.backup.tar.gz**

I tested it myself and it worked. I didn't have to recover any settings.

**_Featuring:_**
[LIST]
[*]Installation of the 32-bit static version of Opera 8.54.
[/LIST]

Later, I would like to add more features like:
[LIST]
[*]Installation of a chrooted environment.
[*]Installation of opera into a chrooted environment.
[*]Installation of plug-ins.
[*]Uninstallation of older opera versions.
[/LIST]

I don't have much free time, but I will try to keep the script up-to-date to install the latest version of Opera.

Anyone who wants can extend the script and post it here. It would be really nice if other people would work on this as well.

---

### Post by davidcrickett on 2006-04-26
I do hope you will update this script and make it available with chroot for the new Opera beta 9 :mrgreen:

---

### Post by rplantz on 2006-04-27
I am writing this in the static version of 9 beta. I installed it before this script was posted, so did it "by hand." Just download opera-static_9.0-20060411.1-qt_en_i386.deb and install it.

I've done some very simplistic timing measurements. It seems that Firefox 1.5 is the fastest. Epiphany and Opera are about the same. One of the big advantages of Opera is since it's 32-bit, I was able to install FlashPlayer.

I also prefer some of the features in Opera.

---

### Post by mrkipling on 2006-05-10
Thank you so much for writing this script! I've had some problems installing Opera on my 64-bit system and just gave up... but now I can use my favourite browser in Ubuntu!

---

### Post by tymek666 on 2006-05-11
thx for this scipt. I hope new opera will aviable in 64bit version too.

---

### Post by bernardfrancois on 2006-05-13
Thanks for the reactions, I'm glad I didn't only write the script to excercise on bash scripting :-)

If I find some time I'll try to make it install the flash player as well. For now I won't make it to install beta versions, and a chrooted environment will be something I'll add in the future (not before July, I've got exams soon).

About a 64-bit version of opera... Maybe we can all start mailing opera to ask them about it. All they have to do is to compile it on a 64-bit machine.

---

### Post by turbojugend_gr on 2006-05-13
Haven't tried this yet, I will now, I need the Flash plugin, m8 you are a saviour, try this also plz...

---

### Post by bernardfrancois on 2006-05-23
I tried installing the flash plugin for the static 32-bit version of opera, but I didn't succeed.
After manually installing the flash plug-in, when I go to the preferences menu in opera, I choose 'content' and then I press the 'Plug-in options...' button, then I press the 'OK' button, I get the following error:

> 
Opera encountered a problem during plug-in setup.
Plug-ins will not work properly.
Check your installation.

Could not start plug-in executable 'operamotifwrapper'.
/usr/lib/mozilla/plugins/operamotifwrapper-3
Please install Motif.

Plug-in path
(Path can be modified in Preferences dialog)

/usr/lib/opera/plugins
/usr/lib/mozilla/plugins


The needed file is available, it is a 32-bit executable, but it doesn't work. I guess the only way out is a chrooted environment? Or did anyone manage to install it?

---

### Post by jsrivo on 2006-10-29
i still keep on getting the following message:

exec: 263: /usr/lib/opera/9.02-20060919.1/opera: not found

does anyone know how i can get this to work?

thanks!

---

### Post by anydoby on 2007-04-04
> **jsrivo said:**
> i still keep on getting the following message:

exec: 263: /usr/lib/opera/9.02-20060919.1/opera: not found

does anyone know how i can get this to work?

thanks!

Oh yes! I have the same error. I have installed opera with both static qt and dynamic, and nothing helped. I see this exact error. Anybody has a clue to this?

---

### Post by Colonel Kilkenny on 2007-04-04
> **anydoby said:**
> Oh yes! I have the same error. I have installed opera with both static qt and dynamic, and nothing helped. I see this exact error. Anybody has a clue to this?

Do you have packages which names start with "ia32-" installed?

---

### Post by jargoman on 2007-05-05
The script link is broken. 

I guess there's no chance of me getting the source code and just compiling it myself.. is there an easier less risky way of installing opera.

---

