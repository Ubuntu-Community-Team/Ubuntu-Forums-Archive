---
title: "Firefox turns black"
date: 2009-08-12
forum: x86 64-bit Users
---

### Post by Jazmac on 2009-08-12
I'm sure it's not just me but I can't find it doing a search. 

I can't figure out why Firefox 3.5 turns black on some sections when I'm browsing.  For example, if I am on a site with flash, sections of the browser window go black and clicking in that area wakes it up.  Or, I might get a black line through the browser page and if I scroll through it, it disappears. 

I have a pretty hefty processor AMD 5000+ and 8 gigs of ram so my guess is a software issue but I don't know what to look at.  I'm running Jaunty.  None of this is the case when I'm running Windows 7 (dual-boot but I don't run it much)

I'm a 4 month old Ubuntu toddler yet. 

Any ideas?

-Jazmac

---

### Post by punkybouy on 2009-08-12
It sounds like a video driver issue.  What kind of video card do have?

---

### Post by Jazmac on 2009-08-12
> **punkybouy said:**
> It sounds like a video driver issue.  What kind of video card do have?

NVidia.  I'm using the recommended version 180 for accelerated graphics.  No good?

-Mrvee

---

### Post by Raffles10 on 2009-08-12
Compiz turns applications black temporarily when they stop responding. You can alter the time it takes compiz to detect non responding applications:

open the gconf-editor, then go to:

apps > compiz > general > allscreens > options /ping_delay , and change the value to something higher. (eg: 6000, 7000, 8000 etc)

To see the range in which you have to work, Highlight ping_delay and look in the description window at the bottom. 10000 works well for me.

This won't stop firefox freezing which it tends to do, especially on flash sites, but it will stop it turning black quite so quickly.

---

### Post by Jazmac on 2009-08-12
> **Raffles10 said:**
> Compiz turns applications black temporarily when they stop responding. You can alter the time it takes compiz to detect non responding applications:

open the gconf-editor, then go to:

apps > compiz > general > allscreens > options /ping_delay , and change the value to something higher. (eg: 6000, 7000, 8000 etc)

To see the range in which you have to work, Highlight ping_delay and look in the description window at the bottom. 10000 works well for me.

This won't stop firefox freezing which it tends to do, especially on flash sites, but it will stop it turning black quite so quickly.

Good idea.  I am running Compiz as a matter of fact.  Cool little piece of code.  Sets it apart from Windows and Mac OSX.

I'll check that out and update the thread.  

Thanks.

Edit: That seems to have resolved it.  I bounced around on a few other websites to be sure and the 10000 setting worked for me as well.  I'm good.  Thanks for the assist Raffles.  That did it.

How do I mark the thread Resolved?

-Jazmac

---

