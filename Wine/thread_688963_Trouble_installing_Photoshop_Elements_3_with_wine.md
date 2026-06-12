---
title: "Trouble installing Photoshop Elements 3 with wine"
date: 2008-02-05
forum: Wine
---

### Post by Kakteed on 2008-02-05
I am having trouble installing Photoshop Elements 3 with wine. My wine version is 0.9.54, and I have both IE and microsoft standard fonts installed.

I am trying to install from a software bundle that I received with my wacom graphire tablet, that includes Photoshop Elements 3.0, Corel Painter Essentials 2, and nik Color Efex Pro 2.0 GE. Currently Photoshop Elements 3 is the only program I want from that.

I cannot seem to run the setup.exe for photoshop elements 3 with wine. I have tried both clicking on it and selecting 'run with wine' (which does nothing) and doing it through the terminal. The command I enter is wine /media/cdrom0/"photoshop elements 3"/setup.exe and when I hit enter it tells me wine: could not load L"D:\\photoshop elements 3\\setup.exe": Module not found.

I am not sure why this is; I know that that is where the setup.exe is, because I have checked the path in the item properties.

Can anyone tell me how to fix this, or what I'm doing wrong? I am very new to Ubuntu, but I thought that I was doing this correctly.

I am also sorry if this is the wrong section.

---

### Post by Kakteed on 2008-02-06
Anybody?

---

### Post by Kakteed on 2008-02-09
Please? I really have no idea what to do, and I would very much like to be able to use my software!

---

### Post by itsjustarumour on 2008-02-10
Hi Kakteed,

I think you might have the command slightly wrong.  Try this in the terminal:

> wine "/media/cdrom0/photoshop elements 3/Setup.exe"

If that doesn't work, make sure you have checked out what does - and does not - run on Wine at [http://appdb.winehq.org/](http://appdb.winehq.org/)

Also remember that file names in Linux are case-sensitive, so if the above doesn't work maybe try substituting the words photoshop elements 3 with Photoshop Elements 3

Hope this helps, and welcome to Ubuntu!

itsjustarumour

---

### Post by Niklas Schröder on 2008-02-14
you have to stick "sudo" in front of the command to give it write permission.  photoshop elements 3 doesn't install sadly...  painter essentials installs without a hitch though.  photoshop needs directx which linux just doesn't do.  sorry...

```

sudo wine '/media/cdrom0/photoshop elements 3/setup.exe'

```

---

### Post by itsjustarumour on 2008-02-14
> **Niklas Schröder said:**
> you have to stick "sudo" in front of the command to give it write permission.  photoshop elements 3 doesn't install sadly...  painter essentials installs without a hitch though.  photoshop needs directx which linux just doesn't do.  sorry...

You can still install Photoshop with Wine though, I'm running Photoshop 6 and it works really well!

> 
sudo wine '/media/cdrom0/photoshop elements 3/setup.exe'


The "sudo" command isn't actually required in this case, as all the apps installed with Wine are installed into the user's Home directory at /home/(username)/.wine/drive_c/Program Files by default rather than (for example) /usr/share so regular user permissions will suffice eg 

> wine "/media/cdrom0/Adobe Photoshop 6/Setup.exe"

was all that I needed to type into a terminal install Photoshop 6.

---

### Post by Niklas Schröder on 2008-02-14
I know it's installed in the /home directory, but for some reason, the installer wouldn't even try to run unless you used "sudo."  But Photoshop Elements 3 and Corel Painter Essentials dot' work.  Painter Essentials installs but it won't let you do anything.  Photoshop just crashes after showing a logo and picking a language.  Oh well.  I'm content with Gimp. 

It could just be an issue with the way the Wacom disk is laid out, it's possible that a bootleg copy might install and run fine.  ;)

---

### Post by itsjustarumour on 2008-02-14
> **Niklas Schröder said:**
> 
It could just be an issue with the way the Wacom disk is laid out, it's possible that a bootleg copy might install and run fine.  ;)

Me?  A bootleg copy of Photoshop?  ;-)

---

### Post by Niklas Schröder on 2008-02-14
Lol.  Well, if you own it, it's not *exactly* illegal.  ;)

---

### Post by itsjustarumour on 2008-02-15
> **Niklas Schröder said:**
> Lol.  Well, if you own it, it's not *exactly* illegal.  ;)

Lol, indeed, "possession is nine tenths of the law" as they say!  ;-)

---

