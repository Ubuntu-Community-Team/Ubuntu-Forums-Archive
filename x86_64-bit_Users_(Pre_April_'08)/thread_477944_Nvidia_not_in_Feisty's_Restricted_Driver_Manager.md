---
title: "Nvidia not in Feisty's Restricted Driver Manager"
date: 2007-06-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by roncrump on 2007-06-18
Hi,

I am just in the process of transferring to the 64-bit version of Ubuntu - when I bought my new laptop I didn't realise I was buying a 64-bit beast and have been running the 32-bit version for a while. I didn't give it a thought - I assumed the default option was still 32-bit.

Anyway, when I was running 32-bit the nvidia drivers showed up in Feisty's Restricted Driver Manager (which is a really nice addition as managing the nvidia drivers on my previous machine under earlier versions of Ubuntu could get a bit scary at times), but under the 64-bit version does not.

Is this something I have or haven't done? Or is it a "feature"?

Will I need to go back to following tselliot's guides to installing the drivers, or can I just apt-get one?

Ron.

---

### Post by John.Michael.Kane on 2007-06-18
Restricted Driver Manager should be installed by default under system--->administration-----restricted driver manager


You check to see if Restricted Driver Manager installed by running the command below

```
sudo aptitude install restricted-manager
```


Edit heres a list of current bug in the restricted-manager. If you feel your issue is a bug you may want to add it to the list.
[https://launchpad.net/ubuntu/+source/restricted-manager/+bugs](https://launchpad.net/ubuntu/+source/restricted-manager/+bugs)

---

### Post by roncrump on 2007-06-19
Thanks for that, but I know that the Restricted Driver Manager is installed and running - the driver for my wireless card was installed and available through it.

My question is rather why the Nvidia driver is not listed in this tool and available to select and activate, as it was under the 32-bit version of Feisty.

---

### Post by Cappy on 2007-06-19
It's a bug, no idea why.

Thankfully, installing it yourself is easy. I see you have a nvidia Geforce 4 Go so you will need the legacy drivers.

```

sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings

```
```

sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
sudo apt-get install nvidia-glx-legacy linux-restricted-modules-`uname -r`

```
(reboot)

Then you can change your resolution with
```
sudo nvidia-settings
```
on the "X Server Display Configuration" tab and when you are done "Save to X Configuration File".

---

### Post by roncrump on 2007-06-19
> **Cappy said:**
> 
Thankfully, installing it yourself is easy. I see you have a nvidia Geforce 4 Go so you will need the legacy drivers.

Because I'm a very lucky chap, I've now got a new laptop (Dell M1210), with a 250Mb Nvidia GeForce Go 7400 TurboCache graphics card.

I guess it's still easy, just a different driver. I'll see what I can see in the info in synaptic.

Off to edit my signature to include my PC specs.

Thanks,
Ron.

---

### Post by Cappy on 2007-06-19
Oh okay, just change that to 

```

sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings

```
```

sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
sudo apt-get install **nvidia-glx-new** linux-restricted-modules-`uname -r`

```
(reboot)

Then you can change your resolution with
```
sudo nvidia-settings
```
on the "X Server Display Configuration" tab and when you are done "Save to X Configuration File".

---

### Post by roncrump on 2007-06-22
> **Cappy said:**
> 
(reboot)

Then you can change your resolution with
```
sudo nvidia-settings
```
on the "X Server Display Configuration" tab and when you are done "Save to X Configuration File".

There seems to be some problem, I followed (well cut and pasted) the instructions in the previous post, then rebooted and ran nvidia-settings and got the following errors:

ERROR: NV-CONTROL extension not found on this Display.

ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.

ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.

ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.

Then within nvidia-settings there was no "X Server Display Configuration" tab on which to set the resolution.

And my xorg.conf still lists nv as the device driver for the display.

Any sugggestions?

Cheers,
Ron.

---

### Post by Cappy on 2007-06-22
=-/

I searched on it ...
It seems the solutions are:
Restricted Drivers Manager (which isn't showing up)
Using envy [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
Or using [http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_2](http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_2)

---

### Post by roncrump on 2007-06-23
Envy seems to have done the job. Thanks for your help.
Ron.

---

### Post by bkly-dog on 2007-06-25
I'm worried about using envy because of having to back things out when upgrading the os, etc., and using something un-stock.

Anyway, I had the same original problem--nvidia drivers not showing up in Restricted Drivers Manager. BUT, I did download all the latest nvidia drivers for my GeForce 7600. Now, when I boot, I get an nvidia splash screen. I'm also able to use the nvidia-settings quite well.

But all the documentation for installing Beryl and other functions say "make sure that nvidia drivers are enabled in Restricted Drivers Manager." Can I safely ignore that and assume it's some kind of bug that the drivers don't show up there and just believe that they are correctly installed?

I'm running amd64 kernel on a core 2 dua Intel laptop.

---

