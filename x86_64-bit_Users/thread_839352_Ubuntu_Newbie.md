---
title: "Ubuntu Newbie"
date: 2008-06-24
forum: x86 64-bit Users
---

### Post by BIGBC on 2008-06-24
About a month ago I built myself a new PC and decided I wanted to play around with it as a learning exercise, so i ordered a Ubuntu distro (Ubuntu 8.04 LTS Desktop Edition 64-bit). It arrived about a week ago and installed with no problems.
Im quite impressed, this is definitely a great OS but Ive got a few problems :

- My Resolution isnt supported; im running a 1680x1050 screen and the only options Ubuntu gives me are: 1600x1200, 1280x1024, 1024x768, 800x600 and 640x480.
Ive tried updating/installing nVidia drivers etc but dont really know what im doing.

- Maximum sound output is really quite. Ive got 160Watt speakers (shake the house powerful) and the max volume on both the speakers and Ubuntu can currently be beaten by my mobile phone =[

I think these are really driver issues, but since im new i dont know how to install the drivers i can find.

I can give you full system specs if you need.

Any help/instruction would be appreciated.

---

### Post by oldos2er on 2008-06-24
To enable the Nvidia driver, go to System, Administration, Hardware Drivers. Click the box under 'Enabled.'

 For sound, right-click on the volume control icon in your top panel, choose 'Open volume control.' You can adjust your sound from there. If that doesn't help, install gnome-alsamixer.

---

### Post by bluepowder7 on 2008-06-24
do you have a 4-channel audio card?  is there a chance that the mixer in ubuntu is sending the rear-channel "surround" sound to your front speakers?  i've had that happen once in a previous life.  also, in a new install of 8.04, the master volume was by default set kinda low (well, 80%, but that made a SURPRISING difference when i cranked it to 100%)

---

### Post by BIGBC on 2008-06-24
Ive got the sound thing figured out, as suggested i am using surround sound and in the volume control it didnt have Surround, Center or Side shown or on, so i Edit > Preferences and checked them and cranked it up.

The Resolution is still wrong, and in the System > Administration > Hardware Drivers there is nothing listed and it says : "No proprietary drivers are in use on this system." does this mean I have failed to install them ?

---

### Post by oldos2er on 2008-06-24
Which nvidia card do you have?

 You might want to install the EnvyNG package.

---

### Post by barney385 on 2008-06-24
Make sure all your repositories are enabled also. I enabled Medibuntu repo's also and they had the new nvidia driver there.

You must have an 8800?

---

### Post by xithilinx on 2008-06-24
I've got an option for you if you're interested..

There is this program for ubuntu that auto installs your video card for you automatically, and even gives you a nifty program if you've got a nvidia card. [ Not to sure about ati :( ] 

It's called Envy and will autoinstall drivers for ati/nvidia. 

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

It'll probably fix your problems with resolutions, if you don't want to get completely technical first.

---

### Post by BIGBC on 2008-06-27
I installed EnvyNG as soon as I encountered this problem (found it in the Administration > Synaptic Package Manager).
When I open it gives me (it does seem to support ATI 2 by the look of things) : 
Install Nvidia driver (automatic hardware detection)
Install Nvidia driver (Manual selection of driver)
Uninstal Nvidia driver

When I run automatic detection it does this :
EnvyNG couldnt carry out the task you chose because of the following error:
```
Traceback (most recent call last):
  File "pulse.py", line 79, in <module>
    autoChoice(sys.argv[1])
  File "pulse.py", line 16, in autoChoice
    objects.nvidiainstallg(data1)
  File "/usr/lib/python2.5/site-packages/Envy/objects.py", line 74, in nvidiainstallg
    task.drivertype()#latest, middle, oldest driver
  File "/usr/lib/python2.5/site-packages/Envy/classes.py", line 863, in drivertype
    raise Exception(error)
Exception: EnvyNG ERROR: Envy does not recognise your card as compatible with any version of the driver.this might happen because either your card is not supported by the driver or Envy's hardwaredetection failed. You can try the manual installation at your risk.

```

So I then tried manual driver installation, which gave me 3 driver options :
173.14.05
96.43.05
71.86.04

I tried running the first, and it returns with :
```
Reading package lists...


Building dependency tree...


Reading state information...


0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

oooh, it just did something different; a bubble flashed up saying system updates available and then it downloaded new updates and installed them.
gonna reboot and post the results.

ps : my Graphics card is a 9800GTX OC

*** EDIT ***

Its now all working beautifully =]
thanks for all your help.
If any of you have good theme download sites i would appreciate it.

---

