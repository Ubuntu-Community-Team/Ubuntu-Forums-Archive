---
title: "Starcraft woes"
date: 2008-01-04
forum: Wine
---

### Post by bitter_mike on 2008-01-04
Hey all. I'm having a bit of trouble getting Starcraft to run under WinE and I think its gotta be something specific to my hardware. Most How-To's and other documentation I've read on the subject indicate that Starcraft works pretty flawlessly under WinE. Here's what I did/where I'm at:

1. I added the Wine repositories and installed the package via Synaptic (I'm running Gutsy btw).
2. I ran winecfg, it detected all my drives just fine, sound worked without me doing anything.
3. I inserted the SC cd, ran the Setup.exe program and it looked like it installed flawlessly.

After I did all that, I tried running the game from the command line using "wine StarCraft.exe" and I get this error message:

X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  563
  Current serial number in output stream:  564
fixme:shell:DllCanUnloadNow stub

After I got that message, I started playing around with the graphics options and by changing the Direct3D vertex shader support from "Hardware" to "none" the output of the error message changed slightly to:

X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  549
  Current serial number in output stream:  550

The differences are that there is no longer that line that starts with "fixme:shell:DllCanUnloadNow stub" and the numbers next to the last two lines changed (from 563 to 549 and 564 to 550). I don't know what that means, but I gather it has something to do with the GLX driver for my card. I'm using the restricted ATI driver (I have an ATI Mobility Radeon X1400).

Anyone have any ideas?

---

### Post by foolsh on 2008-01-05
try configuring wine to use a virtual desktop in winecfg 
I don't know anything about those error codes but starcraft ran at a pretty low resolution if I remember right 
it might have something to do with trying to switch resolutions

---

### Post by bitter_mike on 2008-01-05
Gave that a try, and it opens up a Virtual Desktop looking window, then closes it and gives me the same output in the terminal window. No change.

---

