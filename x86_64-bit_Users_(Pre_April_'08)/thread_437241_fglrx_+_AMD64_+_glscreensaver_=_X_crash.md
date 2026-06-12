---
title: "fglrx + AMD64 + glscreensaver = X crash?"
date: 2007-05-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by aoanla on 2007-05-08
Hello,

I realise that this is partly my own fault for buying ATI, but...

I'm running the 64bit Feisty on

AMD Athlon 64 X2 4800 
ASUS M2V motherboard w/ 2 Gb RAM
ATi X1950 Pro series graphics card

I have the latest fglrx driver installed via Envy (because support for the X1950 is reportedly nonexistent in earlier versions), and fglrxinfo confirms that the system is using the driver for OpenGL and has direct rendering enabled.

So, why are all screensavers which use OpenGL extremely choppy? I'm talking less than 1 FPS in extreme cases in fullscreen.
And why, when I exit fullscreen preview mode for a OpenGL screensaver, does my display go black for several seconds before X restarts?

(Inspection of logs shows that the kernel thinks that it needs to reinitialise the fglrx module, and gdm dies and restarts with 
 May  8 21:06:17 ninhursaga gdm[6817]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
which is interesting.)

It appears that some people have reported similar problems with fglrx some months ago (with no response in whatever forum they posted in), but I hope there is better understanding of the underlying issues now. After all, *some* people seem to have perfectly good acceleration with ATi cards...

---

