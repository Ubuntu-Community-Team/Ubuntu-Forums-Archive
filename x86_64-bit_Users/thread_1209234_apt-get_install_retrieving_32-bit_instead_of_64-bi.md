---
title: "apt-get install retrieving 32-bit instead of 64-bit"
date: 2009-07-10
forum: x86 64-bit Users
---

### Post by kfmfe04 on 2009-07-10
Hi,

I need some help configuring apt-get.  I am running Intrepid 64amd and everything was fine until I tried installing gcc-4.2-multilib so I could run some 32-bit programs.

Now, when I run:

sudo apt-get install gdc dsss tango-gdc

I end up with 32-bit ELF binaries rather than 64-bit ELF binaries.
Where/how do I configure apt-get to get 64-bit binaries whenever possible?

I tried scrounging the man pages, but no luck.
Thanks in advance.

---

