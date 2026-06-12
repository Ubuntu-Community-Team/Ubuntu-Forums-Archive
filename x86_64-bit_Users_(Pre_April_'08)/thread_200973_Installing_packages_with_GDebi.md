---
title: "Installing packages with GDebi"
date: 2006-06-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Symo on 2006-06-21
I've been trying to install a couple of packages with GDebi (Gnash and Swiftfox) but when I rightclick on the directory and click on "Open with GDebi Package Installer", it says "Could not open XXXXXX - The package might be corrupted or you are not allowed to open the file. Check the permissions of the file."

I check the permissions of the file and tick the few boxes that haven't already been ticked but it makes no difference.

I've even tried to install the manual way in the terminal but it doesn't work either. This is what I get back:

> Installing with "make install"...

========================= Installation results ===========================

Copying documentation directory...
true_fopen == 0 for fopen64("/proc/mounts", "r")
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


---

### Post by 23meg on 2006-06-21
Perhaps those are source tarballs rather than deb packages? Debs are meant to be installed with ```
sudo dpkg -i file_path
``` or GDebi, not "make install".

---

### Post by Symo on 2006-06-21
Yeah, you're right - they're source tarballs, so that explains why it doesn't work with GDebi. But why doesn't it work with:

./configure
make
make install

via the terminal?

---

### Post by darkshadow on 2006-06-21
Do you have build-essential installed?

---

### Post by Symo on 2006-06-22
Yup, I have build-essential.

---

