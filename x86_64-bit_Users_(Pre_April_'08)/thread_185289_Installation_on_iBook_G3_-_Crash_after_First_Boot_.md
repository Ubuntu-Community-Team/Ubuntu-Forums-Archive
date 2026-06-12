---
title: "Installation on iBook G3 - Crash after First Boot @ Packpages Install"
date: 2006-05-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by Crushed on 2006-05-31
Dear Ubuntu-Cracks,

first i want to tell you that myself comes from germany so be sorry for my sometimes bad english. My problem is that i tried to install ubuntu on my ibook g3. the installation worked perfectly but after rebooting the system the system shows its loading start screen and then tries to install additional packages. "Preparing for installation.." 0% for 12 hours =) and nothing on...where can i tell my new system that he should not install this packages OR how can i get it working? Hmm i should tell you that the harddisk of my ibook is only 10gb large, not thaat large but hmm...it is possible to get ubuntu usefully started on a 10gb installation?
hopefully any body could help me with it, and greetings from germany.

Stefan Seibert

---

### Post by Ptero-4 on 2006-05-31
I used to have the same iBook model you have and yes ubuntu can be installed easy on that tiny HD. As for the install problems do this. Reinstall but when booting the install CD select server-powerpc. It will install the first stage packages and skip the rest. After first boot you can insert the ubuntu CD and type sudo apt-get install ubuntu-desktop. Use the password for the account you created during the installation when it asks for a password, the ubuntu-desktop package install everything you need.

---

