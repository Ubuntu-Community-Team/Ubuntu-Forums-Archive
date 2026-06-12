---
title: "Real Arcade question"
date: 2008-04-02
forum: Wine
---

### Post by Twitch6000 on 2008-04-02
Well I was thinking of getting my grandparents,yes grandparents on a Linux machine,they don't use windows to much anyways.

Only problem I could see is there gaming thing(wow they play games lol)it is real arcade.

They have 6 games two have alternatives on Linux but,that will not make them happy :/.

So the question is can real arcade somehow work on wine or does it now have a Linux version?

I mean any other ''REAL'' program has a Linux version :(.

I was thinking about putting them on (k)ubuntu or Linux mint btw.(their ram is 512mb :/)

---

### Post by Twitch6000 on 2008-04-02
bump

---

### Post by Twitch6000 on 2008-04-04
bump

---

### Post by Brynster on 2008-04-04
to thwe best of my knowledge i don't think real arcade will work in Linux.

if you go to winehq.org and browse through the appdb section that may cast some light for you.

Sorry i cannot be more helpful than this...

---

### Post by Twitch6000 on 2008-04-04
I can't seem to find it on the wine list any link please >.>?

---

### Post by Stunts on 2008-04-04
Hi!
I'm not sure this is what you are looking for:
MAME
It's got a windows version and the source code. Their website has a lot of ROM's too.
Is you are able to compile it on your grandparent's box that's great.
Have a look and let me know what you think.

[http://mamedev.org/about.html](http://mamedev.org/about.html)

---

### Post by Twitch6000 on 2008-04-04
No I just need some way for Real Arcade to be on a Linux machine for them.

---

### Post by FrozenFox on 2008-04-05
Why not just set up a small partition (5 gb or so perhaps, giving ~3 gigs for ubuntu and however much you need for said games id guess at ~2 gigs) on their machine and install it, then install wine and try to run said games in wine? There's no native version, and since you can't find it on winehq, the only way to know if it works is doing just that. It only takes about half an hour to do all of the above combined if you know what you're doing to some degree (well, the ubuntu side. defragmenting windows prior to resizing its partition would take some time) . Then simply remove windows and resize the ubuntu partition if it works (or start from scratch and tell ubuntu to format the drive). If it doesnt work, remove the ubuntu partition and resize the windows one to take the space back and remove grub if you want via fixmbr or whatnot on the windows repair cd (or just set grub's timer to 0, remove the ubuntu entry, and default it to windows, if you dont want to bother doing that).

---

### Post by Shockwav on 2008-05-05
I'd feel better if someone could verify this, your mileage may vary, some contents may have settled during shipping.

I have got this "working" in wine. (Not all games work, sound and or video issues in others, most work ok.)

:shock: {I didn't just say that did I}

Here's what I did. (Hardy)
You must have a Gamepass ID
1. Wine settings - WinXP, Virtual Desktop 1024x768
2. Download and install Firefox Win32 edition into wine.
3. Copy the Program files\Real folder from a windows partition into the wine c_drive
4. Find the installer for real arcade and run it. You cannot log in, don't bother. Just let it install.
5. Open Firefox(Win32) and go to realarcade.com and log in. Go to my games/downloads and re-download a game that you own.
6. Firefox will ask you what you want to do, choose "open with real arcade"

- Sometimes it will seem to get unresponsive during the logon process, hit Go a few times to shake it loose.
-  Let the game load in RA and play as normal.

The trick seems to be passing the logon cookie to RA from FF withing the Wine environment. Lemme know if it works. Please post any additional tips or tweaks here as well.

---

### Post by samstern on 2008-05-10
Hi All,

I have been using Real Arcade for several years now. How can I get the real arcade downland to work? every time I try to run the stub down loader, real arcade_r1home_stub.exe it fails to connect to the internet. Do you know where on my windows drive I can find the actual installer?

TIA

Sam S.

---

### Post by samstern on 2008-05-10
> **samstern said:**
> Hi All,

I have been using Real Arcade for several years now. How can I get the real arcade downland to work? every time I try to run the stub down loader, real arcade_r1home_stub.exe it fails to connect to the internet. Do you know where on my windows drive I can find the actual installer?

TIA

Sam S.

AFter doing some poking about in a vmware image, I found the file RealOneArcadeBundle.exe located at

C:\Documents and Settings\samstern\Local Settings\Temp\__ArcadeDownloadFoler__realarcade_EN_emoh1r

can be transfered to the linux system. NExt, locate C:\My Download Files for all your games or redownload (using standard firefox) them from the website.


I took the following steps to get this all working:

1) wineprefixcreate
2) wine iexplore.exe [www.google.com]("http://www.google.com")
3) now install windows firefox, java, flash, shockwave and quicktime (some games need quicktime!).
4) now make a desktop shortcut  -- wine "c:\\Program Files\\FireFox\\Firefox.exe"

okies. we are now set. You now have a Desktop Shortcut to start Windows Firefox, the real acrade full installer and your games.

1) wine RealOneArcadeBundle.exe
1a)when it says "wait while accessing your account" use the "x" to close that window.
2) now LEAVE REAL ARCADE RUNNING!!!
3) using firefox and "Open File" open each .rgs file and let it run in real arcade. each will install. If the install seems to have paused, move the installer window with your mouse. 

NB: Real Arcade itself cannot download or install games. You need to use Windows Firefox under wine to get the games to install. making a file association in linux to real arcade for rgs files does not work reliably.

This is my first go with this so my instructions will change as I get a better handle on how to always get this working :>

---

### Post by suhaw on 2008-11-23
For some games, the easier way might be to bypass Real Arcade altogether and get Wine to run the game exe directly.  Tried it yesterday and got it to work for Gem Shop and Diner Dash, but not for Chainz.

---

