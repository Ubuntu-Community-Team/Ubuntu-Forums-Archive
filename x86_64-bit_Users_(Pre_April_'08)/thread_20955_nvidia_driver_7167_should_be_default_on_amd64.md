---
title: "nvidia driver 7167 should be default on amd64"
date: 2005-03-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by AndersAA on 2005-03-19
it fixes some ioctl32 (32bit) problems which I had rather frequently.

and it was a bit of a pain installing them manually, because A : the /etc/init.d/nvidia-glx script will screw it up on next reboot (even when you remove the nvidia-glx package), and B : the 32bit libraries wont install properly, you need to mv some stuff around and install them manually.

---

### Post by daniels on 2005-03-19
I'll be providing packages of nvidia-glx 1.0.7167 and fglrx 8.10.19 (plus 8.12.2, when it's public) when Hoary releases, but they won't be in the main repository.

---

### Post by jdong on 2005-03-19
[QUOTE=AndersAA]it fixes some ioctl32 (32bit) problems which I had rather frequently.

and it was a bit of a pain installing them manually, because A : the /etc/init.d/nvidia-glx script will screw it up on next reboot (even when you remove the nvidia-glx package), and B : the 32bit libraries wont install properly, you need to mv some stuff around and install them manually.[/QUOTE]

Remove the nvidia-glx script ;)


I agree, I'd like to see unofficially provided 7167 drivers. Other than that AGPGART slowdown, everything else on 7167 looks great.

---

### Post by AndersAA on 2005-03-19
I've already solved it myself, putting exit 0 close to the top of the script (incase an update would check if the file wasn't there and automatically install it, if I remember correctly dpkg will not overwrite files that are already in place without atleast asking first.. migth be different with init scripts though ;) ).

---

