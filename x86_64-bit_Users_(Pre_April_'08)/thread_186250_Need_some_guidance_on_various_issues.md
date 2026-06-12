---
title: "Need some guidance on various issues"
date: 2006-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dr. Who on 2006-06-01
I've encountered some issues attempting to install Mozilla plugins to my system.
I'm fairly new to Linux and have managed to get my 64 bit system running pretty well, and I can now access the root.  However, I can't seem to get my mozilla plugins installed!  Ive read some posts on other sites but they are little or no help.  The readme doc that was bundled with the plugins has instructions, and they don't work!
Also I've followed a couple sets of instructions i've seen for changing the splash screen, that won't work either.  Any insight would be greatly appreciated!

---

### Post by henriquemaia on 2006-06-01
Are you talking about gnome's splash screen or the boot splash?

---

### Post by Dr. Who on 2006-06-01
The Ubuntu Splash screen after login

---

### Post by Kilz on 2006-06-01
The problem may be a common one. You see Firefox in the amd version of Ubuntu is thew 64 bit firefox. Most of the media plugins like flash and java are 32 bit plugins and will not work with the 64 bit firefox. 
You can install a chroot system, basicly a 32 bit install inside your 64 bit system to run 32 bit applications. Its a pretty hard thing to setup. Here is a link to the howto [https://wiki.ubuntu.com/DebootstrapChroot?highlight=%28chroot%29](https://wiki.ubuntu.com/DebootstrapChroot?highlight=%28chroot%29)
You can also install a 32 bit Firefox without a chroot. Its not that hard and works real well with 64 bit Dapper. Here is a link to the howto on it. [https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava) This is the way I went.
The choice is up to you.

---

### Post by Dr. Who on 2006-06-01
Thanks for the insight!  That explains a lot.  As for microsoft, trust shouldn't even be used in the same sentence.

---

### Post by Kilz on 2006-06-01
:mrgreen:  Yes I totally agree, but they keep saying some garbage about some trusted computing platform, one that doesn't trust you.

---

### Post by fragos on 2006-06-01
[QUOTE=Kilz]The problem may be a common one. You see Firefox in the amd version of Ubuntu is thew 64 bit firefox. Most of the media plugins like flash and java are 32 bit plugins and will not work with the 64 bit firefox. 
You can install a chroot system, basicly a 32 bit install inside your 64 bit system to run 32 bit applications. Its a pretty hard thing to setup. Here is a link to the howto [https://wiki.ubuntu.com/DebootstrapChroot?highlight=%28chroot%29](https://wiki.ubuntu.com/DebootstrapChroot?highlight=%28chroot%29)
You can also install a 32 bit Firefox without a chroot. Its not that hard and works real well with 64 bit Dapper. Here is a link to the howto on it. [https://wiki.ubuntu.com/FirefoxAMD64FlashJava](https://wiki.ubuntu.com/FirefoxAMD64FlashJava) This is the way I went.
The choice is up to you.[/QUOTE]
I'm experimenting with something called nspluginwrapper.  Its a beta and I've had troubled getting it running.  I've sent an email to the author asking for a little direction in return for an improved Readme/Howto.

---

### Post by Kilz on 2006-06-01
[QUOTE=fragos]I'm experimenting with something called nspluginwrapper.  Its a beta and I've had troubled getting it running.  I've sent an email to the author asking for a little direction in return for an improved Readme/Howto.[/QUOTE]
I tried that, didnt work as you said. Lets hope the author is still working on it.

---

### Post by henriquemaia on 2006-06-02
[quote=Dr. Who]The Ubuntu Splash screen after login[/quote]

Install the **gnome-art **package from synaptic. It will have an entry under System --> Preferences called Art Manager, which will give you an option to change the splash screen.

---

