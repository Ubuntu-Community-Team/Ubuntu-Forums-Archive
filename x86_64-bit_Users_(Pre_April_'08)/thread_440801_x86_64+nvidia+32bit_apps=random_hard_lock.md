---
title: "x86_64+nvidia+32bit_apps=random hard lock"
date: 2007-05-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by ectospasm on 2007-05-12
I get random hard locks when I run 32bit applications.  For instance, the latest time it happened to me shortly after I used Adobe Flash in 32bit Firefox.  The system completely froze--no mouse movement, the speakers emitted this high pitched, monotonous squeal, magic sysreq key did nothing, and my machine disappeared from the network.  I don't say this is purely an Ubuntu problem;  I had been using Gentoo for years, and had it happen to me several times there, too.  I had hoped that it was just some weird combination of libraries or something, but it followed me to Feisty.  Some of the applications I've been using when this happens include Firefox (both 32bit and 64bit, the latter with using nspluginwrapper or whatever it's called so I can use Flash), 32bit OpenOffice.org, VMWare Server, and 3D games and screensavers.

My guess is it has to do something with the binary-only nvidia X driver.   My next step is to use the open source nv driver, which isn't intimately tied into the kernel like nvidia.  Every time I hear that nvidia has fixed crashes and hard locks in their latest driver, it happens to me again.  

I'm posting this to see if anyone has had similar problems.  It may just be an overheating problem that doesn't occur unless I'm running a 32bit program in a 64bit OS;  I may just need to clean the dust out of my 4yr-old box.

---

### Post by ectospasm on 2007-05-12
As it stands, the nv driver doesn't work.  It gave me a blank screen when gdm started, and it even messed up the text on the virtual consoles.  Right now I'm stuck with nvidia.

Any ideas?

---

### Post by Crypto-138 on 2007-05-12
Something similar happens to me too.
It only happens after I suspend and resume Ubuntu, and then use firefox32.

I'm using the Official Nvidia Driver from the repositories, and it freezes even though I already followed [this tutorial.]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend")

I can move the mouse, but nothing else (not even clicks) respond. I'm thinking it has something to do with how the Kernel handles the modules; this never happened to me before upgrading... =/

---

### Post by ectospasm on 2007-05-12
My problem is a bit different, in that nothing is responsive, not even the mouse.  I can't ssh into, or even ping, the machine from another PC on the LAN.  I'd check to see if you can ssh into the machine;  you may be able to kill X from a console.   Of course, to do that, you'd have to install and enable OpenSSH.

---

