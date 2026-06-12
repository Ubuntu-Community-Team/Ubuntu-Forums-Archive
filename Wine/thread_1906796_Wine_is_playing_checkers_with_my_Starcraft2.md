---
title: "Wine is playing checkers with my Starcraft2"
date: 2012-01-10
forum: Wine
---

### Post by Spac3 on 2012-01-10
Hi,
1st off I'm fairly new to both Linux and this Forum.

I'm trying to get Starcarft 2 to work on Ubuntu 10.04 / Wine 1.2

So I'll start off by showing where I started:
[[IMG]http://img27.imageshack.us/img27/7884/05012012133b.th.jpg[/IMG]](http://imageshack.us/photo/my-images/27/05012012133b.jpg/)

I have "fglrx" installed as I've got an ATI Gfx card.
The following commands has also been run to get Wine up to speed.


> wget [http://winetricks.org/winetricks](http://winetricks.org/winetricks)
chmod +x winetricks
./winetricks droid fontfix fontsmooth-rgb gdiplus gecko
./winetricks vcrun2008 vcrun2005 allfonts d3dx9 win7

This is what I got now:
[[IMG]http://img100.imageshack.us/img100/2685/10012012154.th.jpg[/IMG]](http://imageshack.us/photo/my-images/100/10012012154.jpg/)

I hope someone can help me out.
Please.
_____
Spac3

---

### Post by Spac3 on 2012-01-10
Anybody got ANY ideas as to what's going on here?

---

### Post by tkmn on 2012-01-12
A newer Catalyst(fglrx) driver will probably fix the graphics corruption. I don't know which version to recommend for Ubuntu 10.04, hopefully the lastest will work.

[http://www2.ati.com/drivers/linux/ati-driver-installer-11-12-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-12-x86.x86_64.run)

#1. Uninstall fglrx
#2. ./ati-driver-installer-11-12-x86.x86_64.run --buildpkg Ubuntu/lucid
#3. sudo dpkg -i fglrx*.deb

For me SC2 runs almost perfect. Ubuntu 11.10, Wine 1.3.36, Catalyst 11.8

[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

---

### Post by Spac3 on 2012-01-12
I see you're pointing out 10.04, does 11.04 work better?

---

### Post by Spac3 on 2012-01-12
Thanks a lot man, the game is now actually working now :D

if anyone have a similar problem, I used the following lines of code

Install the prerequisite packages:
$ sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0

If you are using the x86_64 architecture (64 bit), be sure to install "ia32-libs" before proceeding!
$ sudo apt-get install ia32-libs

Download the latest Catalyst package.
This package contains both the 32-bit and 64-bit driver.
$ cd ~/; mkdir catalyst11.12; cd catalyst11.12/
$ wget [http://www2.ati.com/drivers/linux/ati-driver-installer-11-12-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-12-x86.x86_64.run)

Create .deb packages.
$ sudo sh ati-driver-installer-11-12-x86.x86_64.run --buildpkg Ubuntu/lucid

Install .debs.
$ sudo dpkg -i fglrx*.deb

Back Up xorg.conf
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

Generic Config
This will work for most people:
$ sudo aticonfig --initial -f

Test your installation
Reboot or fglrxinfo gives an error message. From a terminal window (minimal install must first start x-terminal with 'xinit'), type
$ fglrxinfo
into the terminal. If the vendor string contains ATI, you have installed the driver successfully. 
Eg.

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4770 
OpenGL version string: 2.1 (3.3.11318 Compatibility Profile Context)

---

