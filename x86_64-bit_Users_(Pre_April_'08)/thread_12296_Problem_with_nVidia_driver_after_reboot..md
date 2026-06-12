---
title: "Problem with nVidia driver after reboot."
date: 2005-01-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by martijntje on 2005-01-23
I'm having a slight problem getting my x-server (xorg) to start after installing the nvidia driver and a reboot.

At first, when i installed it, they worked fine. I just did the <Ctrl>+<Alt>+<BckSp> thingy, and a second i saw the nvidia logo, and could run tuxracer without any trouble.

However, after a reboot, x refuses to start. It gives me an error like
> Screens found, but none have a useable configuration

Now, if i remember correctly, this is what happens if the nvidia module isn't loaded (properly). On my old distro, i always did 'modprobe nvidia' if that happened. But apparantly, the module name has changed...

Anyone have an idea what i should do?

---

### Post by gheorghe_pop on 2005-01-23
It might be that your screen resolution it's wrong.I think that when the nvidia module isn't found it gives another error.

---

### Post by martijntje on 2005-01-23
I don't think that my resolution is wrong. I have a very reasonable setting for my monitor. It's an iiyama Vision Master Pro 454 19" According to it's documentation it can go up to 1900xWhatever, but i only run it at 1600x1200.

Besides it runs fine at first.
Oh, and the reason i think the module isn't loaded, is because i had that problem on a few other distros before. It was the exact same error message, fixed by running 'modprobe nvidia' as root.

---

### Post by valadil on 2005-01-23
Try adding nvidia to /etc/modules.  It's a list of modules that get modprobed at boot up.

---

### Post by martijntje on 2005-01-23
[QUOTE=valadil]Try adding nvidia to /etc/modules.  It's a list of modules that get modprobed at boot up.[/QUOTE]
 Thanks, but no thanks. The problem is that the module isn't called nvidia apparantly. If it was, this thread wouldn't be here.

---

### Post by Psy on 2005-01-23
It is called nvidia. Did you reboot with the same kernel as you installed the drivers? If not you have to rebuild them.

---

### Post by Buffalo Soldier on 2005-01-23
[QUOTE=martijntje]Thanks, but no thanks. The problem is that the module isn't called nvidia apparantly. If it was, this thread wouldn't be here.[/QUOTE]
NVIDIA Accelerated Linux Driver Set README & Installation Guide (Official)
[ftp://download.nvidia.com/XFree86/Linux-x86/1.0-6629/README.txt](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-6629/README.txt)

> If you already have an X config file working with a different driver (such as the 'nv' or 'vesa' driver), then all you need to do is find the relevant Device section and replace the line:
Driver "nv" (or Driver "vesa")
with
Driver "nvidia" "

The module IS called nvidia.

---

### Post by valadil on 2005-01-23
Not sure if you've already done this but you may need to grab the restricted modules package for your kernel.  This includes the nvidia driver.  Nvidia does not release their drivers as GPL so they have to be packaged separate from everything else.

---

### Post by martijntje on 2005-01-24
[QUOTE=Psy]It is called nvidia. Did you reboot with the same kernel as you installed the drivers? If not you have to rebuild them.[/QUOTE]
 
 Right, so my computer's just making fun of me, when i try to run the module
 > $ modprobe nvidia
 Password:
 FATAL: Module nvidia not found.
 $
 
 Oh, and yes i rebooted with the same kernel. I have the restricted packages selected in Synaptic. I just downloaded the nvidia-glx package through synaptic, after which i ran 'sudo nvidia-glx-config enable', and pressed <Ctrl>+<Alt>+<BckSp>, after which i saw the nVidia logo on my restarting X-server.
 
 The first time i did the nvidia-glx... thingy, it said something about having created a backup of my XFree86... file. But now it doesn't say anything. And yes, i have tried to run 'sudo nvidia-glx-config disable' first. It just doesn't work.

---

### Post by martijntje on 2005-01-24
Compiled the module myself for the time being, it works. Yippee!
 
 I'd still like to know why it doesn't work with Synaptic, so any comment would be great.

---

### Post by valadil on 2005-01-24
Did you grab the restricted modules for your kernel with synaptic?  The nvidia module itself isn't included in nvidia-glx.  Methinks they need a metapackage to get all the necessary nvidia stuff...

There was a bug some months ago where libglx.a wasn't created and you had to make it yourself from libglx.so in the X extensions directory.  Dunno if this is related.

---

### Post by martijntje on 2005-01-24
Yup, i grabbed the hell out Synaptic. When it didn't work i tried it by installing everything that turned up in a search for 'nvidia'. I believe you mean the nvidia-kernel-common package, right? I definitely had that one installed too.

Anyways, i can't look if it made the the libglx.a now, since i already installed the module manually.

Thanks for the tip.

---

### Post by aroswald1977 on 2006-08-03
Your card isn't an nvidia geforce2 mx/mx 400 by any chance?

I just had about the same thing happen=>

downloaded the driver from the nvidia website, loaded it up using method 2, at his site:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

everything worked GREAT... until <restart>. its like the module loads itself once and then hides <any ideas?>

---

### Post by aroswald1977 on 2006-08-03
seems it can find the module 'nv' either

---

### Post by diefans on 2006-10-12
try this hint, it worked for me:
[http://ubuntuforums.org/showthread.php?t=124649&highlight=nvidia+module+reboot](http://ubuntuforums.org/showthread.php?t=124649&highlight=nvidia+module+reboot)

there are two different places where the modules are located:
/lib/modules
/lib/linux-restricted-modules

installing the new driver unloads this restricted thing and loads the new from /lib/modules. on reboot the driver is beeing loaded from /lib/linux-restricted-modules again. 
thats why the reboot sucks - you have to delete the restricted one


cheers

---

### Post by kleeman on 2006-10-12
Type 
uname -a
to find out exactly which kernel you are running
Open synaptic and search for 'linux-restricted-modules'
Note the exact version (it is the numbers following linux-restricted-modules) and compare it with the kernel you are running. Your problem can occur if these do not match. The nvidia module is in the linux-restricted-modules package and if you have the wrong one installed the system cannot find it.

---

### Post by ahildoer on 2007-01-07
> **martijntje said:**
> I'm having a slight problem getting my x-server (xorg) to start after installing the nvidia driver and a reboot.

At first, when i installed it, they worked fine. I just did the <Ctrl>+<Alt>+<BckSp> thingy, and a second i saw the nvidia logo, and could run tuxracer without any trouble.

However, after a reboot, x refuses to start. It gives me an error like


Now, if i remember correctly, this is what happens if the nvidia module isn't loaded (properly). On my old distro, i always did 'modprobe nvidia' if that happened. But apparantly, the module name has changed...

Anyone have an idea what i should do?

I had the exact same problem. I simply removed the package nvidia-kernel-common. It removed some other general kernel packages, but I have not noticed any problems yet. Also, I do not see the nvidia logo on gdm startup, but acceleration appears to be working.

I removed the package like this:

```
aptitude remove nvidia-kernel-common
```

Just approve the removal of any dependent packages.

---

