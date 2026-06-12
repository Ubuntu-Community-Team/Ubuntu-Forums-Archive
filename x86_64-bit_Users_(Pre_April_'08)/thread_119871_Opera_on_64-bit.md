---
title: "Opera on 64-bit?"
date: 2006-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-01-20
I mean the browser, not the one where the fat ladies sing. ;) 

I do have chroot installed, and I run Firefox32 in it and also RealPlayer and Adobe Reader. I used Opera in the past on Windows and want to try the latest version on my Breezy-64 laptop. But when I open Synaptic32 Opera is not listed. Going to opera.com I find a file to download for Ubuntu Breezy32, but the only instructions for what to do with it seem to be instructions for installing Opera on Windows. I'm too new to Linux to know intuitively how to install it.

Are there instructions somewhere? Also, since it is not listed in Synaptic32 (or the regular Synaptic), does that mean there is something bad with Opera? Will it cause my computer to explode?

---

### Post by dabang on 2006-01-25
Just download Opera for Breezy, chroot to 32bit enviroment and type:

```
dpkg -i /path/to/operaXXXXXXX.deb

```
Maybe you have to install motif, as I think to remember opera complaining about that.

---

