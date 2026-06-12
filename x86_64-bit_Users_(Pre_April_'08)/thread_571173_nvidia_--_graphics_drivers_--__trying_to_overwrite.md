---
title: "nvidia -- graphics drivers --  trying to overwrite"
date: 2007-10-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by sirgogo on 2007-10-09
Hello all:

I've installed 7.10 Gutsy. I'm having trouble installing the restricted graphics driver. When I hit the install button it says tries to install, but comes back with an error:

E: /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-13.6_amd64.deb: trying to overwrite `/usr/bin/nvidia-settings', which is also in package nvidia-settings


It doesn't install at all!!! What's going on and how do i fix it?

Bug tracker ID is #145919. Heres the url: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/145919](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/145919).

Thanks.

---

### Post by jocko on 2007-10-09
One solution is to remove nvidia-settings before you install nvidia-glx-new.

Another is to find the full path and filename for the downloaded .deb file (it's in /var/cache/apt/archives) and install it manually by running:
```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/nvidia-glx-new_XXX.deb
``` (make sure you get the filename correct, use tab completion)

---

### Post by saru411 on 2007-10-09
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

follow this link to get envy. it will install your nvidia driver for you.

after it is installed type this into terminal and set your resolution and save xorg file

> sudo nvidia-settings

---

### Post by sirgogo on 2007-10-10
jocko:

I've tried removing the nvidia-setting in synaptic, but it still wouldnt install. I tried your other method and I found in terminal the following files:

nvidia-glx-new_100.14.19+2.6.22.4-13.6_amd64.deb
nvidia-glx-new_100.14.19+2.6.22.4-14.8_amd64.deb
nvidia-glx-new_1.0.9755+2.6.20.5-16.29_amd64.deb
nvidia-kernel-common_20051028+1ubuntu7_all.deb
nvidia-settings_1.0+20060516-3ubuntu1_amd64.deb
nvidia-settings_1.0+20070502-1ubuntu1_amd64.deb
nvidia-xconfig_1.0+20051122-2_amd64.deb
nvidia-xconfig_1.0+20070502-1_amd64.deb

Which one do I select considering my system conf?

saru411:

Thanks for the post, I'll check it out if this doesn't work. I just want to do it as easy as possible, so that I don't have any unnecessary stuff on this partition.

Thanks a bunch (both of you).

---

### Post by nzadLithium on 2007-10-10
try putting 
sudo apt-get remove nvidia-settings
in the terminal

dunno if it will work but its worth a shot

you want to install nvidia-glx-new with the highest numbers :)

---

### Post by dabl on 2007-10-10
Guys, I don't think nvidia-settings is a "removable" package.  It is the utility front-end for the Nvidia proprietary driver.  So, if you installed the Nvidia driver, by _whatever _means (nvidia-glx, Envy, download from nvidia.com, Automatix, .....), then you have the utility.

@sirgogo -- the Gutsy Restricted Driver Manager was very buggy in Tribe 5, and I haven't touched it since then.  I'm running Gutsy Beta and use the Envy script installer to install the Nvidia driver -- it seems very solid.  You do have to do a "tweak" to the Envy routine, before you run it in Gutsy.  Here are the links you need:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

and then follow the 29 July post "How To" here, before you run Envy on your Gutsy system:

[http://albertomilone.com/wordpress/?m=200707](http://albertomilone.com/wordpress/?m=200707)


That's it -- should work fine for you, like it does for me.  :)

---

### Post by jocko on 2007-10-10
Actually, the package nvidia-settings seems rather useless as it is now.
As far as I can see, it provides the utility /usr/bin/nvidia-settings, which is also provided by the packages nvidia-glx and nvidia-glx-new, but it also provides a menu item and some man pages, which does not seem to be part of the driver packages.

So I think it's safe to remove nvidia-settings (the package) to get rid of the conflict. But [this is a bug]("https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/72979"), maybe if more people add to the bug report, it will get fixed?

---

### Post by sirgogo on 2007-10-23
Okay, sorry for the late post, but I was terribly busy with other things.

Anyway:

ENVY IS GREAT! Although I had some trouble installing my drivers automatically, the manual install went quite well and I'm happy with my graphical performance now. IT WORKED! Thanks a lot for the post.

Also: Envy does NOW offer Gutsy support, so check it out.

---

