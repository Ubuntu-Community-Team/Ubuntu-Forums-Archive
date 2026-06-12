---
title: "64 Bit and Nvidia issue?"
date: 2009-04-23
forum: x86 64-bit Users
---

### Post by rdmike on 2009-04-23
Hi,

I currently have a Nvidia 6150e graphics adapter on a computer I bought about four days ago. Excited about the new Ubuntu release I waited to install it until version 9 came out. That said I have the image downloaded, burned, and checked for defects; all is well there. Unfortunately, when I try to run the live disk everything works well until the desktop environment loads. Then I get a black screen and my monitor (HP w2207h) says "input signal out of range."

I found a thread from February of last year [here]("http://ubuntuforums.org/showthread.php?t=697883&highlight=nvidia+6150e") and it recommended using no apic and no lapic (I think). Anyhoo, I've tried that too and still get a blank black screen.

Now, I don't like integrated graphics and have a new video card but can't install it until I get a new power supply. In the meantime can I assume Ubuntu 9.04 (64 bit) will not support my system? If so, will the 32 bit version work?

Thanks,

---

### Post by audaz on 2009-04-23
I just burned the 64-bit 9.04 cd and tried to run it live as well. It starts loading, then after the progress bar is complete, the screen goes blank and I can't do anything at all.

My specs:
Intel Core 2 Duo T8100
4G RAM
NVIDIA GeForce 9800M GTS

Edit: I checked the CD for errors, and it had none.

---

### Post by rdmike on 2009-04-23
Same as me then.

Specs, if it'll help.

HP Pavilion a6763w Desktop
AMD Phenom 9150e processor
GeForce 6150e integrated graphics controller
7 GB DDR2 RAM
640 GB WDC HD (sata 7200 rpm)
HP w2207h monitor
Realtek Integrated HD audio
Nforce 10/100 network card

Not sure if any other info would be helpful but let me know if needed/wanted.

---

### Post by audaz on 2009-04-23
Just had the same exact problem with the 32-bit cd. NVIDIA issue seems likely.

---

### Post by audaz on 2009-04-23
Just tried the 32-bit cd on my old Dell 1505 with an NVIDIA card (7 series) and it worked.

---

### Post by dBuster on 2009-04-23
Have you tried booting into safe graphics mode?

Once you get into safe graphics mode you can get the latest drivers from launchpad at the following:

[https://launchpad.net/ubuntu/jaunty/amd64/nvidia-glx-180/180.44-0ubuntu1]("https://launchpad.net/ubuntu/jaunty/amd64/nvidia-glx-180/180.44-0ubuntu1")

Works like a charm and I am running nVidia and Jaunty with smooth graphics and no video issues.

I did early on have to make this change and have not undone it since.  

The latest Nvidia drivers are NOT compatible with Xorg1.6 on Jaunty, but I hear there's a temporary workaround until the drivers catch up. It involves modifying your Xorg.conf file:

```

Section "ServerFlags"
Option "IgnoreABI" "True"
EndSection

```

Check [http://ubuntuforums.org/showthread.php?t=1026512](http://ubuntuforums.org/showthread.php?t=1026512) for more information on that.

---

### Post by Bezmotivnik on 2009-04-23
I have an nVidia-based PCIe card in my new AMD triple-core box, and the video w/9.04-64 works fine in live mode.

The menus in Gnome do not, however.  Pull-downs and pull-ups don't.

---

### Post by rdmike on 2009-04-24
I am running a Mandriva One live CD now with no difficulty at all.

I haven't tried running in safe mode yet but will give it a go.

I take it this is an issue that'll have to be resolved via an update then?

---

### Post by murrie on 2009-04-24
Hello there,

Simple solution is to boot from cd and do the install in safe graphics mode.  When finished reboot, then just install the nvidia driver as you normally would.

Have a nice day

---

### Post by rdmike on 2009-05-01
Murrie, that worked perfectly, thank you!

---

