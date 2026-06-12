---
title: "Starcraft Battlenet fonts impossible to read"
date: 2008-11-29
forum: Wine
---

### Post by fishtoprecords on 2008-11-29
I'm running Ubuntu 8.10, fully patched, with wine 1.1.8

And I've got starcraft/broodwar working fairly well in single user mode, thanks to the postings on this forum. I've even got the official no-CD patch working.

But when I go to battle.net, the registration forms are all fubar, and I can't tell what to type or where.

I've even set my laptop to 640x480 so that Starcraft video doesn't have to change (which made seeing my main setting a challenge, since I usually run at 1600x1050

All I really want to do is get the latest patches. But I'm lost as to what to do next.

Hints? tips? links?

Thanks
Pat

---

### Post by Sugi on 2008-11-30
Original Starcraft
[http://ftp.blizzard.com/pub/starcraft/patches/PC/SC-116.exe](http://ftp.blizzard.com/pub/starcraft/patches/PC/SC-116.exe)
Starcraft Brood War
[http://ftp.blizzard.com/pub/broodwar/patches/PC/BW-116.exe](http://ftp.blizzard.com/pub/broodwar/patches/PC/BW-116.exe)

To install with Original Starcraft:
cd ~/Desktop
wine BW-116.exe

OR
To install with Starcraft Brood War:
cd ~/Desktop)
wine BW-116.exe

Cheers,
Sugi


PS: You should upload an image of problem.

I had some fonts issues with BattleNet.  First, try installing "arial.tff" and "tahoma.tff" to ~/.wine/drive_c/windows/fonts

If that doesn't fix it, try removing two fonts from your font folder "ae_AlBattar.ttf" and "sserife.fon"

---

### Post by fishtoprecords on 2008-11-30
> **Sugi said:**
> To install with Original Starcraft:
cd ~/Desktop
wine BW-116.exe


When I tried this, it reports that the no-CD patch was higher than what's in BW-116, so that doesn't do anything

> **Sugi said:**
> I had some fonts issues with BattleNet.  First, try installing "arial.tff" and "tahoma.tff" to ~/.wine/drive_c/windows/fonts

If that doesn't fix it, try removing two fonts from your font folder "ae_AlBattar.ttf" and "sserife.fon"

Interesting. There are no files in ~/.wine/drive_c/windows/fonts
I have installed the mS ttfonts package for Debian. They just are off somewhere else in the Ubuntu tree.

I'll try your fonts

Thanks

---

### Post by fishtoprecords on 2008-12-01
I'm registered. Thanks.

Not exactly sure what did it, perhaps your fonts.

It looked as if the dialog box was not properly cleared between steps of the signup process.

---

### Post by razorboy5 on 2009-08-24
can anyone offer more help on this topic?

i also cannot read Starcraft Brood War when i go on battlenet

added the two fonts

deleted the ae_Albatter.tff but could not find the other so could not delete

also installed msttcorefonts from synaptic

---

### Post by razorboy5 on 2009-08-24
ok sry 

it's not font's problem now i guess

it's just that it's not refreshing... so fonts are laid over each other after a few or two pages it's so messed up i can't read anything... is there a cure?

---

### Post by donkyhotay on 2009-08-25
> **razorboy5 said:**
> ok sry 

it's not font's problem now i guess

it's just that it's not refreshing... so fonts are laid over each other after a few or two pages it's so messed up i can't read anything... is there a cure?

Do you have the black screen where the new text layers itself on top of the old text? If so it's a known issue and not fixable (I've looked). I just memorized where all the battle.net buttons are located so that I don't have to read the text. Admittedly connecting can be a pain but once you've actually connected it starts working correctly again.

---

### Post by razorboy5 on 2009-08-26
yes it's the black screen

i've also gone to my dad's old computer and memorized all the buttons

however i'm getting an even more serious problem now, my Starcraft works fine the 1st time i start it but after exiting the 1st time if i try to get back on it the 2nd time it crashes

i'll post in a new thread since it is a new topic

---

