---
title: "32bit Firefox 3.5 on 64bit Ubuntu?"
date: 2009-10-02
forum: x86 64-bit Users
---

### Post by Seregwethrin on 2009-10-02
Hello;

I want to install Firefox 3.5 32-bit on Ubuntu 64-bit.

How should I proceed?

---

### Post by HappyFeet on 2009-10-02
> **Seregwethrin said:**
> Hello;
I want to install Firefox 3.5 32-bit on Ubuntu 64-bit.


Could you enlighten us as to why?

---

### Post by CoreyB. on 2009-10-02
I'm not the OP, but, from what I've read, Tracemonkey isn't enabled on 64-bit Firefox.

---

### Post by sir4taye on 2009-10-03
Not OP either, but I want to switch to the 32bit so that I don't have some of the buggy flash problems that the 64 bit version has. Is this a tail chasing act?

---

### Post by NoaHall on 2009-10-03
Download a deb, then do ```
 sudo dpkg -i --force-architecture /package/name/location 
```

---

### Post by Seregwethrin on 2009-10-03
> **HappyFeet said:**
> Could you enlighten us as to why?

Because of bugs at 64-bit firefox. There are lots of them.

---

### Post by efef on 2009-10-07
I'd like to know this as well. 

Since Im not an expert I would a slighty more deatiled guide then the suggestion above. It would much appreciated.

I need the 32bit Firefox in order to run a custom plugin used at my company, and it only works in 32 bit.

---

### Post by noob5000 on 2009-10-07
i am quite sure you CAN install 32 bit firefox on 64 bit ubuntu... because yesterday i had this problem that i could ONLY install 32 bit on my 64 bit pc even though i wanted 64 bit firefox :)

here is one way to get 32 bit firefox:

first, type (or copy/paste) this in the terminal:
```
sudo apt-get install libstdc++5 libnotify-bin
```then download the "ubuntuzilla-?.?.?-0ubuntu1-amd64.deb" file (i only typed "?" in case the version changes)  here: [http://sourceforge.net/projects/ubuntuzilla/files/](http://sourceforge.net/projects/ubuntuzilla/files/)
after downloading that file, double-click on it and let the automatic installation of ubuntuzilla happen.

then type this in the terminal:
```
ubuntuzilla.py
```then just follow the instructions, mainly yes / no questions (simple).

that's it.

after i did this, i had 32 bit firefox (3.5.3) on my 64 bit ubuntu (9.04).




btw source: [http://ubuntumanual.org/posts/193/installing-firefox-3-5-in-ubuntu-the-easy-way](http://ubuntumanual.org/posts/193/installing-firefox-3-5-in-ubuntu-the-easy-way)

---

### Post by CoreyB. on 2009-10-08
Anyone know if it is possible to use 32 bit and 64 bit firefox from the repos so you get auto updates?

---

### Post by vhenry on 2009-10-08
Anyone else having problems with Fireftp with 64bit Firefox?

Filezilla seems to work fine, but its always been easier for me to launch fireftp from browser for quick uploads like images.

---

