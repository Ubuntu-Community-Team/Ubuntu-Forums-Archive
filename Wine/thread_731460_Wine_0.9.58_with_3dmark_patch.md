---
title: "Wine 0.9.58 with 3dmark patch"
date: 2008-03-21
forum: Wine
---

### Post by piratesmack on 2008-03-21
A new version of wine just came out today, so I applied the 3dmark patch and made a deb. Let me know if it works.

[http://files.filefront.com/wine+0958+i386deb/;9864470;/fileinfo.html](http://files.filefront.com/wine+0958+i386deb/;9864470;/fileinfo.html)

The 3dmark patch is needed to run COD4...

---

### Post by piratesmack on 2008-03-21
uh oh I can't get cod4 to install in 0.9.58

It crashes when installing directX

I'll try again without agreeing to the directx license agreement and post if it works

---

### Post by piratesmack on 2008-03-21
Call of Duty 4 installs fine if you choose not to install directx9c.
You just have to copy d3dx9_34.dll in the system32 folder

That's weird, though. Choosing to install dx9 never crashed the older versions


You should also choose not to install punkbuster... It doesn't work

---

### Post by bobdob20 on 2008-03-22
Does anyone have a 64bit patched version?

---

### Post by Chriis on 2008-03-22
idem anyone have  patched 64bits deb ?
or this patch can be applied to 64b version of wine?

And WHY this patch can't be include in official release of wine?

We want to play COD4 please ;-)

Thanks

---

### Post by bobdob20 on 2008-03-22
> **Chriis said:**
> 
And WHY this patch can't be include in official release of wine?

We want to play COD4 please ;-)


Yeah, is there any reason why the patch is not included with wine. Surely it just adds alpha glow in, or am i missing something?

---

### Post by piratesmack on 2008-03-22
wow didn't realize how many people used 64bit operating systems. I have a 64bit processor, but use the 32bit version anyway

The 3dmark patch has been around for a while, I don't think the wine developers plan on implementing it.

You can try this to install it on 64bit:
> sudo dpkg --forcearchitecture -i NAMEOFDEB.deb


Also, i believe there is a tutorial out there somewhere that shows how to compile wine with the 3dmark patch for 64bit. It's pretty straight forward

---

### Post by KhaaL on 2008-03-23
Here's another wish to see a 64-bit version of this package :)

---

### Post by Chriis on 2008-03-23
sudo dpkg --forcearchitecture -i NAMEOFDEB.deb


I do not wish to use forcearch for installing wine, it will install a 32b wine on a 64b OS

i did it on edjy, and it was impossible to update/desinstall, just not do it.

---

### Post by SirKhan on 2008-03-26
Thanks for this package!

---

### Post by piratesmack on 2008-03-26
Here's a really good howto on compiling wine and applying th alpha glow patch:

