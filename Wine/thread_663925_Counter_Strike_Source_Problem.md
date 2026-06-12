---
title: "Counter Strike Source Problem"
date: 2008-01-10
forum: Wine
---

### Post by Wamoc on 2008-01-10
I have tried installing CSS and when it runs, it does the loading screen, then crashes to the desktop. I have followed what others did to fix this but have had no results. My sound is set for OSS, I have tried all dxlevels, and set various sound options. When running it from command line it said my sound card drivers do not allow direct access (I have also tried emulating the drivers).
I use an ATI Radeon X1800, and my sound card is integrated (it is a really good sound card in a DFI mobo).
btw, I am using 64 bit Gutsy, and whatever version of wine synaptic will install.

---

### Post by b0rka7a on 2008-01-10
Try to install the latest WINE (0.9.52). [Use this How-To]("http://ubuntuforums.org/showthread.php?t=624644")

---

### Post by ubu-for on 2008-01-10
> **Wamoc said:**
> My sound is set for OSS, I have tried all dxlevels, and set various sound options. When running it from command line it said my sound card drivers do not allow direct access (I have also tried emulating the drivers).

Configure Wine [like I did](http://ubuntuforums.org/showpost.php?p=4078846&postcount=3) and follow the HOWTO.

---

### Post by Wamoc on 2008-01-11
Ok, I got CSS to run now, except for one slight problem...
None of the text appears in the game.  I can probably play, but I would like to be able to see what I am clicking in the game.  I have put the Tahoma font file in the right place and installed the microsoft core fonts package. Any idea what is the cause of this?
Thank you for your help.

---

### Post by Amstell on 2008-01-11
I had that same problem with steam in general and decided to try out crossover.  I know its not free but it works perfect for everything.

  Just a suggestion

---

### Post by ubu-for on 2008-01-11
> **Wamoc said:**
> None of the text appears in the game.  I can probably play, but I would like to be able to see what I am clicking in the game.  I have put the Tahoma font file in the right place and installed the microsoft core fonts package. Any idea what is the cause of this?
Thank you for your help.

Maybe it's a problem with:
- 64-bit Ubuntu
- ATI drivers
- wrong Wine version
- turned on Pixel Shader

Try the forum search or go to the [CSS Wine Website](http://appdb.winehq.org/appview.php?iVersionId=3731) for more information.

---

