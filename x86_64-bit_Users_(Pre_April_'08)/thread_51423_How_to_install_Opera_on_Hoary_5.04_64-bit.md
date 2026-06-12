---
title: "How to install Opera on Hoary 5.04 64-bit?"
date: 2005-07-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Knight Palatine on 2005-07-23
I tried installing Opera using the --force-architecture option. When I attempt to launch the program, I get an error of "missing libqt-mt.so.3 library."

I tried making a link in the Opera directory to the libqt-mt.so.3 library. Still no luck.  ](*,) 

Am I doing something wrong, or do I need to use chroot? I don't know if it matters, but I'm using 64-bit e17 from Tamir's package. (It got sound working in my Firefox mediaplayer plugin. Thank you, Tamir!) 

Thanks for your help.

---

### Post by Gary Powers on 2005-07-23
[QUOTE=Knight Palatine]I tried installing Opera using the --force-architecture option. When I attempt to launch the program, I get an error of "missing libqt-mt.so.3 library."

I tried making a link in the Opera directory to the libqt-mt.so.3 library. Still no luck.  ](*,) 

Am I doing something wrong, or do I need to use chroot? I don't know if it matters, but I'm using 64-bit e17 from Tamir's package. (It got sound working in my Firefox mediaplayer plugin. Thank you, Tamir!) 

Thanks for your help.[/QUOTE]

Download the Debian (Sarge) version of Opera from their site, change to your download directory and from the command line, it's:

dpkg -i opera(whateverthefileis)

You will get an error, missing file in that process, so then do

sudo apt-get install (that package)

It will install followed immediately by Opera and you are in business.  The whole things is about three minutes work.  I create a launcher on the desktop.

Gary

---

### Post by Knight Palatine on 2005-07-24
[QUOTE=Gary Powers]Download the Debian (Sarge) version of Opera from their site, change to your download directory and from the command line, it's:

dpkg -i opera(whateverthefileis)

You will get an error, missing file in that process, so then do

sudo apt-get install (that package)

It will install followed immediately by Opera and you are in business.  The whole things is about three minutes work.  I create a launcher on the desktop.

Gary[/QUOTE]

Many thanks for the reply, Gary. 

dpkg doesn't report any missing files. I'll dig around more when I don't have to be back at work in five hours. Maybe it needs an explicit entry in $PATH.

Daryl

---

### Post by Pse on 2005-07-24
Actually, it's not that hard... I use a static version of Opera with QT compiled in =). If you get that version, you can make a small starting script that sets up the path for other needed libraries for Opera, and it will just work(tm). Flash works great, BTW...
[EDIT] Oh, you will need 32-bit Motif libs if you plan to use the Flash plugin from Macromedia with Opera...

---

### Post by Knight Palatine on 2005-07-26
[QUOTE=Pse]Actually, it's not that hard... I use a static version of Opera with QT compiled in =). If you get that version, you can make a small starting script that sets up the path for other needed libraries for Opera, and it will just work(tm). Flash works great, BTW...
[EDIT] Oh, you will need 32-bit Motif libs if you plan to use the Flash plugin from Macromedia with Opera...[/QUOTE]

Yep, using the static .deb instead of the shared package worked just fine. Many thanks.

Daryl

---

