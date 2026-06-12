---
title: "Update to new NVIDIA drivers"
date: 2008-01-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Chriis on 2008-01-30
Hi All :)

Oki I run with the Nvidia Drivers from synaptic package manager on Gutsy;
NVIDIA binary XFree86 4.x/X.Org 'new' driver (100.14.19+2.6.22.4-14.10)
Works fine but I find that ones on Nvidia Web site.

Linux x64 (AMD64/EM64T) Display Driver
Version: 169.09
Operating System: Linux x64 (AMD64/EM64T)
Release Date: January 21, 2008 

Will Ubuntu include these in Synaptic or not,..and if not, how can i install these.
And will it be safe to do this update outside synaptic?

And can i expect gain from these new drivers?

Thanks 


Chriis :popcorn:

---

### Post by Sockerdrickan on 2008-01-30
If you have a GeForce 8 series card you will get massive gain, you have to manually install these new ones

```
GET DRIVER

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common linux-restricted-modules*

sudo rm /etc/init.d/nvidia-*

CTRL+ALT+F6+LOG ON TO YOUR UBUNTU ACCOUNT

sudo /etc/init.d/gdm stop

sudo sh NV (PRESS TAB TO GET THE REST)

GO THROUGH THE INSTALLATION

sudo /etc/init.d/gdm start
```

---

### Post by Siyfion on 2008-01-31
After doing that and restarting, I had an error message about "failed to initialise HAL" and then the restricted drivers manager went a bit barmy.. :S

also this line: "sudo rm /etc/init.d/nvidia-*" didn't do anything as the directory doesn't exist?

EDIT: Although everything looks to be working...!?

---

### Post by Chriis on 2008-01-31
Get you this error at every restart or once?

And   ----> "sudo sh NV (PRESS TAB TO GET THE REST)" 
i dl the package (.run) file to my desktop,.. how TAB do to know the name of the file I just download!??

Thanks

Chriis:popcorn:

---

### Post by PmDematagoda on 2008-01-31
If you downloaded the driver to the Desktop then navigate to the desktop using:-
```
cd ~/Desktop
```
Keep in mind that Desktop is capital D not simple d.

After you navigate to the Desktop just enter:-
```
sudo sh NV
```
and press Tab to show the available files with NV, one of which(or the only one) being the driver install file.

---

### Post by Sockerdrickan on 2008-01-31
> **Global_Inferno said:**
> 
also this line: "sudo rm /etc/init.d/nvidia-*" didn't do anything as the directory doesn't exist?

EDIT: Although everything looks to be working...!?

It only does something if you have nVidia startup scripts already

---

### Post by Siyfion on 2008-01-31
Ah I see... What about the Restricted Driver Manager throwing a wobbly? And that HAL error msg? Any idea's?

---

### Post by Chriis on 2008-01-31
"What about the Restricted Driver Manager throwing a wobbly? And that HAL error msg?"

Can you explain more?
Maybe post the exact error msg plz :)

Thanks 

Chriis

---

### Post by Siyfion on 2008-01-31
> **Chriis said:**
> 
Can you explain more?
Maybe post the exact error msg plz :)


The exact error msg is a few posts up, it was in what I would call a message box, with a button basically to say "ok".

As for the restricted driver managers wobbly, i'll do it again and get back to you with exactly what it said.

---

### Post by Chriis on 2008-01-31
Oki a installed these drivers and it's seem to work better and faster :)

I followed [COLOR="DarkGreen"][SIZE="3"]Tux0r's[/SIZE][/COLOR] instructions and it worked great! 

I also received:
[COLOR="SandyBrown"]You need to install the package
linux-restricted-modules-2.6.22-14-generic
for this program to work.[/COLOR]
when i try to start restricted driver manager but ,..


Thanks all 

ps: I'love Ubuntu and it's communauty :popcorn:

---

### Post by Siyfion on 2008-01-31
> **Chriis said:**
> 
You need to install the package
linux-restricted-modules-2.6.22-14-generic
for this program to work.

Thats the one!

---

### Post by Nullexe on 2008-02-01
This worked great for me, thanks!

---

