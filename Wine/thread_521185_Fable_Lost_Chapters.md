---
title: "Fable: Lost Chapters"
date: 2007-08-09
forum: Wine
---

### Post by Nexus... on 2007-08-09
Hey I just picked up a copy of Fable: Lost Chapters it works fine on my Windows partition but whenever I try to install it on Ubuntu through wine and I think it crashes before the CD key prompt....is there anyway I could get it working?

---

### Post by hikaricore on 2007-08-09
Well I checked the WINE Application Database and it does look like Fable will run under WINE.

You may want to check here: [http://appdb.winehq.org/appview.php?iVersionId=3827](http://appdb.winehq.org/appview.php?iVersionId=3827)

For more information on what works and what doesn't.
I didn't read much but there could be something on there to help ya.

---

### Post by iota on 2007-08-10
Actually, apparently it won't, on mine it gets stuck at the select installation type screen.

It requests the dll msgpid.dll

I tried installing it, it now it says "failed to find dll function: mgspid.getpidx"

I'm guessing this problem only occurs with people who have the dvd version? I've tried it with every version of wine between 0.9.42 and 0.9.37 but no luck so far.

---

### Post by Nexus... on 2007-08-10
Yeah that's the bit it stops at with me, I have the DVD version aswell, it's when I click next that it stops.

---

### Post by iota on 2007-08-10
Yeah, it's really starting to get on my nerves now. I tried installing it with a program called playonlinux but that doesn't work either. I think that expects you to have the cd version too.

I think I might just have to use an old ide drive and stick a copy of windows on there to play this one. The games a little old, and not very popular in linux from what I can see on the wine appdb page, so I wouldn't hold my breath for a fix.

I hope you fix your problem, but if you don't want to resort to windows for this one I'd suggest returning it to the store and trying to get a cd copy.

---

### Post by Nexus... on 2007-08-10
I have Windows with Fable installed. Just a quick one does Serious Sam 2 work?

---

### Post by iota on 2007-08-10
[http://appdb.winehq.org/appview.php?iVersionId=7277](http://appdb.winehq.org/appview.php?iVersionId=7277)

It looks like serious Sam is a little buggy, especially the installer (again). But the guy managed to install it under windows then move it across.

---

### Post by Nexus... on 2007-08-11
That's what I managed to do but now it wants Vertex Shading :(

---

### Post by Mogurijin on 2007-08-17
I got Fable to run, save for some graphical hiccups, by having it installed in Windows then copying all of the files. Plus you'll need to dig through your Windows registry to find some stuff to copy to your Wine registry.

HKEY_LOCAL_MACHINE\Software\Microsoft\Microsoft Games\ Fable

HKEY_CLASSES_ROOT\CLSID\{25E609E4-B259-11CF-BFC7-444553540000}

HKEY_CLASSES_ROOT\CLSID\{A65B8071-3BFE-4213-9A5B-491DA4461CA7}

I hope that helps. At least to get you started ;)

---

### Post by Mogurijin on 2007-08-26
For those of you having problems with the mgspid.dll, copy the one from the fable cd into your system32 folder of the .wine folder.  Now the problem I am having with the installer is it does not want to accept my key.

---

### Post by Mogurijin on 2007-08-26
Ok, I can now enter my product key.  I had to copy the pidgen.dll to my system32 folder (found the dll on the cd again).  My new problem comes when I switch disks.  Shortly after disk 2 starts i get the following error message:

Error: -1627 ERROR_FUNCTION_FAILED

Now I wish I had the DVD version :P

---

### Post by iota on 2007-08-26
Meh I have the dvd version, trust me, doesn't work either :P

Some people got it working by copying it across, others say the installer is working fine, to be honest though the appdb seems to provide conflicts between test data and user commentary.

Some users say they experience complete functionality under wine with the latest ubuntu, personally I do not. Nor, judging by the comments, do others. Just wish I could figure out why, maybe some dll that has been stuck in system32 from other games they've installed?

---

### Post by nymlord on 2008-03-11
i tried everything, copying all dll. files into system32 still doesnt work, copied the cd to my computer and again didnt work so i give up and i am just gonna wait to install this, just as ut3, AND hellgate london on a mac book pro :)

---

