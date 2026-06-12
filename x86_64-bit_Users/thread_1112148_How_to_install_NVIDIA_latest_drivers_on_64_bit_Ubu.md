---
title: "How to install NVIDIA latest drivers on 64 bit Ubuntu?"
date: 2009-03-31
forum: x86 64-bit Users
---

### Post by PC_load_letter on 2009-03-31
I tried to install the 180.44 driver on my laptop w/ Nvidia 8400GS and Ubuntu Hardy amd64, kernel: 2.6.24-23. I downloaded the driver from Nvidia and ran the script, but X failed to start. Details of what happened are mentioned in this post:
[http://ubuntuforums.org/showthread.php?t=990978&page=16#640](http://ubuntuforums.org/showthread.php?t=990978&page=16#640)

So, how (if at all possible) could one install the latest Nvidia drivers on 64 bit Ubuntu? Or do I have to live with the 169.12 driver from the repos? 

What I have installed is nvidia-glx-new ver. 169.12, there is nvidia-glx-new-envy ver. 173.14 in Synaptic, but not installed. 

Any help is appreciated.

---

### Post by 3Miro on 2009-03-31
Which version of Ubuntu are you using?

On 8.10, what I did was -
1. Install Linux
2. From the HW manager, select the latest available (in 8.10 it was driver version 1.77.x)
3. reboot (the HW manager does the needed settings for the /etc/X11/xorg.conf)
4. the I go to the Synaptic package manager (or adept, of whatever you are using) and install:
```

nvidia-180-kernel-source
nvidia-180-modaliases
nvidia-glx-180

```
5. reboot and now I have the 1.80 version installed (actually it is 1.80.11 and not the very latest 1.80.44)

I have installed the nVidia driver from their web-page, but you have to follow their instructions very carefully and updating that driver never worked for me (probably my fault).

If the X server is failing now, it is most likely because of a bad setting. Post the output of:
```
cat /etc/X11/xorg.conf
```
and hopefully someone would be able to help you. (this is just the x-server settings file)

---

### Post by philinux on 2009-03-31
> **3Miro said:**
> Which version of Ubuntu are you using?

On 8.10, what I did was -
1. Install Linux
2. From the HW manager, select the latest available (in 8.10 it was driver version 1.77.x)
3. reboot (the HW manager does the needed settings for the /etc/X11/xorg.conf)
4. the I go to the Synaptic package manager (or adept, of whatever you are using) and install:
```

nvidia-180-kernel-source
nvidia-180-modaliases
nvidia-glx-180

```
5. reboot and now I have the 1.80 version installed (actually it is 1.80.11 and not the very latest 1.80.44)

I have installed the nVidia driver from their web-page, but you have to follow their instructions very carefully and updating that driver never worked for me (probably my fault).

If the X server is failing now, it is most likely because of a bad setting. Post the output of:
```
cat /etc/X11/xorg.conf
```
and hopefully someone would be able to help you. (this is just the x-server settings file)


Yes this is what is needed. 180 does not get picked up by jockey.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/342230](https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/342230)

---

### Post by PC_load_letter on 2009-03-31
I'm using 8.04 amd64 right now, the latest Nvidia driver in the repos is the 169.12, pathetic if you ask me. Or am I missing something here? 

