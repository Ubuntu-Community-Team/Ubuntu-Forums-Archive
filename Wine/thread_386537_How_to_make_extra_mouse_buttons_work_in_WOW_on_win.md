---
title: "How to make extra mouse buttons work in WOW on wine?"
date: 2007-03-17
forum: Wine
---

### Post by tcollogne on 2007-03-17
Hello

I am trying to play WOW on Kubuntu, and it works fine. Only thing is that I am used to
use the two side buttons on my mouse in WOW.

I have succeeded in enabling the buttons for firefox, but that is the only application where it works.

Is it possible to enable them for gaming? And if so, how?

Thank you.

---

### Post by lakersforce on 2007-03-17
Yes, I have the same problem...actually I would like to hear if any users have actually ever managed to "circumvent" this "bug". I tried to read through the *HOWTO: WoW on WINE* but it does not seem to contain an answer to this.
Of course you can just use numlock, which I think most of us have gotten used to. But anyway, it would be nice to hear if anyone at all have made it work!!

---

### Post by hikaricore on 2007-03-17
I've seen howtos somewhere about mouse buttons but I forget where.

Here might be a better place to start your search tho:

[http://appdb.winehq.org/appview.php?iVersionId=6482](http://appdb.winehq.org/appview.php?iVersionId=6482)

I'm sure someone else has asked this even possibly solved it.  I don't have time today to look around tho, thought I'd point you in the right direction.

---

### Post by ptesone on 2007-03-17
This guy has a great page with all kinds of fixes and howtos:
[http://www.cs.cornell.edu/~djm/ubuntu/]("http://www.cs.cornell.edu/~djm/ubuntu/")

the 5 button mouse one is here:
[http://www.cs.cornell.edu/~djm/ubuntu/#enable-5button-mouse]("http://www.cs.cornell.edu/~djm/ubuntu/#enable-5button-mouse")

hope it helps!

---

### Post by lakersforce on 2007-03-18
Great...and I have been using the numlock for almost a year :)

I added the 5 button mouse link to the "configuration" part of the WoW guide on the ubuntu wiki.

---

### Post by lakersforce on 2007-03-20
Well, the sidebuttons work, but after adding this a new problem emerged: when I try to quit or log out of WoW the game hangs and I can only quit it by doing a Ctrl+Alt+ Backspace. And then, of course, the sound keeps playing, so I will have to reboot the computer anyways...annoying. Is there anyway to kill the application and terminate the sound without a reboot?

---

### Post by hikaricore on 2007-03-20
> **lakersforce said:**
> Well, the sidebuttons work, but after adding this a new problem emerged: when I try to quit or log out of WoW the game hangs and I can only quit it by doing a Ctrl+Alt+ Backspace. And then, of course, the sound keeps playing, so I will have to reboot the computer anyways...annoying. Is there anyway to kill the application and terminate the sound without a reboot?

```

sudo killall wineserver
sudo killall WoW.exe

```

Should do the trick, don't know why it's hanging after adding mouse buttons, that's an odd one.

Also wine seems to multithread WoW.exe on my system so I just made a script that spams:

> sudo killall WoW.exe

and run it from a terminal about 5 times lol, it works when I need it :P

---

### Post by lakersforce on 2007-03-20
Seems like I was a little quick posting. WoW only hangs when I push the "exit game" button, and not when I log out. Anyway, the code you supplied in the post above works. And you were right about the spamming part: I had to run the command 13 times before I got a response.

---

### Post by hikaricore on 2007-03-20
You could write a better script to do it, something like this:

```

sudo killall wineserver
sleep 2
sudo killall WoW.exe
sleep 1
sudo killall WoW.exe
sleep 1
sudo killall WoW.exe
sleep 1
sudo killall WoW.exe
sleep 1
sudo killall WoW.exe
sleep 1
sudo killall WoW.exe
sleep 1
sudo killall WoW.exe
sleep 1
sudo killall WoW.exe
sleep 1
sudo killall WoW.exe
sleep 1
sudo killall WoW.exe
sleep 1
sudo killall WoW.exe
sleep 1
sudo killall WoW.exe
sleep 1
sudo killall WoW.exe
sleep 1
sudo killall WoW.exe

```

I've just been too lazy to care on my setup.  :)

It could be more refined and made to work in the background without the sleep commands with appropriately placed &&  characters or something.

---

### Post by greebothecat on 2008-06-17
reviving the thread, can't make those 5 buttons work, can't find any of the tutorials you provided earlier (they appear to be moved / deleted).

here's my xorg.conf part:
```
Section "InputDevice"
    Identifier     "Mouse1"
    Driver         "evdev"
    Option "vendor" "0x1241"
    Option "product" "0x1166"
    Option "Phys" "usb-*/input0"
    Option         "Protocol" "auto"
    Option         "ZAxisMapping" "4 5"
EndSection
```

---

### Post by lakersforce on 2008-08-14
You can find the page [[COLOR="DarkOrange"]**here**[/COLOR]]("http://web.archive.org/web/20070922164604rn_2/www.cs.cornell.edu/w8/~djm/ubuntu/feisty/")

Digging around I also found something on the [[COLOR="DarkOrange"]**Ubuntu wiki**[/COLOR]]("https://help.ubuntu.com/community/ManyButtonsMouseHowto")

---

