---
title: "[SOLVED] Driver install"
date: 2008-05-27
forum: x86 64-bit Users
---

### Post by retiree on 2008-05-27
I just installed Hardy and I'm trying to install a driver (NVIDIA-Linux-X86_64-169.12-pkg2.run) for my video card. It has to be run from root terminal.When I open a terminal, and SU for root I get a authentication error after I type in my password. I know the password is definitely correct. Any suggestions? Am I doing it wrong? Thanks for any help, Retiree

---

### Post by logos34 on 2008-05-27
As far as the error goes and getting a root terminal I always use

$ sudo -i

But to install the nvidia driver you have to kill the x server and run it from console.  

ctrl+alt+F1

sudo /etc/init.d/gdm stop

sudo sh NVIDIA...run

I would recommend you try [EnvyNG]("http://www.albertomilone.com/nvidia_scripts1.html") installer first.

---

### Post by wdaniels on 2008-05-27
By default with Ubuntu, root is not given a password, hence the authentication failure with su. You can gain root privileges using the command sudo instead (sudo -i to simulate a root login like with su).

But I'm sure this driver is in the repos anyway, if you enable restricted drivers.

---

### Post by retiree on 2008-05-27
Thanks for the useful post, Retiree

---

### Post by logos34 on 2008-05-27
> **retiree said:**
> (NVIDIA-Linux-X86_64-169.12-pkg2.run)

the other poster was right--that's the one (nvidia-glx-new) in the repos. So use that

I probably should have checked...I always assume people are trying to run the bleeding edge version for video games

---

### Post by retiree on 2008-05-27
Thanks, Problem Solved

---

