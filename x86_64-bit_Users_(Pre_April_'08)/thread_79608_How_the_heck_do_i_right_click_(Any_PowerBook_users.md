---
title: "How the heck do i right click? (Any PowerBook users out there?)"
date: 2005-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by amanda on 2005-10-20
I'm having all kinds of keyboard adjustment issues on my PowerBook* with Breezy Badger, and I can work with those (maybe. I really want command  and control switched--the keyboard only has one control key but it has two command keys and I'm used to using both of them) but what is driving me nuts is that I can't figure out how to right-click without plugging in an external mouse.

control-click is the right-click functionality on the Mac OS. Is there a built-in key combo that will add "right" to my touchpad taps? If not, how do I add it?

* and since it seems to be a popular question, just trust me, I installed ubuntu because I want to use Linux, for the sake of using Linux. I have other reasons, very good ones, but I am not really interested in debating the merits of Linux vis a vis OSX.

---

### Post by thalavoy on 2005-10-20
Press F11 (middle) or F12 (right) click.

Siva

---

### Post by AikenDrum on 2005-10-21
Hi Amanda,   I noted this down when I set mine g3500 ibook up...  i used the apple  key as my right click...

** Setup left Click mouse function to apple keys (default with ubuntu is F12 -  miles away !)
sudo showkey - then press the keys you want to find the scancode for. *eg - apple key = 0x7d = 125decimal
sudo nano /etc/sysctl.conf
change the MouseButton2 entry to the code you want for left click.
reboot.

Cheers - Scott.

---

### Post by amanda on 2005-10-21
Thanks for the tips. f11 and f12 ... was I supposed to find that someplace? Actually when I started with OSX I was totally frustrated by the right click. I think I was at a party, drink in hand, complaining about my trackpad when someone said "oh, just control-click" so I suppose I didn't exactly find that in straightforward documentation either.

I like my labelled function keys (eject, volume up, volume down, mute) the way they are, so I'll try out remapping the right click to another key.

While we are here, though, Scott are you saying that I shouldn't just use the keyboard GUI? And/or are you saying that I could maybe just switch my apple and control keys instead of remapping all control functions to command?

---

### Post by AikenDrum on 2005-10-23
Hey Amanda, 

Sorry - I've come at this iBook of mine from an linux/intel -> linux/ppc point of view.  I never used Mac OS at all.  Which means I just used that little sysctl change to remap mouse button 2 to the apple keys (they both scan the same code to the OS)   So the Trackpad Button is Mouse1,  and either apple key is Mouse2,   rather than Mouse2 being a result of Apple key + Trackpad button. (I'm not sure how you'd set that up....   )

So .. not sure if I've helped  a little,  or just led you up the garden path :)   

Cheers !

---

### Post by bhilton on 2006-08-08
Hi all, I remapped my apple keys to be right click.  Here's how I did it.

sudo nano /etc/sysctl.conf

Change the keycode on the line that contains "button3" from "88" to "125".

Save the file and reboot.


Here's how mine looks now.

# Emulate the middle mouse button with F11 and the right with F12.
dev/mac_hid/mouse_button_emulation = 1
dev/mac_hid/mouse_button2_keycode = 87
#dev/mac_hid/mouse_button3_keycode = 88
dev/mac_hid/mouse_button3_keycode = 125


If you would rather use the alt key, the code is 56.

I'm using an ibook g3 500 running xubuntu, but I think it should work on Ubuntu as well.  This may not work on other systems, but it may be worth a try.  If 125 isn't the correct keycode for your system, have a look at xev or showkey to get the correct code.

Brad

---

