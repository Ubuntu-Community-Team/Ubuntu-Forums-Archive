---
title: "Fonts - Anti-Aliasing/ClearType"
date: 2008-07-14
forum: Wine
---

### Post by myke on 2008-07-14
uu

---

### Post by issueperson on 2008-10-16
I'm going to bump this as I have the same question

---

### Post by Gcentrex on 2008-10-17
Installed as in the core fonts? since they are not all the fonts you will need, I did it the better way copy the fonts folder from my Windows Drive to Wine after I did that all my fonts we looking as if I was using Windows.

---

### Post by issueperson on 2008-10-25
Thanks, but I actually have the fonts.  They just do not appear anti-aliased.  They are pixelated on the screen when I used wine, but not in VirtualBox.

Any other thoughts?

---

### Post by Gcentrex on 2008-10-25
Not really since all my Fonts in "Wine/CrossOver Pro/CrossOver Games" using my windows fonts all look perfectly fine.

I setup my fonts in Linux with the setting "Subpixel smothing (LCDs)" and they all look great in any windows or Linux application.

---

### Post by Aearenda on 2008-10-26
I've read somewhere (and it certainly seems to work this way for me) that anti-aliasing in Wine depends on the font size in use, and the dpi setting in WineCFG. For me, with 96dpi, fonts from 14 points up get anti-aliased; with 120dpi, fonts from 10 points up get anti-aliased.

---

### Post by gnl99 on 2008-10-26
questioning the claimed numbers of itlet's go to the forum Good Services[img]http://pic.piclib.net/sunvv/images/pic/new20_711.gif[/img]About all go to [wow gold](http://www.powerleveling-wowgold.com) Good Services ok![img]http://pic.piclib.net/sunvv/images/pic/16340.jpg[/img]sites where they can express&#65281;[body massage](http://www.chinamassage.org/)-massage vip service in shanghai[escort shanghai](http://www.sh-escort.com/)-Offering Sensual Full Body Massage [massage in shenzhen](http://www.massageinshenzhen.org/)-All of the massage in shenzhen services[massage in hangzhou](http://www.massageinhangzhou.org.cn/)-professional oil hangzhou massage and sensual

---

### Post by issueperson on 2008-10-28
Yeah, I've messed with the DPI and unfortunately on my crappy low-res display anything above 96 appears huge.  Thanks for the tip though.

---

### Post by walmartshopper on 2009-02-11
In wine 1.1.14, all I had to do was open up my user.reg file and change "FontSmoothing" from "0" to "1"

---

### Post by joey-elijah on 2009-02-11
There's a mini application you can install under Wine that lets you set Wine to use whatever font you like - i use it so my Wine apps use the same font as i have Ubuntu using. It helps.

The thread: -
[http://ubuntuforums.org/showthread.php?t=142741](http://ubuntuforums.org/showthread.php?t=142741)

---

### Post by ltwinner on 2009-08-10
> **joey-elijah said:**
> There's a mini application you can install under Wine that lets you set Wine to use whatever font you like - i use it so my Wine apps use the same font as i have Ubuntu using. It helps.

The thread: -
[http://ubuntuforums.org/showthread.php?t=142741](http://ubuntuforums.org/showthread.php?t=142741)

I followed that guide but it displayset didn't give me an option to set the Window Text font. Every other font could be set. So how can the Window Text font be set as it is killing my eyes.

---

### Post by josephmc on 2010-04-17
> **walmartshopper said:**
> In wine 1.1.14, all I had to do was open up my user.reg file and change "FontSmoothing" from "0" to "1"

That did it for me. Thanks!

---

