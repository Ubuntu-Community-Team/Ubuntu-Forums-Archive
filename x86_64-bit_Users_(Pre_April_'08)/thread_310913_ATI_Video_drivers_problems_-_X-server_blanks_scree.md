---
title: "ATI Video drivers problems - X-server blanks screen upon shotdown"
date: 2006-12-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by nikdo on 2006-12-02
Hello you all wonderful ubuntu/linux folks.

I was hoping you could help me with this one, I've been working on it on and off for past 2 weeks:

setup:

- Gateway machine, AMD 64bit dual core, 2Gig ram
- HP w19b 1440x900 wide screen LCD
- on board nvidia (can't remember which one)
- added PCI express ATI Radeon X800 XL 256Mb video card
- running Ubuntu Edgy Eft 6.10 64bit

When running with the ATI board, then one serious problem I have is that I cannot really shut down. When I try, screen goes blank, but no shutdown has been initiated. Need to actually power off the machine. Same problem happens if I try to go to console from x-server ALT+F1...F6. System is blank and I can't even go back to x-server or reset or anything else.
Tried 'vanilla' install of ubuntu 6.10 64bit and ubuntu 6.06 64bit. Installed the ATI drivers via apt-get. The drivers seem to work fine and even the glx gears worked. Not sure if the problem is related to the combination of ATI drivers + 64bit ubuntu. Can't seem to find an answer anywhere.


As an alternative, I have removed the ATI board, reinstalled ubuntu 6.10 64bit and installed the nvidia drivers via apt-get. Strangely enough, when I run the x-server after that, I have two problems: 

1) can't get the proper resolution, even though I specified it in xorg.conf as 1440x900
2) can't get to see the mouse cursor. IT is weird, because the mouse works (you can see it activating on mouse-over events on buttons, etc, but can't see the actual cursor.

If I switch the driver to vesa or to nv, then I get the cursor, but the resolution drops to 640x480 and can't get it higher - despite my settings of 1440x900 in xorg.cong - (and of course the screen is not accelerated and just scrolling the web pages is slow as molasses). There is a mention in the console that the mouse pointer failed.

[If you require any output from some logs, please let me know the commands, thank you.]

I am sorry if I posted in the wrong forum, I am not sure if this is a 64bit problem or just video drivers one. I am quite new at using linux and would appreciate any help as I refuse to give up and return to windows - I have tasted the freedom and don't want to be caged again.

Thank you sincerely for all your help

Peter

---

### Post by The other One on 2007-04-11
Hi Nikdo,

Not sure if you've solved your shutdown problem yet, but I had the same issue and found the answer in [http://ubuntuforums.org/showthread.php?t=397252]("http://ubuntuforums.org/showthread.php?t=397252")

---

