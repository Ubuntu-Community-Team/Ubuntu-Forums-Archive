---
title: "Hype: The time quest won't install."
date: 2008-10-18
forum: Wine
---

### Post by DOS4dinner on 2008-10-18
Hype is a Win95/98/ME 3D action game that has always been a favorite of mine. The demo installed fine (Didn't run, but it did install), so I decided to get my full copy and try it out.

So, I got my CD out and tried installing. It was installing fine...until 99% complete. Then, it gives me this:
fixme:advpack:ExecuteCabW Cab archive not extracted!
fixme:advpack:ExecuteCabW Cab archive not extracted!
fixme:advpack:ExecuteCabW Cab archive not extracted!
fixme:advpack:ExecuteCabW Cab archive not extracted!
fixme:advpack:ExecuteCabW Cab archive not extracted!
fixme:advpack:ExecuteCabW Cab archive not extracted!
fixme:advpack:ExecuteCabW Cab archive not extracted!
fixme:advpack:ExecuteCabW Cab archive not extracted!
fixme:advpack:ExecuteCabW Cab archive not extracted!

From there, a message comes up and says "Install Failed." and closes up. So far, I've tried running it in 95/98/ME compat modes, and all of them do the same thing. Any Ideas?

Running Ubuntu 8.04 and Wine 1.1.6.
Just for fun, I Found where it happens in the wine source code: Line 670-690 of wine/dlls/advpack/install.c. Not sure how that helps, but I'm sure it does.

---

