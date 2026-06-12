---
title: "BIG Gnome problem in Gusty"
date: 2008-06-06
forum: x86 64-bit Users
---

### Post by Thelasko on 2008-06-06
I recently shutdown my machine because severe storms were in the area.  It's been on for about a month, maybe more, but when I restarted, Gnome did not load properly.  All of my custom settings, themes, etc. are gone.  I have also lost sound.  If I try to change the settings I get a notification that gnome-settings-daemon has a problem.

Now for the good part.  I opened the system monitor and discovered 3 programs are stuck running with status "uninterruptible".  Those programs are:
aplay (it references startup.wav)
gnome-settings-daemon
mixer_applet2

I have trouble shutting down my system.  Gnome fails to close, I can force it to quit by tapping the power button but it then it fails to close ALSA.

I tried the old trick of renaming my .gnome files in my /home directory.  That didn't do anything.

Some of you may be asking, "what did you change while your system was up during that month?"  That's a good question, I don't remember everything I installed and uninstalled but here is a short list of what I remember:
Wammu (installed)
Gnokii (installed then uninstalled)
moto4lin (installed)
Multisync (installed)
ftp support for blue tooth (I think it was gnome-vfs-obexftp, I installed it and it worked fine)

As you can see, I was transferring data to and from my phones.  

My machine is an Intel core 2 duo 1.8Ghz with the dreaded G965 graphics card. 2 gigs of ram.  I don't know what the sound card is, it's integrated with the mobo.  It's also a Dell that came factory installed with Vista.

Anybody have any suggestions?

---

### Post by cariboo on 2008-06-06
Can you kill these running programs in a terminal by using:

```
sudo kill 9 ID#
```

and then restart them manually if you need them?

Jim

---

### Post by Cappy on 2008-06-07
Gnome is a bit tricky about where it stores your settings.

The best way to verify if the problem is system wide or user settings is to create a new, temporary, account.

If it is a user setting problem, I would try
```
mkdir gnome_backups
mv --target-directory=gnome_backups .gconf .gconfd .gnome .gnome2 .metacity

```
and see if that helps.

Looking in the system logs at System-->Administration-->System Logs may also reveal the problem.

---

### Post by philinux on 2008-06-07
One thing you can try is create a new user, log in and see if all's well.

---

### Post by doorknob60 on 2008-06-07
Maybe see if it's a systemwide problem or just a Gnome problem. I would install KDE
```
sudo aptitude install kubuntu-desktop
```
and load KDE instead of Gnome from the sessions menu at login and see if things work better. If you don't want to keep KDE, you can simply remove it with this:
```
sudo aptitude remove kubuntu-desktop
```

---

### Post by Thelasko on 2008-06-08
It's definitely **not**a user settings issue.  I tried creating a new account, and had the same problems.  Also note, that the login screen doesn't even have sound (you know the little drumbeat?  That's gone!)

I am 90% certain it's a problem with the ALSA drivers.  I don't know when they changed, or why they were changed, but it seems that only programs that try to use sound are having issues.

I didn't try KDE. I guarantee it won't fix the problem as KDE uses the same ALSA drivers as GNOME.

I still couldn't get cariboo907's code to kill the programs in question.  I think I will try using the OSS drivers instead of ALSA.

I tried uninstalling gnome-vfs-obexftp, that didn't fix it either.

---

### Post by Thelasko on 2008-06-10
bump?  I always get the stumpers.

---

### Post by tenmoi on 2008-06-10
you could read this page [http://www.extremetech.com/article2/0,1697,2114124,00.asp](http://www.extremetech.com/article2/0,1697,2114124,00.asp).

Although it teaches you how to improve boot time you can exploit it to disable services you don't need on start up. Try disabling the troublesome programmes or services ONE BY ONE to see which one is the culprit.

Note: Read carefully and have paper and pencil handy to note down the default parameters before actually applying anything.

hope this'll help.

---

### Post by Thelasko on 2008-06-19
Never mind, I used an old trick from back in my days of using Windows. Reformat and reinstall the OS. It's a shame I had to resort to that. I took it as an opportunity to install Hardy Heron.

Thanks for the help! Should I leave this thread open since the problem was never really solved?

---

