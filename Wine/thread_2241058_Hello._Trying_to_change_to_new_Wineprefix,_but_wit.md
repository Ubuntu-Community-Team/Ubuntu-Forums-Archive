---
title: "Hello. Trying to change to new Wineprefix, but without any luck. (Wine 1.6.2)"
date: 2014-08-23
forum: Wine
---

### Post by SteveL1990 on 2014-08-23
Hello there. I've got a bit of a dilemma on my hands and I was wondering if you guys could help me solve it.

A few days ago, I thought I'd download the free demos of a couple of games I'd been meaning to try, namely, BeamNG Drive and Bugbear's Next Car Game(okay, technically, they're demos). I was able to install them on Windows 8.1 without much trouble, but they are pretty darn slow on there, and given that Ubuntu's always been faster for me(I'm using 14.04/Trusty, btw), I thought I'd try it on Wine. Well, unfortunately, I've had a fair amount of trouble getting things to actually work.

First off, I discovered that both games just wouldn't load under the Wine I'd originally installed; it's a 64-bit version of 1.6.2, btw. So, having found some advice on the internet, both at AskUbuntu, and the official forums at BeamNG(and the Wine FAQ), I was, with a bit of difficulty(including one botched attempt), able to create a separate 32-bit Wineprefix(notice the absence of the x64 folder?): 

[IMG]http://i.imgur.com/HZtAyh8.png?1[/IMG].

However, my main trouble now, is, I'm having trouble making the 32-bit Wineprefix the default, so I can try to install these two games for Wine. Does anyone here know how to get Wine to load new prefixes? I'm at a bit of an impasse and I've had little luck elsewhere. :( 

So, any help is appreciated.

---

### Post by SteveL1990 on 2014-08-24
I've also tried the advice offered on the Wine forums.....

[https://forum.winehq.org/viewtopic.php?f=8&t=23328&p=96170#p96170](https://forum.winehq.org/viewtopic.php?f=8&t=23328&p=96170#p96170)

....and even that hasn't worked. Please, folks, I *desperately* need help on this.

---

### Post by mozalmy on 2014-08-25
You could try this method.

First rename your ~/ .wine directory or you can delete it.

Then, create a new environment:

```
$ WINEARCH=win32 winecfg
```

To make a separate win32 and win64 environment:

```
$ WINEARCH=win32 WINEPREFIX=~/win32 winecfg 
$ WINEPREFIX=~/win64 winecfg
```

Then:

```
export WINEPREFIX=$HOME/.config/wine/
export WINEARCH=win32
```

To create separate wineprefix for each game, you may try this method:

```
export WINEARCH=win32 WINEPREFIX=~/wineBeamNG (or whatever name you like)
winecfg
cd /directory (the directory holding your installer)
wine ./setup.exe
```

```
export WINEARCH=win32 WINEPREFIX=~/wineBugbear's (or whatever name you like)
winecfg
cd /directory (the directory holding your installer)
wine ./setup.exe
```

Hope this works for you. Good luck.

---

