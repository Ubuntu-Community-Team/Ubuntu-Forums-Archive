---
title: "Ubuntu 8.10 Nvidia 9800GT driver installation, help me plz!..."
date: 2009-04-15
forum: x86 64-bit Users
---

### Post by striker_gt on 2009-04-15
[SIZE="4"]_9800gt on Ubuntu 8.10 64 bits_[/SIZE]

I'm getting a lot of trouble trying to install the Nvidia restricted driver for ny MSI 9800GT 512 OC.

I've tried everything and I cannot make it work. Some sort of things like:

[I][http://www.nvidia.com/object/linux_d...64_177.82.html](http://www.nvidia.com/object/linux_d...64_177.82.html)

sudo /etc/init.d/gdm stop

sudo ./NVIDIA-Linux-x86_64-173.14.05-pkg2.run[/I]

and also the built-in installation through synaptic package manager, update manager, command line and a lot of stuff...

*"I have successfully installed Nvidia drivers on ubuntu 8.04 and also compiz fusion but in 8.10 things are getting too much frustrating..."*

I have Linux ubuntu **2.6.27-11-generic kernel** and some installation give me an error saying that the kernel is incompatible...

Another times, with some methods I get the error saying **no screen found** and other times it says that I have errors with xconfig.:(

Also I know to uninstall the messed config with this command

*$ sudo apt-get remove nvidia**


Please can you describe me the method step by step (like a noob), so I can make it work.

Thank you very much for your support! :D

---

### Post by inobe on 2009-04-16
have you gotten all the system updates first ?

i must ask, have you tried activating the driver in "hardware drivers" ?

if you didn't see any listed drivers there' i suggest adding a source to synaptic to get the latest drivers "180.44"



you don't have to manually install the driver, simply add this source to your list.

please add the **"stable source"**

[http://www.avenard.org/files/ubuntu-repos/](http://www.avenard.org/files/ubuntu-repos/)

thanks to this amazing site

[http://www.avenard.org/media/Home.html](http://www.avenard.org/media/Home.html)

when you add the source you may need to manually select the driver in synaptic.

you don't need to remove the previous versions, when you select the 180.44 driver" the older version will automatically be removed.

here is what needs to be selected

nvidia-settings
nvidia-180-kernel-source
nvidia-180-modealiases
nvidia-glx-180
nvidia-common

install them and restart, upon restarting check "hardware drivers" select 180 driver and activate it, logout and and back in' the driver should then be doing it's thing.



------------------------------------------------------------------------------------------------------edit:

i just tryed it on another machine, once the source was added and and i clicked "reload" i was notified of the update, i installed the update and rebooted to a desktop running the 180.44 driver ;)

it was very easy

---

### Post by striker_gt on 2009-04-16
Dude, I think I got a corrupt kernel...

I got to download the whole thing again...
I'm downloading it right now!

Thanks!

---

### Post by inobe on 2009-04-16
[IMG]http://www.itsyourpc.org/duane/files/nvidia_180_44.jpg[/IMG]

```
@k-box:~$ uname -r
2.6.27-11-generic

```

---

### Post by striker_gt on 2009-04-16
I just downloaded Ubuntu 8.04 64 bits  2.6.24-23-generic and I'm very happy :). Everything is working fine now. I guess 8.04 is better becouse it's older and it has better driver support. I just updated my drivers automatically using upgrade manager...

I love Compiz Fusion!

Thank you!

---

