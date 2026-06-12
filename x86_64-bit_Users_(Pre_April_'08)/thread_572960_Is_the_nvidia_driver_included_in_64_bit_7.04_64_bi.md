---
title: "Is the nvidia driver included in 64 bit 7.04 64 bit?"
date: 2007-10-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by besson3c on 2007-10-11
I'm rather disoriented, I'm wondering if anybody here can help me out...

I'm ultimately trying to enable direct 3D in VMWare, and I'm under the impression that the problems I'm running into are due to running a 32 bit version of the nvidia driver. My driver was not manually installed, but simply installed through the Ubuntu restricted driver manager in 7.04...

Is this driver actually 64 bit? If not, will the nvidia driver included in Gutsy be 64 bit? I would like to get direct3D working, but I'm sort of grasping at straws for the time being since I'm rather confused by all of the posts and pages about people manually installing the latest nvidia drivers. Are people doing this in x64 Ubuntu because the included drivers are not 64 bit?

I await your enlightening me :)  Thanks in advance!

---

### Post by saru411 on 2007-10-11
i havent heard of any driver being 32 or 64 bit. im not sure there are 2 different drivers for each platform but envy detects your equipment and sets things up for you. if you do not have the driver installed yet i recommend using envy to install it for you.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

it will install the correct driver for your platform. just follow the instruction while it installs and you will be fine.

after it is installed type

> sudo nvidia-settings

this will bring up the nvidia settings manager. goto xserver display configuration>resolution and set it to what your monitor supports. after its set save it to x configuration file and you will be done.

---

### Post by shad0w_walker on 2007-10-11
As far as I am aware you won't have much luck with any kind of 3D on VMs, they don't have the support generally.

---

### Post by phelixnyc on 2007-10-11
It's included in restricted drivers, you can also install using Envy which detects your os, 32 or 64.

---

### Post by besson3c on 2007-10-11
> **shad0w_walker said:**
> As far as I am aware you won't have much luck with any kind of 3D on VMs, they don't have the support generally.

I'm fairly certain that I've read forum and/or blog posts from users that have gotten VMWare Workstation/Player's Direct3D working, and some have reported getting it working in 64 bit Linux too, although an older post provided instructions for setting up symlinks in /usr/lib32 to do this... I figured that before I wade into all of this I should get an update as to the state of the driver provided in the apt-get repository...

---

### Post by besson3c on 2007-10-11
> **phelixnyc said:**
> It's included in restricted drivers, you can also install using Envy which detects your os, 32 or 64.

I know it's available in the restricted drivers. Like I said, that's how I installed it, and it works fine w. Compiz support too... I was just looking for verification as to whether it was the 32 or 64 bit driver.

Here is the VMWare post in question:

[http://communities.vmware.com/thread/95480](http://communities.vmware.com/thread/95480)

---

### Post by rsambuca on 2007-10-11
It is 64bit as far as I know.  If it wasn't, you would have to do a force installation (which I didn't), or a chroot (which I didn't).

---

### Post by Kilz on 2007-10-11
> **besson3c said:**
> I'm rather disoriented, I'm wondering if anybody here can help me out...

I'm ultimately trying to enable direct 3D in VMWare, and I'm under the impression that the problems I'm running into are due to running a 32 bit version of the nvidia driver. My driver was not manually installed, but simply installed through the Ubuntu restricted driver manager in 7.04...

Is this driver actually 64 bit? If not, will the nvidia driver included in Gutsy be 64 bit? I would like to get direct3D working, but I'm sort of grasping at straws for the time being since I'm rather confused by all of the posts and pages about people manually installing the latest nvidia drivers. Are people doing this in x64 Ubuntu because the included drivers are not 64 bit?

I await your enlightening me :)  Thanks in advance!

Did you install vmware tools? This includes your virtual accelerated graphics driver. But if this is for a game, it wont work. At least it didnt for me. Vmware runs games real slooooooooooow.

---

### Post by besson3c on 2007-10-11
> **Kilz said:**
> Did you install vmware tools? This includes your virtual accelerated graphics driver. But if this is for a game, it wont work. At least it didnt for me. Vmware runs games real slooooooooooow.


I did install VMWare Tools...

Perhaps it's time to look at running WINE as well.

---

### Post by Kilz on 2007-10-11
A lot of games run with wine. I have Diablo 2 and Warcraft 3 running under wine. The setup was a little tricky but well worth it.

---

### Post by besson3c on 2007-10-11
> **Kilz said:**
> A lot of games run with wine. I have Diablo 2 and Warcraft 3 running under wine. The setup was a little tricky but well worth it.

Cool.. I did find some instructions for the game I want to play, Civ IV, but it seems like there is no version of Wine in the apt-get repository for x64 Fiesty? Any idea whether there are plans to provide a build, perhaps in conjunction with Gutsy?

In Ubuntu, are packages associated with OS revisions like they are in some other Unix/Linux distros?

---

### Post by Kilz on 2007-10-11
> **besson3c said:**
> Cool.. I did find some instructions for the game I want to play, Civ IV, but it seems like there is no version of Wine in the apt-get repository for x64 Fiesty? Any idea whether there are plans to provide a build, perhaps in conjunction with Gutsy?

In Ubuntu, are packages associated with OS revisions like they are in some other Unix/Linux distros?

To some extent. But a lot of packages will work from the previous version. An exapmle is I run the nvu package from Edgy in Feisty because there isnt one for Feisty.. As long as the requirements are taken care of it will work. 
As for wine, look at the winehq, the wine projects site. They have a 64bit deb (though its still only a 32bit application, it needs to be because all windows apps are 32bit) for Feisty in their repos.

---

### Post by mkosem on 2007-10-12
I think I recall reading somewhere that Cedega supports x64.  It's probably more likely to be able to run your software than wine.

--Matt

---

### Post by Kilz on 2007-10-12
Cedega will install to 64bit, but its not free. It costs money and an ongoing subscription. Wine while not as user friendly is free.

---

### Post by besson3c on 2007-10-12
It looks like I was reading the VMWare forum post wrong... I *need* the 32 bit NVidia driver to work with VMWare...

Playing around with WINE now with an Envy installed NVidia driver.

---

### Post by besson3c on 2007-10-12
I managed to get Direct3D working in VMWare now, but VMWare crashes (which is not all that uncommon with this experimental feature). I'm getting error messages in launching the game via Wine... perhaps I'll hit up the Wine list for help here.

Thanks for all your help!

---

