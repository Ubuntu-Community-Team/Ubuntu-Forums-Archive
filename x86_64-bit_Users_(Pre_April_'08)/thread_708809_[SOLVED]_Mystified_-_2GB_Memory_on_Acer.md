---
title: "[SOLVED] Mystified - 2GB Memory on Acer"
date: 2008-02-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by dday376 on 2008-02-26
I have an Acer Aspire T180 (AST180-UA350B).  
- AMD64 3500+
- 512 MB RAM pre-installed, now at 1 GB
- Kubuntu 7.10 x86 64-bit

Got the itch, ordered 2 1 GB sticks from Crucial - Ballistix.  I know they're right, cause when I install either one or the other, the system comes up no problem.  However, when I install both, the system slows to a crawl around starting Firestarter, eventually stops showing failure at starting kernel event manager.

Brought it up using only 1GB and don't see anything in the logs that help.

Anyone have any ideas?  Since it seems to work with 1GB, my assumption is that something in Kubuntu?

**Updated**:  So this is weird.  According to [crucial]("http://www.crucial.com/store/listparts.aspx?model=Aspire%20T180&pl=Acer&cat=RAM"), I **must** install the memory in pairs.  What gives?  When I install the pair, Kubutnu dies on me?

---

### Post by dday376 on 2008-02-26
Okay - solved my own problem.  Might be too rare, but here's what happened.

I booted in maint mode, and watched as the messages slowed to a crawl around the networking services.  Clue - networking hardware problem?

I was originally using ndiswrapper for a Broadcom 4306 card.
I removed ndiswrapper and installed the restricted driver.
I installed the second dimm, bringing it up to 2GB.

Everything works.

---

### Post by Jouke74 on 2008-02-27
Now for the real question: how can going from 1 to 2 GB disrupt the Ndiswrapper so much? Must be something wrong with Ndiswrapper <> kernel memory addressing then? Too weird. Did you try option 3 from your Grub menu also, memory testing?

---

### Post by patrickfromspain on 2008-02-27
If I remember correctly, there was once such a bug: broadcom with ndiswrapper not liking 2gb or RAM. To solve it you had to recompile the kernel and then recompile ndiswrapper.

Anyway, google for it, as I'm not completely sure.

---

### Post by Yellow Pasque on 2008-02-27
You should probably mark this as [SOLVED] (under the Thread Tools menu)

---

