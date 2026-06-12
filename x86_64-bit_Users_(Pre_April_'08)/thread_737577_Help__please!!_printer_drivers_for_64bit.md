---
title: "Help  please!! printer drivers for 64bit"
date: 2008-03-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tomanderland on 2008-03-27
Hey guys

Im new to linux and have just installed 7.10 64bit because 32 was suprisingly slow.. for some reason. Im not too good with terminal or installing etc etc but i need to get a Brother MFC 9180 working through my home network, it's attached to a windows XP computer.
I got the printer working in 32 bit ubuntu but now i need it in the 64 bit one ive downloaded the  CUPS and LPR driver from the Brother website, neither will install saying its the wrong architecture. I went to the FAQ and it says this

I'm using an AMD64 bit version of Linux. Can I use the Brother Linux printer drivers?


[I]Yes. Our drivers are created and optimized for 32 bit version of Linux,
but those can be used for 64 bit Linux also. Some additional steps are required.

For rpm users:
1. After the driver installation, and if there is "/usr/lib64/filter/", copy the file which name starts with "brlpdwrapper" ( in the "/usr/lib/cups/filter/" ) to "/usr/lib64/cups/filter/".
Or confirm there are symbolic links between "/usr/lib/" and "/usr/lib64/".

For dpkg users:
1. Install lib32stdc++6(Debian) or ia32-libs(Ubuntu)
2. Restart the system
3. Use "--force-architecture" option when you install the drivers.
4. After the driver installation, and if there is "/usr/lib64/filter/", copy the file which name starts with "brlpdwrapper" ( in the "/usr/lib/cups/filter/" ) to "/usr/lib64/cups/filter/".
Or confirm there are symbolic links between "/usr/lib/" and "/usr/lib64/".[/I]

I installed the ia32-libs with synaptic package manager, then rebooted.. but what does the --force-architecture bit mean? When i double click the .deb file it just comes up with an error, theres no options. Am i supposed to install using terminal? If so what do I write? Any help would be greatly appreciated

Cheers, 
Tom

---

### Post by firecat53 on 2008-03-27
Install from the terminal:

sudo dkpg -i --force-architechture driverfile.deb

If you still have problems, check out the[ getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs") script )

Good luck!
Scott

---

### Post by Tomanderland on 2008-03-27
Thanks for the quick reply, i did that to the lpd file and the cups file this is what came up
[I]
sudo dpkg -i --force-architecture cupswrapperMFC9180-1.0.2-1.i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 87634 files and directories currently installed.)
Preparing to replace cupswrappermfc9180 1.0.2-1 (using cupswrapperMFC9180-1.0.2-1.i386.deb) ...
lpadmin: The printer or class was not found.
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
Unpacking replacement cupswrappermfc9180 ...
Setting up cupswrappermfc9180 (1.0.2-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperMFC9180
cp: `/usr/lib/cups/filter/brlpdwrapperMFC9180' and `/usr/lib64/cups/filter/brlpdwrapperMFC9180' are the same file
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
lpadmin: Unable to copy PPD file![/I]
I still cant get to the printer in that driver list when you go to add a new printer.. maybe thats the unable to copy PPD file? Tryed installing with getlibs too i dont think i did it right but not much happened..

cheers

---

### Post by firecat53 on 2008-03-27
Hmmm....did you check the items in #4?

4. After the driver installation, and if there is "/usr/lib64/filter/", copy the file which name starts with "brlpdwrapper" ( in the "/usr/lib/cups/filter/" ) to "/usr/lib64/cups/filter/".
Or confirm there are symbolic links between "/usr/lib/" and "/usr/lib64/".

It sounds like only one of those two conditions need to be met. You can check for a symbolic link by typing in the terminal 'ls -l /usr' and looking for something like 
   lrwxrwxrwx   1 root root     3 2008-03-05 07:30 lib64 -> lib

Also in the terminal, type 'groups' and make sure lpadmin is one of the groups you belong to. If now, you can go to System -> Admin -> Users/Groups and add a group lpadmin to which you and root belong to. you will have to log out and log back in after you make that change.

I tried installing that deb on my machine and it seemed to install ok, but I didn't get the errors about lpadmin, which is why you should check that.

Good luck!
Scott

---

### Post by Tomanderland on 2008-04-01
Thanks a lot!! Got it working somehow i sort of just tried everything.. great help!

cheers,
tom

---

### Post by mjrwingnut on 2008-04-02
I'm having the same issue with my printer HP Photosmart 3210xi

---

