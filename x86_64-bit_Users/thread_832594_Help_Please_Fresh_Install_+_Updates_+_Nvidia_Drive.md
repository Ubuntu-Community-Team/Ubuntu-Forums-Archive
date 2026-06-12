---
title: "Help Please Fresh Install + Updates + Nvidia Drivers = Blank Screen"
date: 2008-06-17
forum: x86 64-bit Users
---

### Post by cchester on 2008-06-17
Hey guys,

Please help me out.

I just did a new fresh install of Ubuntu 8.04 AMD64 and evrything installed and worked great.

I then did all of the updates and that all went great and I rebooted and logged in and everything was great.

I then installed the restricted drivers for my nvidia card and it was the nvidia-glx-new drivers and it installed and went great.

I rebooted and I saw the normal Ubuntu screen and then in went black and then nothing. I never get to a login screen or anything.

I try and press ctrl+alt+f1,f2,f3,f4,etc and I get nothing no matter what I choose.

Do I have to do another reinstall and not pick the restricted drivers?

Thanks for any help on this.

My system:

GA-K8NSC-939 F8
Amd Athlon 64 3700+
Memory 1GB
Nvidia Geforce 7600 GS AGP 512 MB

---

### Post by Rocket2DMn on 2008-06-18
You can reboot into the recovery mode kernel (second option at the GRUB menu) and remove the drivers
```
apt-get remove --purge nvidia-glx-new
```
Then reconfigure X
```
dpkg-reconfigure xserver-xorg -phigh
```
Then reboot
```
reboot
```
Once you are back in the GUI, I suggest enabled restricted drivers either from System->Administration->Hardware Drivers or using EnvyNG to find the correct drivers and download/install them for you: [http://www.albertomilone.com/envyngfaq.html#A](http://www.albertomilone.com/envyngfaq.html#A)

---

### Post by bufsabre666 on 2008-06-18
reboot then at the grub goto the recovery option, it will load everything and then select fix x or reconfigure x, i forget i did it a while back though, it will change your drivers back to vesa, then when its finished go back into real ubuntu and 

```
sudo apt-get update && sudo apt-get envyng-core envyng-gtk
```

applications->system tools->envyng

install the nvidia drivers, never fails for me

---

