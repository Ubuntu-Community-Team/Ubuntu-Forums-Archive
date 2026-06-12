---
title: "Program config files between 32 and 64"
date: 2008-05-13
forum: x86 64-bit Users
---

### Post by Sam Lars on 2008-05-13
I'm looking to switch to 64 bit, and I was wondering...
My files are all okay from 32 to 64, right? (ogg, txt, documents, etc., even weird ones like devede)
What about program settings in all of the .program folders?  Would it be a bad idea to share a home partition between 32 and 64 bit versions of Ubuntu?

---

### Post by Kilz on 2008-05-13
> **Sam Lars said:**
> I'm looking to switch to 64 bit, and I was wondering...
My files are all okay from 32 to 64, right? (ogg, txt, documents, etc., even weird ones like devede)
What about program settings in all of the .program folders?  Would it be a bad idea to share a home partition between 32 and 64 bit versions of Ubuntu?

Yes the setting folders in your home folder should be ok to keep. File formats will still be the same.

---

### Post by rplantz on 2008-05-13
> **Kilz said:**
> Yes the setting folders in your home folder should be ok to keep. File formats will still be the same.

A C long int compiled in 32-bit mode is 32 bits and compiled in 64-bit mode is 64 bits. From your answer, can we conclude that developers are careful to account for this? (ints are 32 bits and long long ints are 64 bits with both compiles.)

I apologize if my question is too far off topic for this thread, but your answer made me think of it.

---

### Post by Kilz on 2008-05-13
> **rplantz said:**
> A C long int compiled in 32-bit mode is 32 bits and compiled in 64-bit mode is 64 bits. From your answer, can we conclude that developers are careful to account for this? (ints are 32 bits and long long ints are 64 bits with both compiles.)

I apologize if my question is too far off topic for this thread, but your answer made me think of it.

This thread asked a question about setting's files and media\document files.
The setting files in your home folder are text files. Not compiled binaries. Its long been known that you can pretty much take a home partition from a 32bit install and use it for a 64bit install. 
Second, documents are not 32bit or 64bit. A .odt file written on a 64bit computer can be opened, read , and edited on a 32bit computer and vice versa. A mp3 file is an mp3 file. 
Applications - 32bit applications will run on 64bit, but you will have to manually install them (and every one of them has a howto/script avilable). But, and this is important to remember the amount of 32bit application the normal user **may want** to install is in the 5-10 range. **The number of applications they need in the normal Ubuntu install that are 32bit are a whopping [COLOR="Red"]0[/COLOR].**

---

