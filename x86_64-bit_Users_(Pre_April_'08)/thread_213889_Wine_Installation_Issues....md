---
title: "Wine Installation Issues..."
date: 2006-07-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Miki01 on 2006-07-11
Well, I'm missing playing games on the old Windows box. So I thought I'd install Wine. I found a few tutorials on how to install it. Apparently, none work for me. For some, in terminal when I paste in a code, it may say that a directory doesn't exist. Well, first off, I'm already in my Desktop directory, and that directory that doesn't exist, when I click the button on the bottom-left to show my desktop, I can clearly see that that file is there. And other tutorials have told me to start off by downloading the i386 version of Wine from their site. So I add in that channel to my synaptic and reload, I keep getting an error saying "http://wine.budgetdedicated.com/apt/...4/Packages.gz: 404 Not Found"

It keeps saying amd64 in the filename. I don't know what to do. I don't know where to look for the i386 version. I hear members saying that theirs other ways without using chroot. I don't even know what chroot is. I need someone's help to guide me step-by-step in installing it and clearing every single problem that arises. For once, I'm actually thinking that Windows is a better OS... help me change that thought...

Remember, I'm using an amd64-based computer...

---

### Post by Kilz on 2006-07-11
> **Miki01 said:**
> Well, I'm missing playing games on the old Windows box. So I thought I'd install Wine. I found a few tutorials on how to install it. Apparently, none work for me. For some, in terminal when I paste in a code, it may say that a directory doesn't exist. Well, first off, I'm already in my Desktop directory, and that directory that doesn't exist, when I click the button on the bottom-left to show my desktop, I can clearly see that that file is there. And other tutorials have told me to start off by downloading the i386 version of Wine from their site. So I add in that channel to my synaptic and reload, I keep getting an error saying "http://wine.budgetdedicated.com/apt/...4/Packages.gz: 404 Not Found"

It keeps saying amd64 in the filename. I don't know what to do. I don't know where to look for the i386 version. I hear members saying that theirs other ways without using chroot. I don't even know what chroot is. I need someone's help to guide me step-by-step in installing it and clearing every single problem that arises. For once, I'm actually thinking that Windows is the best OS there is... help me change that thought...

You see wine is a problem for 64bit users. The reason is its impossible to make a 64bit package for a 32bit emulator. I have one of the more used Wine howto's. [Take a look]("http://www.ubuntuforums.org/showthread.php?t=185557"), if you have any questions I can answer them.

---

### Post by Miki01 on 2006-07-11
Yeah, I already tried your tutorial... It didn't work for me. Check the last page on your how-to

---

### Post by Miki01 on 2006-07-11
EDIT: Okay... I tried installing Delta Force 2... But I keep ending up with this 

> An error occured during the move data process : - 117

Error. (attachment 1)

Why does it keep happening? When I try the installation again, I get up to 36% and it errors again... Does anyone know why this is happening, and how I solve this?

I was able to install the first Delta Force 1... But kept opening a black window and another smaller one that just says "OK"... (attachment 2)

---

### Post by Kilz on 2006-07-11
> **Miki01 said:**
> Yeah, I already tried your tutorial... It didn't work for me. Check the last page on your how-to
I learned to create install scripts for my Firefox howto. I have created one for Wine now. [Click here]("http://tghc.org/files/wine-install.tar.gz"), download the file, save it to your desktop, extract it. Open a terminal, type in
```
cd ~/Desktop/wine
sudo ./wine
```
once its done it will delete the install folder, type in winecfg and wait a minute for the wine configuration panel to show. You may get a few errors, but if the wine config panel shows ignore them.

---

### Post by Kilz on 2006-07-12
> **Miki01 said:**
> Okay, Wine is installed. However, I don't know how to use it. I clicked on Add Application and located the setup.exe file in my CD. Okay, so now its on the list... How do I install it? Did I even do it right?
Add application on the winecfg is to add settings to wine, not to install the program. To install the open the cd normaly, right click on the exe file, choose open with other application, the application list will open , click at the botton"use custom command" click browse, the select an application will open, scroll down and find wine, highlight it, clock open , open , and the setup for the program should start.

---

### Post by Kilz on 2006-07-12
> **Miki01 said:**
> EDIT: Okay... I tried installing a game... But I keep ending up with this 



Error.

Why does it keep happening? When I try the installation again, I get up to 36% and it errors again... Does anyone know why this is happening, and how I solve this?

Wine isnt perfect. It doesnt run everything 100% of the time. [Look here to see if the application is supported]("http://appdb.winehq.org/"), search for it, and if its supported, see if it needs special setup.
For games even I dont use wine, [Cedega]("http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fwww.transgaming.com%2F&ei=AnW0RLzuMbKCiAGIjKGuDg&sig2=AZFj660aP-B3cwfMu0L98A") is worth every penny, its click , click , install run.

---

### Post by Miki01 on 2006-07-12
Oh, is Cedega easily installable on an amd64 system? What do you mean by worth every penny? Is it a pay-to-use thing?

---

### Post by livingtarget on 2006-07-12
Isn't wine installable by doing "apt-get install wine"?

You'll need to pay for Cedega as it's a commercial product. You'll get better support for games then on wine of course.

[http://www.transgaming.com/](http://www.transgaming.com/)

---

### Post by Kilz on 2006-07-12
> **livingtarget said:**
> Isn't wine installable by doing "apt-get install wine"?

You'll need to pay for Cedega as it's a commercial product. You'll get better support for games then on wine of course.

[http://www.transgaming.com/](http://www.transgaming.com/)
Wine is not available with apt/synaptic for the 64bit versions. Its one of the things that you have to install by howto, or my new install script.
Cedega is a commercial product. It costs $15 for a 3 month subscription. during that time you can get updates that add new games. If you let the subscription run out the program still functions. I paid the $15. I have 10 games loaded into it. Diablo2, WoW, SimeCity4 ect. Each would have probablyy taken me an hour to get running right with wine. My free time is more valuable to me than $1.50 an hour. IMHO commercial isnt a bad thing, sometimes its worth paying for some things. Its a freedom, the freedom to pay if I choose.
I mostly use wine to run Internet explorer for the 1 site I need to run it for in order to get paid.

---

### Post by Miki01 on 2006-07-12
Hmm... Seeing as I don't have a CC to pay for Cedega, I guess I'm out. Is there any other programs you recommend to be able to play Windows based games? I just installed 2 games, but they don't work correctly. One asks me to put the disk into the drive just to play, the disk IS in the drive, but still keeps reading that it isn't. One doesn't open period, and yeah... -_-''

---

### Post by Kilz on 2006-07-12
> **Miki01 said:**
> Hmm... Seeing as I don't have a CC to pay for Cedega, I guess I'm out. Is there any other programs you recommend to be able to play Windows based games? I just installed 2 games, but they don't work correctly. One asks me to put the disk into the drive just to play, the disk IS in the drive, but still keeps reading that it isn't. One doesn't open period, and yeah... -_-''
What games are you trying to install?

---

### Post by Miki01 on 2006-07-12
Delta Force 1, Delta Force 2, TC's Rainbox 6 (first one) and Shadow Force: Razor Unit. And probably Ghost Recon and Q3A if I can find them. Those games aren't too popular, but they're quite fun

EDIT: Well, I just found Ghost Recon, now I just need to remember where I put Q3A...

---

### Post by RAOF on 2006-07-12
Any game which uses CD copy protection (safedisk, and their ilk) will almost certainly not run in Wine (it will say "please insert original cd, or something to that effect).  That means: either download a no-cd crack for the games you own (legality questionable) or don't play it under wine.  Almost all game in the last 5 years have had **some** form of copy protection.

---

### Post by Miki01 on 2006-07-12
Ah, thanks... Well, there goes my fun. I may as well wait until my dad gets a new copy of Windows XP so I can dual boot.

So now... How do I go about uninstalling the games I had installed, and how do I COMPLETELY uninstall Wine after that?

---

### Post by Kilz on 2006-07-12
> **Miki01 said:**
> Ah, thanks... Well, there goes my fun. I may as well wait until my dad gets a new copy of Windows XP so I can dual boot.

So now... How do I go about uninstalling the games I had installed, and how do I COMPLETELY uninstall Wine after that?
Both are easy. But nocd hacks are easy to get and use. The only problem may come if you play the games online on the creators servers. Lke Blizzard games on Battlenet. If you still want Wine gone.
```
rm -rfd /home/<username>/.wine
```
```
sudo apt-get remove wine
```

---

### Post by Miki01 on 2006-07-12
Okay, thanks, its removed. I guess I can just wait for a copy of WinXP so I can dual boot instead (lucky that I did a 50/50 partition just in case). When that time comes, I hear there'll be problems with GRUB after XP is installed though...

---

### Post by Kilz on 2006-07-12
> **Miki01 said:**
> Okay, thanks, its removed. I guess I can just wait for a copy of WinXP so I can dual boot instead (lucky that I did a 50/50 partition just in case). When that time comes, I hear there'll be problems with GRUB after XP is installed though...
Yes windows removes grub from the master boot record. But you can fix that if the have a Ubuntu install cd, just rescue the installed system.

---

### Post by Miki01 on 2006-07-12
Ah, okay thanks a lot, I'll keep it in mind!

---

