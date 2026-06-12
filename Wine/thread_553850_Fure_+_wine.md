---
title: "Fure + wine"
date: 2007-09-18
forum: Wine
---

### Post by tcpip4lyfe on 2007-09-18
I downloaded the Fury Beta.  If you are not familiar with Fury, it's basically world of Warcraft that is only PVP. The install went ok but when I launch the game I get:

```
fixme:shdocvw:WebBrowser_get_ReadyState (0x13a238)->(0x34f91c) repeated over and over
```

Version .45.

Anyone have any sugestions?

---

### Post by cogadh on 2007-09-18
The "fixme" messages are usually just developer notes about what still needs to be finished in Wine and don't usually mean anything to users. However, a message like that would seem to indicate that the game is trying to make use of some web browser function that is not currently implemented in Wine. Is this a browser-based game?

---

### Post by tcpip4lyfe on 2007-09-18
I assume it is trying to open a browser to check for update for the game. The game itself is D3D based on directX 9 so I would assume that it is theoretically possible to get it working.  I installed IE6 to see if that would help but it still does the same thing.  Im currently installing it in VMware XP to see if I can just move the files over to wine.

---

### Post by cogadh on 2007-09-18
Silly question, have you installed the Gecko HTML engine in Wine yet? That might allow it to pull the update (if that is what it is trying to do).

---

### Post by tcpip4lyfe on 2007-09-18
> **cogadh said:**
> Silly question, have you installed the Gecko HTML engine in Wine yet? That might allow it to pull the update (if that is what it is trying to do).

Yep did that already.  No errors on the install either.  Still waiting for XP to install......

---

### Post by merlyn on 2007-12-02
Hi,

This selection from the wine database is interesting.

> 
              [SIZE=3]**Selected test results**[/SIZE]
    
  **What works**
Installer     

**What does not**
The game uses a browser to login and patch but cannot find Internet Explorer so it goes into an endless loop. 

**What was not tested**
The game itself 

**Additional Comments**
Does not run due to not being able to find Internet Explorer.Which implies that all being equal the game ought to run with IE6, installed.

Having said that I had IE6 installed under Wine, for browsing certain sites sites such as my workplace online training, with mixed results.

What's even more interesting about this, it that in a recent promo, Auran recommend **not to use **IE for downloading the client as it does not handle large files very well.

Also just found this entry on the Fury forums regarding patching.

> [B][SIZE=3]Patching Problems[/SIZE]

Solution[/B]

Due to the way in which Internet Browsers helpfully caches files for you, semi-complete patch files can be cached by your system. This can lead to the patch utility trying to use a corrupt or incomplete file. If you're having trouble, please try these steps:

1. Reboot your machine and login.
2. Deactivate any Personal Firewalls and AntiVirus software you have.
3. (Internet Explorer) Open Internet Explorer, click Options->Tools and press the "Delete Files.." button and the "Delete Cookies" button in the "Temporary Internet Files" section. Click "Clear History" button. Click OK.
3. (Firefox) Open Firefox Browser, click "Tools" -> "Options". Goto "Privacy" and press the "Clear Now..." button.
4. Close Your Browser.
5. Reboot your machine and login.
6. Click Start->Run.
7. Type in "%temp%" (without the quotes) and look for any of the Fury patch files (for example "26509_to_29516.zip" or "29504_to_29516.zip" - delete them.
8. Launch Fury.
9. Let the autopatcher start and download and install the full, correct, patch!So it would appear that Firefox is able to access the patching system, at least under Windows anyway.

Cheers.

---

