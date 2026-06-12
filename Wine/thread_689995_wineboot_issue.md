---
title: "wineboot issue"
date: 2008-02-07
forum: Wine
---

### Post by yowshi on 2008-02-07
somehow something has caused wineboot to run everytime i run wine and it is causing issues, i was wondering how do i make it stop auto running or whatever. i have tried winecfg with no success

---

### Post by hikaricore on 2008-02-07
It is normal now I do believe for wineboot to run as you mentioned.

However you can remove programs from the various startup groups easily with this tool:
[http://www.mlin.net/files/StartupCPL_EXE.zip](http://www.mlin.net/files/StartupCPL_EXE.zip)

---

### Post by yowshi on 2008-02-07
it didnt auto run wineboot when  i first installed it

---

### Post by hikaricore on 2008-02-08
wineboot is new in recent versions.

---

### Post by yowshi on 2008-02-08
wineboot as a command was there a version or 2 ago. i had to run it once. it didnt auto run back then, is another exe really the only solution?

---

### Post by hikaricore on 2008-02-08
Just use it to remove the startup items from the WINE "registry".
You'll never need it again after doing that.
Or you can remove them manually which is up to you.

The WINE devs have already stated that implementing "wineboot" without giving users a way to add/remove items from the "startup groups" was
a bit of a mistake on their part, give it time and these features will be added to winecfg.  Until then take what you can get dude.  :p

---

### Post by yowshi on 2008-02-08
ran the exe wineboot wasnt listed in any of the tabs though two other programmes were and i removed them. wineboot still runs anytime i run something that uses wine

---

### Post by hikaricore on 2008-02-08
Wineboot wouldn't be in any of the tabs.. wineboot is what runs the items.

After removing items I had in mine, my WINE use was almost exactly the way it was prior to the update.
IMHO you can either downgrade to 0.9.52 before wineboot was mandatory, or you can attempt symlinking the wineboot binary to /dev/null (or remove it).

As far as i know aside from source modification there is no option to disable wineboot.

---

