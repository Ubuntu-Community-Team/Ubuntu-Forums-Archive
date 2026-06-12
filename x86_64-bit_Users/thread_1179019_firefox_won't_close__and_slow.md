---
title: "firefox won't close  and slow"
date: 2009-06-05
forum: x86 64-bit Users
---

### Post by milio1401 on 2009-06-05
hi guys i have the next problem i just reinstalled 64 intrepid on my pc,everything was fine,then firefox wouldn't close,it'd kind of like hang and greyed out  and i either have to force quit or  do sudo killall firefox,i removed it and reinstalled and i also created a new profile and everything seems to work until i install addon febe and  all my extensions that i had backed up ,that's when it gets messy 


:~$ firefox
ICEDTEAPLUGIN_DEBUG = (null)
Terminated


that's what i get when i  type, firefox in terminal

---

### Post by ajgreeny on 2009-06-05
Why "**sudo** killall firefox"?  You normally run firefox as user and don't need to kill it as root.  it should not be necessary as far as I'm aware to use sudo for that.

---

### Post by diamondnular on 2009-06-05
> **milio1401 said:**
> hi guys i have the next problem i just reinstalled 64 intrepid on my pc,everything was fine,then firefox wouldn't close,it'd kind of like hang and greyed out  and i either have to force quit or  do sudo killall firefox,i removed it and reinstalled and i also created a new profile and everything seems to work until i install addon febe and  all my extensions that i had backed up ,that's when it gets messy 


:~$ firefox
ICEDTEAPLUGIN_DEBUG = (null)
Terminated


that's what i get when i  type, firefox in terminal

Firefox is getting so big now, especially with the huge extension collection. It is advised that to run Firefox faster, you should keep the minimal number of extensions.

That is sad that firefox used to be my fav browser, but now its get slower and slower. Is there any other browsers (light and fast) that I should tried?

---

### Post by milio1401 on 2009-06-06
well i'm a kinda new to ubuntu,and i don't run firefox as super user the reason why i used  sudo killall firefox was because i ran the command as  normal user when it greyed out and nothing happened,and i've always used like 15 extensions nothing had happened,but i decided to reinstalled my OS since it had installed  it  just the day before,thank you for trying to help

---

### Post by lariosa42 on 2009-08-03
I have a similar problem.  Anytime I close firefox (3.0 or 3.5), it freezes.  This happened in Ubuntu 8.04, 8.10, and 9.04.  My only add-on is Adblock Plus (and the Adblock Plus Element Hiding Helper).  Now, I just force-quit FF every time I want to close it.  With FF3.5, this is even more of a pain, since it tries to recover my previous session every time, and gives me a warning since I force-quit last session.

I know this can be fixed by totally deleting my FF profile, but I don't want to do that as I have hundreds of bookmarks, etc., and I haven't gone through my profile to find out exactly what I want and what I don't.

What a pain.  I can't wait until Chrome is a little more stable for Linux.  I'll just off the bloated firefox boat in a second when that happens.

---

### Post by theremper on 2009-08-03
You could remove then reinstall firefox using synaptic

---

### Post by lariosa42 on 2009-08-04
Yep, I've done that.  The problem is that I'm too clingy to my profile settings.  I've done the full remove/reinstall of firefox before.  It works great until I slap my damn .mozilla folder back into my home folder.  Then I have my beloved bookmarks and settings again, but firefox goes back to throwing a tantrum.  One of these days I'll get around to finding out what it is in my profile that is giving me such a hard time.

---

### Post by warp99 on 2009-08-04
Do you have the icedteaplugin installed? If so remove it and the open Java libraries. Then install the Sun Java 6.0 libraries and the 64 bit plugin. After that everything should work normally. You'll also need to change the Java engine for Openoffice.org to Sun Java if you have that enabled. This is located in Tools > Options > Java in OpenOffice.org writer.

Edit:
Sun Java 6.0 packages are located in the multiverse repositories so you will need to enable those in Synaptic.

---

### Post by warp99 on 2009-08-04
I just realized that you're using Intrepid and not Jaunty. Well Intrepid doesn't have a 64-bit Sun Java plugin, but you can use the Sun Java libraries and plugin from Jaunty. This post explains in detail how to do this:

[http://ubuntuforums.org/showpost.php?p=7028890&postcount=66](http://ubuntuforums.org/showpost.php?p=7028890&postcount=66)

---

