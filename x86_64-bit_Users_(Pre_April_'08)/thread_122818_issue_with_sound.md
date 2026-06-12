---
title: "issue with sound"
date: 2006-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jpenguin on 2006-01-28
For some reasone When I launch an app from the Applications Menu I don't get any sound, I get sound if I launch the app from the terminal or a desktop shortcut.

Can somebody help me?

---

### Post by amohanty on 2006-01-28
Right click on the Applications panel item
Select 'Edit Menu'
In the application editor double click on the problem app
Make sure that the command specified in there is exactly the same as the command int desktop link and/or the CLI command.

If it is and you still are not getting any sound, change the application command in the menu editor to:
> gnome-terminal -e <insert full command + args here>

Then try again. If sound works then we can try and deal with a sepcific app and see whats going on.

AM

---

### Post by Jpenguin on 2006-01-28
I tried both of those thing, and I still don't get any sound

---

### Post by amohanty on 2006-01-28
if you do the following:
> sudo killall esd
esd &

do you hear a tinkle?

AM

---

### Post by Jpenguin on 2006-01-28
[QUOTE=amohanty]if you do the following:


do you hear a tinkle?

AM[/QUOTE]
yes, also I don't know why butsound seem to work everywhere now. thanks dude

---

### Post by amohanty on 2006-01-28
Ok it seems you are using esd instead of ALSA. There are two options:

1. Goto System->Preferences->Multimedia Systems Selector and select ALSA for Sink and source and you will not need esd
OR
2. Goto System->Preferences->Sound and check 'Enable Sound Server'

HTH
AM

---

### Post by Jpenguin on 2006-01-28
thx,that worked

Now I am trying to comiple stuff from source
configure gives me > 
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check


what do i install

---

### Post by amohanty on 2006-01-29
sudo apt-get install build-essentials


AM

---

