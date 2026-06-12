---
title: "Cannot install Wine"
date: 2008-10-05
forum: Wine
---

### Post by natetheskate on 2008-10-05
I have installed wine before when still used Ubuntu 8.04 64-bit. Now I installed a clean copy of Ubuntu Studio 8.04 64-bit. But when either go to the terminal or through Synaptic, I get an error saying that:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: lib32nss-mdns (>= 0.10-3) but it is not installable
E: Broken packages

__

Whats going on? Is the wine repository broken or you cannot install wine on Ubuntu Studio? I am also having problems with certain updates, but that is going to be put in a different category.

---

### Post by DaVince21 on 2008-10-06
Use Synaptic's "Fix broken packages" item from the Edit menu? It's not saying "broken packages" for no reason.

---

### Post by Griffin Bain on 2008-10-06
i'm no expert but I recently just did this myself. go to the wine hq page and they have the terminal commands to link your computer to their repository and download it from there. I didn't download wine that way but I upgraded to 1.1.5 that way. they have terminal commands for both upgrading and downloading.

the site is winehq.org

---

### Post by Mr. Man on 2008-10-06
just downloadoad it from the applications > add and remove > and type in wine.
Its called wine windows emulator. you dont need to install it becuase it is done automatically. just make sure it says all available aplications in the box thats next to the search bar (left side). otherwise it might not show up when u search.

     Happy to help!
=D

---

### Post by natetheskate on 2008-10-07
None of those suggestions work. I still get the same message. I am going to submit it as a "broken repository".

---

### Post by natetheskate on 2008-10-08
I went ahead and put Ubuntu x86 8.04 back on and the Wine repository works fine. So apparently there is an issue with Ubuntu Studio 64bit and Wine.

---

