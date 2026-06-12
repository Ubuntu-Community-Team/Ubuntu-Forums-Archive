---
title: "Compaq Turion 64 System Hang"
date: 2005-08-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by harrisxml on 2005-08-09
I just bought my new V2311US notebook w/ Turion 64.  When I put in my AMD64 version of Ubuntu Live it loads all the way to the main window where it shows gnomes loading window but then it SUDDENLY stops.  I'll be moving my cursor around but then all of a sudden it catches while still in the loading window and it never changes.  It will just freeze on the window...  What's the deal?

---

### Post by DancingSun on 2005-08-10
Do you have the ATI chipset?  If so, do a search in the forums.  The new ATI chipsets might be too new as the integrated graphics seems to be causing problems.

---

### Post by Triptych on 2005-08-10
I just purchased an Acer Ferrari 4005 notebook with a 2.0 GHz Turion.  I'll let you know how I fare.

---

### Post by harrisxml on 2005-08-11
Yeah it has integrated graphics, it's a 128mb ATI integrated PCI-E I believe.

---

### Post by jsaumer on 2005-08-12
all you need to do is edit one line in your xorg.conf to get it to boot up.  

This is a quick fix, and is probably not the optimal one.

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Driver         "ati"
        BusID          "PCI:1:5:0"
        Option         "NoAccel"               "true"
EndSection


note the Option line... that line is the key to not freezing after logging in ;)

---

### Post by DancingSun on 2005-08-12
[QUOTE=jsaumer]note the Option line... that line is the key to not freezing after logging in ;)[/QUOTE]
I think that line disables hardware acceleration though...so it's not a fix...just a work around to make your computer bootable to GNOME. Check and see if a bug has been filed on this for Ubuntu (I would think this has already been done from the frequency of this problem I've seen), and file one if it isn't already done so.

But it would probably be more effective if you can contact ATI regarding this bug so they can resolve it in their next driver release.

---

### Post by atrus325 on 2005-08-19
I've got the same computer and ran into the same problem.  My solution was hardly elegant: give up on the ati driver and just use vesa.  Unfortunately I found Ubuntu unbearably slow under the vesa driver.. the mouse was choppy, and whenever I tried to do any, even slightly strenous task, the system would drag to a crawl.

So my second solution was to try Gentoo, which, while the ati stuff still doesn't work, runs vesa much, much better.

In fact, Gentoo works very well with this laptop, and I will continue to use it for now.

The previous response was correct: just write ATI and hope to see some action.

Right now, I'm unhappy enough with them, that I always suggest nvidia whenever I encounter a customer looking for video cards (I work at a major computer retailer).

J.

---

### Post by Gnobody on 2005-08-19
Or you could use the propriatary ATi driver and Ubuntu would work fine...

---

### Post by jamesrw on 2005-08-20
ive got a compaq v2000z w/ turion chip.
was able to fix my boot hang by editng the xorg.conf. changes include:

comment out following in section 'module':
#	Load	"dri"

add the following in section 'device':
        Option          "NoAccel" "true"
        Option          "RenderAccel" "false"
        Option          "MergedFB" "off"

---

