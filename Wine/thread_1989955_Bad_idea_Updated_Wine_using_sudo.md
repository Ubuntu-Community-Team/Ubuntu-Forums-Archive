---
title: "Bad idea: Updated Wine using sudo"
date: 2012-05-29
forum: Wine
---

### Post by concerro on 2012-05-29
I installed and updated Wine using sudo.  I now see in the sticky area that was a bad idea. 
Now I keep getting told it is locked. Do I have to uninstall it and reinstall it or can I run it a different way without doing a reinstall.

edit:When I try to do anything with wine from the terminal I get this -->cannot get pid from lock (lock isn't locked)
I have no idea what that means.

---

### Post by Dlambert on 2012-05-29
> **concerro said:**
> I installed and updated Wine using sudo. I now see in the sticky area that was a bad idea. 
Now I keep getting told it is locked. Do I have to uninstall it and reinstall it or can I run it a different way without doing a reinstall.
 
edit:When I try to do anything with wine from the terminal I get this -->cannot get pid from lock (lock isn't locked)
I have no idea what that means.
 
I would force uninstall, or just use playonlinux.

---

### Post by concerro on 2012-05-29
> **Dlambert said:**
> I would force uninstall, or just use playonlinux.
I have playonlinux. It says it is a front-end application to Wine. Does that mean I can just ignore Wine and use playonlinux. I have it installed, but I have not tried to use it yet.

---

### Post by sffvba[e0rt on 2012-05-29
> **concerro said:**
> I have playonlinux. It says it is a front-end application to Wine. Does that mean I can just ignore Wine and use playonlinux. I have it installed, but I have not tried to use it yet.

PlayonLinux is basically a configuration file that will automatically download and configure the correct version of Wine and any other dependencies that need to be installed to make a specific program work.

I am not sure if the issue you are having with Wine will prevent it from working correctly or not.

Perhaps try and see.


404

---

### Post by Dlambert on 2012-05-29
> **concerro said:**
> I have playonlinux. It says it is a front-end application to Wine. Does that mean I can just ignore Wine and use playonlinux. I have it installed, but I have not tried to use it yet.

Yes, you can ignore your system wine.

---

### Post by dschinn1001 on 2012-05-29
simply do: 
sudo apt-get remove wine*
then close and reopen terminal:
su
and as root the normal:
apt-get install wine

this should work.

---

### Post by concerro on 2012-05-29
Last question hopefully. Is there an online tutorial on how to use Playlinuxonline? I don't know how to run programs I have installed on windows.

---

### Post by sffvba[e0rt on 2012-05-29
> **concerro said:**
> Last question hopefully. Is there an online tutorial on how to use Playlinuxonline? I don't know how to run programs I have installed on windows.

Launch PlayonLinux.
Search for the application you want to install.
Select it and follow the prompts.
Once installed look for Desktop Icon and if none search for it in your normal menu as you would any other application.
Run it as you would any other application.

Not really much more than that to it.


404

---

### Post by concerro on 2012-05-29
LO(PlayLinixOnline) 
I used a USB stick as my virtual drive.
Then I got a message saying "No setup lcoation found in autorun.inf"

---

### Post by Avaritia on 2012-05-30
> **concerro said:**
> LO(PlayLinixOnline) 
I used a USB stick as my virtual drive.
Then I got a message saying "No setup lcoation found in autorun.inf"

You mean your trying to install a windows program from your USB drive?

What program is it?

---

### Post by concerro on 2012-05-30
> **Avaritia said:**
> You mean your trying to install a windows program from your USB drive?

What program is it?
I was not trying to install the program from the my USB at first. PLO told me to create a virtual hard drive, and my usb stick came up as an option. I then downloaded the program directly to the USB. 

The program is herolab. I tried it with Wine later once I realized Wine had to install the program also, not just run it from my Windows hard drive, but nothing happened. 

I have since uninstalled wine, but in the sticky it said that a virtual windows drive would need to be erased or hidden. I don't if Wine created one if I was supposed to create one for Wine. 

I am going to reinstall Wine though the software center once I get more info on the virtual HD issue.

---

### Post by sffvba[e0rt on 2012-05-30
What I would suggest is remove Wine.  Then in your home folder search for the hidden folder .wine and delete it.  Format the USB.

Now try again (but I wouldn't install the application to USB, I would just install it on your HDD and be done with it).


404

---

### Post by cogadh on 2012-05-31
> **concerro said:**
> I installed and updated Wine using sudo.  I now see in the sticky area that was a bad idea. 
Now I keep getting told it is locked. Do I have to uninstall it and reinstall it or can I run it a different way without doing a reinstall.

edit:When I try to do anything with wine from the terminal I get this -->cannot get pid from lock (lock isn't locked)
I have no idea what that means.
Sorry to jump into this so late, but installing Wine itself using sudo is not only NOT a bad idea, it is required. Installing or running applications in Wine using sudo is the bad idea, as it changes the user permissions on the .wine directory (where all of Wine's configurations and your installed applications are) so that your user no longer has the right to use them. 

Uninstalling/reinstalling Wine won't fix that as it does not remove the .wine directory. The easiest way to fix that is to either simply delete the .wine directory (sudo rm ~/.wine), which will delete everything you have installed in Wine, or change the permissions on the .wine directory to give yourself access to it again (sudo chmod 777 ~/.wine), which will keep everything you have installed in Wine.

---

