---
title: "low graphics mode"
date: 2009-08-08
forum: x86 64-bit Users
---

### Post by alaukik.kot on 2009-08-08
hello guys,
   i face problem here...
on booting screen i have 6 ubuntu options 
ubuntu 9.04 kernal generic 2.6.28-14 
ubuntu 9.04 kernal generic 2.6.28-14 (recovery mode)
ubuntu 9.04 kernal generic 2.6.28-13
ubuntu 9.04 kernal generic 2.6.28-13 (recovery mode)
ubuntu 9.04 kernal generic 2.6.27-14
ubuntu 9.04 kernal generic 2.6.27-14 (recovery mode)

out of this only in 2nd last option which is-

ubuntu 9.04 kernal generic 2.6.27-14 
 graphics and display works fine, and in rest all when i try to boot it shows very bold fonts and visually awkward view.
 
first screen message comes as i log in any other option is 
UBUNTU is running on low graphic mode      
(EE) NVIDIA(0): failed to load the NVIDIA kernal mode
(EE) NVIDIA(0):***abort***
(ee) screen(s) found, but none have usable configuration.

after i press OK

another screen comes 

what would you like to do?
[LIST]
[*]Run ubuntu in low graphics mode for just one session
[*]reconfigure graphics
[*]trouble shoot the error
[*]exit to console
[/LIST]

---

### Post by Malta paul on 2009-08-08
You can use the Kernel that works for you, remove your current driver from System>Administration>Hardware Drivers. Then reboot and use the 'recovery mode' with your latest Kernel which should now bootup with the generic video driver.
Go back to 'Hardware Drivers' and select the recommended driver. Reboot again with the latest Kernel and it all should work. :D

---

### Post by Malta paul on 2009-08-08
Have just checked, For info the latest kernel update for Ubuntu 9-04 is 2.6.28-15.
But I am using 2.6.30 stable version and its working great!
:cool:

---

### Post by alaukik.kot on 2009-08-11
in need of desperate help,
   i did exactly as mentioned above, first i logged in from the most latest version of kernal's recovery mode, display did come fine. then i removed the nvidia drivers which were named as   NVIDIA accelareted graphic driver version 180; then i restarted the computer and tried to install those drivers again. now problem is when i go on hardware drivers and tries download those recommended drivers then the process starts and terminates on its own. i tried "  nvidia-xconfig" in terminal as root it gave me this result - 

root@alaukik-desktop:/home/alaukik# nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: No Layout specified, constructing implicit layout section using screen
         "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add new
         CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new
         CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'



earlier it use to work in one of those kernals but now all the kernals are running on low graphics mode


please help....

---

### Post by alaukik.kot on 2009-08-11
please help me out in how to exatly make it start working with normal graphic mode.... when i used to use ubuntu 8.01 that time all visual effects were pleasing :) waiting for them to recover back :)

---

### Post by Malta paul on 2009-08-11
Sorry to hear you are still stuck in low graphic mode.:(

Do you have a live Ubuntu CD? if so can you it boot into a normal screen resolution ?

---

### Post by alaukik.kot on 2009-08-11
k, i'll just try it n come back to you in 15 mins...
 thankx for keenly helping me....

---

### Post by alaukik.kot on 2009-08-11
i tried using ubuntu live cd but i could see tos of squashsf errors and buffer I/O errors.... after ubuntu language selection and ubuntu screen loading there are these series of errors comes...

---

### Post by Malta paul on 2009-08-11
Wow, What is the spec. of your system? Have you got a backup copy of your important files? 

If you have easy access to a reasonable speedy Internet you could try downloading the recovery disk. This has worked for me when my system went wrong.

Keep posting we'll get there mate:)

---

### Post by alaukik.kot on 2009-08-11
i have really pathetic speed of internate but i can keep it on for whole night...
please tell me how to go about this recovery thing...

---

### Post by alaukik.kot on 2009-08-11
i think my cd-rom isn't working

---

### Post by Malta paul on 2009-08-12
If you can, try out your live CD on a friends computer and see if it works OK, If it dose then it could be a hardware fault.
(he may even let you borrow his CD-ROM to try out in your computer?)

Don't give up :)

---

### Post by Deiu on 2009-08-12
I've had a similar problem after purchasing a system with nvidia GeForce GT220. Ubuntu 9.04 couldn't detect/install the appropriate drivers and there were no drivers in the repository list that matched my hardware.

I managed to fix it using the latest drivers from the nvidia ftp server. I have detailed the process on my blog page: [http://andrei.envisioningtech.net/2009/08/geforce-gt220-linux/](http://andrei.envisioningtech.net/2009/08/geforce-gt220-linux/). Since then I have my video card running just fine! :)

---

