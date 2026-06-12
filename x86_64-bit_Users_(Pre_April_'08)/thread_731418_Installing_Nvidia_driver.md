---
title: "Installing Nvidia driver"
date: 2008-03-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by MSdefecter on 2008-03-21
Hi,
I have been trying to get compiz to work for a while now and several posts later I have been told that I need to install the nvidia driver in order to get it working. The trouble is I have a nvidia 8800gts 512mb GPU and was told by somebody on the compiz site that this is not recognized by Ubuntu and so I will not be able to install using the restricted drivers manager. So I went to the Nvidia website and located the latest driver and followed the instructions on how to install it. When I enter the command to do this

sh NVIDIA-Linux-x86_64-169.12-pkg2.run

I get this error message

sh: Can't open NVIDIA-Linux-x86_64-169.12-pkg2.run

Does anyone know how to fix this?

---

### Post by which_chick on 2008-03-21
I'm a newbie and this may not be your problem, but have you checked the properties on the file to make sure you're allowed to run it?  I downloaded one of the nvidia amd64 drivers to check and they aren't set execute-able when you get them.

In a GUI (I use gnome) you can right-click the file, get the dropdown menu, left click properties, go to the "Permissions" tab, and put a check in the "execute" box at the bottom.

You can also do this in a terminal window by typing 

chmod 755 /path/to/file/filename

---

### Post by firecat53 on 2008-03-21
Are you running it from a virtual terminal (ctrl-alt F1)? Or you can boot the recovery entry in grub to a root terminal. And you need to be root to install it. AND you have to make sure the X server is shutdown (sudo /etc/init.d/gdm stop).  

Good luck :)

Scott

---

### Post by cyrus_the_virus on 2008-03-22
Hi,

I can't get the visual effects to work either with the same card even though the nvidia drivers are installeds succesfully on my system :( see: [http://ubuntuforums.org/showthread.php?t=731127](http://ubuntuforums.org/showthread.php?t=731127))

Anyway, to install the driver you need to make sure some packages are installed that are needed by the nvidia installer: kernel-source, gcc, build-essential. CHeck with Synaptic if these are installed and install them if necessary.

Then you need to go into terminal mode (ctrl+alt+F1) (save all open docs before doing so, otherwise you might lose data)
Then from the terminal enter 
* sudo /etc/init.d/gdm stop* to stop the x server
Then run the nvidia installer:
* sudo sh NVIDIA*.sh*
Follow thye instructions on the screen and make sure that the installer cpnfigures your xorg.conf file. When the installer is done reboot with:
* sudo shutdown now -r*

Good luck,
Marty

---

### Post by MSdefecter on 2008-03-22
O.K I have changed the file so that it is an exe file, but I am still having no luck. If I try to install via the exe, it launches via the terminal and then stops shortly afterwards because I need to be the root user. I am still having no luck installing via the command codes that I previously posted

---

### Post by caver1 on 2008-03-22
Have you tried Envy? there is a version for the Amd 64 platform. 
Just to forwarn you it may not help you with compiz. I have a Geforce 8600 vid card and cannot get compiz working no matter if I try restricted drivers or Envy.  If I enable compiz when I reboot I loose my grafics drivers and have to reload them. Without compiz everything is fine.
caver1

---

### Post by which_chick on 2008-03-22
Okay, once the file is executable, then you need to continue on with the rest of the directions that other people here have given...

1.  Check to make sure you don't need any other packages and that you have all the stuff you're going to need.  (nvidia kernel-source, gcc, build-essential)

To do this, go to system -> administration -> synaptic package manager.  It will ask for the admin password, go ahead and give it that.  Then, in the upper right-hand window, look for "nvidia kernel-source" and see that you have it there.  If you do not, you'll have to install it by putting a check in.  Go ahead and check for gcc and build-essential while you're there, checking boxes as necessary.  When you are done, if you DID have to check anything, see that it goes and gets the parts that you need.

2.  Now, save all your open stuff and go into terminal mode (ctrl+alt+F1).  

3.  In the terminal, enter 

sudo /etc/init.d/gdm stop 

to stop the x server

This stops the x server so that you can run your driver update safely.  

("sudo" makes you be root for the command that follows the word "sudo"  NOTE:  it is important to type stuff correctly when you are doing sudo because a typo can have unintended and sometimes disastrous effects.

Once you've done all that, THEN run the nvidia installer, also as root (using "sudo" in front of the sh command, which will solve the "stops shortly afterwards because I need to be the root user" problem you are having.)

Hope this helps.

---

### Post by lH)4~mK0e on 2008-03-22
Is this for Gutsy?  If you don't need anything special, you can try the Restricted Drivers Manager in System --> Administration and get the nvidia driver you need from there.  Make sure you run this in a terminal when you are finished:

```
sudo nvidia-glx-config enable
```

I needed to this do before I restarted in order to get video at all.

---

### Post by MSdefecter on 2008-03-22
I really do appreciate all your help but I just can´t get this to install. I have installed all 3 of the components that you told me I needed. I then ran the terminal mode using ctrl+alt+f1.
I managed to stop the gnome display using the command you gave me but when I try to install the driver using 

sh NVIDIA-Linux-x86_64-169.12-pkg2.run

It tells me that there is no such command. I also tried to use

 sudo sh NVIDIA*.sh

It tells me that it can not open that file

I also tried entering the terminal in the gui and typing sudo and then dragging the driver icon that is stored on my desktop into the terminal. Despite prefixing sudo to the beggining it still stops after a second telling me I have to be the root user.

WTF? Am I not doing?

---

### Post by bailbath on 2008-03-22
Nvidia sh module needs to be installed while x is not running you will probaly still get problems even if you manage to get the .sh to run.Surely it is easier to use the restricted drivers manager? Goto system-adminstration.
IAN

---

### Post by GTengineer on 2008-03-22
have you tried simply downloading the drivers again to make sure the file isn't corrupted?

---

### Post by MSdefecter on 2008-03-22
I agree that It would be a lot easier to use the restricted drivers manager to download the driver, but according to a member of the compiz technical team my graphics card is not supported by the restricted drivers manager and that is why when I go into it, it tells me that my hardware does not require any restricted drivers. That is why I am having to download it manually. 

I did download it again and the same thing is happening, I am now starting to think that it may be back to windows for me. noooooooooooooooooooooooo!!!!!!!

---

### Post by bailbath on 2008-03-23
Couple links for you to pursue-
This first one is a great website and forum for you to try if you use very upto date hardware.
[http://www.phoronix.com/scan.php?page=article&item=582&num=1](http://www.phoronix.com/scan.php?page=article&item=582&num=1)
[http://forums.whirlpool.net.au/forum-replies-archive.cfm/731443.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/731443.html)
Don't give up yet as time heals a lot of hardware issues with open source:)
IAN

---

### Post by firecat53 on 2008-03-24
OK, this may be a too simple question but.....
when you type 'sudo sh NV*run' are you in the same directory you downloaded the file to? That's the only reason i can think why it's telling you that you can't open the file.

Scott

---

### Post by winniepuh652 on 2008-03-24
Hi,
i am a new user here. I have the problem that my video is "Onboard! with "shared memory!. Ubunto can't read on the video card and it can't see the memory. It is a Biostar Board with a NVidia 6 on board .
Can anybody say me what i can do ! 

Execute my english!

---

