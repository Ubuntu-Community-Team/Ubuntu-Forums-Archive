---
title: "nvidia + drivers = no ubuntu"
date: 2007-02-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by #Reistlehr- on 2007-02-03
So the past couple days, i've been sweating it out, and its just, getting bad now. 

I switched from ms to ubuntu, cause i just felt like a change.

Now, i have a HP dv9000z laptop, AMD Turion x2 TL-60, 2 gig ram, nVidia Go7600, broadcom 4310 wireless.

Now, i got ubuntu to install fine yesturday, i even had it running fine, i dont know how i did it, but once i installed the wireless drivers it died. but right now, the main thing is the nvidia drivers. something with the ndiswrapper killed it.

I followed tha albermilone thing in the wiki, and now in the xorg.conf, when driver is set to nvidia, i get a failed to initialize the nvidia graphics device!, but when its set to nv, it works fine, but crappy. Now, i wanted to install beryl, and yesturday it was working fine.

i honestly have no idea how i got it to work, ive been using linux for 3 days now. 

i ended up teaching myself VIM, since i spent 90% of my day using it, playing with the xorg.conf.

honestly, there are so many wiki's and tuts out there that say complelet diffrent things, and keep confusing me, i know one of them got it to work, but i dont know where it is lol.

i wanna completley destroy my 2k parts and use nix 100%, but if i cant seem to get it working, i think ima stick on ms. 

Can anyone give me some pointed on the following:
-installing nvidia drivers (i get a no libc found -- fixed, but i still get the no screens found when driver is set to nvidia. works when its set to nv, but i get a crappy picture, and beryl dont work)
-i can instll beryl fine
-installing wireless broadcom bcm4310 drivers 
-install wine and the directories everything gets sent to... (i installed it with the libs, and linux32 emulator, just i dont know where the programs get sent to)


thanks so much!!!!!!!

---

### Post by phansiizwe on 2007-02-03
> install wine and the directories everything gets sent to...

Do you mean where wine puts your windows programs?

That's under: /home/USER/.wine/

---

### Post by Sqwishy on 2007-02-03
What guide did you follow for installing you're nvidia drivers. If you didn't install them you can download automatix (searchy in synaptic i think its automatix2) then look around and check nvidia drivers and install. Then x shoudn't crash.
For beryl check out teh link!
[http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl+howto](http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl+howto)

Oh and if you dont find automatix check you're repos in synaptic and check the multiverse and universe ones :]

---

### Post by #Reistlehr- on 2007-02-03
> **phansiizwe said:**
> Do you mean where wine puts your windows programs?

That's under: /home/USER/.wine/

thhaank you, thats like one of the main things i couldnt find out yesturday when i had it working. now i just need to get the nvidia drivers up, and i should be fine. 


im gonna check for automatix2.. thank you too

---

### Post by #Reistlehr- on 2007-02-03
well i couldnt fin it after enabling the extra repositories, so i just added automatix to the list and ran it. installed it for the amd64, and bam. now just to see if it installs fine with no x problems.

installed fine. woot. nv splash comes up, which i adore, lol. 

i think this has something to do with installing the nvidia drivers with automatix, my dkestop freezes after about 30 seconds, cant ever ctrl-alt-f2, or restart x.

---

### Post by #Reistlehr- on 2007-02-03
yep. seems that the install of automatix2 and the nvidia drivers make it freeze. i cant even get into tty to run vim to check the conf because it just freezes

---

### Post by #Reistlehr- on 2007-02-03
well, i seem to be in a loop :P i said screw the nvidia drivers, because everythihng i tried kept crashing x. only time i can get a GUI is when driver is set to nv. which is really weird. 

i used automatix2 to instal the drivers, and it kept freezing the after logging on.
i used the envy script, i used nvidia-glx, i used nvidias .run, and they all crashed x.

i just installed AIGLX and installed beryl, and i kept gettings a looping login.

I am pretty much at a loss now. I dont remmeber how i got it working yesturday. i cleaned my desk area today and threw away the pizza box i wrote all my documentation on :'( damn cleanliness.....

Does anyone have any pointers on waht to do? I know i had it working, i was even playing ET, i just cant remmeber what i did to get it to work. hit me up straight forward, takes 43 seconds to install ubuntu, thanks to the image i made. so, any pointers to help out this lil noob would be greatly appreciated. 

**swears to never use MS except for work if he gets it working**




The last thing i tried, [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA)
resulted in the same x crash, no creens found, failed to initialize the nvdiai graphics device.

my mind hurts, and im stumped. any help?

---

### Post by John.Michael.Kane on 2007-02-03
#Reistlehr- have you tried doing a clean install,and then installing the drivers. ie doing the driver install before running update manager.

```
Frist  run sudo gedit /etc/apt/sources.list add the line below to your sources.list
deb [http://www.albertomilone.com/drivers/edgy/latest/64bit](http://www.albertomilone.com/drivers/edgy/latest/64bit) binary/

Then run:
run sudo aptitude update

Next:
sudo aptitude install nvidia-glx

Backup your unmodified xorg:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

Enable the driver:
sudo nvidia-xconfig

Type this in terminal:
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

Copy paste this as is into the new file:

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA X Server Settings
Exec=nvidia-settings
Icon=
StartupNotify=true
Terminal=false
Type=Application
Categories=Application;System;
```

---

### Post by #Reistlehr- on 2007-02-03
to come to think about it, my image was after all the updates.. erm.. i didnt even give that a thought. right now, i just installed the pkg-config and xserver-xorg-dev packages, and im gonna uninstalled -glx, and give it one more shot, if not, ill do exactly as you suggest, thank a ton.

---

### Post by #Reistlehr- on 2007-02-03
@plissken

nope, crashed x with the same error of failed to initialize thenvidia graphics device.

ahh, this is getting to be a burdon. haha

---

### Post by #Reistlehr- on 2007-02-03
I LOVE LINUX!!!!!

i as so dumb, ahhh, i forgot to turn off apic ontop of the acpi=off in the bootline..

---

### Post by Sqwishy on 2007-02-05
> **#Reistlehr- said:**
> I LOVE LINUX!!!!!

i as so dumb, ahhh, i forgot to turn off apic ontop of the acpi=off in the bootline..
:lolflag: Linux loves you too!

---

