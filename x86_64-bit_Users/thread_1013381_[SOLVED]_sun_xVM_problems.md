---
title: "[SOLVED] sun xVM problems"
date: 2008-12-16
forum: x86 64-bit Users
---

### Post by jmorsman on 2008-12-16
good evening everyone;

 I have a Dell XPS M1530 dual core computer that I am running Ubuntu 8.10 64 bit version on. I decided that I wanted to see if I could set up a vm on the machine. I downloaded what I needed from the sun website and installed it on the computer. Everything seemed to go well until I started the vm. The first message I get when the vm starts is "Fatal no bootable medium found system halted." Ok, this does not seem too bad I went to change the settings for the vm and this is the second message I received.

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.

Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {489fb370-c227-4d43-9761-ceb28484fd9f}
Callee: 
IMachine {1e509de4-d96c-4f44-8b94-860194f710ac}

Once the message goes away you can change the settings and the same problem returns, however the settings remain changed. 

Although I keep staring at the same problem I seem to be missing the point. What do I need to do to achieve the 3% rule in this area? 

Thanks,

---

### Post by jmorsman on 2008-12-17
For what it is worth I have managed to find some information on this problem.
 [http://ubuntuforums.org/showthread.php?p=6058465#post6058465](http://ubuntuforums.org/showthread.php?p=6058465#post6058465)
I havent tried it yet but I will let you know if it works.

---

### Post by doobiest on 2008-12-17
First I'd like to know did you create a Virtual disk from scratch now at the point of installing windows onto that virtual disk?

If thats the case the first message sounds like you didnt mount the windows cd/iso on the vm.  Which is something you have to do manually from the menu.

---

### Post by jmorsman on 2008-12-17
Yes I did set up a virtual disk, I made the disk 10g and I figured that should be adequate. I also turned on most of the options in the settings restarting the vm each time to see if the change made a difference. It did not so far. I happen to have a few copies of various windows operating systems I have purchased over the years from 95 - xp, I changed the cd's just in case one of them had a defect from sitting in my desk drawer over the years. I deleted each vm and set up a new one for each cd(using the same virtual disk). finally I created an iso image to my desktop and instead of trying to mount the cd I had the vm try to access the image file on the desktop. I still get the fatal error message. 

I also added the line to fstab from the link that I found earlier. This did remove the second error,

"Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer."

With this error no longer appearing as the vm starts up I do hear the cd/dvd player spin up like it is reading the disc, this is something new that it did not do before. But the error appears again and the vm terminates. 

Sorry for the lengthy explanation I figure if I explain what I have done so far it would make it easier to see what I haven't yet.  

Thanks for the help
12-21-08 It happens to be the windows cd's that seem to have a problem. It seems that nine purchased cd's all have the same problem they no longer work. I did manage to load another operating system in the vm and it works just fine. So windows is out of the picture considering that I am not going to purchase another copy of ms anything again.

---

