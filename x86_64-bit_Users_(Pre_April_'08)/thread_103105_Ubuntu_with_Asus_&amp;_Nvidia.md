---
title: "Ubuntu with Asus &amp; Nvidia"
date: 2005-12-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Newb64 on 2005-12-13
I have assembled my own PC for the sole purpose of teaching myself Linux.  I have an Asus A8v-e Deluxe motherboard and an Nvidia 6600GT graphics engine in my box and both seem to dislike Linux in general.  I have installed Ubuntu 5.04, Mandrake 10.0, and at least one version of Suse to attempt to get all of my hardware working.  I have now installed Ubuntu 5.10 in hopes that the hardware support I need would be included - NOT!  At first I was worried that I had a hardware problem with the board.  The reason for my concern was that I had two problems...I couldn't get the graphics hardware working and I couldn't get any of the network hardware working.  This board has both hard-wired networking and wireless.  Neither function with Ubuntu.  So, for lack of understanding in the Linux world, I installed Windows XP.  Initially, neither the networking nor the graphics was detected.  Only through Windows, Nvidia and Asus updates was I able to get all of my hardware working.  So, now I know it all works.  I would like to get Linux working and believe that the first thing I need functioning is the networking just so I can download any Linux patches or code I may need for the other stuff.  Can somebody point me in the right direction?  Oh, I know that the LAN stuff, maybe wireless is on a Marvell chip.

---

### Post by teaker1s on 2005-12-13
nvidia are generally well supported in linux and wireless is done with 'ndiswapper'
which if you search with synaptic
terminal
'sudo synaptic' you can install

 look here for more help
[https://wiki.ubuntu.com/CommonProblems?highlight=%28problems%29%7C%28common%29](https://wiki.ubuntu.com/CommonProblems?highlight=%28problems%29%7C%28common%29)

---

### Post by Suger on 2005-12-14
The ndiswrapper in synaptic is a little outdated and won't support some recent cards (like my Inprocomm 2200), for which you have to download a more recent version. Can't you plug in an ethernet cable somewhere ?

---

### Post by Zonkle on 2005-12-14
How do you know that the Networking is not working?

Try to go to Administration -> Networking, and look for the ethernet and make sure that it is Activated! In your installation for Ubuntu, it asks you for the Network configurations, and if you pressed on "Not Right now", it will be Deactivaited until you activaite it again and make the configurations.

Cya ;)

---

### Post by Newb64 on 2005-12-18
I didn't give enough info in my question so let me continue.  The network doesn't work because there is an error during install.  The install doesn't detect any network hardware even though it is onboard.  When I have used the sudo command and attempted to install the Nvidia drivers I get another error which I can't remember at the moment but am going to go back and see if I can't recreate.  For the Nvidia driver, it goes part way through the install and then hangs on something about not having a c.lib file or something.  I will go back and try again.  By the way, I do have access to both wired and wireless network but if the machine doesn't know that it has the hardware, then it really doesn't matter if it is plugged in or not.  Heck, Windows didn't recognize the network hardware until I installed a patch from Asus.

---

### Post by brenick on 2005-12-20
I'm using an ASUS A8V-E SE with a Geforce 6600 and it is working OK. This is a new computer for me too.  I presume you have the onboard ethernet enabled in the BIOS. You also might try running Ubuntu live which worked great for me.

I am going to switch to the Nvidia driver for the graphics card as I do get a display problem after a short time running Ubuntu.

---

