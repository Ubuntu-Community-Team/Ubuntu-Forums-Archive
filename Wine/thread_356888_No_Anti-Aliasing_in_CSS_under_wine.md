---
title: "No Anti-Aliasing in CSS under wine?"
date: 2007-02-08
forum: Wine
---

### Post by thewierdone2000 on 2007-02-08
Hey, I am trying to get CSS running properly under linux in wine. So far all but two things seem to be working.

The first one being that I cant select any anti-aliasing, the only option in the drop down box is "none". I run a 7800GTX with the nvidia drivers, and my frames in game are stable, so I was wondering if anyone knew how to enable AA?


Also, I was wondering how to get the game to actually run in full screen. I have the resolution at 1280*1024 (same as my desktop) but it just fills the entire desktop. The gnome task bar/Top bar both show on top of the css window.


Thanks!

---

### Post by buttons on 2007-03-03
This comes a bit late, but for anyone else out there that needs this the solution is pretty simple.  It assumes you have the nvidia drivers and direct rendering working well.

The key is the program nvidia-settings, which is an amazing utility that ships with the nvidia driver.

Running ```
nvidia-settings --load-config-only
```will load any config you have saved in your home directory automatically, should you have already configured the program once or twice.  You can set your FSAA options there, which will be loaded upon running the above command.

Running ```
nvidia-settings -a FSAA=num
```will just set full scene antialiasing for you, where num is the FSAA number appropriate to your card, found in the nvidia driver [readme]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/README/appendix-e.html"). 

Personally I like to run CS on a clean xorg desktop, so I put the following in my ~/.xinitrc```
nvidia-settings -l
nvidia-settings -a GPUOverclockingState=1 -a GPU3DClockFreqs=495,1113
xset m 1/0
~/cstrike
```
The first command loads my nvidia settings (same as --load-config-only), and the second command is necessary because nvidia-settings flatly refuses to put overclocking settings in its config file to protect people from themselves.

The third command there changes mouse motion to 1 (speed) and 0 (acceleration), which is necessary for my Razer diamondback, otherwise it's impossible to control.

The last obviously runs counterstrike, which if anyone's curious looks like this:```
#!/bin/bash
export WINEDEBUG=fixme-all
schedtool -I -e wine "C:/Program Files/Steam/Steam.exe" -opengl -heapsize 512 -width 640 -height 480 -fullscreen -applaunch 10 -console
```Schedtool is basically for ck kernels only (I run [beyond2]("http://iphitus.loudas.com/beyond.html") atm), so unless you've got one, don't use it.  Yes, applaunch 10 is CS 1.6, but the same idea applies for Source.

To run CS without the frilly stuff now, you simply:```
sudo /etc/init.d/gdm stop
startx
```

And restart gdm when you want to get back to your desktop later.

Hope that helps someone!

---

### Post by ijjz on 2007-03-03
> **buttons said:**
> ```
nvidia-settings -l
nvidia-settings -a GPUOverclockingState=1 -a GPU3DClockFreqs=495,1113
xset m 1/0
~/cstrike
```
The first command loads my nvidia settings (same as --load-config-only), and the second command is necessary because nvidia-settings flatly refuses to put overclocking settings in its config file to protect people from themselves.

The third command there changes mouse motion to 1 (speed) and 0 (acceleration), which is necessary for my Razer diamondback, otherwise it's impossible to control.

Awesome, I was wondering about how to enable OC'ing last night.

---

### Post by rennen01 on 2007-03-08
Great info.  Time to test :)

---

### Post by downhillgames on 2007-09-08
First of all, you are editing conf files that don't need to be touched to save resources, etc. You can simply run a seperate X session and your first one will be backgrounded while you are in the 2nd. See this link: [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+extra+XServer](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+extra+XServer)

Secondly, you are telling people to pass args that most likely will not fit their machine specs. (heapsize, especially.)

Thirdly, if you want to overclock your nvidia GPU under Linux, use nvclock or , in Xorg.conf, there is an option enable coolbits.

Fourthly, if you want real FSAA/SM3.0/VS3.0/etc support, use Cedega 6.0 or greater (This does cost a subscription fee or compile it from SVN yourself).

Lastly, you shouldn't be telling people to stop GDM and such to play a game. This is ridiculously over-the-top and pointless.

Hope that helps clear things up,
downhill

---

