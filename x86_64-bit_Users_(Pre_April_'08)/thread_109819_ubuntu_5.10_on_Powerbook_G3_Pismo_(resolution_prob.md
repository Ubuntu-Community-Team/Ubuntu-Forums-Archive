---
title: "ubuntu 5.10 on Powerbook G3 Pismo (resolution problems)"
date: 2005-12-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by tenev on 2005-12-29
it installs fine... first I couldn't see anything because the X-server wouldn't start...wrong resolution. then i lowered the resolution and managed to log in but the screen is way too small. i tried reconfiguring it manually:
$ sudo dpkg-reconfigure xserver-xorg

now i can only see a horizontal stripe. my question is: does anyone KNOW with certainty the working resolution on these machines? thanks.

---

### Post by 8-bitDesigner on 2005-12-30
Try this page, it helped me get my 8500 up, and I'm looking to do the same with a Powerbook 3400 as soon as I can find one of their weird screwdrivers to open in the case.

Here's what I've pulled from the page:

Model - Size - Frame Buffer - Depth - Resolution
PBG3 Pismo  - 14.1" - atyfb? - 24 - (1024x768 ?Hz)

I'm afraid the ?Hz is going to give you crap. Try doing a dpkg-reconfigure xserver-xorg and when it asks you about your monitor characteristics, choose "Medium". After that, I'd say your best bet is 1024x768x60Hz.

---

### Post by shawn12345 on 2005-12-31
ubuntu installed flawlessly on my pismo 400 with dvd/cd,386 ram, sleep,video,everything worked right out of box. only thing i haven't tried is modem. Definently a little faster than OSX tiger or panther (those seem too unsable to me).

Let me know if you need my xorg.conf I can email it to you..

- shawn

---

### Post by tenev on 2005-12-31
thanks! the pkg-reconfigure xserver-xorg command worked... shawn, mine has less memory... maybe that's the reason why.

did you have any issues installing java in your G3? my network is configured so that you have to authenticate via java applet before you can get on the internet. i have tried numerous ways posted in this forum and others but i still cannot get the plugin to work. i'd be curious to know if anyone has a working tutorial link or sth on this. happy new year.

---

### Post by shawn12345 on 2006-01-01
no problems at all. java installed fine. 

Only problem i had was during setup after initial setup when ubuntu goes to boot the window server and install more packages, it  would freeze when starting the xserver. I switched to different console, tailed the logs, was complaining about system date, i reset the 1904 date and no problems..

You're going to have a time running on less memory...i find gnome to be too slow. xfce and fluxbox work nicely though on this.

---

### Post by 8-bitDesigner on 2006-01-12
Yeah, I've got a trimmed out installation of XFCE on my Powermac 8500 and it works like a charm on 196mb. Recently swapped out the old sticks for 256 of faster RAM, and Gnome is still laggy on my system. 

Oh well, as soon as I figure out how to swap in Nautilus as the default file manager, I'll be set with XFCE.

---

### Post by chascon on 2006-01-12
or just use fluxbox or any minimal window manager and throw desktop environments entirely.

---

### Post by shawn12345 on 2006-01-12
see my thread about pismo upgrade. I upgraded my 400 to 7200rpm and a 500 processor. on 384M i'm running gnome with no problems at all now, very nicely. I feel like these gave me a boost 15-20% each over stock 400,4200rpm drive.

Only thing Bugs me now is i'm using a wireless B card. Firefox feels too slow with tabs so i use galeon which feels snappier. 

-shawn

---

