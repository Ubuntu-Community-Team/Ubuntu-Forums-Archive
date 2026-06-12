---
title: "Update Manager says not all apps can be updated"
date: 2009-03-23
forum: x86 64-bit Users
---

### Post by John Jason Jordan on 2009-03-23
Intrepid x86_64.

For the past couple of months Update Manager shows a lot of apps for which there are evidently updates, but they are not automatically checked for update. Sometimes there are other updates that *are* automatically checked. If I tell it to update the ones that are checked it does so, and then the rest become grayed out.

The ones that it doesn't want me to update are:

kde-window-manager
kdebase-runtime
kdebase-runtime-bin-kde4
kdebase-workspace
kdebase-workspace-bin
kdebase-workspace-data
kdebase-workspace-libs4+5
kdelibs-bin
kdelibs5
kdm
khelpcenter4
klipper
ksysguard
libkdecorations4
libkwineffects1
libplasma2
linux-generic
linux-headers-generic
linux-image-generic
linux-restricted-modules-generic
python-plasma
python-plasma-examples
systemsettings
--Recommended updates
dolphin
juk
kdebase-bin
kdebase-data
konsole
kscreensaver
libkonq5
libokularcore1
okular
python-kde4
--Backports
brasero
libstreamanalyzer0
libstreams0

I have only the Gnome desktop with the standard Ubuntu (this is not a Kubuntu computer). However, I do have a lot of KDE apps installed, all via Synaptic from the Ubuntu repos. These include the whole KOffice suite, Okular, K3b, Kpdf, Krita, Konqueror, Ktorrent, and several more.

I don't understand why Update Manager shows these apps as having updates available, but then won't let me install them. Why?

---

### Post by Seiji338 on 2009-03-23
Try```
sudo apt-get dist-upgrade
```

Pay close attention to what it wants to remove, newly install, etc.

---

### Post by John Jason Jordan on 2009-03-24
> **Seiji338 said:**
> Try```
sudo apt-get dist-upgrade
```

Pay close attention to what it wants to remove, newly install, etc.

I thought dist-upgrade was for upgrading a whole version, e.g., from Intrepid to Jaunty. I don't want to do that until Jaunty is final.

---

### Post by dcstar on 2009-03-24
> **John Jason Jordan said:**
> 
.........
I don't understand why Update Manager shows these apps as having updates available, but then won't let me install them. Why?

Probably because you have Settings-Preferences-Distributions set to a specific preference.

---

### Post by Seiji338 on 2009-03-24
> **John Jason Jordan said:**
> I thought dist-upgrade was for upgrading a whole version, e.g., from Intrepid to Jaunty.

This is not the only use. You would have to change your sources.list for that to happen anyway. Apt-get dist-upgrade is for performing upgrades that the standard apt-get upgrade (or the update manager) won't perform. When you run sudo apt-get dist-upgrade look at the packages it wants to remove and newly install. It will be something like remove foo-2.4, newly install foo-2.5. The update manager wouldn't remove foo-2.4 so it wouldn't let foo-2.5 be installed.

---

### Post by philinux on 2009-03-24
From 

man apt-get

> dist-upgrade
           dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing
           dependencies with new versions of packages; apt-get has a "smart" conflict resolution system, and it
           will attempt to upgrade the most important packages at the expense of less important ones if
           necessary. So, dist-upgrade command may remove some packages. The /etc/apt/sources.list file contains
           a list of locations from which to retrieve desired package files. See also apt_preferences(5) for a
           mechanism for overriding the general settings for individual packages.


---

### Post by forestwalkerjoe on 2009-04-21
I am trying to add a thread and its not working.. so .. please dont get biffed at me or help me move this to the right place. 

My issues is on a wubi of Ubuntu 810 , in windows XP.. 

recently the update manager has had updates and i click and allow them to down load.. but it leaves at the bottom of list.. OTHER UPDATES grey'ed out so i cant touch them.. they are :
Other Updates
 ```
kdelibs-bin  executables for all KDE 4 core apps

kdelibs5  core libraries for all KDE 4 apps
```

but they are there each time i have an update and wont download or allow me to click on them or delete them. 

any idea why a GNOME system is trying to get Cores for KDE 4 stuff? 
or why it wont allow them to download? 
I hope fixing this.. doesn't break my system. 

