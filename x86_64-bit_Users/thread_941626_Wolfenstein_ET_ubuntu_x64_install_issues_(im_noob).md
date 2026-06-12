---
title: "Wolfenstein ET ubuntu x64 install issues (im noob)"
date: 2008-10-08
forum: x86 64-bit Users
---

### Post by newname on 2008-10-08
Hi,I am a complete noob to linux but want to get away from windows :)
Lately i have been trying to install wolfenstein ET but cant seem to get it going.heres what i get:::

a@a-desktop:~$ sudo sh '/home/a/Desktop/et-linux-2.60.x86.run' 
[sudo] password for a: 
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install..............................................................................................................................................................................................................................................................................................................................
./setup.sh: 278: /home/a/.setup7542: not found
./setup.sh: 289: /home/a/.setup7542: not found

:( please lend a hand if you can all i need is this os and this game in linux and blam im happy 4 awile.

---

### Post by soxs on 2008-10-08
Have a look at this ;-) should cover everything that is required for et:
[http://gaming.gwos.org/doku.php/guides:64bit:et_wolfenstein?s=enemy](http://gaming.gwos.org/doku.php/guides:64bit:et_wolfenstein?s=enemy)

---

### Post by newname on 2008-10-08
WoW man thankyou. So far so good i would have never figured all that stuff out.


I'm not sure but the game crashes when attempting to d/l maps i think maybe this is permissions error?
What should id do to run this as admin?

---

### Post by soxs on 2008-10-08
> **newname said:**
> WoW man thankyou. So far so good i would have never figured all that stuff out.


I'm not sure but the game crashes when attempting to d/l maps i think maybe this is permissions error?
What should id do to run this as admin?

DO NOT RUN ET AS ADIMN! a) securtity blah blah b) you won't have set any of your settings

You should look where the maps are actually stored, and try to ```
sudo chmod -Rvf 644 /path/to/folder/which/includes/your/et/maps

``` or ```
sudo chmod -Rvf 755 /path/to/folder/which/includes/your/et/maps

``` (the last one will allow the game to execute the maps, though I doubt this is required.)

EDIT: Did you dowload the 2.60 installer or did you patch the game? If you patched, and you won't mind, get the 2.6 installer as said in that howto and try again.

EDIT: As I asume you tried to run it before, you got permission problems according to (no matter if ply now, shortcut or et.blah):
> 
NOTE: It's important that you exit the installer window and do not press the installers play button. It will course permission problems for Wolfenstein.


Code:
getlibs /usr/local/games/enemy-territory/et.x86


---

### Post by newname on 2008-12-09
Thanx again. Sorry for the delayed post here but we recently had a death in the famly and everything got put on hold for awile.

 Im back in the ring with linux and gunna try this again.Ill edit this post with my results when i can.

---

### Post by soxs on 2008-12-10
You're back online, that's the only thing that counts

---

