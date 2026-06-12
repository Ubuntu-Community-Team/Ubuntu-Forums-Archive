---
title: "Ubuntu 8.04- Installed NVidia 169.12, need 180.22"
date: 2009-01-12
forum: x86 64-bit Users
---

### Post by jpummil on 2009-01-12
Greetings!

I did a fresh install of Ubuntu 8.04 LTS this morning and am in the process of setting the workstation up for some CUDA work. However, CUDA needs the 180.22 NVidia drivers and I have already installed the 169.12 drivers just by enabling the restricted drivers at login time. What is the proper method for unloading the 169.12 restricted drivers currently in use and enabling the 180.22 drivers I need? 

Any additional instructions to avoid potential conflicts when the system looks for updates? I plan on sticking with the 180.22 drivers if they work OK.

Also, will my existing nvidia-settings app work with the new drivers, or will I need to do something to enable it?

Thanks!

---

### Post by techstop on 2009-01-12
If the repo doesn't offer the latest drivers you need, you will need to install them manually by downloading from nvidia. You can do this by using EnvyNG (you can find it in synaptic), or manually as below. You may want to disable the restricted driver first.

1. Install dependencies;

```
sudo apt-get install build-essential
```

2. Download driver from nvidia;

[http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)

3. Open a tty by pressing Ctrl + Alt + F1

4. Stop gdm by running;

```
sudo /etc/init.d/gdm stop
```

5. Run the driver installation (change filename as appropriate);

```
sudo sh NVIDIA-Linux-x86_64-173.08-pkg2.run
```

6. Answer yes to all question from installer.

7. Start gdm again;

```
sudo /etc/init.d/gdm start
```

8. Disable the "nv" module before you reboot, or you WILL run into problems;

```
sudo gedit /etc/default/linux-restricted-modules-common
```

Add the following line to the bottom of the file;

DISABLED_MODULES="nv"

You will need to reinstall the driver from steps 3-7 each time you install a new kernel (it's a lot quicker than it sounds).

You can find more info on my blog here;

[http://techstop.com.au/2008/05/hardy-nvidia-beta-drivers/](http://techstop.com.au/2008/05/hardy-nvidia-beta-drivers/)

---

### Post by jpummil on 2009-01-12
Ugh!

Followed instructions, but get the following when trying to start nvida-settings:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

The only unusual thing I encountered when doing the install was this:

Unable to perform the runtime configuration check for library 'libGL.so.1' ('usr/lib32/libGL.so.180.22'); assuming successful installation.

I was unable to go the EnvyNG route because 180.22 was not available thru Envy.

I double checked all of the steps in the instructions and appear to have followed them letter by letter. 

Any ideas?

Thanks!

---

### Post by briandu on 2009-01-12
follow this 

[http://ubuntuforums.org/showthread.p...80#post5064980]("http://ubuntuforums.org/showthread.php?p=5064980#post5064980") msg #430

always worked for me like a dream

---

### Post by mgranet on 2009-01-12
Make sure you have the kernel-headers for your kernel installed as well, so the installer can build a new kernel module for the driver. Also, make sure you have uninstalled the old 169 drivers. As for techstop's instruction to disable the nv driver, I fail to see why. I did not disable nv on my system, and it works fine. It's still installed, just not active in my xorg.conf. If you had the 180 drivers automatically recreate the xorg, it should autoset the proprietary drivers as default.

---

### Post by techstop on 2009-01-12
> **jpummil said:**
> Ugh!

Followed instructions, but get the following when trying to start nvida-settings:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

The only unusual thing I encountered when doing the install was this:

Unable to perform the runtime configuration check for library 'libGL.so.1' ('usr/lib32/libGL.so.180.22'); assuming successful installation.

I was unable to go the EnvyNG route because 180.22 was not available thru Envy.

I double checked all of the steps in the instructions and appear to have followed them letter by letter. 

Any ideas?

Thanks!

This thread has the same issue as you, and was solved by uninstalling the xserver-xgl package;

[http://ubuntuforums.org/showthread.php?t=810659](http://ubuntuforums.org/showthread.php?t=810659)

(Also has a link to the same thread posted by briandu)

---

### Post by jpummil on 2009-01-13
Success!

Using briandu's instructions, I was able to get everything working with the 180.22 drivers (of course...180.60 is out now).

Question, is there a way to pin or lock out kernel and other updates that will perturb my installation. I'm not really obsessed with constantly updating to the newest kernel every time one comes out anyway...just that things work and work well.

---

### Post by crjackson on 2009-01-13
> **jpummil said:**
> Success!

Question, is there a way to pin or lock out kernel and other updates that will perturb my installation. I'm not really obsessed with constantly updating to the newest kernel every time one comes out anyway...just that things work and work well.

Sure, I have instructions in my blog. Go to this link for instructions.

[http://buck-nasty.blogspot.com/2008/08/version-locking-packages-and-kernel.html]("http://buck-nasty.blogspot.com/2008/08/version-locking-packages-and-kernel.html")

---

