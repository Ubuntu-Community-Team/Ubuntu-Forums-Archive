---
title: "my NVIDIA accelarated graphics driver is not enabled! And I need it to be!!!"
date: 2008-02-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by thekylehome@gmail.com on 2008-02-18
Hello Folks!!!

I need to turn off X... Because I am trying to enable my graphics driver...

I type in:

sudo aptitude install nvidia-glx-new
and get:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

then:
sudo nvidia-glx-config enable
and get:
sudo: nvidia-glx-config: command not found

After I did that, I typed in:
wget [http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run)

and it downloaded something, and when it was done, I put in this:
sudo sh NVIDIA-Linux-x86-100.14.19-pkg1.run

Which then says:
ERROR: You appear to be running an X server; please exit X before installing. 



What can I do? I have to get this enabled...
Thanks!

---

### Post by thekylehome@gmail.com on 2008-02-18
When I type in:
glxinfo | grep rendering

I get: direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

So, I should say, HOW DO IT GET DIRECT RENDERING TURNED ON?????????? What does that LIBGL_DEBUG=verbose mean??????

I look foward to a speedy response!!!

---

### Post by mma8x on 2008-02-18
> sudo aptitude install nvidia-glx-new
and get:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

looks like synaptic or another software management program is running.  nvidia-glx-new didn't actually install.  close other programs before using apt-get.

> After I did that, I typed in:
wget [http://us.download.nvidia.com/XFree8...14.19-pkg1.run](http://us.download.nvidia.com/XFree8...14.19-pkg1.run)

and it downloaded something, and when it was done, I put in this:
sudo sh NVIDIA-Linux-x86-100.14.19-pkg1.run

Which then says:
ERROR: You appear to be running an X server; please exit X before installing.


you can't install the nvidia driver with an X server running.  go to a terminal, ctrl-alt-f1, login, type ps aux|grep gdm (or kdm, depending on your display manager).  kill all processes listed as kdm/gdm/X.  then re-run the nvidia installer.  

also, the nvidia-glx-new package isn't compatible with the nvidia proprietary driver.  install one or the other.  on my box, the open-source driver doesn't work correctly.  hth.

---

### Post by Yellow Pasque on 2008-02-18
Have you tried the Envy program to install your driver? It usually works well for nvidia cards.

---

### Post by soxs on 2008-02-19
> **thekylehome@gmail.com said:**
> Hello Folks!!!

I need to turn off X... Because I am trying to enable my graphics driver...

I type in:

sudo aptitude install nvidia-glx-new
and get:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

then:
sudo nvidia-glx-config enable
and get:
sudo: nvidia-glx-config: command not found

The command line stuff is correct, but you hadsomewhere running another thread of synaptics, this is the reason fot that error..


> 
After I did that, I typed in:
wget [http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run)

and it downloaded something, and when it was done, I put in this:
sudo sh NVIDIA-Linux-x86-100.14.19-pkg1.run

Which then says:
ERROR: You appear to be running an X server; please exit X before installing. 

What can I do? I have to get this enabled...
Thanks!

Well, you have to restart your PC with init 3 wichich des not start the x server or simply killl the xserver with /etc/init.d/gdm stop and install the nvidia binary from the console.
NOTE: I really suggest you to do it the first way, the second is somewhat tricky and requires some further knowledge...

---

### Post by jblackthorne on 2008-02-20
The current version NVIDIA proprietary driver is not that bad.  Plus, manually installing from Nvidia's site will mean that you will not longer receive automatic updates.  If you are a gamer, then you probably want the latest driver.  Though, if you are not, then the current distribution version will most likely be just fine. 

The other really critical thing is that you must know which of the Nvidia drivers to install.  There are 3 different versions available.  Gutsy normally properly detects the right driver and selects the correct package for you.  Please check Nvidia's site for complete details, though, if I recall correctly:

* Legacy Geforce 4 and older get nvidia-glx-legacy
* Geforce 4 to fairly recent get nvidia-glx
* Geforce 8 and newer get nvidia-glx-new

If you choose to go with or just want to try out the distribution version:

1.From the System/Administration menu, select &#8220;Software Sources&#8221;.
2.Ensure that &#8220;Software restricted by copyright or legal issues&#8221; is checked
3.From the System/Administration menu, select &#8220;Restricted Driver Manager&#8221;
4.You should see a listing for Nvidia there.  Just click the box to activate it.

If the Nvidia driver does not appear in the &#8220;Restricted Driver Manager&#8221;, then 

* open the Synaptic Package manager.
* Browse to nvidia-
* Activate the desired package.

If you choose to go with the current Nvidia source driver, then simply:

* <ctrl><alt>F1
* login
* type &#8220;sudo su&#8221;
* type /etc/init.d/gdm stop
* install the drivers per nvidia's instructions


P.S.  As others have stated, the &#8220;E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? error is because you had another package manager or installer currently running.

---

### Post by soxs on 2008-02-20
nvidia geforece 7 series requires nvidia-glx new aswell and I think 6 series aswell

---

