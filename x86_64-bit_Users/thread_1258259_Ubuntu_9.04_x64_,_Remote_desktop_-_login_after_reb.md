---
title: "Ubuntu 9.04 x64 , Remote desktop - login after reboot?"
date: 2009-09-04
forum: x86 64-bit Users
---

### Post by edwardtilbury on 2009-09-04
It seems strange that Ubuntu would be like this, since it's a great linux webserver os.

I log into my desktops and servers all the time, rebooting and logging off on Windows, but when I try to use the default VNC program I cannot login after reboot.  Basically I have to be logged in locally to be able to log in remotely.. This is really annoying.

In the meantime I'm going to mickey-mouse it and just keep the login on automatic and maybe password protect the screensaver, but there's got to be a more decent solution.  Thanks.


(oh, and yes I searched, I found a bunch of old threads suggesting vnc4server and walkthroughs of people installing a ton of terminal commands in old versions like 6 etc.. but I'm looking for an updated answer for this version, I would think that this would be solved by 9.04 and maybe I'm just overlooking something.)

---

### Post by edwardtilbury on 2009-09-04
So I enabled this setting in System > Administration > Login Window  called XNEST

it worked once.. I could actually log in , and it was pretty nice, even resized the screen to fit my laptop just like windows RDP, but then after i logged out and tried again it failed, something about missing fonts... wth....

So close.... damn...

---

### Post by raygj on 2009-09-04
> **edwardtilbury said:**
> It seems strange that Ubuntu would be like this, since it's a great linux webserver os.

I log into my desktops and servers all the time, rebooting and logging off on Windows, but when I try to use the default VNC program I cannot login after reboot.  Basically I have to be logged in locally to be able to log in remotely.. This is really annoying.

In the meantime I'm going to mickey-mouse it and just keep the login on automatic and maybe password protect the screensaver, but there's got to be a more decent solution.  Thanks.


(oh, and yes I searched, I found a bunch of old threads suggesting vnc4server and walkthroughs of people installing a ton of terminal commands in old versions like 6 etc.. but I'm looking for an updated answer for this version, I would think that this would be solved by 9.04 and maybe I'm just overlooking something.)

just a thought-if i remember rightly? a user  of "root user"  cannot log in remotely.make a standard "user" account and try to log in using the standard "user" account you made.

---

### Post by bford16 on 2009-09-05
> **edwardtilbury said:**
> It seems strange that Ubuntu would be like this, since it's a great linux webserver os.

I log into my desktops and servers all the time, rebooting and logging off on Windows, but when I try to use the default VNC program I cannot login after reboot.  Basically I have to be logged in locally to be able to log in remotely.. This is really annoying.

In the meantime I'm going to mickey-mouse it and just keep the login on automatic and maybe password protect the screensaver, but there's got to be a more decent solution.  Thanks.


(oh, and yes I searched, I found a bunch of old threads suggesting vnc4server and walkthroughs of people installing a ton of terminal commands in old versions like 6 etc.. but I'm looking for an updated answer for this version, I would think that this would be solved by 9.04 and maybe I'm just overlooking something.)You cannot start VNC after a reboot unless a local user has logged in first, and enabled VNC.  But there are two alternatives that should work.

1. Use SSH.  Assuming your remote computer is automatically connected to the network, you can login via ssh without a local user logged in first.  However, you cannot log in graphically (to GNOME for instance) via this method.  It is possible to run a remote *program* graphically on your local desktop.  Read up on ssh to learn more. [http://www.unixtutorial.org/2009/05/ubuntu-ssh-how-to-enable-secure-shell-in-ubuntu/]("http://www.unixtutorial.org/2009/05/ubuntu-ssh-how-to-enable-secure-shell-in-ubuntu/")

2. Use XDMCP.  This will allow you to log in to the remote machine in graphical mode.  You must have a user account on the remote system, and you must have enabled XDMCP.  You'll have to do some research to enable XDMCP. It is disabled by default, and the method to enable it is different for gdm, kdm, xdm (whichever display manager you are using).

---

