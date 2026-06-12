---
title: "Copying over dlls from windows installation for personal use?"
date: 2008-10-21
forum: Wine
---

### Post by MaxIBoy on 2008-10-21
As soon as I get it recovered, I'll have a spare XP install on a hard drive that I won't ever need again. I was just wondering if it's legal to copy over the as-yet unimplemented DLLs from XP into the WINE directories for personal use. If so, how do I find out which DLLs a program needs in order to work?

---

### Post by CarpKing on 2008-10-22
As far as I know this is completely legal.  You already paid for the use of the files, so you're in the clear.  I'm no lawyer, but you're probably more likely to get in trouble for using Wine itself than for popping a file from a legal and unused copy of Windows into your Wine installation.  And I've not heard anyone seriously suggest that Wine is illegal.

---

### Post by YokoZar on 2008-10-22
It's legal.

It's not that helpful in many cases, though.  Only do it if you see advice telling you to use a "native" version of a particular DLL -- then make sure you set winecfg to use that DLL native as well.

This is a good way to find bugs in Wine, by the way - if it works on native but not with Wine's built-in replacement, then it's by definition a bug.

---

### Post by MaxIBoy on 2008-10-23
Looking forward to getting Paintshop Pro 6 to work!

How do I find out which DLLs it's crashing on?

---

