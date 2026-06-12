---
title: "Intrepid, does not resume from suspend"
date: 2009-02-24
forum: x86 64-bit Users
---

### Post by quixote on 2009-02-24
I just got a new laptop, put 64-bit Intrepid on it, but I can't get suspend to work.  If I select suspend from the logout/shutdown dialog, the system turns off, but it won't come back up.  It just starts a normal boot. ( Hibernate does work.)  It's an MSI 1223, which is the same motherboard as one of Zareason's "UltraLapSR" but mine has an Intel Graphics chipset.

fwiw, based on something I saw in another thread, I ran "lspci | grep VGA"  That gave me:

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

Does anyone have an idea how I might get this to work?  The machine boots really fast, but having suspend would be even nicer! ;)

---

### Post by dtsmith1984 on 2009-02-25
Are you using desktop effects (Compiz)?

---

### Post by quixote on 2009-02-25
I had compiz on "normal."  With it off, whaddya know, suspend works!  I should have thought of that.

Now the problem is:  I love shadowed windows and all that good stuff.  I don't want to give up one or the other.  I want both.  Any suggestions on how to have it all?  ??

---

### Post by philinux on 2009-02-26
Install the **fusion-icon **from synaptic then you can quickly turn it off and on without losing any settings.

You then need to add fusion-icon to your services so it loads at boot up. System>admin>services.

---

### Post by quixote on 2009-03-02
I actually heard about the fusion-icon a few weeks ago, but forgot all about it.  Thanks for the reminder!  That's exactly what I need.  My system seems to get flaky whenever I have compiz running and then use VirtualBox or Stellarium ... or the compiz ADD addon!  Fusion-icon will solve most of my problems though.

---

