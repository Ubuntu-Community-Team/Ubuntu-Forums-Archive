---
title: "ubuntu constantly freezing"
date: 2009-10-27
forum: x86 64-bit Users
---

### Post by 314 on 2009-10-27
my ubuntu all of a sudden started to freeze at first i thought it was the google chrome that i had installed but then it would do it with out chrome installed. even if i just have rythembox open any and all help to resolve this problem would be nice

---

### Post by wilee-nilee on 2009-10-27
I would try the live CD to see if this happens then, also you might list your computer and specs, and any not stock applications your using, and a little more of a description.

---

### Post by Dark_Stang on 2009-10-27
Sounds like you might have a kernel panic going on. Did a kernel update happen recently?

---

### Post by 314 on 2009-10-27
> **Dark_Stang said:**
> Sounds like you might have a kernel panic going on. Did a kernel update happen recently?

yes it did. and here are my specs

[http://paste.ubuntu.com/302588/](http://paste.ubuntu.com/302588/)

---

### Post by Dark_Stang on 2009-10-27
When grub loads hit the escape key and select an older kernel. If it doesn't lockup with the older kernel then you'll just want to roll back to using that one.

---

### Post by 314 on 2009-10-27
how do i roll back to a different kernel

---

### Post by 314 on 2009-10-27
so i am in .15 not .16 and i get no freeze so far Yay

---

### Post by Dark_Stang on 2009-10-27
If that keeps working you can edit your grub menu and simply comment out the latest kernel. Keep playing with it to make sure it doesn't freeze up. If everything works out okay run the following command...
```
sudo gedit /boot/grub/menu.lst
```
That will open up a text editor with root privileges to edit your grub menu. Go towards the bottom. There you will see all the currently installed and bootable kernels. Simply add a # in front of each line for the newest kernel to comment it out. Be sure to comment out the recovery mode lines for that kernel too. Then save the file. Grub will now load the next kernel in the list that isn't commented out.

Edit: edited to add this example... How to comment out the latest kernels...

Before
```
title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		6f01867d-158e-4b55-8b63-9aa4133c2059
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6f01867d-158e-4b55-8b63-9aa4133c2059 ro quiet splash quiet 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		6f01867d-158e-4b55-8b63-9aa4133c2059
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6f01867d-158e-4b55-8b63-9aa4133c2059 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic
```

After....
```
#title		Ubuntu 9.04, kernel 2.6.28-15-generic
#uuid		6f01867d-158e-4b55-8b63-9aa4133c2059
#kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6f01867d-158e-4b55-8b63-9aa4133c2059 ro quiet splash quiet 
#initrd		/boot/initrd.img-2.6.28-15-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
#uuid		6f01867d-158e-4b55-8b63-9aa4133c2059
#kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=6f01867d-158e-4b55-8b63-9aa4133c2059 ro  single
#initrd		/boot/initrd.img-2.6.28-15-generic
```

---

### Post by 314 on 2009-10-27
thanks

---

### Post by sanderj on 2009-10-27
> **314 said:**
> so i am in .15 not .16 and i get no freeze so far Yay

You can help Ubuntu & Linux to report this as a bug on [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

If you do, please specify the hardware you use.

---