X is fine now, I uninstalled the 180.44 driver, then rebooted w/ recovery mode, and after using xfix, everything is back to normal. But no new drivers for me :(

---

### Post by jespdj on 2009-03-31
What's so "pathetic" about driver 169.12? Ubuntu 8.04 is almost a year old, it's no surprise that not all software in the 8.04 repository is up-to-date to the latest versions. You sometimes get updates for 8.04, but those are only for serious bug fixes and security problems.

I am using driver version 177.xx from nVidia on my 64-bit Ubuntu 8.04 laptop. I downloaded the 64-bit driver from the nVidia website and used the following instructions: [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

Note that these instructions are the same for 32-bit and 64-bit.

Note that you do need to have the kernel headers installed, as the instructions explain, because during the installation process the kernel module for the driver needs to be compiled.

---

### Post by sunflowers on 2009-03-31
1. [COLOR="RoyalBlue"]I suggest you, please deactivate your graphic card driver in restricted drivers and go to the[/COLOR] [COLOR="Red"][http://www.nvidia.com]("http://www.nvidia.com")[/COLOR][COLOR="RoyalBlue"] and download the latest version of your graphic card model.[/COLOR]
[COLOR="RoyalBlue"]2. log out.
3. alt+ctrl+F1
4. login with your username.
5. sudo su     then enter your password.
6. enter command bellow :[/COLOR]
    ```
/etc/init.d/gdm stop
```   [COLOR="RoyalBlue"]if you are using gdm  
OR[/COLOR]
    ```
/etc/init.d/kdm stop
```   [COLOR="RoyalBlue"]if you are using kdm.[/COLOR]
[COLOR="RoyalBlue"]7. move to the directory contained new driver
8. enter this command :
```
sh ./NVIDIA*
```    and press enter.
9. follow instruction to complete installing driver.
10. finally :[/COLOR]
    ```
/etc/init.d/gdm start
```
[COLOR="RoyalBlue"]or[/COLOR]
    ```
/etc/init.dkdm start
```

---

### Post by PC_load_letter on 2009-03-31
> **jespdj said:**
> What's so "pathetic" about driver 169.12? Ubuntu 8.04 is almost a year old, it's no surprise that not all software in the 8.04 repository is up-to-date to the latest versions. You sometimes get updates for 8.04, but those are only for serious bug fixes and security problems.

I am using driver version 177.xx from nVidia on my 64-bit Ubuntu 8.04 laptop. I downloaded the 64-bit driver from the nVidia website and used the following instructions: [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

Note that these instructions are the same for 32-bit and 64-bit.

Note that you do need to have the kernel headers installed, as the instructions explain, because during the installation process the kernel module for the driver needs to be compiled.

"Pathetic" because I am experiencing bugs w/ compiz w/ the current driver, and also because we (as part of the Linux community) have long been pressing Nvidia for more up-to-date drivers, now Nvidia seems to be doing their part updating their driver almost every other week (a bit of exaggeration here), but the latest driver in the Ubuntu 8.04 LTS is still 169.12? I mean come on. 

Another thing is that I hope I would be able to use CUDA in my numerical analysis code, so I have to update the drive anyway.

Thanks for your help.

---

### Post by PC_load_letter on 2009-03-31
> **sunflowers said:**
> 1. [COLOR="RoyalBlue"]I suggest you, please deactivate your graphic card driver in restricted drivers and go to the[/COLOR] [COLOR="Red"][http://www.nvidia.com]("http://www.nvidia.com")[/COLOR][COLOR="RoyalBlue"] and download the latest version of your graphic card model.[/COLOR]
[COLOR="RoyalBlue"]2. log out.
3. alt+ctrl+F1
4. login with your username.
5. sudo su     then enter your password.
6. enter command bellow :[/COLOR]
    ```
/etc/init.d/gdm stop
```   [COLOR="RoyalBlue"]if you are using gdm  
OR[/COLOR]
    ```
/etc/init.d/kdm stop
```   [COLOR="RoyalBlue"]if you are using kdm.[/COLOR]
[COLOR="RoyalBlue"]7. move to the directory contained new driver
8. enter this command :
```
sh ./NVIDIA*
```    and press enter.
9. follow instruction to complete installing driver.
10. finally :[/COLOR]
    ```
/etc/init.d/gdm start
```
[COLOR="RoyalBlue"]or[/COLOR]
    ```
/etc/init.dkdm start
```

These are the exact steps that I followed, found them on **the linked thread that I included in my 1st post!**

In all honesty, I did all the steps but the last one, but instead I rebooted the system, still X wouldn't start.

---

### Post by 3Miro on 2009-03-31
Are you sure that 1.80 is no in the 8.04 repos. Update the list and search for them. Even if you have 1.69 installed, you should be able to do the same trick I did (i.e. install 1.69 and then install the packets needed for 1.80).

---

### Post by philinux on 2009-03-31
> **PC_load_letter said:**
> "Pathetic" because I am experiencing bugs w/ compiz w/ the current driver, and also because we (as part of the Linux community) have long been pressing Nvidia for more up-to-date drivers, now Nvidia seems to be doing their part updating their driver almost every other week (a bit of exaggeration here), but the latest driver in the Ubuntu 8.04 LTS is still 169.12? I mean come on. 

Another thing is that I hope I would be able to use CUDA in my numerical analysis code, so I have to update the drive anyway.

Thanks for your help.

Have you enabled the backports repos. See link below.

---

### Post by PC_load_letter on 2009-04-01
Will do. Thank you all guys for the feedback, appreciate it.

---

### Post by loomsen on 2009-04-01
> **PC_load_letter said:**
>  still X wouldn't start.

Easiest way to find out why would prlly be the logfile...

```
tail /var/log/Xorg.0.log
```

---

### Post by PC_load_letter on 2009-04-01
> **philinux said:**
> Have you enabled the backports repos. See link below.

It's not there. See for yourself: A text file w/ all backports packages for Hardy:
[http://packages.ubuntu.com/hardy-backports/allpackages?format=txt.gz](http://packages.ubuntu.com/hardy-backports/allpackages?format=txt.gz)
Got this from the link in your signature. Thanks anyway.

---

