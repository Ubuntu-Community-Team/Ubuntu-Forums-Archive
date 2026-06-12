---
title: "should I even bother?"
date: 2006-02-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by jesusshaves on 2006-02-20
My friend introduced me to Ubuntu linux. He gave me the install cd and i went from there. Before i knew the difference, i didn't know that there was different a different version for AMD 64 processors. Everything seems to be working with the exception of the sound. so my question is. is it worth it to reinstall with th AMD version? Also, could my lack of sound problem be caused by this, or somthing simpler?

---

### Post by abhaysahai on 2006-02-20
you mean to say that Ubuntu for x86 ( eg AMD Athlon) works on your AMD 64 system ??  More amazing is that kernel for x86 is working on AMD 64.
I do not have a 64 bit system, but can someone tell if this is possible. 
Will AMD 64 not give a kernel panic when trying to run a x86 ( actually i386 default with Ubuntu) kernel ?? 


Abhay

---

### Post by MaX on 2006-02-20
[QUOTE=abhaysahai]you mean to say that Ubuntu for x86 ( eg AMD Athlon) works on your AMD 64 system ??  More amazing is that kernel for x86 is working on AMD 64.
I do not have a 64 bit system, but can someone tell if this is possible. 
Will AMD 64 not give a kernel panic when trying to run a x86 ( actually i386 default with Ubuntu) kernel ?? 


Abhay[/QUOTE]

No... AMD64 happily runs 32-bit code, thus you can run i386 compiled software on it. (Although you need to boot into a i386 kernel before doing it)
I'd recommend running 32-bit ubuntu now if you want flash and the latest applications since 64-bit hasn't got these yet.

---

### Post by MighMoS on 2006-02-20
AMD64 processors are completly capable of running 32 bit code without modification, it just wont take advantage of the increased number of registers, and their increased size.  

Its like putting liter of soda into a two liter bottle.  It works, but the rest of the bottle goes to waste.  Simply buying a bigger bottle doesn't do anything special if you're not putting more soda into it.  Sorry, I'm not too great with analogies.

Anyway, in regards to upgrading to the AMD64 CD, its up to you.  Some programs will run faster, on some you wont notice a difference.  The one drawback is that 64-bit code and 32-bit are not interchangable, so for some things that companies release only finished products for, like Flash, wont really work without some effort.

Long story short:  if you're happy the way it is, then you have no reason to change.

---

### Post by abhaysahai on 2006-02-21
[QUOTE=MaX]No... AMD64 happily runs 32-bit code, thus you can run i386 compiled software on it. (Although you need to boot into a i386 kernel before doing it)
I'd recommend running 32-bit ubuntu now if you want flash and the latest applications since 64-bit hasn't got these yet.[/QUOTE]
Thanks for the clarification. 
Well is this AMD specific or we can even run 32 bit code on Intel 64 bit processors ?

---

### Post by MighMoS on 2006-02-21
Intel is a little weirder.  Intel originally came out with ia64 chips, which could **only** run 64-bit code -- everything had to be recompiled.  Needless to say these didn't do too well.  I'm assuming they've mostly ditched that design and gone with something ironically now called AMD64 compatible, but I'm not exactly sure what chips they have.

---

### Post by MaX on 2006-02-22
[QUOTE=MighMoS]...  Sorry, I'm not too great with analogies.
[/QUOTE]
I thought it was great :)

---

### Post by Chemroydal Tissue on 2006-02-23
Your sound problem is most likely just the default setting. Type "alsamixer" (no ""s) in a terminal, and turn off the mutes on what your're going to use. If that doesn't work, post your specs and any error messages.

---

