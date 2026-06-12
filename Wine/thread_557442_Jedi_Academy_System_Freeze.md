---
title: "Jedi Academy System Freeze"
date: 2007-09-22
forum: Wine
---

### Post by cor2y on 2007-09-22
So ok i am using he latest version of wine self compiled.
The installl of Jedi Academy works and went smoothly.
The only problems that i ran into before game play was
1) Wine refuses to recognize Alsa or OSS so in order to hear audio ESD must be selected from the audio tab in winecfg.
2) Trying to play the game in windowed mode results in errors and a closing of wine.

So to play Jedi Academy ESD was selected as Audio Output and No Windowed Mode.
I got to the setup screen etc but when i start a new game, my whole system locks up at the point the  of the  intro movie after the whole star wars word crawl.
Hitting the reset button is the only way to get back into my pc.

ANy ideas from anyone?
I can't even see what errors there were since i can't see the termainal when the game goes fullscreen
and windowed mode doesn't work.
It just won't run in a window.

---

### Post by cogadh on 2007-09-22
Is there a particular reason you used a self compiled version? Wine does provide precompiled Ubuntu .deb packages that you can use.

As for the problem you are having, it is beginning to look like the 0.9.45 version of Wine has some problems, many people are experiencing issues with it. You might try using 0.9.44 or earlier to run the game.

---

### Post by cor2y on 2007-09-22
well i couldn't find/get the latest version via the official repos it just never came through this time.
So i decided to compile it myself.

Also i finally got it to work don't ask me why but my version of Jedi Academy is the first batch of pressed cds and in the past i have never had a problem with it when i was in windows.
But for wine i had to install the 1.01 patch for the game to move past the movies and not cause a system freeze., in windowed mode it will only play on settings that are equal to what my default screen resolution is.

---

### Post by cogadh on 2007-09-22
It isn't availble in the Ubuntu official repos, you need to add Wine's repos to the sources list to get it: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Does the game run at all without using Wine's virtual desktop settings?

---

### Post by cor2y on 2007-09-22
yes it now plays outside of the wiine desktop as well

---

