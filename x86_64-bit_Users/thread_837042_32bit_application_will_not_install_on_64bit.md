---
title: "32bit application will not install on 64bit"
date: 2008-06-22
forum: x86 64-bit Users
---

### Post by skarosg3 on 2008-06-22
Hi all,
I have just downloaded Xampp and while trying to install it i got this error

XAMPP is currently only availably as 32 bit application. Please use a 32 bit compatibility library for your system.

What is this "32 bit compatibility library" and how can i make this to work.

thanks

---

### Post by pixel :-) on 2008-06-22
sudo apt-get install ia32-libs
sudo dpkg --force-architecture -i your_32bit_pakage.deb

---

