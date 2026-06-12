---
title: "VirtualBox freezes my laptop on execution"
date: 2009-10-06
forum: x86 64-bit Users
---

### Post by amitso on 2009-10-06
I have just recently installed VirtualBox 3.0.4 and am finding it crashes my PC on execution.  I have also installed VirtualBox 3.0.6 and 3.0.8, and no improvement what so ever was noticed. Is there something I may be missing in the installation of virtualbox? What's the best way to capture some debug information.

My system is Intel Core2 Duo 2.66GHz running Ubuntu 9.04 64-bit.

Thanks.

---

### Post by Scunizi on 2009-10-06
Are you sure you downloaded the 64 bit version?  Did you install build-essential and dkms?  Have you added yourself to the vbox users group?

---

### Post by amitso on 2009-10-06
> **Scunizi said:**
> Are you sure you downloaded the 64 bit version?  Did you install build-essential and dkms?  Have you added yourself to the vbox users group?

Yes. Downloaded and installed the AMD64 version.

I have build-essential and dkms installed. I installed virtualbox with the deb packaged file so I'm not too sure why these are required.

I have added myself to the vbox user group with the line:

sudo usermod -G vboxusers -a *username*

Any other the suggestions would be greatly appreciated.

---

### Post by Scunizi on 2009-10-07
The last thing I can suggest is getting on IRC and going to the vbox channel..  The server is the same as ubuntu's, irc.freenode.net #vbox .. They are very helpful.  Be aware that the folks in there are typically on a different time zone.  So if you don't get answers right away be patient and repost the question every 20 mins. or so.

If you need an IRC client there are bunches but I suggest only two.  Xchat (not xchat-gnome) for the gui and irssi for cli access.  They are both available in the repos.  I typically use irssi in a terminal window with screen so if I need to restart x I don't loose my connection and can get back to it through a tty or terminal window.

---

