---
title: "16-bit support missing??"
date: 2008-04-14
forum: Wine
---

### Post by wingnux on 2008-04-14
After updating to .59 (even after reverting to .58) I keep getting errors like this:

[email]wingnux@wingnux:~/.wine[/email]/drive_c$ wine /media/cdrom/SETUP.EXE 
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:load_winedos Could not load winedos.dll, DOS subsystem unavailable
winevdm: unable to exec '--app-name': 16-bit support missing


Even when running winecfg!

[email]wingnux@wingnux:~/.wine[/email]/drive_c$ winecfg
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report


Can anyone tell me what is it about and how to solve it? Thanks in advance!

---

### Post by SarahKH on 2008-04-16
It's a bug, kinda.  Basically changes have been made in the sysctl file to protect the first 64k of kernel memory to stop future attacks.

You can revert the change by using:

sudo sysctl -w vm.mmap_min_addr=0 

This *might* allow 16bit apps to work, it might not, but it will stop the complaining.

---

### Post by wingnux on 2008-04-18
Thank you VERY MUCH! =)

---

### Post by click on 2008-04-28
Thank you very much for the solution. It indeed works. However, I want to ask does this setting change disables any other software to work in wine? What was the previously defined setting if I want to reverse it back?

---

### Post by cogadh on 2008-04-28
By running that command it temporarily resets the sysctl setting to allow Wine to work. At the next reboot, it will go back to the original setting. Changing it temporarily or permanently will not affect any other software, but it may make your system very slightly less secure.

---

### Post by error420 on 2008-05-12
> **SarahKH said:**
> It's a bug, kinda.  Basically changes have been made in the sysctl file to protect the first 64k of kernel memory to stop future attacks.

You can revert the change by using:

sudo sysctl -w vm.mmap_min_addr=0 

This *might* allow 16bit apps to work, it might not, but it will stop the complaining.

Installed flawlessly! THANK YOU!

---

### Post by bryanagee on 2008-05-20
Much appreciated. The only scary thing is how many windoze apps rely on that old 16-bit code slag. =)

---

### Post by JGrubbs on 2008-07-03
This worked for me as well! Now I can install my six year old's Lego Land on his Edubuntu system. Thanks!

---

