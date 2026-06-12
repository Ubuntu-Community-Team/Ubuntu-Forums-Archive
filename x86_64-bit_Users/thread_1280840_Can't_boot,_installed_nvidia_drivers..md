---
title: "Can't boot, installed nvidia drivers."
date: 2009-10-02
forum: x86 64-bit Users
---

### Post by Gl33m on 2009-10-02
I did an manual install of the newest 8 series Nvidia drivers. Now every time I boot it starts off fine, after the Ubuntu loading screen instead of going to ask me for a username or password it shows a list of text it's loading and stops right after setting the monitor sleep mode thing. I can press Ctrl+Alt+F1 and log in there, but if i try to force it to load the GUI with startx it says Fatal Error: No Screen Found.

---

### Post by wojox on 2009-10-02
When you log in run:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot

---

### Post by Gl33m on 2009-10-02
That did something; however the problem's still there.

---

### Post by Arup on 2009-10-02
In your synaptic remove linux-restricted-modules and linux-restricted-modules-common

---

### Post by Gl33m on 2009-10-03
Could you explain how to do that for me please? I'm still a bit of a noob.

---

### Post by Arup on 2009-10-03
> **Gl33m said:**
> Could you explain how to do that for me please? I'm still a bit of a noob.

Can you go to Synaptic, in case its text based, just login and type sudo apt-get remove linux restricted modules

---

### Post by Gl33m on 2009-10-03
Well it worked in the sense that it removed it. Still can't boot though, stops at the same problem. Errors for running startx

Xinit: No such file or directory (errno 2): unable to connect to xserver
Xinit: No such process (errno 3): server error
Xauth: error in locking authority file /home/gleem/xauthority

---

### Post by Arup on 2009-10-03
> **Gl33m said:**
> Well it worked in the sense that it removed it. Still can't boot though, stops at the same problem. Errors for running startx

Xinit: No such file or directory (errno 2): unable to connect to xserver
Xinit: No such process (errno 3): server error
Xauth: error in locking authority file /home/gleem/xauthority

Which nvidia package did you install, run1 or run2?

---

### Post by Gl33m on 2009-10-03
185.18.36 pkg 2 was the version, i just downloaded it from the nvidia site, went to download drivers. selected 8 series, clicked linux 64, downloaded it, CTRL+ALT+F1. logged in as root, ended /etc/init.d/gdm, sh NVIDIA.run

---

### Post by Arup on 2009-10-03
Did you do a sudo apt-get build essential Also did you do a sudo /etc/init.d/gds stop

---

### Post by Gl33m on 2009-10-04
> **Arup said:**
> Did you do a sudo apt-get build essential Also did you do a sudo /etc/init.d/gds stop

No, I didn't. Do you mean try that now, or did I do that when installing the drivers?

---

### Post by Arup on 2009-10-04
> **Gl33m said:**
> No, I didn't. Do you mean try that now, or did I do that when installing the drivers?

Those files are needed to build the drivers, its essential, you can do that in text mode as well.

---

### Post by Gl33m on 2009-10-05
Ah, okay. I missed that step then. I'll completely re-install my drivers, but I'll be sure to include those steps. I'll let you know how it goes!

---

### Post by Gl33m on 2009-10-05
I tried to do sudo apt-get build essential and it gave me an invalid error. I know I typed it exactly how you did. Also I did sudo /etc/init.d/gds stop and it said it didn't exist. Are you sure you didn't mean sudo /etc/init.d/gdm stop?

---

### Post by Arup on 2009-10-05
Sorry was late night.

should be sudo apt-get install build-essential

sudo /etc/init.d/gdm stop

---

### Post by Gl33m on 2009-10-05
Ah, okay no problem. Trying it again.

---

### Post by Gl33m on 2009-10-05
I reinstalled the drivers after getting the build essential, but no luck. I even went back through this thread and tried everything else with the newly installed drivers. It did say something about 
"primary device not PCI"
"No device detected"
Does that help at all?

---

### Post by moster on 2009-10-05
Hope you did not delete that file because you need it to deinstall. Like you install it with sh NVIDIA.run same you unistall it but with --unistall at the end.

like this: ```
sudo sh nvidia.run --uninstall
```

after that I personally go to */etc/X11* folder and get back from automatic backup my old *xorg.conf* file
maybe you can do it with, I do not know
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I would have to write crapload more of instructions for everything from start to end... hope you will get it from what I wrote.

---

### Post by Gl33m on 2009-10-05
So basically you're saying completely uninstall my drivers and revert everything back to before I installed them?

---

### Post by Gl33m on 2009-10-05
Drivers successfully uninstalled. xserver-xorg successfully reconfigured. I'm typing this on my Ubuntu partition! Now as for the drivers themselves. Care to help me -properly- install them?

---

### Post by moster on 2009-10-05
> **Gl33m said:**
> Drivers successfully uninstalled. xserver-xorg successfully reconfigured. I'm typing this on my Ubuntu partition! Now as for the drivers themselves. Care to help me -properly- install them?

Yes... I will get back to you in a while :)

---

### Post by Gl33m on 2009-10-05
Sounds great, thanks. And a big thank you to everyone else who contributed to this thread. It was very much appreciated.

---

### Post by Arup on 2009-10-05
> **Gl33m said:**
> Sounds great, thanks. And a big thank you to everyone else who contributed to this thread. It was very much appreciated.

Follow the instructions I posted. 

ctrl+alt+F2

login

sudo /etc/init.d/gdm stop

sudo sh NVIDIA and hit tab. Say yes to all prompts.

---

### Post by Gl33m on 2009-10-05
with build-essential installed
I hit Ctrl+Alt+F2
Log in
```

sudo /etc/init.d/gdm stop
cd Desktop
sudo sh NVIDIA.run

```
I agree to everything.
It still won't work.
I try sudo dpkg-reconfigure  -phigh xserver-xorg
Still won't work.
linux restricted modules aren't installed.

During the installation it does say the following

Unable to perform runtime configuration check library for 'libGL.so.1' ('/usr/lib32/libGL.so.190.32

---

### Post by Gl33m on 2009-10-05
I just tried to install the drivers through synaptic. It has the same issue. Also there seems to be an issue with xauthority. I couldn't even run synaptic without opening the terminal and forcing it to run.

---

### Post by moster on 2009-10-05
Ok, most pain free is to install it trough repos. Free easy steps and you are good to go. This is for Jaunty. **[HERE]("http://webupd8.blogspot.com/2009/08/how-to-install-nvidia-190xx-drivers-in.html")**

---

### Post by Arup on 2009-10-05
> **Gl33m said:**
> with build-essential installed
I hit Ctrl+Alt+F2
Log in
```

sudo /etc/init.d/gdm stop
cd Desktop
sudo sh NVIDIA.run

```
I agree to everything.
It still won't work.
I try sudo dpkg-reconfigure  -phigh xserver-xorg
Still won't work.
linux restricted modules aren't installed.

During the installation it does say the following

Unable to perform runtime configuration check library for 'libGL.so.1' ('/usr/lib32/libGL.so.190.32


The driver you are installing is older beta, that message you get is normal. Whats intriguing is that after all this your drivers haven't been installed properly.

---

