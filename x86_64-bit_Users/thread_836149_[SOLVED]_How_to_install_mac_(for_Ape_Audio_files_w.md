---
title: "[SOLVED] How to install mac (for Ape Audio files with shntool) in AMD 64?"
date: 2008-06-21
forum: x86 64-bit Users
---

### Post by Arrgoss on 2008-06-21
Hello,

I'm trying to organize my music files, some of them encoded with ape. I want to split the big ape file with its corresponding cue. To do that, I came across [this post]("http://aidanjm.wordpress.com/2007/02/15/split-lossless-audio-ape-flac-wv-wav-by-cue-file/") that recommends using the shntool. In order to read the ape files, I need to [install mac]("http://aidanjm.wordpress.com/2007/01/26/using-monkeys-audio-ape-files-in-ubuntu/#comment-3070"), but I'm using a 64-bit machine and I cannot do it normally.

I tried to force architecture, but when I attempted to split the file, it didn't work.

Any suggestion or idea? Anyone is having similar problems?

---

### Post by Kilz on 2008-06-21
> **Arrgoss said:**
> Hello,

I'm trying to organize my music files, some of them encoded with ape. I want to split the big ape file with its corresponding cue. To do that, I came across [this post]("http://http://aidanjm.wordpress.com/2007/02/15/split-lossless-audio-ape-flac-wv-wav-by-cue-file/") that recommends using the shntool. In order to read the ape files, I need to [install mac]("http://aidanjm.wordpress.com/2007/01/26/using-monkeys-audio-ape-files-in-ubuntu/#comment-3070"), but I'm using a 64-bit machine and I cannot do it normally.

I tried to force architecture, but when I attempted to split the file, it didn't work.

Any suggestion or idea? Anyone is having similar problems?

You could follow the compile instructions found in the link you provided.

---

### Post by Arrgoss on 2008-06-21
> **Kilz said:**
> You could follow the compile instructions found in the link you provided.

If I'm here is because I didn't manage to do it in AMD 64. If you mean I should try to compile it from the source code, as alos explained in the post I link, it would have been more useful letting me know that that is the way to get the mac installed in my 64-bit architecture, which I still don't know.

Thanks anyway for trying to help in your own way.

---

### Post by max64 on 2008-06-21
You can convert a package from another distro using alien or download this:

[http://rapidshare.com/files/124065336/mac_3.99-3_amd64.deb.html](http://rapidshare.com/files/124065336/mac_3.99-3_amd64.deb.html).

I converted it from a rpm for fedora 64 bit.

Hope it helps.

---

### Post by Arrgoss on 2008-06-21
Installing it from the source code indeed worked. I'm sorry for my previous rant, kilz, but I could not know that is a way to do it.

Max64, I will try that for the next package :)

---

### Post by Kilz on 2008-06-21
> **Arrgoss said:**
> Installing it from the source code indeed worked. I'm sorry for my previous rant, kilz, but I could not know that is a way to do it.


Its ok, we all learn, yes compiling things from source is one way of getting things to work on your system. Source code is platform independent most of the time. I just suggested it because the howto you linked to had very good instructions.

---

### Post by 4ugeistr on 2008-08-16
> **Kilz said:**
> You could follow the compile instructions found in the link you provided.
Wow! it worked!!!!:guitar:
Thanks, U saved the day!

strange, but the mac readme didn't have these
sudo aptitude install build-essential
sudo aptitude install nasm
in installation instruction.

maybe i was bound to know they were needed...

---

