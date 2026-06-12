---
title: "Seamonkey Browser upgrade"
date: 2009-05-22
forum: x86 64-bit Users
---

### Post by cybrsaylr on 2009-05-22
Just installed SeaMonkey 1.1.15 and they recommend an upgrade to 1.1.16 version. 
Having trouble upgrading to 1.1.16 on 64bit version Jaunty.
Can someone tell me what I have to do to upgrade?

SeaMonkey looks interesting, want to play around with it.
How do you folks rate it?

---

### Post by x33a on 2009-05-22
what problem are you facing upgrading?

---

### Post by cybrsaylr on 2009-05-22
I was expecting it to auto upgrade and it's not.

Not sure what to do then.
Firefox and Opera pretty much auto upgrade and I was hoping SeaMonkey would do the same but it didn't.

---

### Post by x33a on 2009-05-22
it will auto upgrade only if it's available in the repos

post the output of
```
sudo aptitude show seamonkey
```

---

### Post by cybrsaylr on 2009-05-22
Here's the output:

Package: seamonkey
State: not installed
Version: 1.1.15+nobinonly-0ubuntu2
Priority: optional
Section: universe/web
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Uncompressed Size: 90.1k
Depends: seamonkey-browser, seamonkey-mailnews
Recommends: seamonkey-chatzilla
Conflicts: iceape (< 1.1.6), mozilla (< 2:1.8)
Replaces: iceape, mozilla
Description: The Seamonkey Internet Suite
 The Seamonkey Internet Suite is a set of Internet oriented applications. It is
 the continuity of the Mozilla Suite after it has been abandoned in favor of
 Firefox and Thunderbird. 
 
 The Seamonkey Internet Suite consists of: 
 * an Internet browser (Seamonkey Navigator) 
 * an HTML WYSIWYG editor (Seamonkey Composer) 
 * a Mail and News client (Seamonkey Mail & Newsgroups) 
 * an Address Book (Seamonkey Address Book) 
 * an IRC client (Chatzilla) 
   
 This is a meta package that depends on the main components of this suite. It is
 here to ease upgrades, installations, and provide a consistent upgrade path
 from previous versions. 
 
 It can safely be removed with no ill effects.
Homepage: [http://www.seamonkey-project.org/](http://www.seamonkey-project.org/)

---

### Post by x33a on 2009-05-22
so ver 1.1.16 isn't available in the repos. maybe you can try finding a ppa for seamonkey.

edit: maybe this could help

[https://help.ubuntu.com/community/SeaMonkey](https://help.ubuntu.com/community/SeaMonkey)

---

### Post by cybrsaylr on 2009-05-22
Thanks. I'll go through it and give it a try later.

---

### Post by cybrsaylr on 2009-05-23
> **x33a said:**
> so ver 1.1.16 isn't available in the repos. maybe you can try finding a ppa for seamonkey.

edit: maybe this could help

[https://help.ubuntu.com/community/SeaMonkey](https://help.ubuntu.com/community/SeaMonkey)

Well I tried following those directions and it didn't work.
Not sure if I messed up or not. It didn't upgrade to the newer SeaMonkey version. I may have got lost in all the directions. The older version works but the warnings say to upgrade. It seemed more complicated that expected.

---

### Post by x33a on 2009-05-23
updating some apps on ubuntu/linux can be a real pain.

if compiling doesn't work for you, then you will have to stick with the older version.

alternatively, if you don't absolutely rely on seamonkey, you can stick with firefox, thunderbird, xchat, etc :)

edit: i found this repository, but it hosts the 2.0 alpha version, and the stable version is pretty old 1.1.12.

[https://launchpad.net/~fta/+archive/ppa/+index?start=0&batch=75](https://launchpad.net/~fta/+archive/ppa/+index?start=0&batch=75)

---

### Post by cybrsaylr on 2009-05-23
The older Seamonkey version plays fine.
I'm just concerned with the security issues they raise telling you an upgrade will cure.

Tried out installing Epiphany browser. It installed but I can't get it to launch or open! Can't find Epiphany anywhere even though it said it is installed!
First time this ever happened to me with Ubuntu!

---

### Post by x33a on 2009-05-23
which package did you install?

There are 2 softwares named epiphany in ubuntu's repos. one is epiphany (game), another is epiphany-browser.

try
```
sudo aptitude install epiphany-browser
```

---

### Post by cybrsaylr on 2009-05-24
> **x33a said:**
> try
```
sudo aptitude install epiphany-browser
```
x33a,
OK Just did that and still can't find any icon for epiphany or any way to launch it .... same as before.
Terminal says everything is installed and done!

It's real strange....

---

### Post by x33a on 2009-05-24
try starting it from the terminal. if it starts ok, then you can create a menu entry yourself.

on the other hand, if you are looking for a light and functional browser, i would suggest you go for opera. i use it whenever i am not using firefox, and it is even faster than epiphany.

---

### Post by cybrsaylr on 2009-05-25
> **x33a said:**
> try starting it from the terminal. if it starts ok, then you can create a menu entry yourself.

on the other hand, if you are looking for a light and functional browser, i would suggest you go for opera. i use it whenever i am not using firefox, and it is even faster than epiphany.

x33a, 
Thanks for the tip on epiphany, I'll pass on it then.
Opera has been my fav browser the last 10 yrs for its speed but I'm having problems with Opera 9.62 and 9.64 running very slow and erratic on 64bit Jaunty. Opera ran fine and fast on all earlier versions of Ubuntu going back to Feisty Fawn. It seems to be wireless related because when I hardwire my laptop, Opera takes off flying very fast on Jaunty but when I go back on wireless Opera acts slow and erratic again.

SeaMonkey was very fast like Opera when testing it and runs fine and fast wireless.

---

### Post by x33a on 2009-05-25
Try opera 10 alpha or latest snapshot, it's awesome. I've been using it for a few months and rarely faced a problem.

[http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

---

