---
title: "[SOLVED] NVidia 8600GT x 2  - blank screens"
date: 2008-01-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by peter120980 on 2008-01-27
I know this has been covered a few times but i have tried lots of things and am at a complete loss and this is my first linux install so bear in mind i know very little.

Basically its the blank screen after intall or using the live CD etc

I have managed to find a few things that have worked for other people but not for me, some suggest changing the splash to nosplash in the GRUB booloader GUI. Others have pointed to editing the menu.lst in the boot directory but when i view mine it completely empty and i dont have a xorg.conf file either.

I know how to navigate through the different directories and edit file using nano now but im now at a complete loss.

Just to confirm what is happening and what ive tried:
I cant run the LIVE x86 amd 64 CD, it just hangs on a blank screen but the monitor remains on
I can install Ubuntu from the alt CD and install seem to go ok uo tp the point it asks you to remove the disk and reboot computer.
Just after the bootloader GUI after selecting Ubuntu the screen turns itself off but the computer seems to carry on loading
I have tried running reovery mode and can get a command prompt, as soon as i type init 3 etc Ubuntu starts to load but then the screen flashes a few times and goes black but stays on
I have tried using the CTRL+ALT+ -/+ to change resolution but nothing, also when i try to use CTRL+ALT+F2/F3/F4 etc i cant bring up any other consoles, CTRL+ALT+f1 is the only one available
xorg.conf is missing and menu.lst is empty.
I also have windows XP on another partition

My system is: AM2 6000, 320gb sata hd, corsiar 2gb 6400 memory, 2 x PCi-E Nvidia 8600gt running in SLI.

My dad has just installed with no problems and since we are both jsut starting to get into linux we want to run the same Linux if possible and i been told Ubuntu is a nice version to start with. 
If you can help, thank you in advance.

---

### Post by peter120980 on 2008-01-28
Well i think im just gonna go back to windows as much as it pains me to do so, everything I have tried does not seem to work, i.e nosplash stuff and reconfig xserver.
 Anyone with the same problem i hope you have better luck than me

---

### Post by hajk on 2008-01-28
Well, the GeForce 8600GT does not handle splash well in Gutsy. I've just upgraded my old GeForce 6200 to a new 8600GT, and I'm experiencing the same problem (whereas splash worked fine with the old 6200 card). This will no doubt all be sorted out in the upcoming Hardy release. Meanwhile, changing the boot option from splash to nosplash will give you a black screen with boot messages flashing by, followed by the regular gdm login screen. Make sure to install the nVidia restricted driver for the Compiz desktop effects to work.

---

### Post by Perfect Storm on 2008-01-28
> Others have pointed to editing the menu.lst in the boot directory but when i view mine it completely empty and i dont have a xorg.conf file either.

Sounds like you wrote path or mis-typed or forgot that linux is case sensitive when you did it.

---

### Post by peter120980 on 2008-01-28
I am aware that linux is case sensitive now, and the boot.lst is not empty.
As im new to this im not sure what im doing wrong for example when i type "nano /boot/grub/boot.lst" i get a blank text editor, but if I type "cd /boot/grub" then "nano boot.lst" it brings up the file correctly.  

I changed the nosplash thing and still i have the same problems although Im not entirely convinced its all down to the graphics card but then i could be wrong.  I still have no "xorg.conf" file in etc directory.  Could this possibly be located somewhere else of have I missed something in the installation.

I love a good challange but this is becoming tiresome, i never expected it to be easy either.

I have installed the comand line option form the alt cd and that seem to have booted through perfectly ok.  I assume i can now intall GNOME or KDE etc from here or is that just not an option? Ill have to lookup how to install such things as I still dont reall yknow what im doing but any help would be very grateful, many thanks in advance.

---

### Post by John Jason Jordan on 2008-01-28
> **peter120980 said:**
> I am aware that linux is case sensitive now, and the boot.lst is not empty.
As im new to this im not sure what im doing wrong for example when i type "nano /boot/grub/boot.lst" i get a blank text editor, but if I type "cd /boot/grub" then "nano boot.lst" it brings up the file correctly.  

I changed the nosplash thing and still i have the same problems although Im not entirely convinced its all down to the graphics card but then i could be wrong.  I still have no "xorg.conf" file in etc directory.  Could this possibly be located somewhere else of have I missed something in the installation.

I love a good challange but this is becoming tiresome, i never expected it to be easy either.

I have installed the comand line option form the alt cd and that seem to have booted through perfectly ok.  I assume i can now intall GNOME or KDE etc from here or is that just not an option? Ill have to lookup how to install such things as I still dont reall yknow what im doing but any help would be very grateful, many thanks in advance.
The file you need to look at is /boot/grub/menu.lst, not boot.lst. There is no "boot.lst" file, so if that is what you tell nano to open it will think you wish to create a file with that name and open a blank editing window. 

Another thing that may help is to search the forums for the 8600 card. I have read a lot of posts from people who have problems with it. Perhaps one of them has a solution.

---

### Post by peter120980 on 2008-01-28
doh sorry "boot.lst" was a typo, i meant to put "menu.lst" in there, was thinking about something else lol.
I have looked at many solutions none of which seem to help me.  I'll just have to keep looking and see what comes up.

---

### Post by peter120980 on 2008-01-28
OK so i have made a little bit of progress, i can now find the xorg.conf file and menu.lst file and can edit them both. Small progress I know but for me its a big leap lol.

