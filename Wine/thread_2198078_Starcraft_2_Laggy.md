---
title: "Starcraft 2 Laggy"
date: 2014-01-06
forum: Wine
---

### Post by bigtinyman on 2014-01-06
Hi all,

I'm having issues making Starcraft 2 run smoothly with WINE. This is the first time I'm using WINE, so I'm new to how it works exactly. Starcraft 2 is rated to be a platinum game, so it should work flawlessly "out of the box." When I play the game, my frame rate is very low. On my Windows OS, the game runs without a problem. My machine has the specs needed to play the game without a problem. Because of the frame rate issue, it might be a graphics driver problem. But I've tried what I can to make it work with no success.

Any other tips? Information you need from me to see if my graphics driver is working? What else can I try.

---

### Post by Espionage724 on 2014-01-10
Could try a CSMT-patched version of Wine (foresto has a PPA with a patched Wine; PlayOnLinux also has a CSMT-build of Wine). Just make sure to enable CSMT from the registry (HKCU\Software\Wine\Direct3D\CSMT=enabled) and then try SC2 out.

---

