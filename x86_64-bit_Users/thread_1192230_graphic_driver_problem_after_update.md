---
title: "graphic driver problem after update"
date: 2009-06-19
forum: x86 64-bit Users
---

### Post by gahligahli on 2009-06-19
Hello, 

I have just used the update manager to update my 64 bit jaunty system, and upon restart it will not recognise my graphics card drivers correctly.  


I have an nvidia 9800gtx, and it was running fine with the nvidia linux drivers available from their website, now when ubuntu starts i get this:

(EE)Failed to load module "type 1" (module does not exist, 0)
(EE)Failed to load module "freetype" (module does not exist, 0)
(EE)Nvidia(0) failed to load the Nvidia kernel module!
(EE)Nvidia(0) ***aborting***
(EE)Screens found but none have a usable configuration

So I click on the OK button, and choose from the next list to use the default graphics configuration, and here I am back and safe at my desktop.  

Must I just reinstall the Nvidia drivers or is there a way to change the configuration to go back to using it?  or included in the last updates i got is there a new program that simply cannot deal with using nvidia drivers?  

Thank you!

---

### Post by Arup on 2009-06-19
> **gahligahli said:**
> Hello, 

I have just used the update manager to update my 64 bit jaunty system, and upon restart it will not recognise my graphics card drivers correctly.  


I have an nvidia 9800gtx, and it was running fine with the nvidia linux drivers available from their website, now when ubuntu starts i get this:

(EE)Failed to load module "type 1" (module does not exist, 0)
(EE)Failed to load module "freetype" (module does not exist, 0)
(EE)Nvidia(0) failed to load the Nvidia kernel module!
(EE)Nvidia(0) ***aborting***
(EE)Screens found but none have a usable configuration

So I click on the OK button, and choose from the next list to use the default graphics configuration, and here I am back and safe at my desktop.  

Must I just reinstall the Nvidia drivers or is there a way to change the configuration to go back to using it?  or included in the last updates i got is there a new program that simply cannot deal with using nvidia drivers?  

Thank you!

Since the new update has bought about a kernel change, you have to remove the drivers which were compiled against older Kernel and re-install, this is where using drivers from the repos comes in handy but uninstalling and re-installing is not a big task.

---

### Post by gahligahli on 2009-06-19
Thank you for your quick reply mate.  

Unfortunately as I am a noob this will be not so straightforward for me.   I have now read this

[http://ubuntuforums.org/showthread.php?t=80131](http://ubuntuforums.org/showthread.php?t=80131)

and this, 

 [http://ubuntuforums.org/showthread.php?t=481887](http://ubuntuforums.org/showthread.php?t=481887)


but is there anything that i need to know specifically for jaunty?  if it's only a brief explanation then i would be grateful if you could guide me.

---

### Post by Arup on 2009-06-19
Make sure to place the installed driver in your home folder. Do a ctrl+alt+F1 and login. Do a sudo /etc/init.d/gdm stop after that do a sudo sh NVIDIAxxxxxx --uninstall the xx stands for the driver which will be picked up automatically by bash. Make sure to add the --uninstall after that

Once unisntall do a sudo reboot and then go back to the terminal the same way and install the driver.

---

### Post by gahligahli on 2009-06-20
Thanks, that worked.  I hope someone needs my help with this one day so i can pass it on.  

Cheers!

---

