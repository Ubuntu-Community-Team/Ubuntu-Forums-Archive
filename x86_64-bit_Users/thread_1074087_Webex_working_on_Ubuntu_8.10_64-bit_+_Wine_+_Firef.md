---
title: "Webex working on Ubuntu 8.10 64-bit + Wine + Firefox 3"
date: 2009-02-18
forum: x86 64-bit Users
---

### Post by sunbear on 2009-02-18
It seems that the webex plugin does not work with firefox running directly on top of 64-bit ubuntu 8.10. I'm currently attending a distance learning course that uses Webex heavily so I needed a solution.

After weeks of struggling and dead-ends I have managed to get Webex to work on Ubuntu 64-bit on top of Wine.

Here is the setup that works for me:
- Wine 1.0.1
- Firefox 3.0.5 (32-bit windows version)
- Java JRE 1.6.0_12

1) Install and configure Wine for running Windows XP.
2) Copied over a missing DLL (msvcp60.dll)
The main trick to get this to work was to copy the following file from my existing Windows installation (c:\Windows\System32\msvcp60.dll) into my wine directory (~/.wine/drive_c/windows/system32).
3) Download the latest ".exe" of Firefox for 32-bit Windows and install using wine
4) Download the latest ".exe" (for offline installation) of the Java J2SE for 32-bit Windows and install using wine
5) Launch firefox and test that java is working by visiting [http://www.javatester.org/version.html]("http://www.javatester.org/version.html")
6) Attend a webex meeting or a recorded meeting and answer all the questions for downloading the webex plugin

Hope this helps some other people. Also, please chime in if anyone knows of any other easy workarounds to this problem. I tried several dead-ends before I found a solution that worked including:
1) **VMWare** - Couldn't get sound to work under ubuntu 8.10. From google I can see that lot's of ubuntu users seem to be suffering this problem
2) **Adding 32-bit firefox or swiftweasel** - I found a couple of useful links:
[Kilz guide]("http://ubuntuforums.org/showthread.php?p=1174435")
[FirefoxAndPlugins]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins")
I gave up on this when I saw that there was over 100 pages in the thread and not much specific information about 8.10 (intrepid). Overall, I think the Wine approach is probably the quicker fix with fewer potential problems down the line.
3) **ie4linux** - My idea was to try to install Internet Explorer instead of firefox. However, ie4linux doesn't seem to support the latest versions of Wine. Managed to get around this by running the setup script with "--no-gui" however the resulting webex was not stable and was slow. I think the reason for this was that ie4linux seems to use a Window98 wine setup.

---

### Post by sunbear on 2009-02-23
I think I was a bit too hasty declaring victory on this one. At this point I can play recorded Webex meetings, but the live ones are still not working.

---

