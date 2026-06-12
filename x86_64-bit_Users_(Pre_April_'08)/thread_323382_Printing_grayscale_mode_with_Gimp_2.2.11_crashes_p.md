---
title: "Printing grayscale mode with Gimp 2.2.11 crashes print plug-in"
date: 2006-12-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by jvalatka on 2006-12-22
Here is a Gimp problem.  I haven't yet tried to reproduce it on the popular 32-bit platform, but my life's aim is to put all the eggs in the 64-bit basket, so here goes.

My 64-bit Dapper installation is running Gimp 2.2.11 (gimp 2.2.11-1ubuntu3.1).
Also installed is the print plugin (gimp-print 5.0.0~rc2-0ubuntu6).
I'm trying to print grayscale images, but my HP DeskJet 855C keeps trying to print those images in terms of cyan, magenta, and yellow (as well as black).  Since the printer is clunky and isn't using the cyan and yellow ink, everything comes out in black and magenta.  Well, Gimp's print plug-in allows me to select its Output tab and change the output type to Grayscale (instead of Color) so I can print in "shades of gray using black ink".

However, whenever I use this Grayscale option and try to print, I get this error:

=====================
Gimp Message
Plug-In crashed: "print"
(/usr/lib/gimp/2.0/plug-ins/print)

The dying Plug-In may have messed up GIMP's internal state. You may want to save your images and restart GIMP to be on the safe side.
=====================

Can anyone explain this?  I was going to post this as a bug with gimp.org, but then I wasn't sure if this would be specific to Ubuntu, so I thought I'd start here first.

Thanks
Jay

---

