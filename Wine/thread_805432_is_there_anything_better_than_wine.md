---
title: "is there anything better than wine?"
date: 2008-05-24
forum: Wine
---

### Post by ripin1 on 2008-05-24
is there anything better than wine? i just have very bad luck with it. none of my games work under it, the ones that do have severe problems. AND i killed my windows partition so there is no turning back.

---

### Post by jrusso2 on 2008-05-24
Not for free.  There is Cedega and Crossover games and VMware workstation I think supports DX games now

---

### Post by Steve413z on 2008-05-24
Crossover office is good, but i think it's like $40 (i paid it) (still doesn't run everything though) (there is a free trial)

the other thing you could do is use VirtualBox, and install Windows XP on it.

---

### Post by Kinst on 2008-05-24
Crossover is about the same except you pay for it and it *tries* to do configuring for you.

Cedega sucks.

The best option is to go back to dual-booting. Sorry bro.

---

### Post by cogadh on 2008-05-24
CrossOver *is* Wine, but with a nice GUI front end. Cedega is a rip off (monthly fee, poor customer support). Virtual machines only work for playing games that are DirectX 8 or older. If you can't get Wine to work, then dual-booting is your best bet.

BTW - Wine shouldn't have affected your existing Windows install at all, unless you made the colossal mistake of trying to use it to run applications that are installed on your Windows partition, instead of installing them in Linux with Wine as you are supposed to do.

---

### Post by Fazz Munkle on 2008-05-24
> **cogadh said:**
> CrossOver *is* Wine, but with a nice GUI front end. Cedega is a rip off (monthly fee, poor customer support). Virtual machines only work for playing games that are DirectX 8 or older. If you can't get Wine to work, then dual-booting is your best bet.

BTW - Wine shouldn't have affected your existing Windows install at all, unless you made the colossal mistake of trying to use it to run applications that are installed on your Windows partition, instead of installing them in Linux with Wine as you are supposed to do.

I think he meant that he deleted the Windows partition on purpose already so he'd rather not go back and reinstall Windows.

I'm having problems installing older games myself. Starcraft, Hexen, Command & Conquer to name a few. I looked for an explanation online and I get the idea that it has something to so with new lower memory deal and security to prevent malicious code from operating in the lower part of memory. Don't ask me what that means, all I got was "security" and "malicious code." And I do remember something about "preloader" or something when I typed in $ wine /.../*.exe when I did have wine installed (I have CrossOver Games installed now). But then again it seems some people have gotten Starcraft to work as if there was no problem even starting the install. They don't mention anything other than in-game problems, so they obviously got it installed. I run into the same problem with CrossOver Games I'm assuming as no installer for older games will launch with the GUI run program "Run a Windows Command."

Any thoughts?

---

### Post by happyhamster on 2008-05-24
For the preloader issue, see:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

### Post by ripin1 on 2008-05-24
yeah, it wasnt wine that deleted my windows, it was me not knowing what a partition was.

---

### Post by philinux on 2008-05-24
> **happyhamster said:**
> For the preloader issue, see:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

RC1 seems to have fixed this now.

---

### Post by Fazz Munkle on 2008-05-26
Yeah, it seems that RC1 can run older Windows games now. I wish CrossOver Games would get updated to RC1. I ran into some problems (mostly with DirectX and 3D) with some games that I think can be fixed with some WINE tweaking, but I'm too lazy and impatient to do it. :lol: As for DOS games I'm just going to install DOSBox.

---

### Post by pbpersson on 2008-05-26
> **ripin1 said:**
> yeah, it wasnt wine that deleted my windows, it was me not knowing what a partition was.

WOW.....I guess you learned about partitions the hard way :(

---

### Post by cogadh on 2008-05-26
> **Fazz Munkle said:**
> Yeah, it seems that RC1 can run older Windows games now. I wish CrossOver Games would get updated to RC1. I ran into some problems (mostly with DirectX and 3D) with some games that I think can be fixed with some WINE tweaking, but I'm too lazy and impatient to do it. :lol: As for DOS games I'm just going to install DOSBox.
I would expect a CrossOver Games update to follow right after the Wine 1.0 official release in June. Even though CX Games is supposed to be using the "latest, greatest, bleeding edge improvements in Wine technology", it doesn't seem worth it (to me) to release an update for one of the RCs when 1.0 will be out in a matter of weeks. Besides, Wine is currently in code freeze, so the only real difference between the current RCs and the official 1.0 release will be 1.0's greater stability. I'm pretty sure that greater stability is preferable in CX Games.

---

