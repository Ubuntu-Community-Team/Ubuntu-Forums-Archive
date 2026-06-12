---
title: "Installing XP with Virtualbox"
date: 2007-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by pwc on 2007-11-29
I installed Virtualbox on my Ubuntu 7.10 64 bit os and it went smooth, however when I hit start to install XP I get this message:

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

I can't seem to work through this, no matter what I do I still get this message. I know it's probably a simple thing, anybody seen this and work through it?

---

### Post by kelbizzle on 2007-11-29
Maybe you missed the step to add your user to the vbox group.

```
First, we install VirtualBox Open Source Edition :

sudo apt-get install virtualbox-ose virtualbox-modules-`uname -r`

and we add our user to the group of users allowed to run VirtualBox :

sudo adduser $USER vboxusers

Now, you need to restart your computer to apply this modifications.
Instant run

If you want to launch VirtualBox without restarting your computer, run the following command lines :

sudo /etc/init.d/udev reload
sudo modprobe vboxdrv
su -c virtualbox $USER

At the end of the last command, type your password to run VirtualBox.
```

I just restarted so I didin't have any issues. Don't forget to install guest additions.

---

### Post by ptn107 on 2007-11-29
I had the same problem.  You just need to add yourself to the *vboxusers* group.

1) Click *System* -> *Administration* -> *Users and Groups*
2) Click *Manage groups* on the right.
3) Find *vboxusers* on the list, select it and click *Properties*.
4) In the *Group Members* box check your username and exit.
5) Log out of your session and log back in.

---

### Post by DARKGuy on 2007-11-29
Or just...

sudo useradd FooBar vboxdrv

If it complains then it's adduser, I can't remember offhand which one is it. Needless to say, change FooBar by your username :p

---

### Post by pwc on 2007-11-29
OK Thanks guys I got it now and its working. Every thing seems ok but sound not working in XP. It's ok with Ubuntu. 
I did miss that step kelbizzle, what's neat is all the ways to correct it and the response you get on this forum. 
Thanks again to all.

---

### Post by JAPrufrock on 2007-11-29
You will probably have to install your sound card driver for XP.  Ubuntu doesn't need it because it uses its own sound architecture (ALSA).

---

### Post by John Jason Jordan on 2007-11-29
> **pwc said:**
> OK Thanks guys I got it now and its working. Every thing seems ok but sound not working in XP. It's ok with Ubuntu. 
I did miss that step kelbizzle, what's neat is all the ways to correct it and the response you get on this forum. 
Thanks again to all.
In the configurations (details) for the XP machine there is an item labeled Sound. Click on it, then change the driver that it is using (or add one if none is selected). The choices are ALSA OSS or Null. I had it working fine with ALSA, but I recently made a bunch of changes to my sound stuff in an attempt to get RealPlayer to send sound to my bluetooth headphones. Suddenly my virtual machine (Windows 2000) would not launch. I changed it from ALSA to Null and Windows boots fine now. I don't know if it still works in Windows, because I never use or care about sound in Windows anyway.

---

### Post by pwc on 2007-11-30
Yea I found the settings just after my last post, set to ALSA and all ok!
It's all set up and working, ain't Ubuntu great. I only need XP for a few chess programs and Snood(wouldn't work with wine). Now they'll be handy.

Thanks to all for your help.

---

