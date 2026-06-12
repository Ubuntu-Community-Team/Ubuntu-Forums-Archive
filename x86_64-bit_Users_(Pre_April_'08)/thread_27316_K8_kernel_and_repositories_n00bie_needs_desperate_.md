---
title: "K8 kernel and repositories n00bie needs desperate help"
date: 2005-04-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by tikal26 on 2005-04-15
I installed the K8 kernel and it works fine, but because I havea nvidia grphics card I need the generic 64 kenrnel. when I star and get to Grub I have a bout 6 option plus windows XP. 
1st. Do I really need the generic kernel in order to have my nvidia card
2nd. How do I make K8 my default
3rd. DO I need all the kernels like i86x and is there a way to make it so that I only have the k8 and windows option even though I have the others installed. 
Also when I type gedit /etc/apt/sources.list in order to edit it tells me that the file is read only how do I make it editable. I guess that I can live with all the options in my Grub, but I really need to add repositories.
Thanks to all replies

---

### Post by mthaddon on 2005-04-15
As far as editing the repository, simply type

sudo gedit /etc/apt/sources.list 

See this for an introduction to sudo: [http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

For nvidia, you can use whatever kernel you like (I use amd64-k8). Probably easiest to follow this guide:

[http://www.ubuntulinux.org/wiki/BinaryDriverHowto](http://www.ubuntulinux.org/wiki/BinaryDriverHowto)

They have a specific section on Nvidia.

---

### Post by tikal26 on 2005-04-15
I did that and gedit opened , but as I stated before the problem is that I can't edit the file becuse is a read only file. How do I make it editable do I have to do asave as with the same name and overwiete the file thre

---

### Post by mthaddon on 2005-04-15
sudo chmod 644 /etc/apt/sources.list

chmod is the command to change permissions.

READ permission = 4
WRITE permission = 2
EXEC permission = 1

the three number refer to the file's owner, group and others. So in this case we're saying allow owner to read and write, others to read-only.

---

### Post by tikal26 on 2005-04-15
ok so I did this
:~$ sudo chmod 644/etc/apt/sources.list
chmod: too few arguments
Try `chmod --help' for more information.
what did I typed wrong
thanks for you reply

---

### Post by blahrus on 2005-04-15
[QUOTE=tikal26]ok so I did this
:~$ sudo chmod 644/etc/apt/sources.list
chmod: too few arguments
Try `chmod --help' for more information.
what did I typed wrong
thanks for you reply[/QUOTE]
 sudo chmod 644 /etc/apt/sources.list

make sure there is space after 644

---

