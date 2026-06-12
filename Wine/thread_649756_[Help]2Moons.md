---
title: "[Help]2Moons"
date: 2007-12-25
forum: Wine
---

### Post by LeoKnight on 2007-12-25
Hey guys, just wondering does this work with Ubuntu or not XD? hopefully it does coz it'd be great if i could play this on ubuntu.

Thanks alot

/Kev

---

### Post by TidusBlade on 2007-12-25
Checked the Wine AppDB and found the [2Moons](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5722) entry, and unfortunetly it says it works like Garbage in Linux under WINE :(
If the requirements for 2Moons is low then you might be able to play it under Windows XP using VirtualBox ;)

---

### Post by LeoKnight on 2007-12-25
Dammit, i can play it on windows just didn't know if i could play it on Ubuntu, thanks for the reply tho :)

---

### Post by TidusBlade on 2007-12-25
You can always use Virtualbox though, play through a Virtual desktop basically, works for many games, just that DX9 might be a slight problems.

---

### Post by LeoKnight on 2007-12-25
How would i use Virtual desktop to play it on ubuntu 0.o?

---

### Post by kazuya on 2008-01-14
I need to test it out. I am currently running the game on Windows XP. I use XP now just for that game. A little sad. I would try virtual box on Ubuntu and see how it runs. I may then try crossover office or cedega. Anything that would work.
I love that game. I am addicted now to it.

Anyone here playing the game. My character is a Bagi Warrior lvl 31 right now; Name is [akuma] Let me know if you want to party. I need the help that is for sure.

---

### Post by kazuya on 2008-01-16
game would work if not for the gameguard or nprotect stuff implemented in the game. They need to get rid of that thing. Its purpose was to stop Botters, but it is really making it impossible to launch the game. it seems upon launching the game as gamegaurd does not see activex and detects wine or some form of emulation, it closes the app. I am not that knowledgeable, but I am actively investigating and trying to ask the company to think of linux users or at least wine so as to have compatibility..

---

### Post by grondinmf on 2008-10-29
i know this thread is old but hopefully maybe someone will have made some advances....i can get the game to load...once i click on start gameguard starts but then i get error 114...on a windows system this error usually relates to a firewall or something...anyway to get past this in linux...i'm going to try a few thing tonight(different windows compatibility modes running in VM(wich probably wont work)) i'll post shell logs of my tests.

---

### Post by ov3rcl0ck on 2009-04-18
> **kazuya said:**
> game would work if not for the gameguard or nprotect stuff implemented in the game. They need to get rid of that thing. Its purpose was to stop Botters, but it is really making it impossible to launch the game. it seems upon launching the game as gamegaurd does not see activex and detects wine or some form of emulation, it closes the app. I am not that knowledgeable, but I am actively investigating and trying to ask the company to think of linux users or at least wine so as to have compatibility..

How gameguard works is that it creates a sandbox and allocates protected memory, it also does something with a DX overlay to prevent bots. Since allocating memory and creating this type sandboxes requires processing at the kernel level it can't be done because WINE doesn't have a kernel, its simply is a compatibility layer. WINE would need to emulate a kernel or wrap the program such as ndiswrapper does to wireless drivers to process at the kernels level.

---

### Post by NightMKoder on 2009-04-18
> **ov3rcl0ck said:**
> How gameguard works is that it creates a sandbox and allocates protected memory, it also does something with a DX overlay to prevent bots. Since allocating memory and creating this type sandboxes requires processing at the kernel level it can't be done because WINE doesn't have a kernel, its simply is a compatibility layer. WINE would need to emulate a kernel or wrap the program such as ndiswrapper does to wireless drivers to process at the kernels level.

Close, but not exactly. Wine does emulate the windows NT kernel, it's just that wine runs in user-mode, while the operations that gameguard needs are very low-level hardware and need to be done in kernel mode (basically allows you to talk to devices directly). 

However, the main reason wine won't run gameguard is because gameguard uses a very horrible method of protection by creating a virtual device driver without your consent. It's pretty much injecting itself into windows. [http://en.wikipedia.org/wiki/GameGuard](http://en.wikipedia.org/wiki/GameGuard) Wine will not support device drivers, so this is most likely not happening in the near future.

---

