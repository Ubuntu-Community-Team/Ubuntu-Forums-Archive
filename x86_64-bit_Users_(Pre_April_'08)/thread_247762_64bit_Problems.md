---
title: "64bit Problems"
date: 2006-08-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by SlCKB0Y on 2006-08-31
Hi,

A few days ago I was reading all the rubbish in there about 64bit ubuntu not lacking in any way. So I decided to install it. What a bad move... There is so much stuff which seems to be broken, and its really starting to annoy me.

I am running AMD64 3000, geforce 6600 gt 128mb and dapper 64.

I have tried setting up compiz/xgl, it simply doesnt work no matter I try. I have followed numerous guides and reinstalled...nothing. compiz exits without any messages what so ever (great coding). I get no window borders. Also, the 
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) repos for them seem to be all messed up for 64 bit. I couldnt get that version to install because the official package has the same name and is ahead in version number. 

I followed the guide precisely for installing dvd support. Nothing
Same again for aac support in rhythmbox.....no go.

Let me add that im a pretty experienced linux user. I have used nothing but nix since 98, and have used many different distros. I have been able to setup the above things before with ease on 32bit. I am studying comp sci at uni so im not completely useless.

A little help?

---

### Post by Kilz on 2006-08-31
> **SlCKB0Y said:**
> Hi,

A few days ago I was reading all the rubbish in there about 64bit ubuntu not lacking in any way. So I decided to install it. What a bad move... There is so much stuff which seems to be broken, and its really starting to annoy me.

I am running AMD64 3000, geforce 6600 gt 128mb and dapper 64.

I have tried setting up compiz/xgl, it simply doesnt work no matter I try. I have followed numerous guides and reinstalled...nothing. compiz exits without any messages what so ever (great coding). I get no window borders. Also, the 
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) repos for them seem to be all messed up for 64 bit. I couldnt get that version to install because the official package has the same name and is ahead in version number. 

I followed the guide precisely for installing dvd support. Nothing
Same again for aac support in rhythmbox.....no go.

Let me add that im a pretty experienced linux user. I have used nothing but nix since 98, and have used many different distros. I have been able to setup the above things before with ease on 32bit. I am studying comp sci at uni so im not completely useless.

A little help?


Well for a experenced linux user you seem to be having some problems.

The dvd problem
```
sudo apt-get install libdvdread3 debhelper build-essential fakeroot
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

---

### Post by SlCKB0Y on 2006-08-31
> **Kilz said:**
> Well for a experenced linux user you seem to be having some problems.

The dvd problem
```
sudo apt-get install libdvdread3 debhelper build-essential fakeroot
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

Tell me about it. When I say problems....Ive been trying to fix them today. I guess im just used to be able to work out linux problems pretty quickly. Thats why its frustrating. I did EXACTLY this. Did not work. Compiled cleanly, but it wont work in totem.

Does anyone know a solution to my compiz issue? or the m4a issue?

EDIT: I removed totem-gstreamer and installed totem-xine and it works fine. Weird!

EDIT2: a number of hours and I have gotten compiz working. Wow, those themes look really good. Thanks to this page
[http://www.ubuntuforums.org/showthread.php?t=235013&highlight=64bit+compiz](http://www.ubuntuforums.org/showthread.php?t=235013&highlight=64bit+compiz)

---

