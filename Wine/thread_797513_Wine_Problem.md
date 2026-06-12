---
title: "Wine Problem"
date: 2008-05-17
forum: Wine
---

### Post by nathanlawliet on 2008-05-17
I installed Wine through Synaptic, to realize today it was 0.9.46. I had already installed Total Video Converter 3.11, which can install but not run (or apparently, uninstall for that matter).

I went to Add/Remove Programs to remove Wine, and did so. But after that, I realized Wine is still in the menu with Total Video Converter, which hasn't uninstalled. Clicking on "Uninstall" in the TVC Menu doesn't bring up any dialog, and I can't remove Wine because it is technically gone, and I can't install over it because, according to Synaptic:

Could not mark all packages for installation.
wine:
 Depends: libldap-2.4-2 (>=2.4.7) but it is not installable
  PreDepends: dpkg (>=1.14.12ubuntu3) but 1.14.5ubuntu16 is to be installed

Anyone know how to completely remove this?

Thanks,
Nate

---

### Post by Half-Left on 2008-05-17
Do you get latest WINE from winehq? [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by cogadh on 2008-05-17
A little explanation of how Wine works:
When you install and configure Wine, it creates a hidden .wine directory in your home directory. That hidden directory is where all of your Windows applications are installed. Uninstalling Wine does not remove the hidden directory, nor does it uninstall any Windows application you installed with it, though without Wine, they will no longer work. To get rid of the leftover Windows stuff, all you need to do is delete the .wine directory from your home directory, then go into System > Prefernces > Main Menu to manually delete the leftover menu entries.

---

