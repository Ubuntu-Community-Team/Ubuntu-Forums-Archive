---
title: "Switching from edgy-x86 to edgy-amd64?"
date: 2006-10-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by enigma_0Z on 2006-10-29
I've got a pretty happy setup with edgy, and using the x86 (32 bit) programs, but I've got a 64-bit system and have gotten up the never to try changing over. What would the most painless way of doing this be?

Are there any special considerations that I should take into account before I upgrade? (For instance, firefox, ndiswrappers, wine, synaptics touchpad)

---

### Post by The Warlock on 2006-10-29
> **enigma_0Z said:**
> I've got a pretty happy setup with edgy, and using the x86 (32 bit) programs, but I've got a 64-bit system and have gotten up the never to try changing over. What would the most painless way of doing this be?

Are there any special considerations that I should take into account before I upgrade? (For instance, firefox, ndiswrappers, wine, synaptics touchpad)

You're going to have to reinstall from scratch.

---

### Post by chebe on 2006-10-29
For a start, if your /home is not in a dedicated partition, you should back it up. Then take a look at all the applications you are using (espacially 32bits only ones) like wine, opera, ... and have a look on the forum for how to install them.
Reinstall EVERYTHING from scratch, restore your /home (again if it's not in a dedicated partition) install the 32bits apps following the howtos on the forum. and you're in !

---

### Post by enigma_0Z on 2006-10-29
What apps do I have to install in a chroot? I don't wanna deal with a chroot if I don't have to.

---

### Post by kuja on 2006-10-29
You shouldn't need to deal with a chroot at all, of course, you could if you wanted to.

---

### Post by incubus on 2006-10-30
> **enigma_0Z said:**
> I've got a pretty happy setup with edgy, and using the x86 (32 bit) programs, but I've got a 64-bit system and have gotten up the never to try changing over. What would the most painless way of doing this be?

Are there any special considerations that I should take into account before I upgrade? (For instance, firefox, ndiswrappers, wine, synaptics touchpad)

Hmm, also make sure your wireless card has got a 64bit driver.  That's not my case.  Because (stupid) Netgear refuses to make 64bit drivers (even for windows), I can't use it in a 64bit system; this is at the kernel level.

incubus

---

### Post by UncleB on 2006-10-30
So does this mean you can run the i386 build on an AMD64 system?

---

### Post by enigma_0Z on 2006-10-30
The final questions:

Could I just remove everything but /home and then use my existing partitioning setup? As I understand it that should work...

Should I just blow everything away (backup /home to a DVD or something) and set it up with LVM?

---

### Post by kuja on 2006-10-30
You're using the alternate cd right? You should be able to do that, just be sure that it's not formatting the partition. Backups are nice to have either way. Alternatively, you could back up /home, do the install and give home a separate partition, to prepare for future upgrades.

---

### Post by kuja on 2006-10-30
> **UncleB said:**
> So does this mean you can run the i386 build on an AMD64 system?
Yes, that works fine in most cases.

---

### Post by reiki on 2006-10-30
I found it interesting that the edgy i386 kernel didn't have support for dual cores while the edgy generic kernel does. I mean... not all that unexpected regarding the i386 kernel NOT haveing smp support, but interesting that the generic kernel DOES have smp support.

---

### Post by kuja on 2006-10-31
Edgy has made changes with regards to the kernels in general, both in the x86 and x86_64 versions (not sure aobut PPC or Sparc). 

In Edgy, there is only one 64-bit kernel, the generic.
I'm not sure about the 32-bit though. Seeing as the decision seems to be linked to lower maintenance, there should be as few kernels as possible. I would assume that in Edgy 32-bit there would be only one kernel as well, the generic. I'm not sure what installing the 386 would do, but if you tried to install, say, the K8 kernel in the 64-bit, it's just a dummy package that installs the generic. I would think it would be the same thing to try to install i386 or i686. Am I making any sense? If not, maybe I should try posting this at some time when I'm fully conscious.

---

### Post by RAOF on 2006-10-31
Actually, the -386 kernel **is** different to the -generic one.  There are still some drivers that aren't multi-processor safe, so the -386 kernel is built without SMP support.  It's there for ultra-maximum-compatibility, whereas the -generic one should work, and has all the goodies like SMP turned on.

---

### Post by kuja on 2006-10-31
> **RAOF said:**
> Actually, the -386 kernel **is** different to the -generic one.  There are still some drivers that aren't multi-processor safe, so the -386 kernel is built without SMP support.  It's there for ultra-maximum-compatibility, whereas the -generic one should work, and has all the goodies like SMP turned on.

Hmm, I suppose that makes some sense. Granted, at that point I'd be compiling my own kernel anyway ;)

---

### Post by UncleB on 2006-11-03
Thanks. I'll try that. The Live64 CD just hung a little way in.

---

