---
title: "Trouble booting OS X"
date: 2005-11-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by chimaera on 2005-11-26
Hi, 

I have a dual-boot setup (actually triple-boot), 2x linux and OS X 10.4.3. The problem is, that I hardly can't enter OS X. Most of the time, after selecting OS X within yaboot, I see the small apple on grey screen, and where OS X's login screen should pop up, I only get a black box, and that's it. Two things: the black box is smaller and it appears much earlier than the actuall login window does normally (guess it's not any graphic issue or a borked login window). 

I was able to fix this one time yesterday by booting from the OSX install -disk and "repairing" the partition OS X is installed. Strange thing was, that after doing so, the powerbook didn't boot directly into OS X as I expected, but yaboot seems to have been overwritten for i jst got the small symbol telling me that no OS or bootable medium could be found. After booting from the ubuntu install-disk in rescue mode and re-writing yaboot into the MBR, I was able to boot into OS X one time, after restarting I was presented the black window again. The two linux-installations work fine, though. 

Any ideas on this? I'm aware that this might be as well a borked OS X installation, but on the otehr hand, it's a pretty fresh, not fiddled-around-much-with install.. Is OS X picky about the partition it's installed on? Or is yaboot? I guess the problem is somehow related to the fact that OS X isn't booted even after using Install-DVD to repair it, but I just can't figure it out..

Thanks..

---

### Post by autocrosser on 2005-11-26
Two things to try--

1. Boot into openfirmware--hold the <Option> key down during boot--you should see a screen with disc icons--both Linux & OSX (assuming your book is newer than 2000/1)--choosing OSX this way SHOULD change you pram settings---if not then---

2. Reset the PRAM--you may have a corrupt setting--key combo is <Apple><Option><P><R> (Known as the "four finger salute' ;))--let the unit "chime" at least three times then either hold the <Option> or let it boot normally--this will reset all the base settings to default.

OSX is normally pretty "bullet-proof"-- and I have not seen Ubuntu cause problems unless it's been "messed" with---

Lastly--check the OSX with a good utility--Disc Utility is OK, but I use something like TechTool if I'm serious about repairs---

---

### Post by Rxke on 2005-11-26
[QUOTE=chimaera]After booting from the ubuntu install-disk in rescue mode and re-writing yaboot into the MBR, I was able to boot into OS X one time, after restarting I was presented the black window again. The two linux-installations work fine, though.[/QUOTE]

did you boot into OSX then rebooted straight again into OSX? Or did you do a Linux-session in between?

---

### Post by ssam on 2005-11-26
have you been mounting the mac os x partition in linux?

---

### Post by chimaera on 2005-11-26
[QUOTE=Rxke]did you boot into OSX then rebooted straight again into OSX? Or did you do a Linux-session in between?[/QUOTE]
rebootted directly into OSX again

[QUOTE=ssam]have you been mounting the mac os x partition in linux?[/QUOTE]
see above. but i had mounted it before (and unmounted it cleanly).

i also tested the suggestions of autocrosser, with no success. i always get the black square on the screen when trying to start os x.

---

### Post by ssam on 2005-11-26
if you get to the grey screen with the apple logo then it is very unlikely to be yaboot/linuxs fault.

you could try geting mac os x to do a verbose boot. as soon as you get past the yaboot screen (by pressing x, or letting it time out to mac osx) then hold apple+V (if i remember correctly). this will boot mac os x with out the shiney splash screen so you can see whats going on.

---

### Post by chimaera on 2005-11-26
I used the verbose mode to check the boot-messages, and the problem seems to be that that / can't be mounted. I just don't get it why. if i boot from the  install-dvd and run diskutil, i can boot osx one time. guess i either have to get a decent disk-utility or repartition the whole disk.. maybe the part.-table is borked or something.. anyhow, thanks for your help.

/edit
typos all around..

---

### Post by autocrosser on 2005-11-26
Well--'fraid its time for TechTool--I've used Tool for several years now & it will clean up problems better that any other utility I've tried.

---

