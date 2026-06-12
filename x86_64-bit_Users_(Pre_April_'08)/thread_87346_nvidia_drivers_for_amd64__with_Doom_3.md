---
title: "nvidia drivers for amd64  with Doom 3"
date: 2005-11-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by darkpark on 2005-11-07
When I installed the amd64 drivers for my nvidia 6800gt they installed fine but when the installer asked me whether i'd like to install the 32bit compatibility glx support i said yes but i didn't load the module succesfully.  Despite that problem, my opengl screensavers and the glxgears program work without any problems.  Now when i try to run doom 3, it fails to initialize its opengl drivers.   Anyone experience this problem?

---

### Post by jimboberella on 2005-11-07
What is the text of the error? I had trouble with UT2004 and Armyops but it was just a location problem, in that the app was looking in the qwrong place for the libs.

Are you running 32bit or 64bit Doom3?

---

### Post by vgeddes on 2005-11-08
The problem you are having with the compatibility libs is well documented, I had it too once. The Nvidia Installation Howto provides a solution.

---

