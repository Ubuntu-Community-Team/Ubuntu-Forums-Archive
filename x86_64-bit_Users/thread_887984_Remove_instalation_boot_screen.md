---
title: "Remove instalation boot screen"
date: 2008-08-12
forum: x86 64-bit Users
---

### Post by Sonic_RJ on 2008-08-12
Hi,
It's my first time posting on this forum, I hope I'm doing it right, if not, please warn me.

I've been looking for solving my problem but all i can find is about the boot after the installation of Ubuntu, well, better start explaining.

When you put the Ubuntu 8 CD in the computer (I am running a Windows Vista 64) it gives you the option of restarting the PC and booting from the CD. Since (I don't know why) that wasn't working, I've chosen another option in which it installed something that would allow me to have a screen where I could choose from Windos Vista and booting from the Ubuntu Live CD.

I have already installed Ubuntu and it's working fine, but that boot screen is still appearing, meaning I have two boot screens. The first one is the one that should appear (which I choose from Ubuntu, Ubuntu Secure, Memory test and Windows Vista). But after choosing Windows Vista from that, it appears the other screen that installed before I had installed Ubuntu which I choose between Live CD, Vista and Memory Test.

Well, i think it's easy to notice that I don't want that second screen, but I don't know how to remove it.

I hope someone can help me.

Thanks.

Sonic_RJ

---

### Post by Yellow Pasque on 2008-08-12
I'm confused, is the Live CD still in your drive? Is your BIOS giving you a boot screen?

---

### Post by Stunts on 2008-08-12
I think I understand you problem:
First when you turn on your computer you get a GRUB screen, with 4 options:
Ubuntu
Ubuntu recovery
Memory test
Win Vista

Then, when you choose Vista, you get a new screen - Where you can choose Vista or Ubuntu.

I've never used Wubi, but my guess is that you are getting a GRUB boot loader, and windows's boot loader is altered - giving you two options, which is typical of a wubi install (I think).

My question for you is - how did you install Ubuntu? Did you install using Wubi (in windows) or did you boot directly from the LiveCD?

I think this is it, but we should get the attention of someone more experienced with Wubi installs then me.

---

