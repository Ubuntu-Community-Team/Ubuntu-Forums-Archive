---
title: "How do I install older version of wine?"
date: 2007-12-09
forum: Wine
---

### Post by flippykid on 2007-12-09
I'm not 100% sure on what I need to do, I downloaded wine (newest) from a package thingy, and then I installed all my stuff (cs etc) but then someone told me that since the version .9.47 there has been extra lag in counter-strike 1.6, and well when I play I get about 20 - 30 fps at best which makes no sense on a game made in the year 2000, anyways I was hoping someone could help me uninstall my version of wine so I can install the older version, and another thing this time I had to download the older version, how do I install it? It´s a folder with all this stuff but I have no idea how to install it, and people say you need to uninstall the curent version that you have, so could you tell me how to please. If I missed any info just tell me. :D

---

### Post by Vadi on 2007-12-09
Here you go: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Make sure to remove the current version of wine first!

---

### Post by flippykid on 2007-12-09
> **Vadi said:**
> Here you go: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Make sure to remove the current version of wine first!

-_- I don't think you understand my current situation, I already have the file, all I need are instructions on how to uninstall the current version with the new one.

---

### Post by cogadh on 2007-12-09
To remove the current one:
```
sudo apt-get remove --purge wine
```
To install the new one, just double-click the package file. Once it is installed, it will prompt you to update to a newer version. You can force it to not nag you about that by following the instructions here:
[https://help.ubuntu.com/community/SynapticHowto#head-ec06ac55f7b20957887c4b9cfdea6efd07727415](https://help.ubuntu.com/community/SynapticHowto#head-ec06ac55f7b20957887c4b9cfdea6efd07727415)

---

### Post by flippykid on 2007-12-09
> **cogadh said:**
> To remove the current one:
```
sudo apt-get remove --purge wine
```
To install the new one, just double-click the package file. Once it is installed, it will prompt you to update to a newer version. You can force it to not nag you about that by following the instructions here:
[https://help.ubuntu.com/community/SynapticHowto#head-ec06ac55f7b20957887c4b9cfdea6efd07727415](https://help.ubuntu.com/community/SynapticHowto#head-ec06ac55f7b20957887c4b9cfdea6efd07727415)

Thanks for the help but there is only one problem, It's a tar.bz2 file, I extracted it but all I see are these files, where do I put them? and the list of packages that that other guy sent dosn't have the version that I need

---

### Post by cogadh on 2007-12-09
Thats Wine source code, you'll need to compile it before you can install it. What version of Wine are you trying to use?

EDIT - Also, the packages that are listed under "Feisty" in the archive will still work in Gutsy.

---

### Post by flippykid on 2007-12-09
> **cogadh said:**
> Thats Wine source code, you'll need to compile it before you can install it. What version of Wine are you trying to use?

EDIT - Also, the packages that are listed under "Feisty" in the archive will still work in Gutsy.

OMG really? That saved me so much hassle, Alright Now I can get version 0.9.46, I was looking all over to see if there was a version for gutsy, thanks for the help once again. EDIT: Oh and if i reinstall wine do I lose all my stuff installed on it? because I don't want to reinstall everything, or can I just move something and then move it back?

EDIT: Alright i have it 100% installed, and everything works, but when i go to aps menu wine stuff isn't there, like winecfg and stuff, do i have to add them manually?

---

### Post by cogadh on 2007-12-09
Yep, the older versions don't add that stuff on their own.

---

### Post by OvenMitt Bandit on 2008-01-09
How do you add that stuff on your own?

---

