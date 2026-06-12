---
title: "Install NVIDIA and Xserver does not start"
date: 2006-12-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cariboo1938 on 2006-12-25
I have installed:
Ubuntu 6.10_amd64
2.6.17-10-generic
Video Card:GEFORCE FX5200 TD128 AGP8X
and I tried to install nvidia driver 9631 following [THESE]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA#Installing_from_repository") instructions. 
After reboot Xserver does not start. I couldn't find a solution how to install nvidia drivers. 
What can I do? I tried several proposals which I found on the Forum but nothing worked yet. 
Does someone know the right procedure?
Help needed!
Merry Christmas to all who believe, and to all who don't --- too!

---

### Post by pay on 2006-12-25
Can you post```
cat /etc/X11/xorg.conf
```

---

### Post by Cariboo1938 on 2006-12-25
> **pay said:**
> Can you post```
cat /etc/X11/xorg.conf
```Thanks for the quick response.
I attached my xorg.conf

---

### Post by pay on 2006-12-26
You are using the nv driver, change it to the nvidia driver. eg ```
Section "Device" 
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]" 
Driver "nvidia" 
BusID "PCI:1:0:0"
```

---

### Post by logos34 on 2006-12-26
Have you tried Method 2 on the nvidia driver install howto? 

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

If that doesn't work then go with the 8776 driver install (method 1).  You should not have any problems with the latter.

---

### Post by Cariboo1938 on 2006-12-27
> **logos34 said:**
> Have you tried Method 2 on the nvidia driver install howto? 

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

If that doesn't work then go with the 8776 driver install (method 1).  You should not have any problems with the latter.Thank you logos34 for the reply. Yes, I tried both. As soon I get 'nvidia' instead of 'nv' in File xorg.conf 
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nv"
EndSection
the x server does not start after reboot.
Now I try automatix. Maybe I have not the right kernel version?

---

### Post by Cariboo1938 on 2006-12-27
> **pay said:**
> You are using the nv driver, change it to the nvidia driver. eg ```
Section "Device" 
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]" 
Driver "nvidia" 
BusID "PCI:1:0:0"
```I have the video card GeForce FX5200 AGP8 . What would I have to use in this case?

---

### Post by logos34 on 2006-12-28
you might want to glance over this link (from an ubuntu page):

[https://bugzilla.novell.com/show_bug.cgi?id=113203](https://bugzilla.novell.com/show_bug.cgi?id=113203)

might shed some light on your problems.

Also:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
 
[https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper) (-->'Problems section' - see if there's anything not mentioned in the edgy version)

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) (if you try manual install again see section 'Remove Conflicting Software')

Either driver supports your card (geforce 6200 turbocache).

see:
[http://download.nvidia.com/XFree86/Linux-x86/1.0-8776/README/appendix-a.html](http://download.nvidia.com/XFree86/Linux-x86/1.0-8776/README/appendix-a.html)
[http://download.nvidia.com/XFree86/Linux-x86/1.0-9631/README/appendix-a.html](http://download.nvidia.com/XFree86/Linux-x86/1.0-9631/README/appendix-a.html)

There is an kernel update problem affecting the 9631 driver but that does not appear to apply in your case. 

The generic kernel is not the problem. 

By all means try automatix method.

---

### Post by Cariboo1938 on 2006-12-29
> **logos34 said:**
>  
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
 [https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper) (-->'Problems section' - see if there's anything not mentioned in the edgy version)
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) (if you try manual install again see section 'Remove Conflicting Software')
Either driver supports your card (geforce 6200 turbocache).
see:
[http://download.nvidia.com/XFree86/Linux-x86/1.0-8776/README/appendix-a.html](http://download.nvidia.com/XFree86/Linux-x86/1.0-8776/README/appendix-a.html)
[http://download.nvidia.com/XFree86/Linux-x86/1.0-9631/README/appendix-a.html](http://download.nvidia.com/XFree86/Linux-x86/1.0-9631/README/appendix-a.html)

There is an kernel update problem affecting the 9631 driver but that does not appear to apply in your case. The generic kernel is not the problem. 

By all means try automatix method.Thank you logos34 for the excellent list of knowledge resources concerning NVIDIA driver installation. I keep you posted and for now I wish you all the Best for the New Year.
Cariboo

[COLOR="DarkOrchid"]UPDATE: "By all means try automatix method"[/COLOR]
My file "xorg.conf" tells me that I have the graphic driver "nv" installed.
> EndSection
Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nv"
EndSection
Section "Screen"I followed the instructions to 'Remove Conflicting Software' [HERE]("https://help.ubuntu.com/community/NvidiaManual") and then I tried to use Automatix2 to install a new nvidia driver and got the following warning:> Automatix has detected that the correct nVidia driver is either correctly installed or you are attempting to overwrite an existing driver installation. This is NOT recommended.If you still want to continue hit YES, or else hit NO to resume with the rest of the options chosen.Now I'm confused:confused:  and don't know how to check which driver is installed?

---

### Post by Cariboo1938 on 2007-01-05
Thanks all for helping!
I gave up the idea to install NVidia driver version 9631 on Edgy Eft. 
Instead I used ```
sudo apt-get install --reinstall linux-restricted-modules-`uname -r` nvidia-glx
```to install nvidia drivers. 
I also had to edit /etc/X11/xorg.conf where I replaced "nv" by "nvidia". 
After reboot, during a split of a second I saw the nVidia  Logo and after that the X server started. 
I wonder how I could check which driver version I have installed now? Is there an upgrade possible for newer driver versions?

---

### Post by logos34 on 2007-01-05
> I wonder how I could check which driver version I have installed now

$ nvidia-settings

Look under opengl/glx info.

---

### Post by Cariboo1938 on 2007-01-07
> **logos34 said:**
> $ nvidia-settings
Look under opengl/glx info.Thanks logos34, this "nvidia-settings" is a cool tool. Where could I find other such helpful commands? Is this "opengl/glx info" a command or a web site?

---

### Post by logos34 on 2007-01-07
no it's in the nvidia-settings window -- 'NVIDIA X Server Settings'.  The driver should also be listed on 'Graphics card info' just under the penguin icon.
On the left pane click 'your-desktop' to drop it down and you should see opengl/glx

---

### Post by AzureCHENG on 2007-02-28
I had the ubuntu 6.06.1 Dapper and Nvidia driver  NVIDIA-Linux-x86-1.0-9746-pkg1 and had the same problem.

But I find out if I re-install the driver and do a gdm restart then it will working find.  Now I using this methord to work around it.

Hope this can help!

---

### Post by Cariboo1938 on 2007-03-10
What finally worked for me to install NVIDIA's newest driver


Follow the instructions at:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by manjo on 2007-03-10
Install linux sources, header files.

- google for NVIDIA-Linux-x86_64-1.0-9746-pkg2.run

- download it 

- Alt+f1, kill gdm, kill X

- run NVIDIA-Linux-x86_64-1.0-9746-pkg2.run, it will ask a bunch of questions answer them appropriately and you should be good to go, if you dont know what the answer is, answer YES to all the questions. 

Cheers

---

### Post by Moordrik on 2007-03-13
I had the same problem you did regarding trying to get the proprietary Nvidia drivers to install and X to start correctly every time I rebooted.  I was about to give up then came across a script that takes care of this for you, and it actually worked VERY well.

is called ENVY and you can get it at:[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

It autodetects what your card is (Nvidia or ATI) and downloads the proper driver, dependencies for the driver, builds the driver, installs the driver, and configures x.org for you.  It worked like a charm for me.  


Sending props to this guy for creating this!

---

