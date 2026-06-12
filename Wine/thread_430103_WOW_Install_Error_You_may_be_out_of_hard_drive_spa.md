---
title: "WOW Install Error: You may be out of hard drive space"
date: 2007-05-01
forum: Wine
---

### Post by segt on 2007-05-01
Hello,

I get the following error message when trying to install WOW with Wine 0.9.36 (running the setup program from the CD or from the hard drive)

> Sorry, the installer was unable to start up. You may be out of hard drive space.

I've read on several websites that this is due to the TEMP and TMP environment variables being set to invalid values. This is controlled through the registry and I used **wine regedit** to browse to the following key.

> HKEY_LOCAL_MACHINE\System\CurrentControlSet\Contro l\Session Manager\Environment

I changed both variables to just a backslash so it uses the current directory as the temporary directory. This was the recommended solution, however it has not worked for me. I've also verified that I do in fact have enough disk space in my home directory to install (more than enough.) Are there are other ways to fix this problem?

---

### Post by thexaspect on 2008-01-08
i just had this error witht he 2.3.2 patch, and i did the suggested trick, worked like a charm. wine needed to install gecko though, in order to render html in the loader, besides that, worked great, playing now as a matter of fact =)

---

### Post by Nicasio on 2008-07-06
I had the same problem, changed the settings in wine regedit as suggested and I thought it was going to work. I no longer get the "you may be out of hard drive space" message instead it starts up the installer and when I go to select where to have it installed I get a new error message that reads "Invalid directory chosen" but does not give me an option for a valid installation directory. 

Anyone have any suggestions?

---

