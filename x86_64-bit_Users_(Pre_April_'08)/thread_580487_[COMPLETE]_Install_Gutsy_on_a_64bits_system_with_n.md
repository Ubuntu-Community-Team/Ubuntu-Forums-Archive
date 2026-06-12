---
title: "[COMPLETE] Install Gutsy on a 64bits system with nvidia video card"
date: 2007-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Silent Ninja on 2007-10-18
I've some trouble with nvidia video cards, and the latest release of ubuntu, so, now that i got it fixed (or bypassed i think), i'm gonna share the data to you too:

Many (if not all) users with a 64 system and a newer nvidia video card (may not happen with old ones), may have trouble at the splash loading screen, or at loadind the live cd or installing even. The only thing you'll see is a blank screen. If it's your case here's the solution:



THEY MAY BE SOME FASTER OR BETTER WAY TO DO IT, BUT THIS IS THE EASYEST I'VE FOUND!!
THEY MAY BE SOME FASTER OR BETTER WAY TO DO IT, BUT THIS IS THE EASYEST I'VE FOUND!!



FIRST: INSTALLATION
It happened to me that when i tried to run the live cd it hanged up on loading. The quicker solution i've found was, to set my language, keyboard, and at the VGA selection (F4), i've set 1024x768, and it worked, i guess, it was something about the screen refresh (60hz in my laptop), but, that seems to fix it, since it automatically detected my max screen resolution after that. Once the gnome (i've only tried with ubuntu) loads, you may be able to install the system normally.



SECOND: GETTING TO THE LOGIN SCREEN
Now is the big deal, you may not be able to log in to linux, so.. the solution comes here, at grub loading, press the ESC key and load ubuntu in recovery mode. Once you're logged (it may ask you for the root password, or not if you hadn't changed it), starts the magic.

- Edit the file /boot/grub/menu.lst.
(you may use the command "nano /boot/grub/menu.lst" without the quotes)

- Around the line 132 (it may vary if you have multiple kernels or systems), you'll find the first kernel loading command, here you have to take out the "splash" so.. search in the line (at the end mostly) and remove that word, then save (ALT+X, Y, ENTER), and you're done.

- You may still have some trouble to get it to work, first try to reboot, if it worked, stop reading the file, if it doesn't, go back to recovery mode and keep reading.



THIRD: THE RESTRICTED DRIVERS

- It's not imperative to install restricted drivers, but they come with 3d and some times also 2d acceleration commands for your nvidia video card, so they may come in handy. Once you're on the text recovery console again, type this command: "startx" (it'll get you to a gnome screen), click on quit, or press enter, and then, when you're back in the text mode, type... "exit"

- I think this shouldn't happen, but it'll take you to the gnome login screen. Once you log in, you'll see your desktop and everything else (on some restricted colors or status). You'll need an internet conection beyond here, so, if you have one, start configurating the network. 

- Once that's done, go to the synaptec package administration (it's on system > administration), and go to preferences (or options, it may be different since i'm using a spanish translation of ubuntu), and go to "repositories", then put the x on the "restricted" repositories, accept it, and install the "nvidia-glx-new" package. It may also work if you do this (once you've added the repositories) from the restricted drivers manager.

- It'll ask you to reboot and, tadá, your ubuntu linux is now shinning. I think this will be fixed on the next days by the ubuntu team, but.. in the meanwhile, this works. You'll be able to enable/configure compiz after this, and of course play some games if you have winex or cedega.



PS: I DIDN'T found all the solutions by myself, i was also encouraged or helped by some people here, and I really appreciate it. So the credit goes to them and the Ubuntu Community

---

### Post by eduardoeltortuga on 2007-10-18
I tried to put an X there but it won't let me.

---

### Post by Npl on 2007-10-18
I got a GF 8600 GT, and I installed Gutsy with no problem. Though I used the "alternate" CD, cant get easier IMHO.
But then it might be just a bug that I luckily dint encounter.

---

### Post by Nick Payne on 2007-10-18
I always use the Alternate install CD and have had no video problems with either a Geforce4 MX440 on a Dell workstation or a Geforce 7600 on an HP workstation.

---

### Post by oodledoodle on 2007-10-19
did not work for me with 64 bit and an nvidia 6800gs agp. i still get the black screen before the login window when i enable nvidia drivers :(

---

### Post by Silent Ninja on 2007-10-19
> **oodledoodle said:**
> did not work for me with 64 bit and an nvidia 6800gs agp. i still get the black screen before the login window when i enable nvidia drivers :(

Please check that you've deleted the "splash" from the kernel loading at the menu.lst file. 

BTW, using the alternate cd, or updating from an older ubuntu version, this doesn't happen, it's just for the live cd installation (clean install), because if you already had the new drivers, you'll see everything just fine.

---

