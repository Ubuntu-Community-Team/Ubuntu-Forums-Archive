---
title: "64-bit firefox?"
date: 2007-04-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by boogachamp on 2007-04-23
Hey guys,

I just installed my new 64 bit Kubuntu OS and am looking forward to setting up all my apps and learning along the way.  Do most people use a 32 or 64 bit version of firefox?  I imagine you can only get a 654bit version by compiling it yourself?  I know there are also ways to get around using flash ..... is this true if you do you a 64bit veriosn of firefox?

Let me know if this does not even make sense :P


-boogs

---

### Post by Tanker Bob on 2007-04-23
> **boogachamp said:**
> Hey guys,

I just installed my new 64 bit Kubuntu OS and am looking forward to setting up all my apps and learning along the way.  Do most people use a 32 or 64 bit version of firefox?  I imagine you can only get a 654bit version by compiling it yourself?  I know there are also ways to get around using flash ..... is this true if you do you a 64bit veriosn of firefox?

Let me know if this does not even make sense :P


-boogs
I'm running 64-bit Firefox exclusively.  Flash 9 (via HOWTO here in the forum), Java support (from repository), and all necessary multimedia plugins (xine and vlc from repository) all work fine.  I hear that some extensions do not work in 64-bit, but all 40 or so of mine work fine.

Others run 32-bit Firefox using Kilz' excellent tutorial in his signature.  I guess more extension work there.

I'm very happy with 64-bit Firefox.  YMMV, but I doubt it.

---

### Post by Kilz on 2007-04-23
> **Tanker Bob said:**
> I'm running 64-bit Firefox exclusively.  Flash 9 (via HOWTO here in the forum), Java support (from repository), and all necessary multimedia plugins (xine and vlc from repository) all work fine.  I hear that some extensions do not work in 64-bit, but all 40 or so of mine work fine.

Others run 32-bit Firefox using Kilz' excellent tutorial in his signature.  I guess more extension work there.

I'm very happy with 64-bit Firefox.  YMMV, but I doubt it.

Where did you get a java plugin that works in the 64bit browser?

---

### Post by jamesford on 2007-04-23
id be interested in knowing about the java too

---

### Post by illpig on 2007-04-23
same here!

---

### Post by boogachamp on 2007-04-23
woohoo, I sparked interest....or something!

I wish I was better at linuxing :P

---

### Post by Kilz on 2007-04-23
> **boogachamp said:**
> woohoo, I sparked interest....or something!

I wish I was better at linuxing :P

The reason is , that as far as I know. There is no working 64bit java plugin and nspluginwrapper dosnt support java.

---

### Post by JAPrufrock on 2007-04-23
I use 32bit FF using Kilz's howto for the plugins (Java, MPlayer, Flash).  I recently installed 64 bit Feisty, and it was much easier than the install I did a few months ago with Dapper.

---

### Post by Tanker Bob on 2007-04-23
> **Kilz said:**
> Where did you get a java plugin that works in the 64bit browser?
I found the same Blackdown Java 2 runtime system and mozilla plugin in Feisty x86-64 repositories that I used in i386 Edgy:
```

sudo aptitude install j2re1.4-mozilla-plugin j2re1.4
```

Works like a champ--Java in 64-bit Firefox, no workarounds required.

---

### Post by boogachamp on 2007-04-23
So did you compile firefox on your own to get a 64 bit version.  I would like to give it a try and am not sure where to start.

---

### Post by Tanker Bob on 2007-04-23
Nope, the 64-bit Firefox version is in the Feisty AMD64 repository.

---

### Post by jamesford on 2007-04-23
tanker bob, works!
thank you

---

