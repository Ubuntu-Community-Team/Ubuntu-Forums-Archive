---
title: "downloading wine NOT from ubuntu machine"
date: 2008-04-05
forum: Wine
---

### Post by antemon on 2008-04-05
gutsy 7.10
wine 0.9.58 i386 
celeron 2.26

since my PC with ubuntu on it doesn't have an internet connection, I can't get to the terminal or update manager to get WINE.

hence, have to rely on a windows machine to get it.
don't know where to download it, and seeing that the sudo commands are internet address, I tried it out.

form here
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

went here
[http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list)

which showed:
b [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main #WineHQ - Ubuntu 7.10 "Gutsy Gibbon"
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main #WineHQ - Ubuntu 7.10 "Gutsy Gibbon"

went here
[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)
and selected **parent directory**

which landed me here
[http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)

which has links to *.deb files for wine's latest release

headed back home and double click the deb file. it seemed as if it would be succesful, but didn't install. error I forgot to save on my thumbdrive.

tried it with a previous version of wine before 0.9.58, same result.
I nice guy in the wine channel gave me a deb file, but i seem to have lost it :(
[COLOR="Blue"][B]
does anyone know what I'm doing wrong??? Or can point me to a working compiled wine?[/B][/COLOR]


reading previous threads, I came across 
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
haven't tested yet but seeing it's budgetdedicated's archive, should still have the same results

---

### Post by cogadh on 2008-04-06
You were probably missing an additional required package for the Wine install (most likely binfmt-support). Re-run the Wine DEB install (use the one from [http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/) or [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html), they are both the same) then post back with the exact error message and I can give you more specific instructions.

---

### Post by YokoZar on 2008-04-06
Yes, Wine has quite a few dependencies you'll need to satisfy for installation.

Easiest thing to do if you don't have internet is to get an Ubuntu DVD and install the default Wine included there; this will install an old Wine but also all its dependencies.  Then you can update to the new package.

---

### Post by antemon on 2008-04-06
something about **binfmt-support**...

---

### Post by cogadh on 2008-04-06
It would be easiest to follow YokoZar's advice above, but if that is not an option, you can do this:
[LIST=1]
[*]Download the binfmt-support_1.2.10_all.deb package from here: [http://us.archive.ubuntu.com/ubuntu/pool/universe/b/binfmt-support/](http://us.archive.ubuntu.com/ubuntu/pool/universe/b/binfmt-support/)
[*]Install the binfmt-support package
[*]Install Wine
[/LIST]
I don't know if the binfmt-support package has any additional dependencies. If it does, just post back with those errors and I can direct you to the additional packages that may be required.

---

### Post by antemon on 2008-04-07
Thanks, I'll do it a bit later.

and no I can't do the DvD thing, for one it's a rather dated PC barely meeting the recommended system requirements and has no DVD. And two I have no idea where to download the DVD or if I have time to download any more.

thank you for your help again:)

---

### Post by antemon on 2008-04-07
it's btching about libaudio2 now. I think I'll search around for all of WINE's dependincies and hopefully they are all in the link you provided. thanks cogadh

---

### Post by antemon on 2008-04-08
found libaudio2 somewhere, installed it but it had dependency issues as well :/

I'll just bring this thing to a friend's place and leech off his internet connection.

can I just bring the hard disk I installed ubuntu on or both HDDs? ubuntu is on second master, I'm worried about GRUB.

---

### Post by russ18uk on 2008-04-08
[http://packages.ubuntu.com](http://packages.ubuntu.com) is what I use since I'm in the same boat as you. I don't know of any way of getting a package to list all dependencies unavailable safely, but I tend to install using sudo dpkg -i package.deb then write down the dependencies required that way.

---

### Post by Google Spider on 2008-04-08
Sorry for poking in, but here's what I do to install packages on a PC with no internet connection. This method works with mint, and should also work with Ubuntu.

I have a machine with internet access so I just 

1)install whatever I want on it with apt-get 

2)then burn the **whole** contents of **/var/cache/apt/archives** on a CD.

3)then I go to internet-connection less PC, log in as root and paste all contents of the CD into /var/cache/apt/archives. Then open Add/remove programs or Synaptic and **Reload**. It should then install the package from the cache instead of looking for internet connection.

---

### Post by antemon on 2008-04-10
That's cool, only the PC I'd have to use is on windows...

---

