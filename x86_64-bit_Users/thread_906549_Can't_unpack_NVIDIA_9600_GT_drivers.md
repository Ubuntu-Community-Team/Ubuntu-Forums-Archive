---
title: "Can't unpack NVIDIA 9600 GT drivers"
date: 2008-08-31
forum: x86 64-bit Users
---

### Post by CapTlnsano on 2008-08-31
From a brand new install- 

Read up on these drivers and found out i need to download them direct from NVIDIA and so i get the NVIDIA-Linux-x86_64-173.14.12-pkg2.run file. I tripple check this file and make sure its correct for the 9 series geforce cards. 

From following NVIDIA's instructions on their drivers, i try and drop into terminal, disable xserver with sudo /etc/init.d/gdm stop which works fine. 

Try to unpack the drivers via 
sudo sh NVIDIA-Linux-x86_64-173.14.12-pkg2.run

only to be prompted with:
sh: Can't open NVIDIA-Linux-x86_64-173.14.12-pkg2.run

Bear in mind, this is a BRAND NEW fresh install because the first run through on this yielded little i wiped the machine and started new. I've also uninstalled any and all nvidia packages and linx-restricted modules...

*The driver file is located in home folder for simplicity. 

I feel like im missing something ridiculously simple but I've been at this for hours with no luck so any help would be greatly appreciated.

---

### Post by skunkTrader on 2008-08-31
What happens if you try
```
sudo sh ./NVIDIA-Linux-x86_64-173.14.12-pkg2.run
```

---

### Post by CapTlnsano on 2008-08-31
> **skunkTrader said:**
> What happens if you try
```
sudo sh ./NVIDIA-Linux-x86_64-173.14.12-pkg2.run
```
Negative, output looks like:

austin@Core2Ubuntu:~$ sudo sh ./NVIDIA-Linux-x86_64-173.14.12-pkg2.run
[sudo] password for austin: 
sh: Can't open ./NVIDIA-Linux-x86_64-173.14.12-pkg2.run

---

### Post by skunkTrader on 2008-08-31
try
```
chmod +x ./NVIDIA-Linux-x86_64-173.14.12-pkg2.run
```

---

### Post by CapTlnsano on 2008-08-31
> **skunkTrader said:**
> try
```
chmod +x ./NVIDIA-Linux-x86_64-173.14.12-pkg2.run
```
No luck there either

austin@Core2Ubuntu:~$ chmod +x ./NVIDIA-Linux-x86_64-173.14.12-pkg2.run
chmod: cannot access `./NVIDIA-Linux-x86_64-173.14.12-pkg2.run': No such file or directory
austin@Core2Ubuntu:~$

---

### Post by mcgillicutty on 2008-08-31
I am having the same problem as well same damn thing

---

### Post by Steveway on 2008-08-31
You need to cd to the directory that the file is in of course, duh. 
How should the Operating System know that you mean that file?

---

### Post by Victormd on 2008-08-31
Does envy-ng support the 9600 GT?
If you haven't tried it, you can install by:
```
sudo apt-get install envyng-gtk envyng-core
```
Or look for it under the synaptic package manager. It should download and automatically install the most updated driver...

---

### Post by Victormd on 2008-08-31
> **CapTlnsano said:**
> austin@Core2Ubuntu:~$ chmod +x ./NVIDIA-Linux-x86_64-173.14.12-pkg2.run
chmod: cannot access `./NVIDIA-Linux-x86_64-173.14.12-pkg2.run': No such file or directory
austin@Core2Ubuntu:~$

Good catch Steevway.

Captinsano, you'll need to change to the directory where you downloaded the file, most likely **cd ~/Desktop**.

---

### Post by mcgillicutty on 2008-08-31
can somebody walk me through how to install the driver I dont know how to use linux I just installed it yesterday

---

### Post by Victormd on 2008-08-31
> **mcgillicutty said:**
> can somebody walk me through how to install the driver I dont know how to use linux I just installed it yesterday

It would probably be easier (more straight forward) to use envy-ng (see my previous post). Envy-ng is a program that installs Nvidia and ATI drivers automatically so you don't have to worry about it. Simply open a terminal and type:

```
sudo apt-get install envyng-gtk envyng-core
```
(this will install the proper version of envy-ng - assuming you're using Ubuntu)

Then go to **Applications>System Tools>EnvyNG**, Select NVIDIA and mark the "Install the NVIDIA driver (Automatic Hardware Detection)" option (see the attached image). Click on APPLY and after a few secs. you should be good to go.

---

### Post by mcgillicutty on 2008-08-31
[attach]83550[/attach]

---

### Post by mcgillicutty on 2008-08-31
ryan@Sirius:~$ sudo apt-get install envyng-gtk envyng-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envyng-gtk
ryan@Sirius:~$

---

### Post by Victormd on 2008-08-31
You might not have all the repository sources enabled.
Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and under the Ubuntu Software tab, mark the first 4 options under "Downloadable from the internet" [main, universe, restricted, and multiverse] then click on CLOSE and a dialog box will pop-up asking you to reload, click on reload then open a terminal and type:
```
sudo apt-get update
```
```
sudo apt-get install envyng-gtk envyng-core
```

---

### Post by nbayiha on 2008-08-31
Follow this thread, it explain all step by step .

[http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver+hardy](http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver+hardy)

---

### Post by mcgillicutty on 2008-08-31
ok envy is installed but i dont think it did anything I did not find my card

---

### Post by CapTlnsano on 2008-08-31
Solved- 


:) Told you it was something ridiculous. On the previous install i had put that file in the home directory. Either way, driver install was flawless after getting the correct Libc files. 

Thanks guys.

---

### Post by nikgare on 2008-09-01
You should just be able to install **nvidia-glx-new** via synaptic to give you the right drivers for your card.

---

### Post by Jouke74 on 2008-09-01
Different ways lead to Rome. Please mark the thread as solved. :guitar:

---

### Post by Victormd on 2008-09-02
> **mcgillicutty said:**
> ok envy is installed but i dont think it did anything I did not find my card

Sorry, should have checked back earlier. Did you get it to work?

---