when i use the above DIST code i get this:
 ```
rj@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  kdelibs-bin kdelibs5
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
rj@ubuntu:~$ 
```
thanks 


FWJ

---

### Post by John Jason Jordan on 2009-04-21
> **forestwalkerjoe said:**
> I am trying to add a thread and its not working.. so .. please dont get biffed at me or help me move this to the right place. 

My issues is on a wubi of Ubuntu 810 , in windows XP.. 

recently the update manager has had updates and i click and allow them to down load.. but it leaves at the bottom of list.. OTHER UPDATES grey'ed out so i cant touch them.. they are :
Other Updates
 ```
kdelibs-bin  executables for all KDE 4 core apps

kdelibs5  core libraries for all KDE 4 apps
```

but they are there each time i have an update and wont download or allow me to click on them or delete them. 

any idea why a GNOME system is trying to get Cores for KDE 4 stuff? 
or why it wont allow them to download? 
I hope fixing this.. doesn't break my system. 

when i use the above DIST code i get this:
 ```
rj@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  kdelibs-bin kdelibs5
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
rj@ubuntu:~$ 
```

First, you succeeded in adding your post to this thread, which is the appropriate thing to do.

Second, I don't think the Wubi installation has anything to do with the problem. 

Third, I finally (Just Sunday night) managed to resolve the issue for myself. I did not do the dist-upgrade. Instead I opened Synaptic and clicked on the Upgradable button. Synaptic would allow me to upgrade all the ones that Update Manager showed as grayed out. Instead of just selecting them all and upgrading them I checked each one to be sure it was installed. I noticed that for libplasma2 there was a libplasma3 right next to it that was not installed. I selected libplasma3 and marked it for installation. That caused Synaptic to want to uninstall libplasma2, and several of the other grayed out KDE apps, including KOffice and KFormula. I decided to let it go ahead. 

Finally I decided to use Synaptic to just uninstall all the remaining apps that were grayed out in Update Manager. Then I reinstalled them, except for a couple that I decided I never used anyway.

After I did all that I not longer have any grayed out items in Update Manager. Everything is working fine.*

Fourth, I don't know for sure, but I think this issue has to do with some KDE apps that some people running Gnome installed back in the days of KDE 3.0. When KDE came out with version 4.0 it was not done all at once. Somehow in the process some parts of KDE 3.0 failed to get upgraded.

Anyway, I would recommend just using Synaptic to uninstall them, then reinstall. The reinstall will add the current required dependencies and libraries.

* Everything is working fine except I can't reinstall KFormula. It is listed in Synaptic as installable, but if I select it to install it Synaptic says it has to uninstall KOffice and a lot of other KDE apps. KFormula is one app that I do use, so I want it back. But I'm going to leave it alone until after Thursday when Jaunty is released. After I dist-upgrade to Jaunty we'll see what happens if I try to reinstall KFormula.

---

### Post by philinux on 2009-04-21
Open synaptic package manager.

Click on Custom Filters. Then click on Upgradeable Upstream. Mark all upgrade then apply. It might want to remove some packages before it can upgrade the two you mention. Watch out if it wants to remove loads of stuff. If it does quit synaptic.

---

### Post by forestwalkerjoe on 2009-04-23
JJJ.. so i Did as suggested.. and synaptic removed the two items that would not upgrade and .. well yup.. it did and then the Upgrade manager said.. "HEY" we got stuff to upgrade!" all the sudden. 
I did the simple downloads of those upgrades and now it says.. jaunty is ready. 
I really , for some reason, thought it would be a rather quick thing to upgrade.. i have never upgraded a DIST before.. i have had as many as 11 Linux versions installed on my PC.. but never upgraded one to another. 
So it has me listed as waiting 8 to 12 hours to complete.. IS THAT FOR REAL? 
Lets just hope it doesn't crap out much of my programs and apps.. or mess up again.. my sounds as 8:10 did.. till we found the work arround in pulse audio. 
Does it reset all settings? will i lose my saved Emails from the THUNDERBIRD client? so on.. so forth? 

FWJ

---

