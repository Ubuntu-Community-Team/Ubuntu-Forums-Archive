---
title: "32bit apps"
date: 2009-02-04
forum: x86 64-bit Users
---

### Post by moveright on 2009-02-04
I'm assuming that all 32 bit apps will run on the 64 bit OS just not take advantage of the extra ability?

---

### Post by srobinson09 on 2009-02-04
You would be correct in assuming that!

Yes they do work on a 64bit OS.

---

### Post by moveright on 2009-02-04
> **srobinson09 said:**
> You would be correct in assuming that!

Yes they do work on a 64bit OS.

thanks!  so knowing that, it must also be true that if one has an AMD 64 bit processor, there is no reason why one should not install 64 bit ubuntu correct?

---

### Post by jespdj on 2009-02-04
> **moveright said:**
> thanks!  so knowing that, it must also be true that if one has an AMD 64 bit processor, there is no reason why one should not install 64 bit ubuntu correct?
Indeed. And the same when one has a 64-bit Intel processor; despite the name, the "amd64" version of Ubuntu is NOT only for AMD processors.

Most newer Intel processors (including all Core 2 processors) are 64-bit.

Note that almost all software for Ubuntu is available in a 64-bit native version; it's not like Windows where most software is only available in a 32-bit version.

---

### Post by moveright on 2009-02-04
> **jespdj said:**
> Indeed. And the same when one has a 64-bit Intel processor; despite the name, the "amd64" version of Ubuntu is NOT only for AMD processors.

Most newer Intel processors (including all Core 2 processors) are 64-bit.

Note that almost all software for Ubuntu is available in a 64-bit native version; it's not like Windows where most software is only available in a 32-bit version.
you've been extremely helpful.  thanks!

---

### Post by paulisdead on 2009-02-04
Not exactly.  Any 32bit app you have, can only interact with 32bit libraries, and won't know what the hell to do when confronted with a 64bit lib.  Someone around here had a tool called getlibs that helps fetch the libraries necessary to run a 32bit app, and puts them in /lib32.

It really isn't too bad, these days.  I'm down to just one 32bit app, MyPasswordSafe.  Though, if you're heavily into flash, sticking with 32bit might still be a consideration.  The 64bit alpha of flash is leaps and bounds better than using a wrapper, but it still has it's issues for me.  That's really my only complaint with 64bit now.

---

### Post by stchman on 2009-02-05
> **moveright said:**
> I'm assuming that all 32 bit apps will run on the 64 bit OS just not take advantage of the extra ability?

This is pretty much a non factor as the repos contain both the 32 and 64 bit debs.  Yes, if you download a pre-compiled binary you can unpack it and it will run.

I find that I so rarely have to venture outside Ubuntu's repos.

---

