---
title: "problem installing nvidia video drivers"
date: 2007-10-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by hotballz87 on 2007-10-07
i just got the 7.04 64bit version of ubuntu, and am trying to install the drivers for my nvidia 7 series videocard. i have the drivers, but when i try to run the program, it gives me this error:


Could not open the file /home/steve/Desktop/NVID&#8230;x86_64-100.14.19-pkg2.run.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.


what is there to do, such as what character coding do i use to run this, or is there something i can do to run this, or other types of drivers to use.

i am still fairly new to linux, and am only now really sitting down to spend the time to learn everything about it

---

### Post by saru411 on 2007-10-07
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

this script will install it for you and if you allow it to, it will configure your xorg also. to change any settings after you are finished installing enter sudo nvidia-settings into terminal an save xorg after you have it set up.

cheers

---

### Post by rahjman on 2007-10-07
It seems that the driver binary doesn't have the "executable" property. Just right click the file and turn on the check box abut it. Then run ./NVID…x86_64-100.14.19-pkg2.run at console. If you don't hava a working xserver, then type "sudo chmod 777 NVID…x86_64-100.14.19-pkg2.run" to make it executable.

---

### Post by incidence on 2007-10-07
> **rahjman said:**
> If you don't hava a working xserver, then type "sudo chmod 777 NVID…x86_64-100.14.19-pkg2.run" to make it executable.

Sometimes its not a great idea to give everybody all the permissions. To make it only executable, you could just run chmod +x NVID…x86_64-100.14.19-pkg2.run. Or chmod 700.

---

### Post by hotballz87 on 2007-10-07
> [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

this script will install it for you and if you allow it to, it will configure your xorg also. to change any settings after you are finished installing enter sudo nvidia-settings into terminal an save xorg after you have it set up.


i used this program, and it made it really easy to do, it installed drivers, and set it up. i did have to change my screen resolution, but that was simple.
thanks for the help

---

### Post by saru411 on 2007-10-07
you're welcome. i find using envy is the easiest way to install and set up video drivers for newbies. i know it helped me when i first started using linux/ubuntu. i hope you grow to like this fine o/s =)

---

