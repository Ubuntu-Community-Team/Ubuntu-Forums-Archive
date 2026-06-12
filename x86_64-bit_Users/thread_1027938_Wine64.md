---
title: "Wine64"
date: 2009-01-01
forum: x86 64-bit Users
---

### Post by OmnyDevi on 2009-01-01
Greetings,

I have been on [http://wiki.winehq.org/WineOn64bit#head-c47d9e53f952c5b6260467e0dc158321229216de](http://wiki.winehq.org/WineOn64bit#head-c47d9e53f952c5b6260467e0dc158321229216de) trying to find out how to get Wine to work with my COD4 game I purchased. I have run into a question though that I thought someone here might know!

The site suggests to:
sudo apt-get build-dep wine

which I did

Then the next step is:
You can make these links in a temporary folder within the wine tree. 
mkdir -p `pwd`/lib32
ln -s /usr/lib32/libX11.so.6 `pwd`/lib32/libX11.so
ln -s /usr/lib32/libXext.so.6 `pwd`/lib32/libXext.so
ln -s /usr/lib32/libfreetype.so.6 `pwd`/lib32/libfreetype.so
with a lot more links to be made. 

Thats all fine and dandy..but...where exactly is the wine tree? Or what is it? I have seen the /usr/lib32/*.so but I don't know what the hell the mkdir -p 'pwd'/lib32 means, nor do I know what a wine tree is. 

Any help is much appreciated!

---

### Post by jespdj on 2009-01-02
The "wine tree" is the set of directories (a.k.a. the directory tree) which contains the source code files for Wine.

Note that Wine64 is not just Wine for 64-bit Ubuntu; it's a version of Wine that emulates 64-bit Windows. The page that you refer to is about compiling 32-bit Wine on 64-bit Ubuntu platforms, so it's not about Wine64 as the title of your post suggests. You most likely don't need 64-bit Windows or Wine64 to run that game.

As far as I know, Wine is available for 32-bit as well as 64-bit Ubuntu in the repository, so the only thing you'd have to do to install Wine is:
```
sudo apt-get install wine
```
Maybe you're making it much more difficult than it is.

---

### Post by stchman on 2009-01-02
WINE is not going to play all Windows games.  My instincts say that CoD4 probably will not work under WINE.

---

### Post by Rog-Mahal on 2009-01-02
The only way to know is to try. Those commands given on the winehq page are old. As long as you have ia32-libs installed you won't have to do those things. Just install wine like the earlier post said and try it out. I know that wine supposedly has compatability for vista programs, but the most recent thing I've installed with wine has been starcraft :-p

---

### Post by Kilz on 2009-01-02
> **OmnyDevi said:**
> 

Any help is much appreciated!

Ok, as others have said, you dont need 64bit wine. What you do need is information. The Wine application database is a good place to learn how to make wine work with games. [COD4 has a page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=10429") and it looks like it may run for you. You may want to bookmark the home page of the app database.

---

### Post by ghoti2007 on 2009-01-04
COD4 works flawlessly :)  (without punkbuster, of course)

There isn't a "true" 64 bit of wine, yet either.  I beleive the mailing lists recently had someone comment that they had a "hello, world" app compile with wine - but they are focusing on getting everything solid before migrating to 64bit.  At least, that was the last I read some time ago :)

---