[http://ubuntuforums.org/showpost.php?p=4047498&postcount=13](http://ubuntuforums.org/showpost.php?p=4047498&postcount=13)

---

### Post by robokiller on 2008-04-17
i have tried every tutorial there is that i could find on how to compile wine.  the thing is is that no matter how hard i try, i cant get it to compile without errors on 64bit.

it keeps spitting out error 2's and from what i have gatherd, it it almost impossible to compile on 64bit.

if somebody does manage to get it to compile... PLEASE make a deb!!!!!

thanks

---

### Post by piratesmack on 2008-04-20
> **robokiller said:**
> i have tried every tutorial there is that i could find on how to compile wine.  the thing is is that no matter how hard i try, i cant get it to compile without errors on 64bit.

it keeps spitting out error 2's and from what i have gatherd, it it almost impossible to compile on 64bit.

if somebody does manage to get it to compile... PLEASE make a deb!!!!!

thanks

[http://wiki.winehq.org/WineOn64bit#head-c47d9e53f952c5b6260467e0dc158321229216de](http://wiki.winehq.org/WineOn64bit#head-c47d9e53f952c5b6260467e0dc158321229216de)

---

### Post by beefcurry on 2008-04-21
Hardy updates your wine to 0.9.59 without the patch. Watch out if when your upgrading ;). You will need a separate patched one for 0.9.59. I was told this worked, I have not yet tried it. [http://www.bennyp.org/wine/wine-0.9.59-3dmark.patch](http://www.bennyp.org/wine/wine-0.9.59-3dmark.patch) documented [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10429](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10429)

---

### Post by piratesmack on 2008-04-21
> **beefcurry said:**
> Hardy updates your wine to 0.9.59 without the patch. Watch out if when your upgrading ;). You will need a separate patched one for 0.9.59. I was told this worked, I have not yet tried it. [http://www.bennyp.org/wine/wine-0.9.59-3dmark.patch](http://www.bennyp.org/wine/wine-0.9.59-3dmark.patch) documented [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10429](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10429)

Yeah that patch works, but for some reason I can't get multiplayer to launch in Wine 0.9.59 or 0.9.60.

I'm the guy who tested COD4 with Wine 0.9.60 on the appdb page, btw

---

### Post by beefcurry on 2008-04-21
I was hoping multiplayer would work in 0.9.59 since mine never worked before. I am currently compliling it with the patch and will get back once I've tried it.

=============

Edit: Yes it works, I used the patch in the link above and compiled a 0.9.59 in Hardy 8.04 RC1. I can confirm both single player and multiplayer works, let me add multiplayer has NEVER worked for me before.

---

### Post by piratesmack on 2008-04-21
> **beefcurry said:**
> I was hoping multiplayer would work in 0.9.59 since mine never worked before. I am currently compliling it with the patch and will get back once I've tried it.

=============

Edit: Yes it works, I used the patch in the link above and compiled a 0.9.59 in Hardy 8.04 RC1. I can confirm both single player and multiplayer works, let me add multiplayer has NEVER worked for me before.

Really? multiplayer always worked for me, just no punkbuster. But I just can't seem to get it working in Wine 0.9.60, it just locks up.
Can someone try compiling Wine 0.9.60 with Ben P's 3dmark patch and let me know if they can get multiplayer working? I'll also try compiling it again, maybe I screwed something up somewhere?

---

### Post by piratesmack on 2008-04-22
Edit:
I just realized the reason multiplayer wasn't working for me was because of my sound card. (I have no idea why single player worked with my soundcard but multi didn't)

So I just popped my old soundcard in and it the game runs great with wine 0.9.60

---

### Post by leveliv on 2008-09-10
Force Arch doesn't work with the debs...

I havent tried compiling it but I will..What I rememeber is back when I used 32bit I could never get it to compile properly but everything so far that I have compiled on 64bit has worked fine :P

im on 8.04 btw

---

### Post by MYGRA1N on 2009-03-25
yeah this annoys me 2. they STILL dont include the ffxi patch, which has been around for ages. and they also dont include the fallout 3 patch. its as frustrating as hell compiling from source, only to be told you need about a 10000000000000000000000000000000 dependencies :confused:

---

### Post by KhaaL on 2009-03-25
> **MYGRA1N said:**
> yeah this annoys me 2. they STILL dont include the ffxi patch, which has been around for ages. and they also dont include the fallout 3 patch. its as frustrating as hell compiling from source, only to be told you need about a 10000000000000000000000000000000 dependencies :confused:

Of course if a community member would be able to provide these debs, then we wouldnt have the need to compile and get all those dependencies 

*hint hint!* :biggrin:

---

### Post by MYGRA1N on 2009-03-25
> **KhaaL said:**
> Of course if a community member would be able to provide these debs, then we wouldnt have the need to compile and get all those dependencies 

*hint hint!* :biggrin:

lolol, sorry i gave up on compiling after having to make the twelfth trip to synaptic to get dependencies. and ummmm yeah i dunno how to make debs :-?

---

