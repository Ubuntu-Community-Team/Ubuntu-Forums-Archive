---
title: "[SOLVED] Heroes 3 in 64-Bit"
date: 2007-10-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by HadesScorn on 2007-10-30
All-

New linux user here. About 2 weeks ago I became fed up with the "wonderful" Vista. As an early adapter, I figured I'd try their 64 bit version. Major disappointment. Anywho, switched over to Gutsy Gibbon 64 bit. For the most part, very happy with how its been performing.

However, I've got one problem. I'm a huge retro gamer, and one of my favorites is HOMM3. I happed to have a [old] Loki disk for linux of it courtesy of my brother. Trying to install it in Linux gives me the following messages:

user@user-desktop:/media/iso$ sudo bash setup.sh
[sudo] password for user:
This installation doesn't support glibc-2.0 on x86_64

Please contact Loki Technical Support at [email]support@lokigames.com[/email]

Obviously hard to do as Loki went out of business a while ago. I've tried to figure this out via googling, but I can't solve it. I've got the original Windows version, but I'd much rather run it on semi-native code. Any help is much appreciated.

UPDATE: Solved. If you've got this issue on 64 bit Loki games, try the following:

```
sudo linux32 bash ./setup.sh
```

---

### Post by aidanr on 2007-10-30
[http://icculus.org/lgfaq/#imusingcocaine](http://icculus.org/lgfaq/#imusingcocaine)

---

### Post by HadesScorn on 2007-10-30
Not quite certain which line i'm being refed to. Here's my output for the two likely candidates:

user@user-desktop:/media/iso$ linun32 setup.sh
bash: linun32: command not found
user@user-desktop:/media/iso$ sudo bash linux32 setup.sh
/usr/bin/linux32: /usr/bin/linux32: cannot execute binary file

user@user-desktop:/media/iso$ export SETUP_LIBC=glibc-2.1.
user@user-desktop:/media/iso$ sudo bash ./setup.sh
This installation doesn't support glibc-2.0 on x86_64

Please contact Loki Technical Support at [email]support@lokigames.com[/email]

---

### Post by Cappy on 2007-10-31
Try
```

export SETUP_LIBC=glibc-2.1

```

It looks like you copied an extra period in there

---

### Post by HadesScorn on 2007-10-31
Cappy-

user@user-desktop:/media/iso$ export SETUP_LIBC=glibc-2.1
user@user-desktop:/media/iso$ sudo bash ./setup.sh
[sudo] password for user:
This installation doesn't support glibc-2.0 on x86_64

Please contact Loki Technical Support at [email]support@lokigames.com[/email]

Once again, the brick wall.

---

### Post by Cappy on 2007-10-31
For gutsy you just use
```
sudo apt-get install ia32-libs
export SETUP_LIBC=glibc-2.1
sudo linux32 ./setup.sh
```

Feisty users and below will need to (DO NOT RUN THIS ON GUTSY!)
```
sudo apt-get install linux32
```
before the above code


I know that a chroot will work but that is almost always overkill.

---

### Post by HadesScorn on 2007-10-31
Somewhat hesitant to follow through on that one due to the following:

Reading package lists... Done
Building dependency tree
Reading state information... Done
ia32-libs is already the newest version.
The following packages were automatically installed and are no longer required:
  libsdl-ttf2.0-0 libgtk1.2 libglib1.2 python2.4 librsvg2-common neverdata
  python2.4-minimal libgtk1.2-common xmms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ubuntu-minimal util-linux util-linux-locales
The following NEW packages will be installed:
  linux32
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  util-linux
0 upgraded, 1 newly installed, 3 to remove and 0 not upgraded.
Need to get 5632B of archives.
After unpacking 5353kB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'

---

### Post by bremen on 2007-10-31
The first line that Cappy gave is unnecessary (and will really mess up your system) I just installed Heroes3 on an AMD64 Gutsy install using exactly these commands:

```
export SETUP_LIBC=glibc-2.1
sudo linux32 bash ./setup.sh
```

Actually I'm pretty sure the export line isn't required either, but it won't kill you.

---

### Post by Cappy on 2007-10-31
> **bremen said:**
> The first line that Cappy gave is unnecessary (and will really mess up your system) I just installed Heroes3 on an AMD64 Gutsy install using exactly these commands:

```
export SETUP_LIBC=glibc-2.1
sudo linux32 bash ./setup.sh
```

Actually I'm pretty sure the export line isn't required either, but it won't kill you.

Bremen is correct, it seems in Gutsy you don't need to install linux32 (which is why that warning is there).

---

### Post by HadesScorn on 2007-11-02
Huzzah! Worked like a charm. Many thanks to you both on this one. I can put this one down as solved. For those browsing for it:

```
sudo linux32 bash ./setup.sh
```

is all it takes.

---

### Post by Baby Boy on 2007-11-02
> **HadesScorn said:**
> Huzzah! Worked like a charm. Many thanks to you both on this one. I can put this one down as solved. For those browsing for it:

```
sudo linux32 bash ./setup.sh
```

is all it takes.
Great. Now I can play this amazing game again.

(You should mark this thread as solved via *Thread tools*)

---

### Post by Evanlec on 2007-11-02
i dont understand how u can run linux32 without installing linux32 package?
what is the linux32 package then and why is it so dangerous if it appears to be already installed?

---

### Post by HadesScorn on 2007-11-02
I guess we've got emulation in gutsy. Trying to change that popped up the error message.

---

### Post by peryn on 2007-11-02
Thanks! It works great :)
But fullscreen doesn't work - plz help

---

### Post by bremen on 2007-11-03
Somehow I doubt fullscreen mode will work.  Best you can do, I suppose, is to lower the screen resolution.

---

### Post by brianbarry on 2007-11-03
Can someone please tell me what I lose by uninstalling "linux-util" package, in order to install "linux32"?

Brian

---

### Post by Cappy on 2007-11-03
> **brianbarry said:**
> Can someone please tell me what I lose by uninstalling "linux-util" package, in order to install "linux32"?

Brian

MANY ESSENTIAL UTILITIES - DO NOT DO IT. NEVER REMOVE util-linux.

Again ... **linux32 is already installed for Gutsy!**

Only Feisty and below needs to ```
sudo apt-get install linux32
```.

---

### Post by HadesScorn on 2007-11-03
Fullscreen will not work as the game's code cannot create better than 800x640. personally, I don't mind as it lets me throw on a movie while I play. :)

Have to say again, this solution works great. I'm happily halfway through the game already. Videos load [such as HOMM3 has], haven't had a single freeze yet, etc.

---

