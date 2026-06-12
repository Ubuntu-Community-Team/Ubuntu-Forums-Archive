---
title: "Freeze after log in"
date: 2006-05-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by synapz on 2006-05-13
(EDIT FROM LAST POST)

I have installed the linux for my AMD 64 but had toi change the driver of my nvidia 7700gt to vesa instaead of nv for it to work, now im wondering is it possible to install my AOL DSL on Linux?

[http://yolinux.com/TUTORIALS/LinuxTutorialAOL.html](http://yolinux.com/TUTORIALS/LinuxTutorialAOL.html)

I found this but dont understand it


any help would be apreciated.

pc specs

CPU: DualCore AMD Athlon 64 X2, 2366 MHz 
Motherboard: MSI K8N Diamond / K8N SLI Platinum (MS-7100) (3 PCI, 2 PCI-E x16, 4 DDR DIMM, Audio, Gigabit LAN, IEEE-1394)
VGA: BFG 7800 GT
1.50 GB of RAM 
DangerDen Ultimate Water Cooling Pack
Hiper Type-R 580W Modular Power Supply - Black (SLI Certified)

---

### Post by turbojugend_gr on 2006-05-13
Hi there, first of all I have a very similar system to yours, so I can help you big time. Since you just installed, try to reinstall your system and follow the instructions.

I assume that you experience no problem during the setup, if not plz inform me for it as accurately as possible.

When you are done with the setup be carefull to choose the Resolutions that your monitor supports. Remember to use the Spacebar to select them or deselect them. 
I own an nVidia 7800GTX and had no problem with my first boot so you shouldn't too. Propably something wrong with your choices during installation, anyway. If you still experience the same problem try opening a terminal (CTRL+1 for instance) and type:```
sudo pico /etc/X11/xorg.conf
``` by doing so a text based editor should open with the configuration file of your X server (the actual Window Manager). To exit this when you are done you should CTRL+X and answer Y(yes) to save changes.
Try to find the point where it says Section Device and try changing this "VESA" or something to "nv". after you are done you should be ok, if not I am here for more help.

---

### Post by synapz on 2006-05-13
i cant open nothing with ctrl + f1 It wont work on the login screen and if i log in it freezes before i can press crl +f1. I just tried to install another version of linux and the same thing happened there. I do know when ubuntu is loading up i see a line saying PCI: Cnnot alocate 3rd section or somtething. And later on when everything checks with ok i get one fail, Chosing resolution i think it was. something along those lines. Thanks

---

### Post by synapz on 2006-05-14
also i just tried installing Fedora and i got to a screen where it said "Using anaconda to install" or something like that . then the next line said "Probing for video card; nvidia corporation uknown device 92". Then a screen poped up with an X for a cursor but after a few seconds the screen went distorted it lines. Maybe a VGA porblem wih Linux?

---

### Post by tymek666 on 2006-05-14
Try login into text mode (choose safe mode in grub) and then edit xorg.conf.

---

### Post by tseliot on 2006-05-14
[QUOTE=tymek666]Try login into text mode (choose safe mode in grub) and then edit xorg.conf.[/QUOTE]
That is "Recovery Mode" ;)

---

### Post by slfd2525 on 2006-05-14
actually...

at the login screen, you must press ctrl-alt-F1
this takes you to the CLI
I had to edit xorg.conf as well, the refresh rate was too high for my work monitor.

---

### Post by tseliot on 2006-05-14
[QUOTE=slfd2525]actually...

at the login screen, you must press ctrl-alt-F1
this takes you to the CLI
I had to edit xorg.conf as well, the refresh rate was too high for my work monitor.[/QUOTE]
Actually "Recovery Mode" doesn't start the Xserver.

What you did is getting to the CLI after the xserver crashed. That's an option when the Xserver doesn't make freeze the entire computer.

---

### Post by synapz on 2006-05-14
lol, guys im brand new to this, i havnt got a clue what to do lol, tell me a little clrearer please im thick ](*,)

---

### Post by tseliot on 2006-05-14
Almost as soon as you turn on your computer you will be able to see the GRUB menu (which contains the list of your kernels)

Select the line with "Recovery Mode" and press ENTER.

The xserver won't be started (i.e. you'll see only the command line)

then type:
```
nano -w /etc/X11/xorg.conf
```

Scroll down the file with your keyboard and get to the "Section Device".

Then set the driver to "vesa" instead of "nv".

Press CTRL+X to exit (save the file)

Then reboot by typing:
```
reboot
```

Boot as usual and your video should work. Then I suggest you to install the nvidia proprietary driver (so as to enable 3D acceleration and a better video quality). I've written a guide and a script (to automate the installation) about that.

---

### Post by synapz on 2006-05-14
MWHA! I love you it works now!

---

### Post by tseliot on 2006-05-14
[QUOTE=synapz]MWHA! I love you it works now![/QUOTE]
Now you can use my script to install the driver:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

---

### Post by synapz on 2006-05-14
it wont work because i currently have no internet connection because i have AOL and i dont know how to get it to work on Linux, i found [http://yolinux.com/TUTORIALS/LinuxTutorialAOL.html](http://yolinux.com/TUTORIALS/LinuxTutorialAOL.html) but i dont understand how to install it lol

any help on this would be fantastic

---

### Post by tseliot on 2006-05-14
[QUOTE=synapz]it wont work because i currently have no internet connection because i have AOL and i dont know how to get it to work on Linux, i found [http://yolinux.com/TUTORIALS/LinuxTutorialAOL.html](http://yolinux.com/TUTORIALS/LinuxTutorialAOL.html) but i dont understand how to install it lol

any help on this would be fantastic[/QUOTE]
sorry but I've never used AOL

---

