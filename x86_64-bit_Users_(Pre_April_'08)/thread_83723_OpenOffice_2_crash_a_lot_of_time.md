---
title: "OpenOffice 2 crash a lot of time"
date: 2005-10-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by JuanC on 2005-10-29
Hi ,

I try to create some documents with OpenOffice 2 Writer , but it's a pain , sometimes when i try to change font inside document OpenOffice crash , also when i try to change to italic some text , OpenOffice crash ...

With these crashes i lose a lot of parts in my document #-o 

These bugs are fixed in the final version?

OpenOffice 1.1.5 is more stable?

And when an AMD64 native version of OpenOffice?

---

### Post by bunced on 2005-10-30
If you are still using hoary, the answer to both the crashing and the AMD64 is to upgrade to Ubuntu Breezy - this has a stable OpenOffice and a 64 bit version. If it is breezy that is crashing, I suggest you report it as a bug or use 1.1.5

---

### Post by JuanC on 2005-10-30
I use Breezy for Amd64 , clean install directly from Install CD.

---

### Post by kawinter on 2005-10-31
[QUOTE=JuanC]I use Breezy for Amd64 , clean install directly from Install CD.[/QUOTE]

Me too!  Brand new install of Breezy on AMD 64.  OO2 crashes all the time on font formatting changes.  Want to see it fall over quickly?  Try the format painter that transfers the formatting from one bit of text to another.  That'll lock it up every time.  It is my understanding that it is really a 32 bit application that was tweaked to work with 64 and that the package is not going to be stable for a while.  Does any one else know anything about this?

Meanwhile the trick is to save everything about every 4 seconds....

---

### Post by gomadtroll on 2005-10-31
My issue, using the sum function for a column of numbers entered into a table created in OOwriter2 freezes the app. I think this is a KDE issue since when I switched to Windowmaker the problem dissapeared. I prefer WindowMaker so it is not problematic for me but Kubuntu/KDE Desktop users have issues.
Breezy/Kubuntu/AMD64, with other apps installed.
Greg

---

### Post by JuanC on 2005-11-03
Any news about how to fix this bug?

---

### Post by JuanC on 2005-11-08
Only us has problems with OpenOffice2 , Kubuntu and AMD64?

While bug fixes or the final version of OpenOffice2 enter on repositories , I install [KOffice](http://www.koffice.org).

KOffice works perfectly , I don't get any crash since i installed KOffice.

I use KWord a lot and I like so much and also it can Open/Save OASIS OpenDocument files.

---

### Post by JuanC on 2005-11-17
Try this :
```

# apt-get install libstlport4.6c2

```

Fix these crashes in my case.

---

### Post by scflymedic on 2005-11-17
I've experienced complete crashes when using the fax wizard, letter wizard and the agenda wizard...any clues?  Oh, by the way I'm using OO2 32 bit on 32 bit breezy.

---

### Post by metoo on 2005-11-21
Which version are you using? There is a final version out over at
[http://people.ubuntu.com/~doko/](http://people.ubuntu.com/~doko/)
then select the directory i386, amd64 and powerpc

For amd64 the line in /etc/apt/sources.list looks like this:
deb [http://people.ubuntu.com/~doko/OOo2-amd64](http://people.ubuntu.com/~doko/OOo2-amd64) ./

Don't use it much, but it doesn't crash on me.

---

### Post by Navyblue on 2005-11-24
My ooffice2 on Kubuntu AMD64 crashes sometimes, though i wouldn't call it often, but I don't use it often.

Btw, it also look gnomish, another box of mine with 32bit looks alright.

---

### Post by hbj on 2005-12-01
Yes - it crashed a lot for me too and I used the 'save every few seconds' method until switching to running in a chroot.

---

### Post by K-mies on 2006-02-01
Do you have openoffice.org2-kde package installed? I removed it few days ago and openoffice seems to work correctly now. First I tried solve this problem by switching to old 1.1.5 version. When I selected some text (openoffice.org2-kde package installed), it crashed.

---

### Post by amd-64 on 2006-02-01
I initially removed openoffice.org2-kde which helped decrease crashes a bit. 

Recently OO2 started freezing on text selection in oowriter2 and oocalc2. I removed openoffice.org2-gnome too and so far no crashes.


Breezy 

OO2 2.0.1 from the following repo

deb [http://people.ubuntu.com/~doko/OOo2-amd64](http://people.ubuntu.com/~doko/OOo2-amd64) ./

---

### Post by HunterCo on 2006-03-12
[QUOTE=amd-64]
OO2 2.0.1 from the following repo

deb [http://people.ubuntu.com/~doko/OOo2-amd64](http://people.ubuntu.com/~doko/OOo2-amd64) ./[/QUOTE]
I cannot find any files in the repository you have listed here... I've seen it mentioned on a number of posts, but no dice. Have the files been taken down, or were they moved some place else?

---

### Post by wylie348 on 2006-06-13
I also get an application 'hang' or crash with openoffice writer when I attempt to use the letter wizard.
?

---

### Post by scunc_dvl on 2006-07-26
I found a package update for OpenOffice today, it was a big one, and thank goodness it seems to have stopped all the lockups, and even Klipper support works now. 

Amen maintenance!

---

### Post by pacoman on 2006-12-07
SOLUTION:

  I updated my JRE to the Blackdown version and changed which one that Open Office uses in the settings and the problem was fixed.

---

