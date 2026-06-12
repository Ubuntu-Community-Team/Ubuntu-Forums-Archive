---
title: "Wine uninstall/reinstall question"
date: 2008-11-13
forum: Wine
---

### Post by jnewl on 2008-11-13
I really, really want to be able to play AGEOD's American Civil War under Linux, but according to the Wine games bug database, here's what you have to do:

[INDENT]Impossible to play game with wine 1.1.6 "out of the box".

Here is what has been done (under an Ubuntu Hardy Heron 8.04):
- complete remove of wine package with "sudo apt-get remove --purge wine
winbind",
- remove of directory .wine in $HOME of user,
- installed wine 1.1.6 (as stated on [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) )
- installed gamed (no problem),
- installed patch 1.09e (no problem).

Then try to launch game with following commands:
nohup wine AACW.ece > wine.txt
or
export WINEDEBUG=relay; nohup wine AACW.exe > wine+relay.txt &

[/INDENT]

My question is, is it o.k. to go ahead and do this? Or will I end up breaking something important (e.g. will I not be able to play any game *except* AACW?). I play a lot of Windows games under Linux, so the sacrifice of everything else to play just this one game isn't worth it to me.

I'm running Intrepid Ibex, btw, if that matters.

---

### Post by cogadh on 2008-11-14
Well, if you already have games installed in Wine, running those commands will delete all of it and you will have to reinstall everything. I also question the use of the "nohup" command. Technically, that will make wine continue to run even if you log out (a reboot will stop it). I really don't see the logic in using it.

---

### Post by jnewl on 2008-11-14
Ok, but uninstalling and reinstalling won't screw up Wine as its configured under Ubuntu? I mean, I don't know if anything's been done to the standard Wine package under Ubuntu or not. That's pretty much why I'm asking. It seems like uninstalling and reinstalling isn't going to change anything unless what's there right now is different from what's going to be installed. But they both have the same version number.

Am I being clear or just making things worse? :)

---

### Post by cogadh on 2008-11-15
The Wine package those instructions tell you to install is virtually identical to the default Wine package in the Ubuntu repositories, except it is a newer, unstable version of Wine. Both the default Ubuntu packages and the WineHQ packages are maintained by the same person, so you don't really have to worry about the WineHQ package doing anything strange to your system. The only potential problem you might have is, because you would be switching to the unstable Wine package (I'm assuming you've been using the 1.0.1 package from the Ubuntu repositories up till now), it may have bugs or regressions that could affect the way your other games work. Chances are, it won't change anything and some of your other games may even work better, but with the unstable packages, new bugs or regressions are always a risk.

---

### Post by jnewl on 2008-11-15
Jesus Christ, cogadh, I want to marry you. [-o< So seldom do we get a complete, accurate answer to our questions these days that finally getting one makes it seem like I won the lotto or something. Thanks mucho. I understand perfectly now.

---

### Post by carusoswi on 2008-11-15
I want to remove wine completely.  Uninstalled it using add/remove, but some bits must still be present.  Navigated to Home, but no files were shown (must be doing something wrong).  Can you help?  In order to install MSOffice and get it to associate with files created in XP, I need to install ie6 (I know this from previous experience - makes everything work, although I don't know why).  Right now, when I try to install ie6, it complains that a newer version is already installed, and then, aborts.  I know there isn't a newer version of ie installed in Ubuntu (I'm using Crossover), and the only thing I can think of is that a previous installation to install Office using wine aborted, so now I need to start from scratch - really from scratch.

Can you help?

Thanks.

Caruso

Caruso

> **cogadh said:**
> The Wine package those instructions tell you to install is virtually identical to the default Wine package in the Ubuntu repositories, except it is a newer, unstable version of Wine. Both the default Ubuntu packages and the WineHQ packages are maintained by the same person, so you don't really have to worry about the WineHQ package doing anything strange to your system. The only potential problem you might have is, because you would be switching to the unstable Wine package (I'm assuming you've been using the 1.0.1 package from the Ubuntu repositories up till now), it may have bugs or regressions that could affect the way your other games work. Chances are, it won't change anything and some of your other games may even work better, but with the unstable packages, new bugs or regressions are always a risk.

---

### Post by cogadh on 2008-11-15
The Wine "fake Windows" directory is a hidden directory (labelled ".wine") in your home directory and it is not removed when you uninstall Wine. If you want to get rid of it, you need to unhide files in the file browser (CTRL+H), or you can skip that and just delete it by running this in a terminal:
```
rm -rf ~/.wine
```

> **jnewl said:**
> Jesus Christ, cogadh, I want to marry you. [-o< So seldom do we get a complete, accurate answer to our questions these days that finally getting one makes it seem like I won the lotto or something. Thanks mucho. I understand perfectly now.
You're welcome, glad to help.:)

---

### Post by carusoswi on 2008-11-15
Thanks for the reply.  I followed your instructions.  Ran the code from the terminal.  The .wine folder no longer shows up under HOME, but wine still shows up with the aps in the menu that I want to remove.  Tried also deleting these aps from the trash (empty trash), but permission is denied.  Tried changing permissions under properties for these folders, I can set for read/write, but it doesn't take when applied.

Need more advice, sorry, and thanks.

Caruso

> **cogadh said:**
> The Wine "fake Windows" directory is a hidden directory (labelled ".wine") in your home directory and it is not removed when you uninstall Wine. If you want to get rid of it, you need to unhide files in the file browser (CTRL+H), or you can skip that and just delete it by running this in a terminal:
```
rm -rf ~/.wine
```


You're welcome, glad to help.:)

---

### Post by cogadh on 2008-11-15
Those are just shortcuts that get left behind after removing Wine (Wine has a very messy uninstall), you should just be able to delete them from the menu normally (use the menu editor). Not sure about the permissions issue on the trash, I've never run into that before.

---

### Post by carusoswi on 2008-11-16
Thanks.  I never realized there was a menu editor, but it was easy enough to find under preferences, and it worked like a charm.

Caruso

> **cogadh said:**
> Those are just shortcuts that get left behind after removing Wine (Wine has a very messy uninstall), you should just be able to delete them from the menu normally (use the menu editor). Not sure about the permissions issue on the trash, I've never run into that before.

---

