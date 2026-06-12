---
title: "Password Problem"
date: 2007-04-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Justin123 on 2007-04-04
I Recently have been having some problems with installing a Nvidia GPU driver on my computer.  It keeps telling me that I have to run the installer as root and so I have been trying to do that by running the command with sudo.  The only problem that i have been having is that when I run as root it askes me for a password and when I type my pasword it says that it is incorrect.  I already reinstalled ubuntu to try and reset the system but that didn't work.  Thanks in advance, Justin

---

### Post by prince_niceguy on 2007-04-04
The root password is not set to the password you give during installation. For setting the root password, go to users and reset the root password to the one you desire.

Then you would be able to do a su to root and then install the driver. However, sudo should work. Check out some of the nvidia installation threads they will give you some hints.

---

### Post by Justin123 on 2007-04-04
> **prince_niceguy said:**
> The root password is not set to the password you give during installation. For setting the root password, go to users and reset the root password to the one you desire.

Then you would be able to do a su to root and then install the driver. However, sudo should work. Check out some of the nvidia installation threads they will give you some hints.

I read the "READ ME" on the OS and it said that it was my password that I needed, not root's.

---

### Post by Kilz on 2007-04-04
> **Justin123 said:**
> I read the "READ ME" on the OS and it said that it was my password that I needed, not root's.

You should not need to use anything but sudo and your password. try to use use ```
sudo bash
``` and then the commands that need root.

---

