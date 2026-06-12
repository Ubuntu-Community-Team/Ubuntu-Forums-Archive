---
title: "playonlinux ie install hangs"
date: 2018-03-03
forum: Wine
---

### Post by JamButty on 2018-03-03
Internet Explorer is the main reason I still have a dual boot (some critical websites which run only there), so I wanted to try it via Wine. PlayonLinux seems like a friendly frontend so I installed that. Then
1. tried to install IE8 from playonlinux - it hung for 30 minutes before I canceled it.
2. Thinking it might be a 32/64 bit issue, looked into that, then used 
> WINEARCH=win32 winecfg to temporarily set it to a 32 bit environment and tried install again. Hung for 10 minutes.
3. I canceled it, saw the log near the end had problems with the font
> Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
I had seen all the traffic about fonts installation during the initial Playonlinux install, so that did not seem right. Rebooted.
4. next install attempt (with erase option, rebuilding 32bit virtual disk) did the same thing, with the same errors near end of log.

Suggestions? (64 bit native architecture running 17.10 artful)
thanks

---

### Post by Yellow Pasque on 2018-03-03
Do you have libfreetype6:i386 installed?

---

### Post by JamButty on 2018-03-04
yes?
> apt list --installed
got me this entry 
> libfreetype6/artful-updates,artful-security,now 2.8-0.2ubuntu2.1 amd64 [installed,automatic]
the only "i386" reference is 
> wine32/artful,now 2.0.2-2ubuntu1 i386 [installed,automatic]
but when I tried to install that I got 
> libfreetype6:i386 is already the newest version (2.8-0.2ubuntu2.1).
so it looks like I already had it.

---

### Post by dragonfly41 on 2018-03-04
An alternative approach you might consider is to install Windows in a virtual machine in VirtualBox on Ubuntu.

[https://stackoverflow.com/questions/3701484/how-to-test-in-ie-with-linux](https://stackoverflow.com/questions/3701484/how-to-test-in-ie-with-linux)[https://stackoverflow.com/questions/3701484/how-to-test-in-ie-with-linux](https://stackoverflow.com/questions/3701484/how-to-test-in-ie-with-linux)

and see one link in that discussion for IE8 testing ...
[URL="https://https://developer.microsoft.com/en-us/microsoft-edge/"]
https://developer.microsoft.com/en-us/microsoft-edge/[/URL]

---

### Post by JamButty on 2018-03-04
Yes, that is a possibility. Maintaining the dual boot is a lot easier. My hope would be to eliminate as much reliance on Windows as possible and the Wine approach seems the most minimal and simple. I  have read of so many headaches with Wine, I was hoping the playonlinux had dummy-proofed it for n00bs like myself. I am not a gamer nor are MS products like WORD etc. necessary to me. If it weren't for poorly designed websites that only follow IE standards, I could jettison it entirely. 
I will look more closely at VM possibility - perhaps it is not as complex as I have been led to believe, though I might still need to buy some kind of Windows SW to do that. I have an ancient XP install CD that I tried without success to install a few years ago. The pre-installed 10 system cannot be reinstalled anywhere else. If I wipe that, it is just gone. MS is famous for refusing any real help with pre-installed versions.

---

### Post by dragonfly41 on 2018-03-04
I dropped trying wine a long time ago.

However reading here ..

[http://www.rdeeson.com/weblog/126/how-to-run-internet-explorer-7-8-and-9-in-linux-with-or-without-wine](http://www.rdeeson.com/weblog/126/how-to-run-internet-explorer-7-8-and-9-in-linux-with-or-without-wine)

have you installed winetricks IE8
(see at bottom of page).

---

### Post by JamButty on 2018-03-04
Theoretically I am now up on IE8 using winetricks. However, so far I cannot connect to any page other than the default open page, [https://www.winehq.org....running](https://www.winehq.org....running) like 300Baud.

---

### Post by dragonfly41 on 2018-03-05
Perhaps you can find some tips in the wine sub-forum ..

[https://ubuntuforums.org/forumdisplay.php?f=313](https://ubuntuforums.org/forumdisplay.php?f=313)

---

### Post by monkeybrain20122 on 2018-03-05
VM is an overkill anyway if all you need is IE and dualboot is even more ridiculous. The overhead is totally unjustified.I think you need some tricks to get wine apps to connect to the internet because it may be a security concern. But instead of actually using IE have you tried using a user-agent switcher addon on Firefox? Sometimes you can easily access IE only websites (WTF?? This is 2018) by simply setting a user agent string in Firefox to spoof it.

---

### Post by monkeybrain20122 on 2018-03-05
> **marks1 said:**
> Try Virtualbox.  It will run Windows 10 and all applications smoothly.  The WIndows 10 iso is available on the MS website for free download.  If you already have Windows 10 installed you can also install it under linux as long as you are installing on the same machine.  You will to need burn the WIndows iso on DVD and install it using Virtualbox.

As a general point this is not true. I have Win apps that require OpenGL or some other graphic features, they work out of the box in wine (or playonlinux if a specific version of wine is required) but don't run in Vbox.

---

### Post by JamButty on 2018-03-05
[**[COLOR=#000000]dragonfly41[/COLOR]**]("https://ubuntuforums.org/member.php?u=1261878") - I will dive into that wine subforum. It looks like I was naive about the dummy proofing of Wine's complexities by playonlinux. It will probably take quite a bit of digging to have a decent picture of how it works and fix problems.
[**[COLOR=#000000]monkeybrain20122[/COLOR]**]("https://ubuntuforums.org/member.php?u=1843403") I have added the FF user agent switch extension and will play with it. I don't have  much hope for that as the problems are unlikely to be intentional barriers to other browsers, but simply bad/lazy web design that prevent proper functioning on other major browsers.

---

### Post by QIII on 2018-03-05
Moved to Wine to attract the attention of the right crowd.

:)

---

