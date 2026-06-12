---
title: "cant instal Radon 8500 driver"
date: 2007-06-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Blue Toes on 2007-06-23
I went to the ATI website and downloaded the .run file for linux, but whenever i try to run it the terminal opers for a second loads somthing then closes .   I tried using the cd that came with the card and it only seems to have windows setups and those either come up with the error 'would not find instal.ini file' or 'error installinf iKernal.exe  Can anyone figue out at least one of these problems?

---

### Post by tjotser on 2007-06-23
i would suggest ENVY, it's a GUI to install Nvidia and ATI cards

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) 

I have no experience with ATI cards

---

### Post by BobCFC on 2007-06-23
Try opening the Terminal first then typing the command.  That way it should stay open so you can see the error messages.  Then paste the juiciest bit of the error into google.

You can use TAB to autocomplete after typing first few letters

---

### Post by Cappy on 2007-06-24
8500 requires you to either use Envy or use this guide:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a)

The other methods won't work for 8500/8600.

---

### Post by Blue Toes on 2007-06-24
the error message that comes up is

./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

---

### Post by Cappy on 2007-06-24
It's also in that guide if you search on "Bad substitution"
It looks like you need to
```
sudo apt-get install fakeroot
```
too

---

### Post by mahalai on 2007-11-01
i've same problem .i'll try to fix it as u.

---

### Post by Anthrax9 on 2007-11-02
Use [Envy]("http://albertomilone.com/nvidia_scripts1.html") it is the best way to install graphics drivers on ubuntu
it has saved me a lot of hassle[-o<[-o<

---

### Post by mahalai on 2007-11-02
Anthrax9  	
I don't think so.

I used envy after that my pc be come black screen 2 time.

---

### Post by Anthrax9 on 2007-11-03
> **mahalai said:**
> Anthrax9  	
I don't think so.

I used envy after that my pc be come black screen 2 time.

when i wasn't using envy my screen used to turn black envy stopped that 
maybe u did not clear your old installs before using envy
that could be a reason envy not working for you...:neutral:

---

