---
title: "[SOLVED] Can I decrypt files without the original encryption key file?"
date: 2008-11-25
forum: x86 64-bit Users
---

### Post by Linux user 66 on 2008-11-25
I've lost the encryption key file I used to encrypt 4 text files. When I reinstalled my system, I forgot to also backup the key file.

I remember the password I used to encrypt the files, but the system won't decrypt them without the key file.

Is it possible to decrypt these files without the original encryption key file?

---

### Post by insane_alien on 2008-11-25
if you have a supercomputer and a few million years then yes.

---

### Post by meldroc on 2008-11-25
What program did you use to encrypt the files?

---

### Post by Linux user 66 on 2008-11-27
> **meldroc said:**
> What program did you use to encrypt the files?

The standard one in Ubuntu, *GnuPG*, with *seahorse* as front end. 

I imagined that it could just maybe be possible to decrypt these files since I still remember the password, but I guess the files were too tied with the encryption key file that I'm missing.

---

### Post by meldroc on 2008-11-30
I regret to say that if you don't have the secret key in GnuPG to decrypt your files, you're boned.

GnuPG is very strong encryption - the kind that likely thwarts three-letter-agencies.  If you don't have the key, brute-forcing the encryption will take more computing power than is available on this planet.  All the password does is decrypt the key, which is itself encrypted to ensure that only authorized people can use it.  If you're missing the key itself, the password will not help you.

I wish I had better news for you. :(

---

### Post by Linux user 66 on 2008-12-01
> **meldroc said:**
> I regret to say that if you don't have the secret key in GnuPG to decrypt your files, you're boned.

GnuPG is very strong encryption - the kind that likely thwarts three-letter-agencies.  If you don't have the key, brute-forcing the encryption will take more computing power than is available on this planet.  All the password does is decrypt the key, which is itself encrypted to ensure that only authorized people can use it.  If you're missing the key itself, the password will not help you.

I wish I had better news for you. :(

That's what I was afraid of. Never mind.

Thanks anyway.

---

### Post by albandy on 2008-12-01
There's no way to restore the crypted files, but perhaps you can recover the original ones if are stored in an unused part of the disk.

read this:
[http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)

---

### Post by Linux user 66 on 2008-12-01
> **albandy said:**
> There's no way to restore the crypted files, but perhaps you can recover the original ones if are stored in an unused part of the disk.

read this:
[http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)

Thanks for the tip!

---

