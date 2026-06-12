---
title: "Cannot log in to Ubuntu"
date: 2006-12-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by girionis on 2006-12-16
Hello, I have restarted my ubuntu linux 6.06 and after I restarted it I cannot login into the os. I get prompted with the login screen but when I enter the username and password it gets me back to the login screen again. I am not sure what is going on but this started all of a sudden. I am using 2.6.15-27-amd64-generic kernel. I am not sure where to start in order to fix the problem, I can only login in using the fail safe mode and get the shell command prompt. Can anybody give me any idea of how I can go on or what logs I should possibly check in order to see the problem?

Thank you for your time.

Regards

---

### Post by padre999 on 2006-12-16
You can get this behaviour if the disk is full...

see [http://ubuntuforums.org/showthread.php?t=297337](http://ubuntuforums.org/showthread.php?t=297337)

---

### Post by girionis on 2006-12-16
Hello padre999  thank you for your reply. I have 22 GB of free space on my hard drive, so I do not think this is an issue of running out of space. I can login using the failsafe terminal session on the ubuntu login page, but I am not sure what to do after that. What logs I should check or anything. Any more ideas?

Thank you

---

### Post by taurus on 2006-12-16
Maybe you want to check the permission of ~/.dmrc...

Boot into recovery mode from GRUB menu and at the prompt, run

```
ls -la /home/**username**/.dmrc
```

---

### Post by girionis on 2006-12-16
Hello taurus this is what I get

-rw------- 1 panos panos 26 2006-03-13 20:07 /home/panos/.dmrc

I can read and write it, shall I change it to also execute it?

Thank you

---

### Post by taurus on 2006-12-16
No.  That's the right permission.  

Try holding down <Ctrl><Alt>F2 to get into a console.  Now, log in with your username and password to see if you can actually log in at all.  And if you can, then we know that your username and password are good.  It's Gnome then...

To get back to GUI login screen, press <Alt>F7.

---

### Post by girionis on 2006-12-16
Right it seems that more people have the same problem

[http://www.linuxquestions.org/questions/showthread.php?p=2546870#post2546870](http://www.linuxquestions.org/questions/showthread.php?p=2546870#post2546870)
[http://www.ubuntuforums.org/showthread.php?t=292580](http://www.ubuntuforums.org/showthread.php?t=292580)
[http://ubuntuforums.org/showthread.php?t=283220](http://ubuntuforums.org/showthread.php?t=283220)
[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/68291](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/68291)

Will look into them and will let you know.

---

### Post by girionis on 2006-12-16
> **taurus said:**
> No.  That's the right permission.  

Try holding down <Ctrl><Alt>F2 to get into a console.  Now, log in with your username and password to see if you can actually log in at all.  And if you can, then we know that your username and password are good.  It's Gnome then...

To get back to GUI login screen, press <Alt>F7.

Yes I can login from the console. I can also login in "failsafe terminal" session. I have looked at the links I posted above, they are talking about a tdfx driver in the xorg.conf file vut doing

cat /etx/X11/xorg.xonf | grep tdfx 

returns nothing. So it must have been something else. Any more thoughts?

---

### Post by taurus on 2006-12-16
Could be a permission to one of the config files for Gnome!!!  

From the console (after you log in), paste the output of this command here then!

```
ls -la ~/.gconf
```

p.s.  Actually, that should have been

```
cat /etc/X11/xorg.conf | grep tdfx 
```
not /etx/X11/xorg.xonf...

---

### Post by girionis on 2006-12-16
Yes you are right, it is /etc and not /etx, it is just that I cannot copy/paste from the terminal window and I wrote all the information by hand, so I made a mistake, sorry.

Now the result of the 

ls -la ~/.gconf shows three directories

apps
desktop
system

Thank you

---

### Post by taurus on 2006-12-16
What are the permissions and owners of those files?  Another way to test is to create another user and see if you can log into Gnome with that new user?

---

### Post by girionis on 2006-12-16
Right we are making progress :) I created naother user and I can login properly :)

What files do I need to compare in order to see the differences between the two users?

The result of the ls -la ~/.gconf is

drwx------ panos panos 4096 2006-11-05 23:36 apps
drwx------ panos panos 4096 2006-03-13 20:07 desktop
drwx------ panos panos 4096 2006-03-13 21:58 system

Thank you for your help and time.

---

### Post by taurus on 2006-12-16
The new user should only have a handful of . files for Gnome so may want to check the .gnome, .gnome2, .gome_private, .gconf, & .gconfd...

---

### Post by girionis on 2006-12-16
I have way too many files in the gnome2 folder of the old user compared to these I have with the new user. The rest of the folders are more or less the same.  Anyway it will take me a bit of time to go through all of them. If I manage to resolve the issue I will let you know. Meanwhile if you can think of something else please let me know.

Thank you again for helping me.

---

### Post by taurus on 2006-12-16
I probably would concentrate my energy in ~/.gnome2...

---

### Post by girionis on 2006-12-17
No luck. I even deleted all .gnome related and .metacity files and rebooted but still get the same problem. Any more ideas?

---

