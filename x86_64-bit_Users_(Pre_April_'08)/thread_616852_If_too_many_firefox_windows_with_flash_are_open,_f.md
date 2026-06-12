---
title: "If too many firefox windows with flash are open, flash dissapears"
date: 2007-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by savagenator on 2007-11-18
Hello everyone. I am using 64-bit ubuntu, and have been using nspluginwrapper to make flash work in gutsy. So far though, it has worked (until that recent sound problem, i thought alsa was supposed to be good) but ever since the beginning if I play a big flash file ( a flash game perhaps) all the flash dies on me and gives an error. Right now I can't even give you the error since flash has vanished after I ran a script GetFlash from a guide, which I shouldn't have done.

Any help would be appreciated

EDIT: I posted my error below, and I do know i should not have used GetFlash...

---

### Post by Kilz on 2007-11-18
> **savagenator said:**
> Hello everyone. I am using 64-bit ubuntu, and have been using nspluginwrapper to make flash work in gutsy. So far though, it has worked (until that recent sound problem, i thought alsa was supposed to be good) but ever since the beginning if I play a big flash file ( a flash game perhaps) all the flash dies on me and gives an error. Right now I can't even give you the error since flash has vanished after I ran a script GetFlash from a guide, which I shouldn't have done.

Any help would be appreciated

Exactly, because on that [howto with the Getflash script]("http://ubuntuforums.org/showthread.php?t=476924") it **[COLOR="Red"] says in big bold letters not to install it to Gutsy.[/COLOR]** but to file a bug report. Uninstall nspluginwrapper. Then reinstall flashplugin-nonfree. Then file a bug report on your problem.

---

### Post by savagenator on 2007-11-18
Ok, well i figured out what i did wrong, its very strange: I deleted the file /home/user/.mozilla/plugins/libflashplayer.so so that it will use the other files libflashplayer.so in /usr/lib/firefox/plugins/npwrapper.libflashplayer.so

anyway I still have the problem
*** NSPlugin Viewer  *** ERROR: NPN_GetURLNotify() invoke: Message type invalid
*** NSPlugin Wrapper *** ERROR: NPP_NewStream() invoke: Message type invalid
*** NSPlugin Wrapper *** ERROR: NPP_URLNotify() invoke: Message type invalid
*** NSPlugin Wrapper *** ERROR: NPP_NewStream() invoke: Message type invalid


is what shows up. Thats when the flash failed in firefox and all pages with flash have a blank spot where flash used to be

Secondly, a problem which I almost forgot, is that only 50% of my CPU is used with flash, or npviewer.bin specifically. How do I make sure it uses all of my proccessing power? (i have a dual core amd CPU)

And I apologize for the first post, I was in a rush and did not think to completely solve the problem i knew i could fix myself.

EDIT: different one, seems to happen more often:
*** NSPlugin Wrapper *** ERROR: NPP_Write() invoke: Connection reset by peer
*** NSPlugin Wrapper *** ERROR: NPP_DestroyStream() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_New() invoke: Connection closed
LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/libflashplayer.so [/usr/lib/firefox/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]

---

### Post by savagenator on 2007-11-19
Bump....Can anyone help me? or is it just a nspluginwrapper bug?

---

### Post by savagenator on 2007-11-25
Bump again, its getting to be a real bummer not to be able to watch anything serious in flash...

---

### Post by savagenator on 2007-11-25
can anybody help?

---

### Post by savagenator on 2007-12-10
Well, it finnaly stopped happening. I am assuming that the problem happened becuase nspluginwrapper did not have multiple libflashplugin.so peices in the following places:

/usr/lib/firefox/plugins/
/usr/lib/mozilla/plugins/
/usr/lib64/firefox/plugins/
/usr/lib64/mozilla/plugins/

which is very wierd to say the least, I would think that would not matter

---

### Post by Antarctica on 2008-01-06
Yeah I'm having the same problem.  I installed the updated version of nspluginwrapper and every now and then Flash will cut off, so bump.  I wonder if somebody can help us.

---

### Post by Kilz on 2008-01-06
> **Antarctica said:**
> Yeah I'm having the same problem.  I installed the updated version of nspluginwrapper and every now and then Flash will cut off, so bump.  I wonder if somebody can help us.

[sure, try this.]("http://ubuntuforums.org/showthread.php?t=476924")

---

