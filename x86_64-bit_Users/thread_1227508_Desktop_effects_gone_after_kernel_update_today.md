---
title: "Desktop effects gone after kernel update today"
date: 2009-07-30
forum: x86 64-bit Users
---

### Post by sanumala on 2009-07-30
Hi

when I started my box today ubuntu suggested updates and i did. and kernel was updated to 2.6.28-14-generic after that when i restart my box got error saying ubuntu is running in low grapics mode.  

Once i started in low graphics mode I have activated 180 version of nvidia from system-->admin..>hardware drivers 

But the problem is my extreme desktop effects are gone..

Then I have deactivated 180 version and downloaded the latest version NVIDIA-Linux-x86_64-185.18.29-pkg2.run from nvidia and installed it 

But in both cases it is giving error saying "could not activate desktop effects"  

Whats wrong with latest 2.6.28-14 kernel???

and My virtualbox is also failing saying kernel drivers are not installed???

---

### Post by SoftwareExplorer on 2009-07-30
Did you install all the available updates? Sometimes I have had problems when there is a new kernel and I don't install all of the updates.

---

### Post by sanumala on 2009-07-31
I have solved it.

ctrl+atl+f1

#sudo /etc/init.d/gdm stop

#nvidia-installer --update

#sudo /etc/init.d/gdm start

Login into GUI i.e init 5 and then 

alt+f2  and run following two commands.

#gconftool-2 --set --type=bool /apps/metacity/general/compositing_manager false

#compiz --replace

Now compiz desktop effects are working fine on 2.6.28-14-generic kernel.

---

### Post by SoftwareExplorer on 2009-07-31
> **sanumala said:**
> I have solved it.

Yay.

> **sanumala said:**
> Hi
My virtualbox is also failing saying kernel drivers are not installed???
does that part work now? If I remember correctly, installing the 'dkms' package help virtualbox keep working through kernel changes.

---

### Post by sanumala on 2009-07-31
OMG!

I haven't tested yet. I will try that today :)   I have lot's of photoshop stuff on that virtualbox

---

### Post by sanumala on 2009-07-31
update:  virtualbox is working fine now after the following steps

#sudo apt-get install dkms

#sudo su

#/etc/init.d/vboxdrv setup

Thanks.   :popcorn:   Lets have some popcorn.

---

### Post by SoftwareExplorer on 2009-07-31
> **sanumala said:**
> update:  virtualbox is working fine now after the following steps

Good.

> **sanumala said:**
> Thanks.   :popcorn:   Lets have some popcorn.
You're welcome. :)
:popcorn:

---

### Post by bford16 on 2009-07-31
[QUOTE=sanumala;7713050]update:  virtualbox is working fine now after the following steps

#sudo apt-get install dkms

#sudo su

#/etc/init.d/vboxdrv setup

Just to nitpick, the "sudo su" isn't necessary.  You can do "sudo /etc/init.d/vboxdrv setup".  Having dkms installed may also prevent having to reinstall the video drivers after a kernel update.

---

### Post by sanumala on 2009-07-31
> **bford16 said:**
> Having dkms installed may also prevent having to reinstall the video drivers after a kernel update.

I dont think so...  

Actuay when i run sudo apt-get install dkms apt-get notified that its already installed and new. But After kernel upgrade. I my ubuntu box ran into low graphics mode and i have to install my nvidia drivers back using nvidia-installer --update

Can anybody help me to understand more about dkms package

---

### Post by SoftwareExplorer on 2009-08-01
I just once read on virtualbox's website that it made virtualbox work properly after a kernel upgrade. Don't really know about nvidia drivers though.

---

