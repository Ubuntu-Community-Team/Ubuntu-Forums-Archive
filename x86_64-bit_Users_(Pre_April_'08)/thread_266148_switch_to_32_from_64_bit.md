---
title: "switch to 32 from 64 bit?"
date: 2006-09-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Desabrir on 2006-09-26
So I want to sitch from 64 bit to 32 bit because of lack programs etc... can I just slap the 32 bit ISO in the drive and let it do a windows type "repair" to revert it to 32 bit?

h4n5

---

### Post by amohanty on 2006-09-26
Before I go on... why exactly do you want to do it?

Short answer: _no_

TO do so without reinstalling you would have to replace a whole bunch of stuff, starting of with the:
32 bit kernel
32 bit glibc
32 bit almost everything...

So depending on the answer to the question above, you may be better of with a complete reinstall, or you could possibly get by with the bare minimum of 32 bit libraries.

Also look into running 32 bit programs in chroot mode.

HTH
AM

---

### Post by incubus on 2006-09-27
desabrir,

As amohanty said, that procedure would be so complicated that it's probably not worth it. Think of converting Windows 64bit to 32bit; I don't think that's even possible. So a clean, fresh install is the way to go.

But again agreeing with amohanty, do give it some thought before taking that route. With chroot you can have the best of both worlds. Let us know if we can help you with any problem there.

best,
incubus

---

### Post by Kilz on 2006-09-27
> **Desabrir said:**
> So I want to sitch from 64 bit to 32 bit because of lack programs etc... can I just slap the 32 bit ISO in the drive and let it do a windows type "repair" to revert it to 32 bit?

h4n5

What lack of programs?

---

