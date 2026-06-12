---
title: "Installing ubuntu on a 7200/120?"
date: 2006-03-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by naked on 2006-03-08
I have a *really* old mac that I'd like to put linux on.  Perhaps ubuntu isn't the best choice.  But I did make a PPC install cd and I could get it to boot at all.

Any ideas?  Is there something special I have to do for an Apple to boot from a cd?  Is there a special way to burn the ppc iso?

Thanks

L

---

### Post by jdp on 2006-03-08
First things first, the 7200 is a 601 CPU.  I'm not positive that Ubuntu has 601 support or not.  I know they've got 604, as I've installed on a 7600/132 and an 8500/120.

You're gonna need to do an OldWorld style install.  The 7200 is an OldWorld Mac, in that it uses an actual ROM chip, and not ROM-in-RAM that it loads from the HDD at boot up.  Thus, it's only smart enough to boot MacOS until something like [EMILE](http://emile.sourceforge.net/index.php) gets further developed.  So, you're going to have to do an install like I describe [on Applefritter](http://www.applefritter.com/node/8936).  Be wary that the stock video might not work right off for a GUI.  I still haven't got a GUI running on the stock video on my 7600 or 8500, but it does work with an ATI video card in a Beige G3.

---

### Post by Yimmy on 2006-04-11
So how did you get the kernel copied over to the mac partition to boot into ubuntu?

---

### Post by linear on 2006-04-11
That's covered in the wiki: [OldWorldMacs]("https://wiki.ubuntu.com/Installation/OldWorldMacs").
 
EDIT: Never mind; I see from the other thread that you tried and it didn't work for you.

---

