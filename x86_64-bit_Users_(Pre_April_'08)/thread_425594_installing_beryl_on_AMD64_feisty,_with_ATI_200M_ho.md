---
title: "installing beryl on AMD64 feisty, with ATI 200M: how-to guide requested"
date: 2007-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by loso on 2007-04-27
I've tried a ton of different how-to guides for installing beryl, and none of them have worked on my laptop.  Once beryl is installed, and I try running it, I get a white screen.  The only thing still visible is the cursor.  I got beryl running on my desktop, so while I might be retarded, I'm not incapable...

It's a Dell inspiron 1501 with an AMD turion 64 X2  processor, and an ATI 200M graphics card.  If anyone has gotten beryl to work on these specs, you'll be my hero.

---

### Post by marsmissionaries on 2007-04-27
i have gotten it to work with the standard how-tos for ATI drivers with XGL. 

my processor is the turion 64 ml-30 just search the forums for a how-to

---

### Post by campbr2 on 2007-04-27
Can you post the how-to that helped you, because I have a Turion64 and ATI 200M but can't get Beryl to work.

---

### Post by samir5y on 2007-04-28
I encounter the same problem. I have a Compaq Presario V2000 with ATI Mobility 200M shared 128 RAM. I have installed the proprietary software which is not supported by UBUNTU.
How do I make Compize work on my laptop?

---

### Post by strumluff on 2007-04-28
> **loso said:**
> I've tried a ton of different how-to guides for installing beryl, and none of them have worked on my laptop.  Once beryl is installed, and I try running it, I get a white screen.  The only thing still visible is the cursor.  I got beryl running on my desktop, so while I might be retarded, I'm not incapable...

It's a Dell inspiron 1501 with an AMD turion 64 X2  processor, and an ATI 200M graphics card.  If anyone has gotten beryl to work on these specs, you'll be my hero.

I also have a turion 64 processor and the ATI Xpress 1100 which is basically the same as the 200M.
The only way to get your card to work is to use the ATI/XGL method which you can do simply by following this howto: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

Now as for the white screen problem, this has been a right pain for me too but currently I am using a workaround by changing the startberyl.sh script to use this:

```
#!/bin/bash
#
# Start beryl-manager within gnome-session
#
if (( `ps -A -o comm | grep -c '^Xgl$'` == "1" )); then
      LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl & beryl-manager
else echo "${0}: Error: beryl-manager not launched. Xgl not running?"
fi
```

instead of this:

```
#!/bin/bash
#
# Start beryl-manager within gnome-session
#
if (( `ps -A -o comm | grep -c '^Xgl$'` == "1" )); then
       DISPLAY=:1 beryl-manager
       DISPLAY=:1 beryl-xgl
else echo "${0}: Error: beryl-manager not launched. Xgl not running?"
fi
```

Also make sure that you downgrade the core to version 0.2.0 as it says in the howto.

Hope it does the trick for you too. Oh yeah one more thing, try changing the rendering path from beryl-manager I find that I get less white panels/windows when using the pixmap option. Copy would give you the least problems but with less performance. Anyway a few more months and then fglrx should support the composite extension so we don't have to use blasted XGL :)

EDIT: Ah I nearly forgot, you must not reload the window manager from beryl-manager otherwise the white screen will be back. If you want to reload then you will need to close beryl and run the LD_PRELOAD line again. Reloading the window decorator is fine though.

---

### Post by loso on 2007-04-29
strumluff, you might just be my hero :)  But I'm not willing to do such a duct-tape job, just to undue it all when beryl's bugs are fixed...  Thanks for all you help though, it brings closure on this issue for me.

---

