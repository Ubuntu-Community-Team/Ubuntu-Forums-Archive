---
title: "Cannot remove compiled Wine 1.4rc in Lucid and reinstall 1.3.37"
date: 2012-02-14
forum: Wine
---

### Post by miked00 on 2012-02-14
I'm running Lucid Lynx. I had installed Wine 1.3.37 from Ubuntu  Wine PPA and I had my programs working. I wanted to install Wine 1.4rc3  so that I could install Office 2010. So I compiled 1.4rc3 from source.  Then I ran into regressions that stopped some programs from working.
  No matter what I do, I cannot seem to get Wine 1.3.37 to reinstall. I  have completely removed Wine, I have used Synaptic to "completely  remove" packages, and I have tried to reinstall the current version from  Ubuntu Wine PPA which should be Wine 1.3.37. When I go to "About" under  winecfg, it always shows Wine 1.4rc3, and some of my programs don't  work.
  Thanks for the help.


  Lucid Lynx Backported kernel from Oneiric (3.0.0.-15) with Intel Glasen drivers for Sandy Bridge

---

### Post by ajgreeny on 2012-02-14
Look in the source files folder for something with uninstall in the name, eg **make-uninstall**

---

### Post by miked00 on 2012-02-14
Could not find any uninstall targets, but I did run "whereis wine" and found the compiled files. I then deleted them. Problem solved.

---

