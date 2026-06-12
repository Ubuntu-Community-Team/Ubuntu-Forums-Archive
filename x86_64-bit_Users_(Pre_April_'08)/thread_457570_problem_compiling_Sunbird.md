---
title: "problem compiling Sunbird"
date: 2007-05-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by noflexdan on 2007-05-28
Hi forum

I have a problem compiling Sunbird. I get this error when i try to run configure:configure: error: --enable-application=APP is required.

I don't know what parameter i should give this?

Anyone has a deb file for amd64 of sunbird ;)

Tia.
//noflex

---

### Post by kuja on 2007-05-28
Erm, I certainly don't have a deb; however, try running this to buy a clue: 

./configure --help 

and it should spit some stuff out, most likely including something to do with the - -enable-application option which it says is required.

---

### Post by stickk on 2007-05-28
You may want to take a look at the Mozilla build documentation. 
[http://developer.mozilla.org/en/docs/Build_Documentation](http://developer.mozilla.org/en/docs/Build_Documentation)

---

### Post by Arenlor on 2007-12-16
Just for anyone else who runs into this error and searches, APP should be calendar

---

