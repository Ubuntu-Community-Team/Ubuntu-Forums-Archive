---
title: "32bit to 64bit compatibilty"
date: 2007-11-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by pedro_cesar on 2007-11-19
I'm gonna install a 64bit Gutsy in my DELL Inspiron 531 which is now running 32bit Feisty, I have already been told that I have to format, that doesn't concern me anymore; since I have all the software I need, the thing is that all the software I have is 32bit (including Compiz Fusion), so I want to know if they will work under a 64bit system. If they don't where can I get them:

--Production
PGadmin
PostrgreSQL
ReportLab software for python
Python
Emacs21
Inkscape
DIA
VMWare Server
DHCP3 Server

--Eyecandy
Compiz Fusion
Affinity Search
Avant Window Navigator
Kiba Dock
gDesklets
SplashScreen

--Otros
Amarok
XMMS
Pidguin
ENVY
FireStarter

--------------------------------------------
Computer Specs.

AMD 64 X2 Athlon 5000+
2 GB DDR667 SDRAM (Right Now I also have an extra 512 DDR400 but I'm gonna take it out)
nVidia GeForce 8600GT 256MB DDR3
250 GB SATA HD
DVD-R/CD-R

---

### Post by dewey on 2007-11-19
The only problem I noticed with what you posted is the SplashScreen.  Many users of 64bit gutsy have experienced issues with their splash screens, personally, mine only shows for about 2 seconds and disappears.

But, it's not really a problem for me at all, it's just a splash screen.

---

### Post by pedro_cesar on 2007-11-19
Right Now The Eye Candy (Except for the beryl) is what worries me the least, what I really need to be sure about is the Production section, since that's what I work with.

P.S. I find that the dullest the system is, the harder it is for you to be pleased about working in that station, and therefore although Compiz Fusion is not exactly a production software, is equally important to me.

---

### Post by John.Michael.Kane on 2007-11-19
**--Production**
PGadmin
Package: pgadmin3 (1.4.3-2.1ubuntu1) location [universe] Architecture amd64
[http://packages.ubuntu.com/gutsy/misc/pgadmin3](http://packages.ubuntu.com/gutsy/misc/pgadmin3)

PostrgreSQL
Package: postgresql-8.1 (8.1.10-1) location [universe] Architecture amd64
[http://packages.ubuntu.com/gutsy/misc/postgresql-8.1](http://packages.ubuntu.com/gutsy/misc/postgresql-8.1)

ReportLab software for python
Package: python-reportlab-accel (0.60-20061203-2ubuntu1) location [universe] Architecture amd64
[http://packages.ubuntu.com/gutsy/python/python-reportlab-accel](http://packages.ubuntu.com/gutsy/python/python-reportlab-accel)

Python
Package: python (2.5.1-1ubuntu2)  Architecture
[http://packages.ubuntu.com/gutsy/python/python](http://packages.ubuntu.com/gutsy/python/python)

Emacs21
Package: emacs21 (21.4a+1-5ubuntu4) [universe] Architecture amd64
[http://packages.ubuntu.com/gutsy/editors/emacs21](http://packages.ubuntu.com/gutsy/editors/emacs21)

Inkscape
Package: inkscape (0.45.1-1ubuntu5) Architecture amd64
[http://packages.ubuntu.com/gutsy/graphics/inkscape](http://packages.ubuntu.com/gutsy/graphics/inkscape)

DIA
Package: dia (0.96.1-3) [universe] Architecture amd64
[http://packages.ubuntu.com/gutsy/graphics/dia](http://packages.ubuntu.com/gutsy/graphics/dia)

VMWare Server
[https://help.ubuntu.com/community/VMware/Server/AMD64](https://help.ubuntu.com/community/VMware/Server/AMD64)

DHCP3 Server
Package: dhcp3-server (3.0.5-3ubuntu4) Architecture amd64
[http://packages.ubuntu.com/gutsy/net/dhcp3-server](http://packages.ubuntu.com/gutsy/net/dhcp3-server)

**--Eyecandy**
Compiz Fusion
Package: compiz-fusion-plugins-extra (0.5.2+git20070928-0ubuntu1) Architecture amd64
[http://packages.ubuntu.com/gutsy/x11/compiz-fusion-plugins-extra](http://packages.ubuntu.com/gutsy/x11/compiz-fusion-plugins-extra)

Affinity Search
(Affinity seems to have been removed from the guide below, As upstream Affinity development appears to have ceased.)

Avant Window Navigator
[Repository is for Gutsy 32-bit and 64-bit.]("http://ubuntuforums.org/showthread.php?t=385981&highlight=Avant+Window+Navigator")

Kiba Dock (There is no package listed in the Ubuntu repos for this program. You may have to compile it from source.)

gDesklets
Package: gdesklets (0.35.3-4ubuntu2) [universe] Architecture amd64
[http://packages.ubuntu.com/gutsy/gnome/gdesklets](http://packages.ubuntu.com/gutsy/gnome/gdesklets)

SplashScreen (not sure what this is in reference to. only package listed in the Ubuntu repos is the one below.)
Package: gnome-splashscreen-manager (0.2-7ubuntu1) [universe] Architecture all
[http://packages.ubuntu.com/gutsy/gnome/gnome-splashscreen-manager](http://packages.ubuntu.com/gutsy/gnome/gnome-splashscreen-manager)

**--Otros**
Amarok
Package: amarok (2:1.4.7-0ubuntu3) Architecture amd64
[http://packages.ubuntu.com/gutsy/kde/amarok](http://packages.ubuntu.com/gutsy/kde/amarok)

XMMS
Package: xmms (1:1.2.10+20070601-1) [universe] Architecture amd64
[http://packages.ubuntu.com/gutsy/sound/xmms](http://packages.ubuntu.com/gutsy/sound/xmms)

Pidgin
Package: pidgin (1:2.2.1-1ubuntu4) Architecture amd64
[http://packages.ubuntu.com/gutsy/net/pidgin](http://packages.ubuntu.com/gutsy/net/pidgin)

ENVY
Architecture all
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

FireStarter
Package: firestarter (1.0.3-6ubuntu1, 1.0.3-5ubuntu1) [universe] Architecture amd64
[http://packages.ubuntu.com/gutsy/admin/firestarter](http://packages.ubuntu.com/gutsy/admin/firestarter)

Hope this helps.

---

### Post by pedro_cesar on 2007-11-19
Sooo many thanks. I'll probably format tonight then, and tomorrow -not to say later tonight- we'll see how it went :D

---

### Post by pedro_cesar on 2007-11-22
I went through all those pages, and I didn't get the info in them... Are those repositories? I installed the programas -not all yet- from the repositories and they seem to work fine... Are these programs 32 or 64 bit?

---

### Post by John.Michael.Kane on 2007-11-22
All the programs you asked about, and linked to above have 64bit counterparts which one can install from the repos using synaptic or apt-get from the terminal.

Here is an example install line for almost all the programs you asked for.
```
sudo aptitude install firestarter xmms dhcp3-server gdesklets gnome-splashscreen-manager amarok postgresql-8.1 emacs21 python-reportlab-accel pgadmin3 inkscape dia
```

python, and pidgin are already installed, and are 64bit versions. simply type python in the terminal to start using it.

Vmware, and Avant Window Navigator can be installed using the guides posted

what exactly is the problem you are having?

---

### Post by Kilz on 2007-11-22
> **pedro_cesar said:**
> I went through all those pages, and I didn't get the info in them... Are those repositories? I installed the programas -not all yet- from the repositories and they seem to work fine... Are these programs 32 or 64 bit?

Those links are to the [ubuntu package site]("http://packages.ubuntu.com/") it is a complete searchable list of all packages that are in the repositories. You could also search in synaptic for the same results.
In the Download section of each page is a list of the architecture's the package is available in. You might want to bookmark the link above in case you have any more questions about program availability.

---

### Post by pedro_cesar on 2007-11-23
I thought so, thanks for your help, I've installed all the software from the repositories already. I must say that the system indeed runs better with the 64bit version. 

Now I want to know how can I restore my SplashScreens.

---

