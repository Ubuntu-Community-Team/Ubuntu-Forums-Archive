---
title: "Flash player for firefox"
date: 2008-03-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by casinaroyale on 2008-03-20
Guys

Is there a good flash player for firefox for the amd64 machines??
I tried that gnash, which sucks big time.

Someone please help me out with this....... Presently this is the only reason why I am forced to go back to my Windows everytime to watch a youtube video

Thanx

---

### Post by chucky chuckaluck on 2008-03-20
> **casinaroyale said:**
> Guys

Is there a good flash player for firefox for the amd64 machines??
I tried that gnash, which sucks big time.

Someone please help me out with this....... Presently this is the only reason why I am forced to go back to my Windows everytime to watch a youtube video

Thanx

download it from here and just follow the installation instructions (you have to close the browser when you actually run the installer). [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

---

### Post by epee on 2008-03-20
I tried the tar file, and the installer complains that it DOES NOT support X86-64.

64-bit support in general sucks.

---

### Post by chucky chuckaluck on 2008-03-20
> **epee said:**
> I tried the tar file, and the installer complains that it DOES NOT support X86-64.

64-bit support in general sucks.

oh. sorry about that.

---

### Post by dabl on 2008-03-20
Do this:

[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

### Post by casinaroyale on 2008-03-20
@dabl

You saved my day !! Thank you    !!! :KS:KS

---

### Post by Sockerdrickan on 2008-03-20
> **epee said:**
> I tried the tar file, and the installer complains that it DOES NOT support X86-64.

64-bit support in general sucks.

That was proprietary software so no one can do anything about it. google "gnash" though.

---

### Post by kushykush on 2008-03-21
I have tried everything, but Adobe Flash is not installing.  When I click on the tar install file the window does come up. When I click "run in terminal" something quickly happens but nothing gets installed.  

I am new to Linux and Ubuntu, and I never imagined that installing a simple plugin into Firefox will be this complicated.  I have spent 3 hours trying to install Flash plug in and am getting no where.  

If you are experienced then please give detail directions.  For example, the Adobe website says when the tar.gz file is extracted "in the terminal navigate to this directory."  Well, how do you navigate to this directory?  what do you exactly type in the terminal?  

In Windows installing the Flash player is done automatically in a few seconds.  What a bummer.

---

### Post by PmDematagoda on 2008-03-21
Just install Flash on Ubuntu with:-
```
sudo apt-get install flashplugin-nonfree
```
Or visit a web page with Flash, Firefox will then prompt you if you want to install Flash(This holds true for Ubuntu 7.10, not sure about 7.04).

---

### Post by Kilz on 2008-03-21
> **PmDematagoda said:**
> Just install Flash on Ubuntu with:-
```
sudo apt-get install flashplugin-nonfree
```
Or visit a web page with Flash, Firefox will then prompt you if you want to install Flash(This holds true for Ubuntu 7.10, not sure about 7.04).

The flash packages are (or were) broken in 64bit, and usually the remnants of 2 or 3 different failed install methods make flash not work. My script (its a sticky) usually removed s a lot of the issues and gets everything running.

---

### Post by corpsed on 2008-03-21
> **Kilz said:**
> The flash packages are (or were) broken in 64bit, and usually the remnants of 2 or 3 different failed install methods make flash not work. My script (its a sticky) usually removed s a lot of the issues and gets everything running.

but it will not work on the 8.04 Hardy beta, correct?

---

### Post by Kilz on 2008-03-21
> **corpsed said:**
> but it will not work on the 8.04 Hardy beta, correct?

Hardy should have a working flashplugin-nonfree package for 64bit. If it doesn't **[COLOR="Red"]File A Bug Report [/COLOR]** on launchpad while Hardy is still in development.

---

