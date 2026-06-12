---
title: "Problems with 32 versions of Firefox, Thunderbird, and Sunbird"
date: 2007-06-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Johnny K on 2007-06-29
I'm running 32 versions of Firefox, Thunderbird, and Sunbird. I installed Firefox32 with Kilz's install script. I'm don't remember how I installed Thunderbird. I installed Sunbird using [this tutorial]("http://ubuntuforums.org/showthread.php?t=278206").

Anyway, the point is that whenever I try to launch any of these applications from Terminal, I get this error (the only difference between the error messages is the name of the application and the number after "-bin:"):
```
(firefox-bin:10527): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Gtk-Message: Failed to load module "gail": libart_lgpl_2.so.2: cannot open shared object file: No such file or directory

```

libart_lgpl_2.so.2 exists in /usr/lib and /usr/lib32, but not in /lib or /lib32. What's causing this error?

---

### Post by Kilz on 2007-06-29
> **Johnny K said:**
> I'm running 32 versions of Firefox, Thunderbird, and Sunbird. I installed Firefox32 with Kilz's install script. I'm don't remember how I installed Thunderbird. I installed Sunbird using [this tutorial]("http://ubuntuforums.org/showthread.php?t=278206").

Anyway, the point is that whenever I try to launch any of these applications from Terminal, I get this error (the only difference between the error messages is the name of the application and the number after "-bin:"):
```
(firefox-bin:10527): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Gtk-Message: Failed to load module "gail": libart_lgpl_2.so.2: cannot open shared object file: No such file or directory

```

libart_lgpl_2.so.2 exists in /usr/lib and /usr/lib32, but not in /lib or /lib32. What's causing this error?

My guess would be that the libart_lgpl_2.so.2 in the /usr/lib32 is a 64bit library copied into place. You need the 32bit version of that file for the 32bit applications to use it. But a good question is, is everything working for you? If so ignore the error.

---

### Post by Johnny K on 2007-06-30
> **Kilz said:**
> My guess would be that the libart_lgpl_2.so.2 in the /usr/lib32 is a 64bit library copied into place. You need the 32bit version of that file for the 32bit applications to use it. But a good question is, is everything working for you? If so ignore the error.
Thanks for the reply :)

Not everything is working. Thunderbird freezes whenever I get a new email, and Sunbird immediately closes and brings up the Netscape feedback form whenever I try to launch it.

(I'm pretty sure) Thunderbird always froze after a new email, but Sunbird used to work perfectly. So I tried reinstalling Sunbird, but that didn't change anything.

Where can I find a 32 bit version of libart_lgpl_2.so.2 (and libart_lgpl_2.so.2.3.17, the file it links to)? I've tried every kind of synaptic search and did a bit of googling, but haven't found anything.

TIA :p

---

### Post by Kilz on 2007-06-30
> **Johnny K said:**
> Thanks for the reply :)

Not everything is working. Thunderbird freezes whenever I get a new email, and Sunbird immediately closes and brings up the Netscape feedback form whenever I try to launch it.

(I'm pretty sure) Thunderbird always froze after a new email, but Sunbird used to work perfectly. So I tried reinstalling Sunbird, but that didn't change anything.

Where can I find a 32 bit version of libart_lgpl_2.so.2 (and libart_lgpl_2.so.2.3.17, the file it links to)? I've tried every kind of synaptic search and did a bit of googling, but haven't found anything.

TIA :p

[You can get the package that contains them here]("http://packages.ubuntu.com/feisty/libs/libart-2.0-2") . Download the i386 package. Then use ```
sudo dpkg -x libart-2.0-2_2.3.17-1_i386.deb ~/Desktop
``` to extract the files
It will extract the internal file structure in the deb. Then copy the files in /usr/lib in that extracted tree to /usr/lib32.

---

### Post by Johnny K on 2007-06-30
That seemed to fix the libart_lgpl_2.so.2 problem, but Sunbird still won't launch and I now get this message:
```
(sunbird-bin:7942): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
GTK Accessibility Module initialized
*** Calendar schema version is: 5
Starting calendar alarm service
observer added
Segmentation fault (core dumped)

```

Which is the same as the old message, but without the warning about libart_lgpl_2.so.2. Firefox32 and Thunderbird are giving the same message, less lines 4-7. I have Sunbird and Thunderbird installed in /opt if that makes a difference.

---

