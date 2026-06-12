---
title: "Breezy update nightmare"
date: 2005-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by teripittman on 2005-11-20
I've been using Hoary on a Mac G3 for awhile now and been happy with it. Decided to upgrade. Now the upgrade seemed to go well enough. But here are the list of things that don't work right any more (and granted some of these may be Gnome issues).

My SupraExpress modem does not terminate correctly any more. The only way I can connect again is to reboot the computer. It seems like it turns off, but must not be delivering the correct commands to shut it down properly.

My mouse now needs three clicks to get anything to activate. This is a Logitech trackball. Was working fine in Hoary but is a pain to use now.

I was set up to sync my Palm on /dev/ttyUSB1. That setting has disappeared and I can't sync any more. Yes, I can dig around on the Net again and try to figure out how to set that up again. But why did it have to blow that port away in the first place?

I have been happily spreading the word about ubuntu, as it seemed like the first distro to work out of the box. Now it looks like I have at least several frustrating hours ahead of me to get the basics to work right again. I wish I could just roll the whole thing back to hoary. At least things worked like they should.

Can anyone save me a little pain here and give me some idea of a fix for this? I've already had to reboot the computer several times after trying to shut down my modem connection and don't have a lot of patience left for Google searches.

---

### Post by teripittman on 2005-11-20
Quick update: I fixed the problem with Palm sync using the info here: [http://pilot-link.org/README.usb](http://pilot-link.org/README.usb) One down, two more to go. I may try swapping over to a mouse to see if that fixes the mouse issue. But that still leaves me with the ugly modem issue. Any fixes for that would be welcome.

---

### Post by ssam on 2005-11-21
reconfiguring xorg may fix the mouse. i think the command is
```
sudo dpkg-reconfigure xserver-xorg
```.

did you have to do anything to get the modem to work with hoary?

---

### Post by teripittman on 2005-11-21
I didn't have to do anything special with the modem, as far as I can remember. I tried to take notes from the install, but don't see anything about the modem. It detects it and dials out okay. It doesn't seem to be sending the correct termination command. Sometimes, it shows the modem deactivated and the modem "on" light is still lit. Other times, the light does go out but I can't dial back out again. Using the network config tool and autodetect shows that the modem is busy. I can disconnect the phone line and get the modem to drop off but I still can't dial back out. 

Modems and linux have been a problem for me ever since I started playing around with it. I couldn't get any of the Windows based linux distros to work on our PC due to this. It's just frustrating to know that it was working okay in the last version and somehow doesn't work in this one. I have been using the Gnome modem applet, by the way, but I see the same behavior if I activate and deactivate from the Admin network tool. And neither tool gives you a list of modems to choose from, or any way to script the one that you are using. 

Thanks for the help with the mouse and I'll post my results here too.

---

### Post by teripittman on 2005-11-22
This seems to have helped with the mouse problem. Thanks! I tried running pppdconf (think that's the right program). The modem still seems to be hanging. I seem to have better luck activating from the networking module than from the Gnome modem applet. So I may just have to chalk this up as a Gnome issue and just not use that applet any more (at least for activation.) Gotta be a better fix out there somewhere.

---

### Post by ssam on 2005-11-22
is this a 56k dial up modem? (some people are calling the broadband things modems, but they arn't really).

have you tried using wvdial? there is a basic set up instruction at [http://www.tldp.org/HOWTO/PPP-HOWTO/x314.html](http://www.tldp.org/HOWTO/PPP-HOWTO/x314.html) and google will find you many more.
```
man wvdial
```
also has lots of info.

---

### Post by teripittman on 2005-11-26
Nope, it's an old supra express external modem. Thought I should give an update. Came home after the holiday to find that the Mac wouldn't even boot into Mac OS. Just wouldn't even bring up the smiling computer. Tried a different hard drive with the same result. So I swapped things over to another G3. That one gave me the brown screen of death 3 times then finally boot into Ubuntu. The most interesting thing is that I now have a 1024 resolution! I'd tried the fix before and it wouldn't work. It does on this G3. I also swapped out the modem and keyboard, which fixed the modem issues. I am still having a problem with disappearing ttyUSB ports, but can recreate them and have them work again. Don't know why that one is happening either.

Things seem to be working and most of my problems seem to be hardware related. So I'll hack around and see if I can't fix the last few issues. Thanks for all your help!

---

