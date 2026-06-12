---
title: "Touchpad"
date: 2005-11-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Axios on 2005-11-08
Hi

The touchpad on my iBook 12" 1,2 Ghz G4 works fine, just wondering how to right click, or even how do the middle click?

When i runned OSX on it, i had a driver, so that when I used to fingers, it would scroll down and sideways, is this possibly to get running in Ubuntu also?

Another thing, is there and option to disable the touchpad when I plug in a mouse? I had this setup in OSX, so that when I plugged in my mouse it automaticly disabled my touchpad, this was really neat, because when Im using the keyboard I sometimes stroke the touchpad. This isn't as mouch a problem since I cant tap the touchpad in Ubuntu either.


I am really impressed with Ubuntu PPC.

---

### Post by yeti on 2005-12-03
Im having trouble with this too... more just how to get right/middle click, so if anyone can point us in the right direction that would be great.

---

### Post by er-ku on 2005-12-04
[oops... sorry for double posting]

---

### Post by er-ku on 2005-12-04
Hello,

[QUOTE=Axios]The touchpad on my iBook 12" 1,2 Ghz G4 works fine, just wondering how to right click, or even how do the middle click?[/QUOTE]

By default in Ubuntu, you use F11 and F12 keys for middle/right click.

That's incomfortable however, so i'd suggest you to connect an USB mouse to your laptop. :)

[QUOTE=Axios]When i runned OSX on it, i had a driver, so that when I used to fingers, it would scroll down and sideways, is this possibly to get running in Ubuntu also?[/QUOTE]

You may give [GSynaptics](http://gsynaptics.sourceforge.jp/) a try. I haven't tried it on a PowerPC though.

[QUOTE=Axios]Another thing, is there and option to disable the touchpad when I plug in a mouse? I had this setup in OSX, so that when I plugged in my mouse it automaticly disabled my touchpad, this was really neat, because when Im using the keyboard I sometimes stroke the touchpad. This isn't as mouch a problem since I cant tap the touchpad in Ubuntu either.[/QUOTE]

This should be possible, but I don't know HOW to do that. Someone should probably write a Wiki how-to on how to do that. ;)

---

### Post by Axios on 2005-12-05
There isn't a .deb for ubuntu ppc :(

---

### Post by hentaidan on 2005-12-05
[QUOTE=Axios]This isn't as mouch a problem since I cant tap the touchpad in Ubuntu either.[/QUOTE]

Do you mean that you can't "tap to click" with the touchpad? Can you still use the mouse button? If so I (and others) would greatly appreciate how you managed it!

On my ibook I use the apple keys as right click, and the enter (the one to the right of the right apple key) as middle click, or apple key + mouse button.

If you want to remap your keyboard you can use xmodmap; there should be a post further down about how to use it in conjuction with xev, or take a look at the man page for both.

---

### Post by yeti on 2005-12-05
I found this on another thread ([http://ubuntuforums.org/showpost.php?p=431865&postcount=3](http://ubuntuforums.org/showpost.php?p=431865&postcount=3))

```
Hi Amanda, I noted this down when I set mine g3500 ibook up... i used the apple key as my right click...

** Setup left Click mouse function to apple keys (default with ubuntu is F12 - miles away !)
sudo showkey - then press the keys you want to find the scancode for. *eg - apple key = 0x7d = 125decimal
sudo nano /etc/sysctl.conf
change the MouseButton2 entry to the code you want for left click.
reboot.

Cheers - Scott.
```

Only I found that to change the right click to the apple keys that I had to use the MouseButton3 field.

---

