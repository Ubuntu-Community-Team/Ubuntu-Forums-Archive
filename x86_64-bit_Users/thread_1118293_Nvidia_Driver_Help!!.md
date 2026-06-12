---
title: "Nvidia Driver Help!!"
date: 2009-04-06
forum: x86 64-bit Users
---

### Post by tampablendie on 2009-04-06
Hey guys I'm relatively new to Ubuntu and have run into a serious video driver problem.  I downloaded the install file from Nvidia specifically for my platform.  I disabled X by running

 sudo /etc/init.d/gdm stop

I then ran the install file

 sudo sh NVIDIA-Linux-x86_64-180.44-pkg2.run

Upon restart there is a header saying that it is checking battery life( don't know why because this is not a laptop??) then there seems to be an error message saying something like

 running local boot scripts etc/rc.local

I'm not a hundred percent on that as the error whips by, and is then followed by a window stating that my video driver is not configured and that I am in low graphics mode.  So I configure the video driver and go to desktop.

I have tried to go to the menu item nvidia xconfig settings.  But it always gives me an error stating that I'm not running an x config file and to run

   nvidia-xconfig

which I do and still I can't get into nvidia xconfig settings.  So I disabled the proprietary drivers in hardware settings and restarted.  Everything booted up alright with no errors, so I tried to enable the proprietary drivers again and rebooted.

Now the system crashes everytime I try to boot with multicolored screen.

Help!! ;-)  Thanks in advance guys!

---

### Post by burns1111 on 2009-04-06
A guy has come up with a repository for nvidia related drivers.  My interest was really on the VDPAU media player integrations he did.  Check it out at:

[http://www.avenard.org/files/ubuntu-repos/]("http://www.avenard.org/files/ubuntu-repos/")

Cheers

---

### Post by tampablendie on 2009-04-06
Thanks but could you tell me how to disable the bad driver so I can get back into the desktop?

---

### Post by tonyric on 2009-04-07
Boot using the rescue mode entry in grub..... Then run the following:

sudo pico /etc/X11/xorg.conf

find the line:

Driver "nvidia" (the key is the nvidia in the parenthesis)

Change "nvidia" to "nv"

Save with a Crtl+o

sudo reboot

you should now be running using the default open source nvidia drivers.

Tony

---

### Post by loomsen on 2009-04-07
not really use for a grub disk there.

Boot into single user mode, choose root or netroot whichever one you'd like, and copy and paste this:

## First remove everything installed (as you are in a root shell now, NO sudo

```
dpkg -l nvidia* | grep ii | cut -d " " -f3
```

## This will show your installed packages

```
aptitude remove  `dpkg -l nvidia* | grep ii | cut -d " " -f3`
```

and then maybe the best idea for you is to get envyng and let it choose the appropriate driver for you.

```
aptitude install envyng-core
```

When done

```
envyng-core -t
```

And follow instructions on your screen. Actually you don't need the .run package, same version in the repos (usually very soon after nvidia releases any stable driver)

```
nvidia-xconfig
```

You won't see anything except a message that it's been written.

```
exit
``` to leave the root shell, and resume normal boot.

---

