---
title: "You've Broken Flash"
date: 2009-10-20
forum: x86 64-bit Users
---

### Post by Mark76 on 2009-10-20
Please confirm that start/pause no longer works properly in any embedded flash movie on youtube or bbc.co.uk.

---

### Post by absinthe on 2009-10-20
Doesn't work properly here either. No pause no skip no nothing.

---

### Post by akakingess on 2009-10-20
Mine works on You Tube, running Desktop 9.04 64-bit.

---

### Post by Niko Johnson on 2009-10-20
are you sure you have the plugin installed ```
 sudo apt-get install flashplugin-nonfree 
```

---

### Post by Niko Johnson on 2009-10-20
try running the apt update code, some times stupid errors like this take stupid answers to solve ```
 sudo apt-get update 
```

---

### Post by GandG on 2009-10-20
Controls in the BBC iPlayer (TV and Radio) and in YouTube are working fine for me - using Firefox 3.0.1.4 and Opera 10.

---

### Post by Mark76 on 2009-10-21
Damn it. I forgot to mention I'm running Karmic and Seamonkey 2 (beta 2), which, I think, is based on FF-3.5 :mad:

I had no problems with it on 9.04. Even using the same browser.

Edited to add. Same problem in Opera 10 on KK.

---

### Post by renkinjutsu on 2009-10-21
it's on and off for me..

but a workaround exists.. either use the spacebar to pause/play
and for other buttons, rightclick on the flash area, hold down the button and click somewhere else on the page to get rid of the rightclick-menu, and with the button still being held down, move your cursor back over to the flash video to click the buttons

---

### Post by Mark76 on 2009-10-21
Does anyone know if this is just a 64 bit problem?

---

### Post by GandG on 2009-10-21
> **Mark76 said:**
> Damn it. I forgot to mention I'm running Karmic and Seamonkey 2 (beta 2), which, I think, is based on FF-3.5 :mad:

I had no problems with it on 9.04. Even using the same browser.

Edited to add. Same problem in Opera 10 on KK.

Hi again, if its a Karmic 64 install its probably best posting such queries in the Development & Testing Karmic Forum. Think posting here probably assumes Jaunty or below?? In the Karmic forum there are several separate posts which discuss  64 Flash problems and offer a few solutions.

For me (in a new full Karmic install) the controls under Firefox worked through not installing the Ubuntu-Restricted-Extras, creating a .mozilla/plugins folder, downloading the 64 bit Alpha player directly from Adobe, extracting it then placing the libflashplayer.so file in the new plugins folder.

A similar arrangement partially works using Opera though here the controls only work under Compiz if a left mouse click outside the flash player window is actioned immediately before hitting a flashplayer control button. Change the Window Manager to  Metacity and normal flash controls under Opera are restored. Might Seamonkey be similarly affected?

Did a substantial partial upgrade this morning to check whether anything new might affect my flash stuff and it still works as described above. (Linux 2.6.31.14, Firefox 3.5.3 , Opera 10 build 4585)

64 bit only? Think this is the case since Flash in my Acer One (32 bit) running Karmic seems fine - though this config has not been updated for some weeks.

---

### Post by Mark76 on 2009-10-21
I have the flash plug in from Adobe and I'm not using Compiz.

---

### Post by GandG on 2009-10-21
> **Mark76 said:**
> I have the flash plug in from Adobe and I'm not using Compiz.

I installed SeaMonkey 1.1.17 in Karmic64 to see if it did anything 'peculiar' :) It automatically picked up (unprompted) the .mozilla  plugin previously mentioned and the You Tube and BBC IPlayer controls under SeaMonkey worked fine.

The only thing that I can suggest is that there may be a 'problem' flash player .so somewhere in your usr lib which might be being used instead of the expected Adobe alpha version ???

---

### Post by Mark76 on 2009-10-21
Nope. The only flash plugin I have is the one from Adobe for 64 bit Linux.

I tried playing a BBC video in Flaming Ferret in an icewm session and it worked fine.

---

