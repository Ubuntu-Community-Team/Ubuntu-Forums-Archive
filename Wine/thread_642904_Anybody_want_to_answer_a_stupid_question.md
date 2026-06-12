---
title: "Anybody want to answer a stupid question?"
date: 2007-12-17
forum: Wine
---

### Post by natebenn on 2007-12-17
I am following a guide from Linux-gamers.net on how to install steam and successively tf2 on Ubuntu 7.04. I am a total noob so progress is slow but that's to be expected. I have the steam.msi sitting on my desktop now but everytime I enter 

"wine msiexec /i SteamInstall.msi"

I get a popup that says

"The specified installation package could not be opened. Please check the file path and try again."

It seems like there is a simple solution but I don't have a good enough understanding of Linux yet to figure it out. Anybody know how to remedy this? Thanks a million!

---

### Post by jken146 on 2007-12-17
Are you sure it should be '/i'?  '-i' is the usual way of specifying an option i for a command, and I'd expect /i to be the path to the file called i, which is located in the root directory (this file probably doesn't exist, which would be the problem).

---

### Post by natebenn on 2007-12-17
That makes sense. How do I find what the path to the steam file is? It's on my desktop but I still don't understand the structure of linux so it makes it hard to figure out the path.

---

### Post by jken146 on 2007-12-17
OK, all your personal files are stored in /home/yourusername and /home/yourusername/Desktop is where the desktop is.  Note that Linux file names are case-sensitive.

---

### Post by jken146 on 2007-12-17
> **natebenn said:**
> wine msiexec /i SteamInstall.msi"


You need to change directory (command: cd) to the directory where your .msi file is (in this case the desktop). ```
cd ~/Desktop
```

By the way, ~/ means "my home directory".

---

### Post by natebenn on 2007-12-17
Alright I'll have to give that a shot when I get home. Thanks for the direction!

---

### Post by natebenn on 2007-12-17
Ok so if I understand it all here is what I do and what happens.
Open terminal and punch in "wine msiexec cd ~/Desktop Steaminstall.msi"

I've tried that but I get a paragraph or so in the terminal that tries to explain usable commands for installing programs, most of which is still greek to me. Am I entering it into the terminal incorrectly?

---

### Post by isaacj87 on 2007-12-17
Hey,

I just tried it doing this...

1) Save SteamInstall.msi to your desktop.

2) Right click the file and choose "Open with other application"

3) When the new window opens, theres something at the very bottom that says "Use a Custom Command." Click that and a text field will appear. Copy and paste this.
```

wine msiexec /i 

```

4) Click open and you're done.

---

### Post by natebenn on 2007-12-17
Freakin SWEEEET! You are the man!! Dang it doesn't get any easier than that! I'm entirely speechless, I just didn't think I was ever gonna figure things out. Thanks to both of you guys for all of your input. I'm sure you'll be hearing from you around the forums again. :) Have a great on, I'm on my way to Steam and TF2!!! :) :)

---

### Post by isaacj87 on 2007-12-17
> **natebenn said:**
> Freakin SWEEEET! You are the man!! Dang it doesn't get any easier than that! I'm entirely speechless, I just didn't think I was ever gonna figure things out. Thanks to both of you guys for all of your input. I'm sure you'll be hearing from you around the forums again. :) Have a great on, I'm on my way to Steam and TF2!!! :) :)

No Problem man! Glad to hear it installed. Just let me know if you have any problems with the update thing getting stuck at 26%. I just figured out a workaround for it...

---

### Post by natebenn on 2007-12-17
well you called it...26% on the button and it quits. :rolleyes:What is the next step?

** Nevermind, got it working**

New question though.... :) All the guides to installing Valve games I've seen somewhere involve the use of the cds to install. I don't have any cds, I've always downloaded the games within steam and installed them from there; is that still possible or is there going to be a trick to doing this? Thanks again, it's so greatly appreciated.

---

### Post by aoanla on 2007-12-19
Yes, it is quite possible to install within Steam using Wine. 
All of my Steam games were installed this way.

---

