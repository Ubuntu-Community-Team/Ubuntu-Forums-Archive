---
title: "Can't get or instal NVidia GFX drivers"
date: 2007-11-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Borg on 2007-11-07
Just built my new system AMD64 4600 and installed the new Gutsy 64.

All went well except the partition bit but thats another question.

Now my screen only shows on 2/3 of my monitor. I can't get Envy to instal or seem to get restricted drivers to work.

How do i get NVidia drivers to load ?

Thanks

---

### Post by dabl on 2007-11-07
> **Borg said:**
> 

I can't get Envy to instal 



What does this mean?  The web site is here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You want to download the file "envy_0.9.8-0ubuntu11_all.deb" which is about halfway down the page.  When it is downloaded to your desktop, you right-click it and choose "Install with Gdebi".

Which part of this procedure is not working for you?

---

### Post by Borg on 2007-11-07
It means Envy will not install

when I try to install it it says it is not supported for my system

---

### Post by dabl on 2007-11-07
This is pretty weird ... what Nvidia card did you install?

---

### Post by Borg on 2007-11-08
A brand new PCI-e EN8500  GT

---

### Post by dabl on 2007-11-08
Hmmmmmmmm.  I just spent 5 minutes on Nvidia's web site and can't even find your card. Is that card in the "nForce" product line?

Look here: [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

If you can set the OS to Linux, 32-bit or 64-bit according to your CPU, and then find your "product type" and the actual card, it should tell you the Linux driver that will work for it.  But I couldn't figure out where you card is in the Nvidia product lines.  :confused:

---

### Post by Borg on 2007-11-08
Its a G Force 8 ,

this stupid old keybored is sticking on a lot of keys

---

### Post by Borg on 2007-11-08
Although it won't make much difference. I will still have to boot into XP to play nay decent games :(

---

### Post by dabl on 2007-11-08
Aha.

Well, then I cannot understand why Envy would not install the new 100.14.19 Nvidia driver on it -- that's what you need.  Did it throw an error message or anything?

However, be that as it may, if you're deep into gaming then Linux is probably not for you, I'm afraid -- at least not the video-intensive stuff. :)

---

### Post by NullHead on 2007-11-08
> **Borg said:**
> Just built my new system AMD64 4600 and installed the new Gutsy 64.

All went well except the partition bit but thats another question.

Now my screen only shows on 2/3 of my monitor. I can't get Envy to instal or seem to get restricted drivers to work.

How do i get NVidia drivers to load ?

Thanks

did you try installing [http://www.nvidia.com/object/linux_display_amd64_100.14.19.html](http://www.nvidia.com/object/linux_display_amd64_100.14.19.html) ??
I've searched on the sight and it sent me to that driver page...

---

### Post by Borg on 2007-11-08
It wasn't the drivers that didn't install it was ENVY itself

---

### Post by NullHead on 2007-11-08
So you don't have any GFX at all presently? Well so you double click on envy and It doesn't do it's thing? Was there any errors? or did just nothing happen?

---

### Post by Borg on 2007-11-08
OK need to install the drivers with X not running, do I just reboot and pick recovery mode ?

---

### Post by NullHead on 2007-11-09
Well an easier way to do that is to load up the normal way and just kill gdm so the installer can continue.```
sudo pkill gdm
``` 
When your done you can start it again.```
sudo gdm
```
And you should be good to go.

---

### Post by Borg on 2007-11-09
Cool  thanks

---

### Post by Borg on 2007-11-09
well thats deff kills it, so much so all I get is a black screen and no where to put the next command line in :)

LOL oh well

---

### Post by dabl on 2007-11-09
Since you have an AMD CPU, I think you need a kernel boot option (entry in your /boot/grub/menu.lst file) like this:

iommu=off


I stumbled across that here:

[http://www.nvnews.net/vbulletin/showthread.php?t=58498](http://www.nvnews.net/vbulletin/showthread.php?t=58498)


But then you still need the Nvidia driver correctly installed, and I'm still scratching my head about your Envy problem.

---

### Post by NullHead on 2007-11-09
> **Borg said:**
> well thats deff kills it, so much so all I get is a black screen and no where to put the next command line in :)

LOL oh well

Oh yes I forgot to tell you to do that in a ctrl+alt+f1 terminal ... sorry but you need to install the driver from the command line.

---

