---
title: "kdm Does not find Nvidia 8178 driver after reboot..."
date: 2006-01-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by scunc_dvl on 2006-01-13
Having a GeForce 6600, I have been there and done that and read many posts on installing the latest NVidia drivers (tseliot's being particularly helpful), and my installation has worked some time with my previous Ubuntu 5.10 installation (best of all I got Doom3 working with the 32-bit driver fix suggested).... Anyways this problem is narrowed down enough I think this is definitely a KDM/X11 issue, likely a module mishap, and I'd like to know what is going on so I could make the simple fix.

Let me describe then, my problem in point form:
[INDENT]
--have amd64-k8 headers installed (fine)
[INDENT] uname -r returns "2.6.12-9-amd64-k8"[/INDENT]
--build-essential and the necessary gcc-3.4, ld
--(linux source installed but not g'unzipped, this is OK)

--linux-restricted-modules-amd64-k8 installed *(I don't think this is OK because it seems to also install nvidia-kernel-common, which is in version 1.0.7667+1 and it should probably be completely removed.. However Adept wont let me remove it without removing all the other k8 restricted modules, so I seem to be stuck with it.)*

--nvidia-glx is removed and so is the file in /etc/init.d

I boot up in recovery mode, point CC to the right gcc-3.4 then run "sh TheEnormousNameoftheNvidia1.0.8178-pkg.run". Which only warns me because it detects all the old Nvidia installs I made to my kubuntu. I let it save the settings to my xorg config file.

I type "exit" (still in recovery mode...), and Nvidia works, whoo!

Then I reboot, thinking I accomplished the installation fine again..

Then KDM gives me that terrible pause on ** Checking Battery State... [OK]*, which means it aint working.
[/INDENT]

If I boot again in recovery mode and run the .sh installer, then type Exit, Nvidia is working again.

x.x

Forward this to tseliot's enormous related thread, if this should be answered there... (It is about a 70-page thread remember :P ) I think what should be happening through is xorg should pick the right module to load, assuming it's staying installed somewhere anyway. I'm such a noob :-({|=

Oh and go ahead and be technical, I should know this stuff soon.

---

### Post by MartinG on 2006-01-13
The usual solution for this is what you hint at above, remove linux-restricted-modules, at least in 32-bit stuff. See e.g. 
[http://ubuntuforums.org/showthread.php?p=652878](http://ubuntuforums.org/showthread.php?p=652878)

However, this can cause problems if you're using other modules in that package apart from the nvidia one.

---

### Post by scunc_dvl on 2006-01-13
I resorted to removing those linux-restricted-modules, which lets me boot with Nvidia intact. (The fact kdm doesn't seem to find .xinitrc and doesn't auto-load my nvidia-settings annoys me so, but I'm leaving it as is). Looking at the package descriptions for the restricted stuff, I'm probably missing out on acpi (power management) support, and particularly in KDM that isn't changing anything (PowerNow has always worked, i.e. I've never seen an instance where it's running at full or 1/2 CPU speed at the wrong time..).

Another solution to try perhaps is to use a command to load the right kernel module..I know it's possible somehow, but I'm so NOT willing to do any more tweaking with -this- anytime soon :P

Pretty sure this is the same error by the way, as I've seen this come up often during my past tweaks in kubuntu:

[INDENT]Error: API mismatch: the NVIDIA kernel module is version 1.0.7667, but
this X module is version 1.0.8178. Please be sure that your kernel
module and all NVIDIA driver files have the same driver version.[/INDENT]

---

### Post by defuseme2k on 2006-01-13
you will mismatch because there are still old nvidia things loaded :P.  I bet if you tried, you could reinstall the driver, and then xorg will load right up, but after the next reboot you are confronted with the kernel module mismatch thing.

dpkg --purge nvidia-kernel-common

reboot.

---

### Post by mo_x on 2006-01-14
I think you should first upgrade your kernel to 2.6.12-10-amd64-k8. Then remove all packages related to the nvidia driver with the --purge option. Then reinstall the 1.0.8178 driver.

---

