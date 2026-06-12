---
title: "nVidia graphics driver installation help."
date: 2006-07-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Ausus on 2006-07-30
Hi All,

I'm Trying to install the latest nVidia graphics driver with the run extension.
I'm running into problems.

I tried to load the driver as per nVidia web-site.
I was running into problems then, was told I was not in the "root".
I solved this with sudo -i, then I could carry on installing.
Now next problem is x-Server is running.

What do I do now.


Regards

:confused:

---

### Post by Titus A Duxass on 2006-07-30
Try using Automatix, that installs nvidia for you.

---

### Post by Ausus on 2006-07-30
Hi Titus,

I dont have Internet on my Ubunto linux box.

Where can I offload the file in question.


Regards

---

### Post by Titus A Duxass on 2006-07-30
Okay, that is a problem.  
How did you get the drivers in the first place?

What do you mean the x-server is running?

Normally nvidia settings do not start until you restart X, do this by logging  out or the windows way (reboot).

---

### Post by Ausus on 2006-07-30
Hi Titus,

I use my work PC at work, and off-load files I require.

The last comment from the nVidia driver suggest that I switch off X Server.


Regards

---

### Post by Titus A Duxass on 2006-07-30
Did you try restarting the X-server by logging out or rebooting.

Can you give more information about the last message?

---

### Post by tseliot on 2006-07-30
Please, read my guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

### Post by Ausus on 2006-07-30
Hi Titus,


I never made a screen snap shot of the problem.

It seem some how I first have to switch the X server off, before the nVidia graphics card will continue.

nVidia say's that prior to begining the installation you should exit th X server and kill all OpenGL application. The default run level should also be at VGA level and not directly to X.


Regards

---

### Post by Titus A Duxass on 2006-07-30
Do as TSEliot says. He has put together a really good guide.

---

### Post by Ausus on 2006-07-30
Hi Titus,

Could yuo direct me to this guide.


Regards

---

### Post by Titus A Duxass on 2006-07-30
Click on the link in his post.

---

### Post by Ausus on 2006-07-30
Hi Titus,

I was to quick with the scrool button.



Regards

---

### Post by Ausus on 2006-07-30
Hi tseliot,


I will follow your script and do the installation.


Regards

---

### Post by Ausus on 2006-07-31
Hi Titus or Tseliot

Do you ever time you install nVidia driver that you have to re-compile the kernel to get the graphics card installed.


Ok I dont have internet access from home on my Linux box.
Thus I have to do it the hard way.
This is the file which I have:NVIDIA-Linux-x86_64-1.0-8762-pkg2.run What else is required that should be on my system.(For example using the nVidia guide Method 1 to 3.

The above mentioned file will it run on the current Ubuntu kernel or not.

The script file which I off-loaded requires internet access on you linux box.


Regards

---

### Post by dazvid on 2006-07-31
> **tseliot said:**
> Please, read my guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

tseliot has already posted in this thread ^

---

### Post by Titus A Duxass on 2006-07-31
Okay, have you tried following the how-to from tseliot?

What steps have you done so far?

---

### Post by Ausus on 2006-07-31
Hi Titus,

I have done the script file, need internet access.

I looked at the help file how to install nVidia drivers.

My question is do I need to compile every time I do driver upgrade even if I dont upgrade my Kernel.

Can I skip the compile thing and do a straight install.

---

### Post by Ausus on 2006-07-31
Hi All,

I'm battling to get the driver installed under Method 2:
My graphics card Nvidia XFX 7800GTX graphics card.

If I use the following commands from Method2:

1)sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

It tries to obtain the missing files via the internet.
My Ubuntu linux kernel is default as per installation.

2)sh /path_to_the_installer/NVIDIA-Linux-x86-1.0-8762-pkg2.run --extract-only

At the command promt "no such file or directory".

At this point I'm stuck.

---

### Post by ferox_2 on 2006-07-31
.

---

### Post by _teo_ on 2006-08-01
Hi, I might get you wrong, but... I'll try to explain.

> **Ausus said:**
> 
2)sh /path_to_the_installer/NVIDIA-Linux-x86-1.0-8762-pkg2.run --extract-only

At the command promt "no such file or directory".

At this point I'm stuck.

This should be interpreted as follows:
1) I usually copy the NVidia driver in location like /tmp
2) you may type in console ```
ls /tmp
``` and you should see the NVIDIA-Linux-x86-1.0-8762-pkg2.run in there
3) at last you type in console ```
sh /tmp/NVIDIA-Linux-x86-1.0-8762-pkg2.run --extract-only
``` and it should work, because path_to_the_installer is tmp in this case

And yes, you need to recompile your driver every time the kernel is updated.

PS: I must acknowledge that I followed tseliot's guide and it works.

---

### Post by Ausus on 2006-08-01
Hi _teo_

Tnx for your post.
I'm new to Ubuntu-Linux.Still learning.
At least from your post I have learned something.
I can see where I made my mistake.

Regards

---

