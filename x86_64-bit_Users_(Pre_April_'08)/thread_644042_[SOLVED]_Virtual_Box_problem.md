---
title: "[SOLVED] Virtual Box problem"
date: 2007-12-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Luis Macias on 2007-12-18
Hi im trying to run Vista form virtualBox OSE, i followed the instructions of this link [http://www.arsgeek.com/?p=1348](http://www.arsgeek.com/?p=1348) , but i get this error:


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 This is what i get when trying to run vista, can anyone help?? Thanks

---

### Post by johnnybirdman on 2007-12-18
> **Luis Macias said:**
> Hi im trying to run Vista form virtualBox OSE, i followed the instructions of this link [http://www.arsgeek.com/?p=1348](http://www.arsgeek.com/?p=1348) , but i get this error:


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 This is what i get when trying to run vista, can anyone help?? Thanks

seems like you might have forgot to add yourself to the users.  see these instructions here.  worked for me with 2000 and xp. [COLOR="Blue"] [http://ubuntuforums.org/showthread.php?t=603661](http://ubuntuforums.org/showthread.php?t=603661)[/COLOR]
If you did do this, as the message states, you need to reboot.

---

### Post by Luis Macias on 2007-12-20
thanks for the answer, i tried to follow the instructions on the link and helped a little, but now i et this error:

FATAL: Could not read from the boot medium! System halted.

I dont have the vista cds so im using a iso i found in another turoial, could this be the problem?

Thanks in advance
--
Or is there a way to open the vista os i have in another partition???

---

### Post by mips on 2007-12-20
> **Luis Macias said:**
> thanks for the answer, i tried to follow the instructions on the link and helped a little, but now i et this error:

FATAL: Could not read from the boot medium! System halted.

I dont have the vista cds so im using a iso i found in another turoial, could this be the problem?

Thanks in advance
--
Or is there a way to open the vista os i have in another partition???

Is the iso good and is it actually bootable? Sounds like you are trying to use a pirated copy?

---

### Post by Luis Macias on 2007-12-21
I got the ISO from a tutorial, but its not like the iso of the OS, what i understood is that the iso image is to make believe virtual box that u have a cd, but it will use the copy of vista i have installed ( cause i dont havethe cds), maybe this doesnt make sense (sorry im newby). That´s why im asking if there is a way to open the vista i have installed from virtual machine.

Thanks for helpuing

---

### Post by mips on 2007-12-21
Sorry, I dot know how to do that but now I understand what you mean. You basically want to boot vista installed on a existing partition on VB. Can you not just specify the drive in VB to boot from instead of a disk image?

---

### Post by Luis Macias on 2007-12-21
I dont couldnt find that option in virtual box, maybe ill hvae to try another app.

Thanks for ur help

---

