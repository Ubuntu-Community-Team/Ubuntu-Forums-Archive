---
title: "MDF to ISO"
date: 2007-05-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by DaGGer on 2007-05-18
Ok well I did the mdf2iso --cue source destination code. Now the problem I'm having is that it comes up and says 

"/home/dagger/Torrent/UnrealTournament2004/UnrealTournament2004.mdf is already ISO9660.
dagger@dagger-desktop:~$ mdf2iso --cue /home/dagger/Torrent/UnrealTournament2004/UnrealTournament2004.mdf /home/dagger/Games/
mdf2iso v0.3.1 by Salvatore Santagati
Licensed under GPL v2 or later
/home/dagger/Torrent/UnrealTournament2004/UnrealTournament2004.mdf is already ISO9660."

And I don't know what to do from here.  its obviously not an ISO and I can't use gmount-iso to use it.  So I'm really rather stuck here.

---

### Post by jamesford on 2007-05-18
in my experience most images can be renamed to .iso and work just fine

---

### Post by DaGGer on 2007-05-18
Ok well that worked, thanks.

But now I have a problem trying to install the game.  Now I'm trying to install UT2K4 and I've got it up and installing but when it tries to install to the dir /usr/local/games/ (something close to that) it says I don't have permission.  So I ended up just putting it in my home folder under /Unreal/.  It installed and it runs sort of.

I can start it but it just shuts off whenever it wants.  I don't know whats going on with it.

---

### Post by DaGGer on 2007-05-18
well never mind, sorry about that.  I restarted the computer and it works fine.  I forgot about doing that, noob mistake.  So thanks for your helps.

---

