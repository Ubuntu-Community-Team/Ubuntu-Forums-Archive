---
title: "Ubuntu 64-bit - Unable to start X-Server"
date: 2007-08-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by raj108 on 2007-08-10
Hi,
   I have a Dell XPS laptop with Intel Duo Core processor (64 bit enable via bios VT option).
I am running the host as WinXP 32- professional. I installed VMWare to install Ubuntu as virtual machines.
(1.) I was successfully able to install Ubuntu 7.04 (32-bit) and it works perfectly fine. When I power on the virtual machine it boots up and starts the x-server and takes me to the graphical logon prompt.

(2.) I installed a second virtual machine successfully , this time Ubuntu 7.04 (64-bit) . The OS installed without any errors. However when I power on the machine it does not start X-server and takes me to the Unix logon console. I can login and it then takes me to the shell prompt

VMWare documentation says that we can have a 32-bit host running a 64-bit guest operating system

Can some one help me fix what could be wrong with my 64-bit installation.

Cheers,
R:confused:

---

### Post by dabl on 2007-08-10
> **raj108 said:**
> Hi,
 (64 bit enable via bios VT option).

I'm not sure what that is, or means -- my Core 2 Extreme doesn't need any "settings" in the BIOS to run either 32-bit or 64-bit OSs.

> 
(2.) ...  I can login and it then takes me to the shell prompt

VMWare documentation says that we can have a 32-bit host running a 64-bit guest operating system


Well, I'd say it IS running the 64-bit Ubuntu!

As far as the X server, doesn't VMWare provide a "faux" video display system, for the guest OS to use?  I run Win XP in a VMPlayer machine under Ubuntu, and when I look at the "graphics card", there is a name of a chip that has never been anywhere near my computer.  So, I'll speculate that your GUI-less Ubuntu needs to be tweaked for whatever "fake" graphics system is being offered by your VMWare machine.

Absent a better plan, if you log in to Ubuntu (text mode) you can enter ```
sudo dpkg-reconfigure xserver-xorg
``` and on the first screen choose "NO" to auto-detect, and on the second screen choose "VESA", and then finish the script as best you can.  When you're done, it will drop you back at the command line.  Enter ```
startx
``` and you should get a GUI -- just not the highest performance that your actual graphics chip is capable of.

Hope this helps!  :popcorn:

---

### Post by Kilz on 2007-08-10
> **raj108 said:**
> Hi,
   I have a Dell XPS laptop with Intel Duo Core processor (64 bit enable via bios VT option).
I am running the host as WinXP 32- professional. I installed VMWare to install Ubuntu as virtual machines.
(1.) I was successfully able to install Ubuntu 7.04 (32-bit) and it works perfectly fine. When I power on the virtual machine it boots up and starts the x-server and takes me to the graphical logon prompt.

(2.) I installed a second virtual machine successfully , this time Ubuntu 7.04 (64-bit) . The OS installed without any errors. However when I power on the machine it does not start X-server and takes me to the Unix logon console. I can login and it then takes me to the shell prompt

VMWare documentation says that we can have a 32-bit host running a 64-bit guest operating system

Can some one help me fix what could be wrong with my 64-bit installation.

Cheers,
R:confused:

You may need to install the vmware tools to load the graphics driver for the virtual graphics.

---

### Post by raj108 on 2007-08-11
I tried both the options 
(1.) Installed and reconfigured xserver-xorg
(2.) Installed vmware tools to provide enhanced graphic capabilities 

After making some headway I get this error message when I run startx


XIO: fatal IO error 104 (Connection reset by peer) on X Server ":0.0" 

Can you please advise

---

### Post by Kilz on 2007-08-11
> **raj108 said:**
> I tried both the options 
(1.) Installed and reconfigured xserver-xorg
(2.) Installed vmware tools to provide enhanced graphic capabilities 

After making some headway I get this error message when I run startx


XIO: fatal IO error 104 (Connection reset by peer) on X Server ":0.0" 

Can you please advise

Did you install the server edition, or option?

---

### Post by raj108 on 2007-08-12
I have installed Ubuntu 7.04 Server Edition (64 - bit) 
VMWare is also VMWare Server 1.03

---

### Post by Kilz on 2007-08-12
> **raj108 said:**
> I have installed Ubuntu 7.04 Server Edition (64 - bit) 
VMWare is also VMWare Server 1.03

That is the reason it only takes you to the command line interface. A server install does not install a desktop. For the most part, servers dont need one. A desktop uses up a lot of resources that a server can use for other things, like serving things. You can install a desktop. But now you have some choices

You could install [a low memory desktop ]("https://help.ubuntu.com/community/Installation/LowMemorySystems")and start it yourself when you need a desktop. This is what I did using the icewm option.

You can also install one of these, but they use up a lot more resources.

```
sudo aptitude install xubuntu-desktop 
```
will install the lighter xfce desktop - it doesnt use as many resources as gnome or kde
```
sudo aptitude install ubuntu-desktop
```
will install the gnome desktop, it uses more resources 
```
sudo aptitude install kubuntu-desktop 
```
Kde uses the most resources, so it isnt a good fit for a server. But it is an option.

---

### Post by raj108 on 2007-08-16
Thanks,
 I installed the VMWare Tools and this fixed the problems. It installed the necessary drivers
to fix the display resolution and I was able to startx.

Cheers,
R

---

