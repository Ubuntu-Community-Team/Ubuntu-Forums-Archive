---
title: "Photoshop CS2 Error using Wine-Doors"
date: 2008-02-07
forum: Wine
---

### Post by ondo311 on 2008-02-07
It opened up once, the first time right after installation (it installed perfectly)

But now I get this error:

[IMG]http://i94.photobucket.com/albums/l110/sneeker5/PSError.png[/IMG]



Sooo... hardware problem, whats this mean?

---

### Post by mooha on 2008-02-07
I think that for the moment the better way you use applications designed to run under Windoz on your gnu/linux machine is virtual machines.

---

### Post by ondo311 on 2008-02-08
Ok, so,.. sorry i have no idea what all that means lol

---

### Post by Avis Phlox on 2008-02-13
I believe he means that it would be better to run PhotoShop, a Windows-based programme, on Windows, thru a virtual machine when you're on Ubuntu.  

I know, it can get really confusing because it seems one has to go thru so many layers to do what you want.  I, too, have been looking to see how I can abandon the Windows OS and move to Linux.  My reason is that I'm sick and tired is WinXP and its vulnerabilities.  Not to go off on a tangent but there's a trojan virus on my system that no anti-virus seems to recognise.

But anyway, I know how it is to have the need to use PhotoShop.  People have been trying for a long time (seems long) to successfully install PS CS2 and CS3 using Wine but it's either an error with hardware or registry, there's no resolution.  

What mooha suggested is this:

Once you're in Ubuntu, download and install something like VirtualBox.  It's a programme that lets you install many other operating systems on your harddrive but it makes it seem as if it's a whole other machine.  So, you can install Windows XP on this 'virtual machine' and within that XP, you can install and run your PhotoShop programme.  It's the only sure way, for now.  

I hope I got that right...

---

### Post by FrozenFox on 2008-02-13
What version of wine are you using? 0.9.55 (and i think 54 too) are supposed to work well with cs2, but the version in the repositories for ubuntu is old. If you don't know what version you have, you're probably using an old version. You might be able to fix your problem by going [http://www.mepislovers.org/forums/showthread.php?t=13883](http://www.mepislovers.org/forums/showthread.php?t=13883)   to this thread, download the .deb at the end of the first post, and running that, rebooting and trying cs2 again.

---

### Post by jhyland87 on 2008-04-02
Im working with this problem too.. I THINK its because im on the tryout version.. are you?

ill put in a serial on a new one and ill see what happens.

---

### Post by Kinst on 2008-04-02
I had photoshop working perfectly from a wine-doors install. Then I screwed around with some winetrick stuff and it started giving me the error you get. Try removing wine, deleting your .wine folder manually, then getting the latest version and starting from scratch with wine-doors. It should work.

---

### Post by jhyland87 on 2008-04-02
Thats exactly what I did, however it seems to give me an error like a day or two later. so ill check tonight, i reinstalled wine and wine-doors yesterday and reinstalled PScs2

---

### Post by jhyland87 on 2008-04-02
by the way, hold down ctrl alt shift while opening photoshop and click ok, it will open it... not a perfect fix but it seems to work, ill tell you if it works tonight.

---

### Post by jhyland87 on 2008-04-02
ok.. I still get that error. Its a software error, not hardware.

---

### Post by Kinst on 2008-04-03
Hm. Well I reinstalled all my wine apps today (I have onenote, word, powerpoint, excel and photoshop working now). I did wine-doors and then activated photoshop. I'll let you know if it starts to screw up again. :(

---

### Post by jhyland87 on 2008-04-03
it will.

---

### Post by hessiess on 2008-04-03
i think its becouse some font is missing, but i dont know which one

---

### Post by jhyland87 on 2008-04-03
I added every font I could..

Honestly, I notice that it only does it after a day or so.. Maybe its reading the date on the ubuntu os wrong.

---

### Post by Kinst on 2008-04-03
What's it say when you run "wine photoshop.exe" in konsole in photoshop's folder.

---

### Post by jhyland87 on 2008-04-03
> **Kinst said:**
> What's it say when you run "wine photoshop.exe" in konsole in photoshop's folder.

its not found

---

### Post by jhyland87 on 2008-04-03
> **hessiess said:**
> i think its becouse some font is missing, but i dont know which one

YOU WERE RIGHT!

run these 2 lines in the terminal.

wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)
sh winetricks corefonts vcrun6

then start photoshop

:guitar:

---

### Post by Kinst on 2008-04-03
Nice.:)

---

