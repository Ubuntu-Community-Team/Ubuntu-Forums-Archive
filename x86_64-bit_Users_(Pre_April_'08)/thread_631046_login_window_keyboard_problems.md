---
title: "login window keyboard problems"
date: 2007-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tig3rzhark on 2007-12-04
I have an Acer Aspire 5100-3583 laptop.  I currently am running gutsy and so far have had many problems that have plagued me for a long time.

Currently I started up my computer and I can no longer type in my username let alone my password.  I can run the terminal under recovery mode but when I want to login into the desktop, I cannot even get a letter inputted unto the computer.  

I have tried restarting it with no success of being able to login to the desktop.  I'm looking for some help please!

---

### Post by Pitel on 2007-12-05
I have the same problem... I always have to reboot multiple times before i can log in. But mouse is working, and also REISUB shortcuts are working, co my keyboard is fine... and it it fine until gdm start (I can change numlock LED, in gdm, i can't)

---

### Post by azbarcea on 2007-12-05
hi

> **Tig3rzhark said:**
> I have an Acer Aspire 5100-3583 laptop.  I currently am running gutsy and so far have had many problems that have plagued me for a long time.

Currently I started up my computer and I can no longer type in my username let alone my password.  I can run the terminal under recovery mode but when I want to login into the desktop, I cannot even get a letter inputted unto the computer.  

I have tried restarting it with no success of being able to login to the desktop.  I'm looking for some help please!


let's understand few things:
1. after u press the **power button**, and the BIOS starts, you **are** able to use your keyboard, that means you can enter into the BIOS menu and so on.
2. after your (K)Ubuntu starts, and the progress bar finishes (splash image), then, the **kdm** starts (this is where you are asked for user and password).
3. The keyboard is now frozen.

(if this is so, than u may change your keyboard layout: [https://bugs.launchpad.net/ubuntu/+bug/95886](https://bugs.launchpad.net/ubuntu/+bug/95886) - this is the bug)

4. If your keyboard freeze only after you enter user and password ... that another nasty bug. I resolved it by deleting $HOME/.kde folder (not a very pleasent solution), all my KDE settings were deleted... but after few minutes everything was back to normal.

---

### Post by Davjack on 2008-04-29
Hi,

> **azbarcea said:**
> let's understand few things:
1. after u press the **power button**, and the BIOS starts, you **are** able to use your keyboard, that means you can enter into the BIOS menu and so on.
2. after your (K)Ubuntu starts, and the progress bar finishes (splash image), then, the **kdm** starts (this is where you are asked for user and password).
3. The keyboard is now frozen.
> **Pitel said:**
> I have the same problem... I always have to reboot multiple times before i can log in. But mouse is working, and also REISUB shortcuts are working, co my keyboard is fine... and it it fine until gdm start (I can change numlock LED, in gdm, i can't)I have the same bug on a Ubuntu 8.04 desktop 32-bit

> **azbarcea said:**
> (if this is so, than u may change your keyboard layout: [https://bugs.launchpad.net/ubuntu/+bug/95886](https://bugs.launchpad.net/ubuntu/+bug/95886) - this is the bug)I'm not sure that your link is about the correct bug.

---

### Post by Pitel on 2008-04-29
Well, my keyboards (on both desktop and laptop) are working... laptop on hardy, desktop still gutsy. I has been a long time, so I don't remember what has changed.

---

