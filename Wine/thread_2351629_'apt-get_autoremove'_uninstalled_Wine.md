---
title: "'apt-get autoremove' uninstalled Wine"
date: 2017-02-05
forum: Wine
---

### Post by peter1897 on 2017-02-05
I installed playonlinux with 'sudo apt-get install playonlinux' which also installed wine. Then i added new ppa repository because i wanted to install another package, i didn't have added any other new ppa until that. After i installed the new package i run 'sudo apt-get autoremove' and it listed bunch of packages to be uninstalled among which were the wine packages. I select 'yes' to see if it will really uninstall 'wine' and it did.
Why this did happen? I think the problem is the new ppa repository that i added which i deleted and reinstalled 'wine'.

---

### Post by howefield on 2017-02-05
Thread moved to the "*Wine*" forum.

---

### Post by ian-weisser on 2017-02-05
Check the package names and version numbers carefully.

Offering to remove older packages with a slightly-different-name is expected behavior.
Are you absolutely sure it's offering to remove the newest?

---

### Post by peter1897 on 2017-02-05
I don't think it was about removing old packages. It said that these are unused packages.

---

### Post by ian-weisser on 2017-02-05
Yes, that's exactly why you should check the package names and version numbers carefully.

---

### Post by peter1897 on 2017-02-05
Yes, but it didn't installed a new version of wine and removed the old version. It uninstalled it completely.

---

### Post by Dennis N on 2017-02-05
PlayOnLinux builds of Wine are not installed by apt, or "registered" in a package manager as being installed. So, for that reason, I don't see PlayOnLinux builds of Wine being affected by autoremove. But Wine installed from a repository by apt might be if it was installed as a dependency. 

PlayOnLinux places it's Wine versions in subfolders of ~/.PlayOnLinux/wine/linux-x86/

so you can check if one is still there.

_**Update**_
This may clear things up:
Here is what I think can happen:
 
PlayOnLinx (POL) as installed by apt from the Ubuntu repository, depends on Wine. So, Wine will be automatically installed as a dependency at that same time IF apt has not previously installed Wine on your computer. A package _automatically installed as a dependency_ and no longer required is subject to autoremoval. So, Wine installed this way could be autoremoved. But, Wine you _manually install_ beforehand with apt is not.

In addition, when you install a game or other application through POL, POL also installs another version of Wine that's best (or even customized) for that game or application. Since these are **not** known to apt they also won't be autoremoved. These are the versions I was referring to above.

---

### Post by peter1897 on 2017-02-06
I guess then it is better to install Wine with apt-get then through playonlinux.

---

### Post by Dennis N on 2017-02-06
> **peter1897 said:**
> I guess then it is better to install Wine with apt-get then through playonlinux.

It should not matter if you keep PlayOnLinux installed. PlayOnLinux depends on Wine; so the Wine dependency should not be autoremoved IF PlayOnLinux remains installed - It's only when a package was automatically installed as a dependency AND is no longer required that it becomes autoremovable.

I think you have be be careful with autoremove - if some Linux game is installed without using apt, and you then use apt to manually install some library the game needs, that library could be autoremoved.

---

