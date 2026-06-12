---
title: "how to install kernels from kernel.org"
date: 2006-10-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by xstaticxgpx on 2006-10-05
This may be a dumb question, but, I remember there used to be a thread on how to build/install a kernel from kernel.org. That thread seems to have disappeared and I'm a little shakey to do it without a how-to to follow. Would anyone be willing to post a link or write up a how-to for me? Thanks 8-)

---

### Post by Chickencha on 2006-10-05
You can find a pretty good howto on this [here](http://ubuntuforums.org/showthread.php?t=217657).  That guide isn't for the latest kernel version, but it will still work.  I've verified this myself.

One thing that guide doesn't mention is that if you use EVMS, you should patch the kernel as described [here](http://evms.sourceforge.net/install/kernel.html).  I'm not completely sure who needs that patch and who doesn't, but I know that people with multiple hard drives have had some trouble getting any hard drive besides the one they boot from to work.  Probably best to add the patch just to be on the safe side.

I hope that helps.

---

### Post by xstaticxgpx on 2006-10-05
> **Chickencha said:**
> You can find a pretty good howto on this [here](http://ubuntuforums.org/showthread.php?t=217657).  That guide isn't for the latest kernel version, but it will still work.  I've verified this myself.

One thing that guide doesn't mention is that if you use EVMS, you should patch the kernel as described [here](http://evms.sourceforge.net/install/kernel.html).  I'm not completely sure who needs that patch and who doesn't, but I know that people with multiple hard drives have had some trouble getting any hard drive besides the one they boot from to work.  Probably best to add the patch just to be on the safe side.

I hope that helps.

it does, thanks :)

---

### Post by xstaticxgpx on 2006-10-05
also, is there anyway for me to re-add the ubuntu loading screen? or make it so i see some sort of loading text/graphic... i hate just having a black screen.

---

### Post by kuja on 2006-10-05
Is it "just a black screen", with no text? It should at least spit text at you... anyhow, I'm sure you'd have to pull teeth to get it to work with usplash (maybe not, oh well)

Anyhow, there is a kernelhowto in the ubuntu wiki. I liked the old version of it better, but I suppose it would work for you.

---

### Post by xstaticxgpx on 2006-10-05
after i see the "kernel loading" i just get a black screen where the ubuntu boot screen used to be, no text or anything... ill check out the wiki and post back

---

### Post by Chickencha on 2006-10-06
I'm not sure how to get the graphical loading screen because I'm too lazy to figure it out, but to see the text, you'll need to follow this procedure:

```

sudo nano /boot/grub/menu.lst

```

You should find a line that looks something like this (this is mine):

```

title		Ubuntu, kernel 2.6.18
root		(hd0,0)
**kernel		/vmlinuz-2.6.18 root=/dev/sda2 ro quiet splash**
initrd		/initrd.img-2.6.18
savedefault
boot

```

Remove the word "splash" from the line in bold so that it reads

```

kernel		/vmlinuz-2.6.18 root=/dev/sda2 ro quiet

```

I believe that should do it.

---

### Post by xstaticxgpx on 2006-10-06
that did it, thanks!

---

