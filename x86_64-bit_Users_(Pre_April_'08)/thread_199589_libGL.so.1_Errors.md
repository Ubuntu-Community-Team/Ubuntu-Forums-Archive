---
title: "libGL.so.1 Errors"
date: 2006-06-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by chessforce on 2006-06-19
If you are using NVIDIA's 64-bit proprietary drivers with Ubuntu Dapper and are receiving the following error when trying to run programs requiring OpenGL (e.g. glxgears):
```

glxgears: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

```

you can try the following to see if it fixes the problem:
```

cd /usr/lib
sudo rm libGL.so.1
sudo ln -s libGL.so.1.0.8762 libGL.so.1

```

P.S. The libGL.so.1 symlink might automatically revert back to its original target at times (especially if you run `ldconfig`), at which point you will need to repeat the above steps to fix the problem again.

---

### Post by chessforce on 2006-07-23
If you are using NVIDIA's proprietary drivers with Ubuntu Dapper and are running into errors, such as the following, when trying to execute 32-bit programs utilizing OpenGL within the 64-bit environment (e.g. using Wine after following the [Wine set-up under Ubuntu Dapper x86-64 version without chroot]("http://www.ubuntuforums.org/showthread.php?t=185557") to run a OpenGL-powered game):
```

fixme:win:EnumDisplayDevicesW ((null),0,0x55c1f4d4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x55c1f50c,0x00000000), stub!
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  29 ()
  Serial number of failed request:  437
  Current serial number in output stream:  437

```

you can try a procedure similar to the one in the prior post:
```

cd /usr/lib32
sudo rm -f libGL.so.1
sudo ln -s libGL.so.1.0.8762 libGL.so.1

```

P.S. The symlink might revert, as stated in the earlier post, to the orignal source (e.g. after running `ldconfig`).

---

### Post by Kilz on 2006-07-24
Thank you for the fix. I had to do some editing on my wine howto today. I added the error, with a link to this post.

---

### Post by chessforce on 2006-07-24
> **Kilz said:**
> Thank you for the fix. I had to do some editing on my wine howto today. I added the error, with a link to this post.

You are welcome.  Thank you very much for writing the Wine HOWTO, which I found to be very useful!

---

### Post by ravikm on 2006-09-12
hi,

this is wat i get when i run glxgears:
"Error: couldn't get an RGB, Double-buffered visual"

any solution to this?

thanks,
ravi.

---

### Post by Kilz on 2006-09-12
> **ravikm said:**
> hi,

this is wat i get when i run glxgears:
"Error: couldn't get an RGB, Double-buffered visual"

any solution to this?

thanks,
ravi.

That error is displayed because you do not have the drivers for your video card setup. If you tell me the name of the card I might be able to give you a link to a hoto that will help.

---

### Post by ravikm on 2006-09-12
> **Kilz said:**
> That error is displayed because you do not have the drivers for your video card setup. If you tell me the name of the card I might be able to give you a link to a hoto that will help.

i have NVIDIA GeForce 6100 on ASUS A8N-VM.

thanks,
ravi.

---

### Post by Kilz on 2006-09-12
> **ravikm said:**
> i have NVIDIA GeForce 6100 on ASUS A8N-VM.

thanks,
ravi.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
That page should help you

---

### Post by ravikm on 2006-09-13
> **Kilz said:**
> [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
That page should help you

when i run "sudo nvidia-glx-config enable"

> Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

i ran "md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum".

> 74370dfc7b5b5c38bfc35c6c589368de  /etc/X11/xorg.conf


i ran "sudo nvidia-glx-config enable" again.

> A backup of xorg.conf has been stored as:
/var/backups/xorg.conf.2006-09-13-18:49:34.
If the new configuration will not work you will be able to
revert the changes simply using this command:
cp /var/backups/xorg/xorg.conf.2006-09-13-18:49:34 /etc/X11/xorg.conf


Warning: your X configuration has been succesfully changed.
In order to take full advantage of the changes, X needs to
be restarted.

after hitting ctrl-alt-backspace, xserver did not start... i reverted to the backup. 

thanks,
ravi.

---

### Post by Kilz on 2006-09-13
> **ravikm said:**
> when i run "sudo nvidia-glx-config enable"



i ran "md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum".



i ran "sudo nvidia-glx-config enable" again.



after hitting ctrl-alt-backspace, xserver did not start... i reverted to the backup. 

thanks,
ravi.


Did you try and manulay edit the xorg.conf? If so copy/paste it here.

---

### Post by ravikm on 2006-09-14
> **Kilz said:**
> Did you try and manulay edit the xorg.conf? If so copy/paste it here.

the present xorg.conf part is

> Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:5:0"
EndSection

i replaced "vesa" with "nvidia" for the driver & then hit ctrl-alt-backspace. xserver did not start.

should i edit in some other way??? (identifier, busid)???

thanks,
ravi.

---

### Post by kuja on 2006-09-14
It isn't quite that simple for the nvidia card. If you were using vesa before dri was probably still trying to load and that would conflict with nvidia's proprietary driver.

Try configuring x with this command
```

sudo nvidia-xconfig --no-logo --composite

```

---

### Post by ravikm on 2006-09-15
> **kuja said:**
> 
Try configuring x with this command
```

sudo nvidia-xconfig --no-logo --composite

```

the drivers r installing. after restarting xserver, glxgears gave random output then screen froze but mouse pointer moved. with these (nvidia) drivers, screen is freezing after abt 2 mins after logging in / after running any application.

thanks,
ravi.

---

### Post by reeper_aut on 2006-12-15
I've installed wine and it works, but i always get an error related to the one before:

err:ddraw: DDRAW_Create Couldn't load WineD3D - OpenGL libs not present?

gears works fine
libs should be right there.

not sure if this is related, but there is one more:

fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot

---

