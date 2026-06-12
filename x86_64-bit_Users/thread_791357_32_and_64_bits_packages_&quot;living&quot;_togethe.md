---
title: "32 and 64 bits packages &quot;living&quot; together? (Without &quot;chroot&quot;)"
date: 2008-05-12
forum: x86 64-bit Users
---

### Post by negora on 2008-05-12
Hi there:

Thanks to the information which I've found on this community, I've came to the conclusion that there're 2 ways to make 32 bits apps work on the Ubuntu family:

1 - Using "ia32-libs", "getlibs-all" and "dpkg -i --force-architecture" to install 32 bits DEB packs like if they were 64 bits ones.

2 - Building a "chroot" environment, which is better to keep things separated and be able to update them with "apt-get", but it means more work at the beginning.

I chose the first one. However, I'm guessing if it would be possible to keep the 32 and 64 bits versions of the same package installed in the same system withput conflicts. Checking for a possibility, my imagination "told" me that maybe it would be necessary to rebuild the package of the 32 bits version with a new name and make it point to the "lib32" directories. Is it better for this cases to choose the "chroot" option?

Thanks a lot.

---

### Post by Kilz on 2008-05-12
> **negora said:**
> Hi there:

Thanks to the information which I've found on this community, I've came to the conclusion that there're 2 ways to make 32 bits apps work on the Ubuntu family:

1 - Using "ia32-libs", "getlibs-all" and "dpkg -i --force-architecture" to install 32 bits DEB packs like if they were 64 bits ones.

2 - Building a "chroot" environment, which is better to keep things separated and be able to update them with "apt-get", but it means more work at the beginning.

I chose the first one. However, I'm guessing if it would be possible to keep the 32 and 64 bits versions of the same package installed in the same system withput conflicts. Checking for a possibility, my imagination "told" me that maybe it would be necessary to rebuild the package of the 32 bits version with a new name and make it point to the "lib32" directories. Is it better for this cases to choose the "chroot" option?

Thanks a lot.

In a 64bit install 32bit and 64bit libraries are kept in separate directories /usr/lib (64bit) and /usr/lib32 (32bit). The only way to have problems is forcing in a library package. Because on a 32bit system 32bit libraries are in /usr/lib. Never ever force in library packages, use getlibs.

---

### Post by negora on 2008-05-12
Hello Kilz:

I know, I know, that's what I do. I only force program packages and get library packages via "getlibs", which should unpack the libraries in the corresponding "lib32" folders.

But my question was referred to install program packages with the same name. For example, let's supose that I want to keep Firefox 2 in 64 and 32 bits versions. The first one is easy to install: Using Adept Manager, for example. But, for the second one, if I'm not mistaken, I've to use "dpkg -i --force-architecture", although I use "getlibs" to take the needed libraries later. This would cause a conflict of names in the Debian packages DB, because there would be 2 firefox-2 packs. Is it right? How to avoid that issue?

Thanks.

---

### Post by Grishka on 2008-05-12
> **negora said:**
> Hello Kilz:

I know, I know, that's what I do. I only force program packages and get library packages via "getlibs", which should unpack the libraries in the corresponding "lib32" folders.

But my question was referred to install program packages with the same name. For example, let's supose that I want to keep Firefox 2 in 64 and 32 bits versions. The first one is easy to install: Using Adept Manager, for example. But, for the second one, if I'm not mistaken, I've to use "dpkg -i --force-architecture", although I use "getlibs" to take the needed libraries later. This would cause a conflict of names in the Debian packages DB, because there would be 2 firefox-2 packs. Is it right? How to avoid that issue?

Thanks.

you'd have to repack a .deb file to put the binaries in a different path. still, that's not the best of ideas. the ideal solution, I guess, would be renaming the binaries to, for example, firefox-32 or analogous. still, repacking a .deb file cannot be avoided.

---

### Post by negora on 2008-05-12
**Ghriska:** That's what I needed to know. About the conflict of the binary file names, I understand that's a problem too... But I had thought of using absolute paths to call certain programs (once I had rebuilt and installed the package for the 32 bits version; called "firefox-2-32bits" for example). In the case of Firefox 2, I would use "/usr/lib/firefox/firefox-2" and "/usr/lib32/firefox/firefox-2" respectively.

However, that statement from you has made me wonder another issue... I supposse that if you execute code for 32 bits, the binary tryes to look for common libraries in the corresponding "lib32" folder, not in "lib". Is it right? I hope it's not like the case of binaries, in which they're accesible anywhere just by its name.

Thank you very much for your answers.

**Kilz:** Thanks to you too for your advice, althought I was asking that other thing ;) .

---

