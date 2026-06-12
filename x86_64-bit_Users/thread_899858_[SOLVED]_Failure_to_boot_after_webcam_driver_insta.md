---
title: "[SOLVED] Failure to boot after webcam driver install"
date: 2008-08-24
forum: x86 64-bit Users
---

### Post by causeitsme on 2008-08-24
I am running Ubuntu Hardy on an Acer Laptop with a webcam that lsusb lists as an ALI. I followed the instruction on a how to and thought everything was fine. Last command was modprobe -a. I got no error messages so I did the next step in the how to. Reboot.

Rebooted to Grub and I selected Ubuntu and it didn't start up as normal. I usually get a screen with Kernal Alive ..... and then the Ubuntu splash with the progress bar.
What happened was it jumped to a screen scrolling through with all sorts of actions that were occuring and then it got to bluetooth startd [OK] and stopped, did nothing else.

I did a hard reboot and went into Recovery Mode and it gave me options to boot normally, repair, shell, and another repair option.

No matter what I do it gets to bluetooth and freezes when you finally try to boot normally.

Is there a way I can enter shell and disable the webcam and bluetooth *(or whatever comes after bluetooth)so I can then boot and undo everything I did in the how to?

---

### Post by causeitsme on 2008-08-25
Bump, anyone? Is there anything similar to windows safe mode on Ubuntu which would allow me to start up and change those things I did before?

---

### Post by causeitsme on 2008-08-26
So, no one knows of a way to do this? Is my only solution to wipe the drive and reinstall?

---

### Post by kdorf on 2008-08-26
What's probably happening is the bluetooth kernel module is causing your system to freeze. Run recovery mode, select root shell, and run the following commands:
```
cd /etc/modprobe.d
cp blacklist blacklist.bak
echo "blacklist bluetooth" >> blacklist
```

This will force your system to ignore the bluetooth kernel module. Hopefully it will help.

EDIT: It might also be the bluetooth init script. Try blacklisting the kernel module, and if that doesn't help, we can disable the system service.

---

### Post by causeitsme on 2008-08-26
> **kdorf said:**
> What's probably happening is the bluetooth kernel module is causing your system to freeze. Run recovery mode, select root shell, and run the following commands:
```
cd /etc/modprobe.d
cp blacklist blacklist.bak
echo "blacklist bluetooth" >> blacklist
```

This will force your system to ignore the bluetooth kernel module. Hopefully it will help.

EDIT: It might also be the bluetooth init script. Try blacklisting the kernel module, and if that doesn't help, we can disable the system service.

Hi, Thanks for answering!

I followed your instructions and then typed reboot in the shell and the computer restarted and went to the grub menu. I selected the first option which is Ubuntu (not the recovery option). 

I got the black screen with 'Kernal Alive' and then the Ubuntu splash screen with the progress bar and all seemed to be well. Then the progress bar froze at about 1/8 of the way and wouldn't finish booting. 

Then I did a hard restart and went back and did your instructions again and again tried to restart normally, this time the progress bar almost went all the way to the end when all of a sudden the screen changed from the splash to the same screen from before (showing the services starting). It was showing that again it was frozen on Bluetooth.

So, that changed something but, didn't fix it.

How do I blacklist the kernel module?

---

### Post by causeitsme on 2008-08-27
Ok, so I've been googleing and trying to get things sorted out in single user mode and I'm still stuck. This is what I've tried so far:

In Recovery Mode, in root shell, I tried to get sysv-rc-config installed by doing 
```
sudo apt-get install sysv-rc-config
```
I got a message that it couldn't find sysv-rc-config.

So, I thought: I must not have network access. So I did 
```
/etc/init.d/networking start
```. I got a message that seemed to indicate it was online. Something like Networking [OK]

So, I 
```
sudo apt-get install sysv-rc-config
```
Same result, couldn't find sysc-rc-config

So I tested the connection by ```
sudo apt-get update
```

Here I got a lot of messages that it couldn't locate (or couldn't connect, I forget exactly) to any of the repositories. So, I guess it's not going online. (I'm not wired, I'm assuming that enabling networking will allow my wireless to connect) - Is this correct?

I do know that Bluetooth is blacklisted because when it wouldn't update I did.
```
etc/init.d/udev restart
```
This returned a message about bluetooth being blacklisted and froze the system and I had to do a hard reboot. (The reason for doing this command is I had found this code (below) online that said it would get my networking going.)
```
etc/init.d/udev restart
etc/init.d/module-init-tools restart
etc/init.d/networking start
```

I would like to be able to post the last terminal session I did before this system failure, but, I can't seem get far enough in to do this, I saved that session in Documents as a text file. I figure if I have this I could show someone and they would know what to do to undo it. Can anyone tell me how to get that text file out of there with the system only at root shell?

---

### Post by silverglade00 on 2008-08-27
cat /home/your_user_name/Documents/the_file_you_saved.txt | more

That will type it to the screen so you can read it one page at a time.

---

### Post by causeitsme on 2008-08-27
> **silverglade00 said:**
> cat /home/your_user_name/Documents/the_file_you_saved.txt | more

That will type it to the screen so you can read it one page at a time.

Thanks!!

Turns out the problem was an fdi file I'd added to hal for cheese to work. Apparently when hal is started it's causing some conflict in my system I guess.

For anyone curious I was following this tutorial:

[http://ubuntuforums.org/showpost.php?p=5055135&postcount=6]("http://ubuntuforums.org/showpost.php?p=5055135&postcount=6")

I'm gonna mark this solved as it did what I needed - Got my system back up!

Thanks to everyone who helped!:guitar:

---