### Post by John Jason Jordan on 2009-04-23
> **forestwalkerjoe said:**
> JJJ.. so i Did as suggested.. and synaptic removed the two items that would not upgrade and .. well yup.. it did and then the Upgrade manager said.. "HEY" we got stuff to upgrade!" all the sudden. 
I did the simple downloads of those upgrades and now it says.. jaunty is ready. 
I really , for some reason, thought it would be a rather quick thing to upgrade.. i have never upgraded a DIST before.. i have had as many as 11 Linux versions installed on my PC.. but never upgraded one to another. 
So it has me listed as waiting 8 to 12 hours to complete.. IS THAT FOR REAL? 
Lets just hope it doesn't crap out much of my programs and apps.. or mess up again.. my sounds as 8:10 did.. till we found the work arround in pulse audio. 
Does it reset all settings? will i lose my saved Emails from the THUNDERBIRD client? so on.. so forth? 
FWJ

I've always done dist-upgrades, for the past three years. The only time it failed to work perfectly was when my cable modem died in the middle of the upgrade. Not Ubuntu's fault, but it sure made a mess. 

And I am trying to upgrade to Jaunty right now. The download speed is so slow it is actually stopping now and then. Yeah, it varies from several hours left to several days left. I guess it's just because there are gazillions of us hitting the servers all at the same time.

---

### Post by John Jason Jordan on 2009-04-23
> **John Jason Jordan said:**
> .. I am trying to upgrade to Jaunty right now. The download speed is so slow it is actually stopping now and then. Yeah, it varies from several hours left to several days left. I guess it's just because there are gazillions of us hitting the servers all at the same time.

I just aborted the dist-upgrade. It was stuck on file 510 for half an hour with nothing coming down.

---

### Post by Newfoundlander on 2009-04-23
> **John Jason Jordan said:**
> I just aborted the dist-upgrade. It was stuck on file 510 for half an hour with nothing coming down.

Mine was stuck at file 147 for about two hours.  I cancelled it and I'm trying again now.

---

### Post by forestwalkerjoe on 2009-04-23
ok.. even bigger issue. i have been doing the DL for this upgrade ALL day long.. since 7:30 am. 
it has failed twice. it gets all the way through the 1200 + files to download.. Except the last 200 and then fails saying it can not get files from various places. When i restart the update manager it goes through all the process again.. until i get to the download of New packages.. the rate of transfer varies heavily.. from baud rate to 60 KPS. but still it dumps in those last 200 files.. WHAT THE HECK is GOING ON HERE? 
can some one assist me in this upgrade please? or show me how to get the upgrade OUT of my system so if i reboot i wont find i have a broken Ubuntu 8:10?
FWJ

---

### Post by John Jason Jordan on 2009-04-23
> **forestwalkerjoe said:**
> ok.. even bigger issue. i have been doing the DL for this upgrade ALL day long.. since 7:30 am. 
it has failed twice. it gets all the way through the 1200 + files to download.. Except the last 200 and then fails saying it can not get files from various places. When i restart the update manager it goes through all the process again.. until i get to the download of New packages.. the rate of transfer varies heavily.. from baud rate to 60 KPS. but still it dumps in those last 200 files.. WHAT THE HECK is GOING ON HERE? 
can some one assist me in this upgrade please? or show me how to get the upgrade OUT of my system so if i reboot i wont find i have a broken Ubuntu 8:10?

I would recommend going into Software Sources and change the server. By default I think it is set to Main, or perhaps a server in your country. There is a button where you can test it for which gives you the best bandwidth, because in Ubuntulandia not all servers are created equal.

I finally managed to get all the files (1804 in my case, because I have a lot of apps installed) and it is currently on "installing the upgrades."

As long as it hasn't finished downloading the files your Intrepid installation should not be affected. At least I think that is true.

---

### Post by forestwalkerjoe on 2009-04-24
i was able to complete the download stage.. took for ever and had to keep restarting.. BUT>. after install of all and a reboot.. the splash was different.. when i logged in.. and thats cool and all.. but i don't see any thing different in here. Except for the fact that i have NO sounds at all. non of my music plays.. and no music on FF browser if i try and sound page. 
NOW what? have i now run into bug or glitch? 

any one have any ideas? i was set up with pulse audio last time.. and it seems to still be there.. but.. no sounds. 


FWJ

---

