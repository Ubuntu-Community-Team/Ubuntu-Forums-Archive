---
title: "Gutsy successfully installed on AMD64"
date: 2007-06-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by aikishugyo on 2007-06-14
I'm delighted to state that I could upgrade to Gutsy successfully. My motivations were that I could not get TexLive integrated into Feisty, and managed to damage my initramfs while trying to resolve dependencies from Sanjoy Mahajan's backporting attempts which are really for Edgy IIRC. Here my steps.

0. Boot up on Debian partition (or liveCD) and  copy existing system Feisty /home and /etc to backup (my Debian partition in this case).

1. Install bare Feisty system over broken one, and get network and X working as before. Of course, you can merely use the Gutsy CD if you have one, but I am testing the upgrade here. My X server uses nVidia modules.

2. Download Gutsy liveCD image and burn to CD in case upgrade fails.

3. Add Gutsy restricted and main repositories to /etc/apt/sources.list

4. Install new Gutsy linux-image-2.6.22-6-generic and headers. This brings in the libc6 and a few other dependencies.

5. Reboot into new linux-image. No X server since restricted modules aren't installed yet. Install those, along with ubuntu-restricted-extras which pulls in a load of other stuff including Sun's Jave 6.

6. Reboot and find X working hopefully :-) Edit synaptic preferences to prefer gutsy, remove /etc/apt/preferences (in my case), and do an upgrade. For me this downloaded 228MB and eventually freed 56MB.

7. Reboot system again, add Gutsy universe and multiverse to repositories and do another upgrade. This one fetched 114MB and left 247 packaged not upgraded.

8. Now I did dist-upgrade and this upgraded the 247 packages, downloading 719MB and installing 81 new packages. It also removed a dozen or so. Wait several hours... Among the goodies that will install here are ghostscript 8.60, cups 1.2.11, xpdf 3.0.2, gimp 2.3.16, openoffice 2.2.1~rc3, scilab 4.1.1 and of course, finally, the full TexLive 2007. Fantastic! Also an emacs-snapshot-gtk from 29 May 2007 (the one in Feisty is from 18 December 2006).

9. Another reboot because there happened to be another linux-image upgrade in there. Then make sure ubuntu-desktop is there with its dependencies. I also added Gutsy backports and proposed updates to synaptic's preferences, and installed keychain which had somehow gotten lost.

10. Reboot to make sure it all works. Indeed it does. Thank you Ubuntu, this release looks like it will transcend anything done before. After checking that cups still does its stuff, I have to say that it absolutely rocks.

---

### Post by Kilz on 2007-06-14
Sounds great, 
BUT
You do realize that 
1. Gutsy is still in Alpha testing. It is nowhere near good enough for most users in terms of stability. 
2. That updates will break things , and no one will have the slightest clue how to fix it , except in the Gutsy section. Where they might blame that you have the 64bit version for the problem without any clue as to whats actualy wrong.
3. Because of #2 you are going to have to look and check what each and every update does. Making sure that by installing one new package it isnt going to remove your x11 config for example.

Other readers reading your post should think about it(newbies should run the other way). If someone just wants to test Gutsy, I would recommend a virtual machine. That way your main install stays safe.

But its nice to hear that it is in at least an installable state.

---

