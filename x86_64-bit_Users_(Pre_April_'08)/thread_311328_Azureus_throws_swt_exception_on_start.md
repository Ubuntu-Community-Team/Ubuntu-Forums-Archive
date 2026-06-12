---
title: "Azureus throws swt exception on start"
date: 2006-12-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by istrebitjel on 2006-12-02
Hi,

I installed azureus and it's dependencies (swt-3.2) via Synaptic on my fresh Ubuntu 6.10 64bit installation.
However Azureus fails to start with the following exception:
```
Exception in thread "main" java.lang.UnsatisfiedLinkError: memmove
   at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:67)
   at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
   at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:80)
   at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:61)
   at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:110)
   at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
   at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)

```

**But I got it working**, after I reverted back to swt-3.1 (which also removed azureus) and installed azureus from sf.net.

I'm starting this thread for two reasons:
- other people with this problem find help :)
- someone can teach me how I can file a bug on this :-k 

I went to [https://bugs.launchpad.net/malone/](https://bugs.launchpad.net/malone/) but azureus doesn't accept bugs and swt doesn't exist... what should I do?

Thanks,
Istrebitjel

---

### Post by duhblow7 on 2006-12-02
Ditto on the error above.

---

### Post by thanil on 2006-12-04
Same problem over here! Any suggestions?

---

### Post by istrebitjel on 2006-12-04
Sorry, I wasn't very clear above - I did this to get it working: 
"I reverted back to swt-3.1 (which also removed azureus) and installed azureus from sf.net."

Or you can also try [KTorrent]("http://ktorrent.org/"), which can be easily installed via [Automatix2]("http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38")

---

### Post by jrjazzman on 2006-12-05
I'm having same problem on 32-bit edgy.  Anyone know what's causing this?

---

### Post by mkw87 on 2006-12-15
I am having the same problem on 64-bit Edgy.  Any one figure anything out yet?

---

### Post by chaos215bar2 on 2006-12-22
I know this is a bit repetitive, but same here on Edgy 64.

---

### Post by Chubtoad on 2006-12-24
I'm having the same problem here on Edgy32bit  

istrebitjel , can you please post the commands you used to revert to the old swt version? Thank you,

---

### Post by Ubangi on 2006-12-29
Same here on edgy 64bit....

---

### Post by kesman on 2006-12-29
And here too, edgy 64-bit and azureus from the repositories...

There's quite a lot of discussion about this all over the forum, and the only solution to get azureus working, is NOT to install it from apt but directly from sf and then run it from the extracted directory, wherever that might be...

---

### Post by tribut on 2007-01-02
still no solution for this?
i'm seeing the same error (UnsatisfiedLinkError: memmove) and installing from third-party websites can't be the only way to resolve this...

tia,
felix

---

### Post by bronson on 2007-01-05
There's a simple answer in another thread...  I'm about to try it out.

[http://www.ubuntuforums.org/showpost.php?p=1939871&postcount=4](http://www.ubuntuforums.org/showpost.php?p=1939871&postcount=4)

---

### Post by bronson on 2007-01-05
Worked like a champ.  Let's hope Ubuntu throws a new set of packages in the amd64 Edgy updates.  Until then, I just need to remember to start Azureus with "~/Azureus/azureus'.

I also notice that I can't drag&drop links to Azureus to start a torrent the way I can on i686.  But clicking on the link and selecting "Open in Azureus" works fine.

---

### Post by bronson on 2007-01-05
Sorry, I didn't see your dislike of installing from "third-party sites."  Erm, I don't think the upstream source would be considered third-party.  It's the origin.  How much more first-party can you get?  :)

Even so, the package in Edgy is flat out broken.  Since installing the upstream version is so easy, I wouldn't hold my breath for anyone to try to debug the Ubuntu packaging...

---

