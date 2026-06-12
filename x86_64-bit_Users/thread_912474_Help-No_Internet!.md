---
title: "Help-No Internet!"
date: 2008-09-06
forum: x86 64-bit Users
---

### Post by txwooley on 2008-09-06
I am a complete noob to Ubuntu.  I have tried researching my problem but it seems everyone is speaking Greek.  I loathe Windows and ordered the Ubuntu 8.04(64-Bit) disk to learn a little something.  The problem is, it won't even detect my Atheros AR5007 wireless network card.  It is listed in restricted hardware and enabled, but not in network connections.  Please forgive me if I usa too many Windows terms but I hope to be revising my vocabulary soon.  Can anyone help me in plain English?

My comp is HP Pavillion dv6000 with AMD Turion 64x2 and 3GB RAM

---

### Post by tuxxy on 2008-09-06
You read the [wireless guide ]("https://help.ubuntu.com/8.04/internet/C/index.html")

---

### Post by txwooley on 2008-09-06
I tried to use the guide like you said.  It recognizes my hardware but says it is a restricted driver.  The guide tells me how to use a windows driver-but only as a .inf file.  My stupid vista has it as a .sys file.  I can't find any .inf files like old windows used!  Do I need to DL the .inf from Atheros?

---

### Post by txwooley on 2008-09-06
I finally found the driver.  When I go to ndisgtk and select "Install new driver", I select netath.inf  It then tells me this is an invalid driver.  I tried selecting any net-... driver and get the same result.  Is this because I have a 32-bit Windows trying to install a driver for 64-bit Ubuntu?  Please help!:confused:

---

### Post by rbringh on 2008-09-06
This got my HP DV9910 going.
[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

---

### Post by cleopete on 2008-09-08
I got my Atheros from Acer's driver page.  They had both 32 and 64 bit drivers with the .inf (it's in the subdirectory "Drivers"). I have an Aspire 5100 which came with Vista (briefly), but Acer has been pretty good about supplying XP drivers for their stuff.  Acers often use Atheros, you could probably find yours there, [http://www.acerpanam.com]("http://www.acerpanam.com").

I've had problems getting it to connect, but I think that may be a keyring issue. It was fine until I installed the amd64,  I've been having a lot of problems since then.

---

### Post by Yellow Pasque on 2008-09-10
> Is this because I have a 32-bit Windows trying to install a driver for 64-bit Ubuntu?
Yes. You need a 64-bit driver.

---

