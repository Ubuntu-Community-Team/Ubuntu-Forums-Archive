---
title: "does wine of 12.04 64bit run 32bit windows apps?"
date: 2012-05-22
forum: Wine
---

### Post by ahso4271 on 2012-05-22
Hi
does wine as of 12.04 64bit software center run 32bit windows apps? if not how?
thanks

---

### Post by thatguruguy on 2012-05-22
Wine emulates 32-bit Windows. So, yes.

---

### Post by prshah on 2012-05-22
> **ahso4271 said:**
> Hi
does wine as of 12.04 64bit software center run 32bit windows apps? 


Hello,

Yes, wine on 12.04 64 bit runs 32 bit windows apps (though you should check appdb.winehq.org for other caveats for your particular app).

For example, "Mass effect 1" works great out-of-the-box with Wine.

However, "Mass effect 2" does not work properly in Wine 32-bit (sound cuts out after a few sconds). I have to use wine64 in order to have it run properly. However, "Mass Effect 1" does not even launch with wine64.

Note that you need a different prefix for wine (32bit) and wine64 (64 bit); you cannot use the same ~/.wine/ directory for both.

---

### Post by ahso4271 on 2012-05-23
Thanks, so for using 32bit i call wine and for 64bit wine64 each with it's own .wine? Simple...was fearing it to be more complicated. ;)  I've had a look at compilation, but 32bit dependencies on 64bit seem a mess. Hence I'll try the default.

---

### Post by prshah on 2012-05-23
> **ahso4271 said:**
> Thanks, so for using 32bit i call wine and for 64bit wine64 each with it's own .wine? 

I recommend a slight change; try using wine 32 for apps by default; for those that dont work, try using wine 64.

Note that I THINK that wine 32 / 64 bit refers to the underlying structure of WINE itself, and not the Windows binary.

Examples:

To run something with the default .wine (assumed 32-bit)```

wine setup.exe
#or to be completely sure
WINEPREFIX=/home/user/.wine wine setup.exe

```
and for 64 bit wine (note change in WINEPREFIX, and wine command)```

WINEPREFIX=/home/user/[color=red].wine64 wine64[/color] setup.exe
```

If your given wineprefix does not exist, depending on whether you use the wine/wine64 command, a new setup will be created as 32/64 bit respectively.

---

### Post by thatguruguy on 2012-05-23
> **prshah said:**
> 
Note that I THINK that wine 32 / 64 bit refers to the underlying structure of WINE itself, and not the Windows binary.


This is correct.

The following is from the [Wine FAQ]("http://wiki.winehq.org/FAQ#head-b89ca9d7cdf2bc2ddfb23b3e5829219df48524f8"):
> Note that Wine for 64-bit actually runs in 32-bit mode. This is  necessary, as virtually all Windows applications are 32-bit. Support for  64-bit Windows applications is currently experimental (see [Wine64]("http://wiki.winehq.org/Wine64")). 

The fact that you have installed Wine on 12.04 64-bit does NOT mean that you are running Wine64. Wine64 is a completely separate package.

---

