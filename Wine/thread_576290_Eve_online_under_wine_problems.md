---
title: "Eve online under wine problems"
date: 2007-10-15
forum: Wine
---

### Post by Myronray on 2007-10-15
heya to all linux experts need some help here my wine installed proeprly but i run my eve online client it show black scree but sound is working can anybody help how to run normal eve online  in ubuntu 7.10....

---

### Post by cogadh on 2007-10-15
This doesn't really answer the question, but there is a Linux native Eve client currently in beta testing. You might want to wait for that to be released, rather than mess with running the Windows client through Wine.

---

### Post by koer on 2007-10-18
> **Myronray said:**
> heya to all linux experts need some help here my wine installed proeprly but i run my eve online client it show black scree but sound is working can anybody help how to run normal eve online  in ubuntu 7.10....

first thing you gotta do , is take the arial font from any word processor ( you can find it in the word's file) and put it in the c-drive that wine creates , i think its : drive c - windows - fonts 

```
/home/(username)/.wine/drive_c/windows/fonts
```

then go to :

```
/home/(username)/.wine/drive_c/windows/profiles/(user name)/Local Settings/Application Data/CCP/EVE/settings
```

and open the perfs.ini and write on top :   audio=0

now it should run

---

### Post by Toffeeapple on 2007-10-18
[http://myeve.eve-online.com/ingameboard.asp?a=topic&threadID=558791](http://myeve.eve-online.com/ingameboard.asp?a=topic&threadID=558791)

good bit of info there...

---

### Post by kurros on 2007-10-19
> **cogadh said:**
> This doesn't really answer the question, but there is a Linux native Eve client currently in beta testing. You might want to wait for that to be released, rather than mess with running the Windows client through Wine.

The client in testing is not native but using Cedega.

---

### Post by cogadh on 2007-10-19
You don't need Cedega to run it, it includes the necessary Cedega components within the Linux client, so it will run natively, just not directly natively. I guess you could call it a semi-native port. Either way, it is a version of Eve that will run natively out of the box, without the need for Cedega or Wine.

---

### Post by dalamar666 on 2007-10-19
I have eve running in wine using gutsy and it worked first time.  I have moved the arial fonts over to the right directory and I am having problems with it.  One of the problems that I am having with the game is reading the fonts.  They are quite blurred and sometimes I get various ingame icons in the place of charectors and words.  The other problem that i am having, I am using an ATI Radeon X1650 video card.  Once I installed the XGL driver to run Compiz, the game started running extremely slow.  Like 1.2 fps.  I have removed compiz and the xgl driver but that has not fixed the slowness.  I really do not want to reinstall ubuntu as is standard in windows.  Does anyone know how to undo all the changes made to the driver by the driver?  I am using the driver for the video card that is closed source from ATI.  I have also tried reinstalling that and not having any luck.  I would love to be able to run compiz and eve at the same time.  I am new to linux and so any help will be greatly appriciated.

---

### Post by Myronray on 2008-01-13
thanks all your reply guys and anyway eve online under CCP released cedega together with transgaming at last all eve player happy for there support.


thanks all


myronray

---