I have tried what i can find on the forums such as changing the noslash thing and cahnging to the vesa drivers using the dpkg-reconfigure thing but still i have the same problems. Im thinking maybe im doing something wrong there.

If someone could point me in the right direction of how to use the "sudo dpkg-reconfigure xserver-xorg" properly maybe that would help, form what i can gather i have set the resolution, refresh rates etc to what they should be but theres lots in there i dont understand.  For example, looking at other peoples xorg.conf file the BusID shows the PCI to be set to 1, something like "PCI:1:0:0" whereas mine is set to "PCI:2:0:0". I assume they have PCI-E the same as me (to a certain extent), but do you think this would make any difference?

What about installing the restricted drivers in the recover prompt, is this possible and would it make any differnce to me been able to load to the GUI logon screen?  If so any ideas how i might do this, bare in mind i dont really know what im doing.

I really, really wanna be able to get this to work, i had high hopes for linux but they are fading fast.

---

### Post by John Jason Jordan on 2008-01-28
> **peter120980 said:**
> OK so i have made a little bit of progress, i can now find the xorg.conf file and menu.lst file and can edit them both. Small progress I know but for me its a big leap lol.

I have tried what i can find on the forums such as changing the noslash thing and cahnging to the vesa drivers using the dpkg-reconfigure thing but still i have the same problems. Im thinking maybe im doing something wrong there.

If someone could point me in the right direction of how to use the "sudo dpkg-reconfigure xserver-xorg" properly maybe that would help, form what i can gather i have set the resolution, refresh rates etc to what they should be but theres lots in there i dont understand.  For example, looking at other peoples xorg.conf file the BusID shows the PCI to be set to 1, something like "PCI:1:0:0" whereas mine is set to "PCI:2:0:0". I assume they have PCI-E the same as me (to a certain extent), but do you think this would make any difference?

What about installing the restricted drivers in the recover prompt, is this possible and would it make any differnce to me been able to load to the GUI logon screen?  If so any ideas how i might do this, bare in mind i dont really know what im doing.

I really, really wanna be able to get this to work, i had high hopes for linux but they are fading fast.
I don't know about the PCI:1:0:0 vs PCI:2:0:0.

As for the nVidia proprietary drivers, I think the ones you want are called nvidia-glx-new. To install do "sudo apt-get install nvidia-glx-new." If I recall correctly, installing them automatically changes the xorg.conf file so it will use them. If it does not look in the xorg.conf file and search for "nv" and "nvidia." There is a line where it says which driver to use. 

If the apt-get command says it can't find the file, it is because you don't have the restricted repositories enabled. There is a command line way to add repositories, but I don't recall the command, nor do I remember the URL for the repository. I'm in a hurry right now, but perhaps you can find the details elsewhere.

You should also run "lspci" and look for your video card. Write down exactly what it is called, including upper- and lowercase, caps, punctuation, etc. Copy and paste this into the appropriate lines in xorg.conf if it's not already in there.

---

### Post by peter120980 on 2008-01-28
Many thansk for that, about to go give it try, i need to do some reading on this repositories thing as im not really sure what its about.  
I have made some progress though with regards to booting into ubuntu normally.  The bootup still hangs after "loading local scripts....." but this time th monitor does not turn blank, instead i can press enter and get a comand prompt asking me to log in.  Now i have to work on getting the GUI to run.  I can use CTRL+ALT+F1/2/3/4/5/6 but 7 gives me a blank screen.

Im still a long way off getting this sorted but hopefully soon there may be light at the end of the tunnel.  The bright side of this is that im learning about linux all the time and things are slowly starting to make sense.

Well if anyone else knows how to enable the restricted repositories thing from the command line please help me out.

---

### Post by John Jason Jordan on 2008-01-29
> **peter120980 said:**
> Many thansk for that, about to go give it try, i need to do some reading on this repositories thing as im not really sure what its about.  
I have made some progress though with regards to booting into ubuntu normally.  The bootup still hangs after "loading local scripts....." but this time th monitor does not turn blank, instead i can press enter and get a comand prompt asking me to log in.  Now i have to work on getting the GUI to run.  I can use CTRL+ALT+F1/2/3/4/5/6 but 7 gives me a blank screen.

Im still a long way off getting this sorted but hopefully soon there may be light at the end of the tunnel.  The bright side of this is that im learning about linux all the time and things are slowly starting to make sense.

Well if anyone else knows how to enable the restricted repositories thing from the command line please help me out.
Glad to hear you're making headway. As long as you finally have the GUI running you don't need to enable the restricted repositories from the command line. Instead, go to System > Administration > Restricted Drivers Manager. But before you do that make a copy of your /etc/X11/xorg.conf file, just in case. You can always restore the copy from the command line if installing the restricted drivers boogers things up.

---

### Post by peter120980 on 2008-01-29
Omg i finally worked it out, i really cant believe it.  Not sure of the process because i had changed a few things in th xorg file before i discovered what it was.

Basically the BusID for the PCI-E slot is set by default to 2:0:0:0 in the xorg file, my computer however  
has it set to 7:0:0:0 so i changed this in the xorg file and bingo.  I can now boot into xserver and have windows style desktop.  

I still have alot to sort out as i can only use the 'nv' driver and not the restricted ones as i get pinky kind of squares everywhere and the grahics are messed up but its a start.

I will post my xorg file when i get back from work to show what i did, its probably a rule of thumb to do what i did but as i have no real idea of what im doing im quite pleased with myself.

Thanks everyone for your input.

---

