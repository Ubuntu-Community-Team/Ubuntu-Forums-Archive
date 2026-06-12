---
title: "[SOLVED] Flash was working in Hardy...for one day..."
date: 2008-05-04
forum: x86 64-bit Users
---

### Post by KillaKurt on 2008-05-04
It seems like I can't get Flash to work no matter what I do :(

Flash was working FINE...sound and everything!  For ONE day.

I upgraded to Hardy, followed the instructions in the sticky that said to type this command:

"sudo apt-get install flashplugin-nonfree lib32nss-mdns"

And it worked great.

Today...I start the computer up.  Flash no worky.

Is there anything I'm doing wrong?  I tried reinstalling it with that command...to no avail.

I'm a t0tal n00b so keep it simple please!!

---

### Post by openaddict on 2008-05-04
First of all, make sure the flash library is there:

```
ls -l /usr/lib/*flash*

-rw-r--r-- 1 root root 8115888 2008-04-30 21:15 libflashplayer.so
```

That's what mine looks like.  If it's not there remove the package, clean out your package information, and reinstall it like so:

```
sudo apt-get remove flashplugin-nonfree lib32nss-mdns
sudo apt-get autoclean
sudo apt-get update
sudo apt-get install flashplugin-nonfree lib32nss-mdns
```

Make sure it's in your firefox plug-in's directory:
```
sudo cp /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/firefox-addons/plugins/
```

See if that works.

---

### Post by KillaKurt on 2008-05-04
figured it out!!!  I checked mozilla's site and saw that I can start firefox with a -P command line extension which lets me edit the firefox profiles.  I created a new profile and everything works fine, so i'm gonna delete the old profile.  Thank you for your help and concern anyway!!!  :D

---

