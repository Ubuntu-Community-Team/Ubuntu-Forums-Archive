---
title: "initramfs"
date: 2008-04-30
forum: x86 64-bit Users
---

### Post by jhawkjsu on 2008-04-30
I have a dualboot Ubuntu Hardy Heron (running 64) and Vista laptop. I restarted to get back into Ubuntu and I got... 

> BusyBosy v1.1.3 (Debian 1:1.3-5ubuntu12) Built-in shell(ash) Enter 'help' for a list of built-in commands.

(initramfs)


The last time I used Ubuntu (earlier in the day), it installed some updates, but nothing much happened besides that. I just tried recovery mode and it's a no-go, too. It keeps saying (many numbers where the x's are):
> 
[xx.xxxxxx]atkdb.c: Use 'setkeycodes e00d <keycode> to make it known. [xx.xxxxxx] atkbd.c Unknown key released/pressed [...]

So, um, what just happened? Please tell me I'm not stuck using Vista for the time being...

---

### Post by warp99 on 2008-04-30
> **jhawkjsu said:**
> I have a dualboot Ubuntu Hardy Heron (running 64) and Vista laptop. I restarted to get back into Ubuntu and I got... 




The last time I used Ubuntu (earlier in the day), it installed some updates, but nothing much happened besides that. I just tried recovery mode and it's a no-go, too. It keeps saying (many numbers where the x's are):


So, um, what just happened? Please tell me I'm not stuck using Vista for the time being...

It appears that the initrd.img file may have become corrupted, so you either need to update file or create a new file. Now if you have a previous kernel installed on the system you can boot to that kernel, then update the initrd.img of the new kernel. But if you don't have a previous kernel installed you need your Ubuntu install disc to boot to the system, mount the drive and change root into the drive in order to update the file. Example:

Ubuntu is installed to sda2, which is partition two of disk one. Boot to the Ubuntu install disc and open a terminal to issue the following:

Make a directory to mount the drive:
```
sudo mkdir /media/sda2
```
mount the drive to the directory
```
sudo mount /dev/sda2 /media/sda2
```
chroot into the mounted directory
```
sudo chroot /media/sda2
```
now the root drive is the installed partition. Move to the /boot directory to verify the files are there:
```
cd /boot && ls -l
```
output is similar to this:
```

-rw-r--r-- 1 root root  417807 2008-02-11 22:30 abi-2.6.22-14-generic
-rw-r--r-- 1 root root   67666 2008-02-11 22:30 config-2.6.22-14-generic
drwxr-xr-x 3 root root     480 2008-02-13 11:03 grub
-rw-r--r-- 1 root root 7707427 2008-04-06 11:55 initrd.img-2.6.22-14-generic
-rw-r--r-- 1 root root  103204 2007-07-30 18:13 memtest86+.bin
-rw-r--r-- 1 root root 1052627 2008-02-11 22:30 System.map-2.6.22-14-generic
-rw-r--r-- 1 root root 1743752 2008-02-11 22:30 vmlinuz-2.6.22-14-generic
```
update the initrd.img:
```
sudo update-initramfs -u -v
```
then reboot the computer. If the update does not work you can try again and create a new initrd.img with the following command
```
sudo update-initramfs -c -v -k $(uname -r)
```

---

### Post by jhawkjsu on 2008-04-30
Thanks, I'll give it a try!

---

### Post by allenbrimmer on 2008-05-18
I am new to Hardy Heron (dual boot) and have had the same problem as jhawkjsu twice, i.e Ubuntu boot gets to INITRAMFS prompt, then stops.  This happened both times after installing updates.   

Rebooting Ubuntu did not help, but Ubuntu worked again both times after I booted into Windows, shut down and went back into Ubuntu.

I haven't a clue why this works.

---

### Post by Jimmy9pints on 2008-10-02
Does anyone know if this worked?

I have the same problem, albeit intermittently.

---

