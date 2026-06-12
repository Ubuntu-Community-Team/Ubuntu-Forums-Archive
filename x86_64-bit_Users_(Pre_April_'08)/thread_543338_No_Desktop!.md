---
title: "No Desktop!"
date: 2007-09-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by ajkilroy24 on 2007-09-05
I'm new to Ubunto as i just built a new computer and after messing around (frustratingly i might add) with the vista software i decided to put on it i chose to switch to Ubunto 7.04 (64 bit). the problem im having is that i get to the login screen, input my username and password, and then this is where my problem occurrs.  It makes the sound like its loading my desktop and then all i get is a beige screen with what appears to be my desktop shrunk to a few millimeters high in the middle of the screen (random lines and colors). ive tried clicking on things and nothing i do seems to work. i even reinstalled ubunto a few times and tried the recovery mode. 

my system:

4GB DDR2 800Mhz RAM
AMD 64 X2 Brisbane 5000+ 2.6 Ghz processor
ECS KN3-SLI2 nVidia nForce 590 SLI motherboard
EVGA 7800GT video card

any advice welcome because like i said, this is my first linux system and id hate to have to go back to vista!

HELP!!!:confused:

---

### Post by pyrokenx on 2007-09-10
seems like a strange issue,

you obviously ran the CD just fine...  So there must be a working solution somehow.

Try to hit ctrl + alt + backspace... does this restart your display? does nothing happen at all?

if that doesnt do anything for you, then try ctrl + alt + F1 and see if that brings you a console

login with your normal credentials you set for yourself, then use the following command

```
sudo cp -r /etc/X11/xorg.conf /etc/X11.conf.backup
```

Then..

```
sudo nano /etc/X11/xorg.conf
```

hit pagedown till you make it to Section "Device"

change Driver "nv" to Driver "nvidia"

Hit CTRL + O, then press enter, then hit ctrl + X

Then use the following command..

```
sudo apt-get install nvidia-kernel-common nvidia-glx-new
```

then do this

```
sudo reboot
```


I am sorry your having such a bad experience, please try what I have suggested, I am not so sure but I hope that fixes your issues.  Alot of times stuff like that has to do with video.

if you cant issue those commands normally try to do them in recovery mode.

---

