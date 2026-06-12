---
title: "My Mini is blank first boot..."
date: 2006-04-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by mail_order_mini on 2006-04-04
I'm new to linux and to these forums so I'll here's a short intro: I'm Cam, got Mac Mini (1.42GHz) over christmas, I'm 16 and am from New Zealand...

Here's my problem:

I recieved the Ubunt 5.10 cd set in the mail the other day and was eager to try it out. I booted up the live cd and everything worked fine (though I found out throught trial and error than my monitor resolution needed to be seat at 800x600 instead of the normal 1024x786 or whatever for OSX)

I backed up all my stuff onto an external hard drive and then booted off the OSX install cd and used its partitioning utility in Disk Utility to set up some space for Ubuntu (putting linux in the 1st partition as I was told by a website i came accross).

I then reinstalled OSX. Everything was working fine. I started the Ubuntu installation process and it plodded away doing it's thing. It came the time for the computer to reboot. With the cd ejected it did so, I pushed "l" in yaboot's first stage and then pushed return for the second stage. It loads the kernel and I see it working away (text scrolling past) and then the screen just goes blank.

I have searched all over for solutions to this problem (trying to boot in single user mode to edit/look at xorg.conf). The common result was that Ubuntu assumes the highest video settings supported by your graphics card which would be incompatible with my shitty 15' CRT. I have experimented with all sorts of key combinations suggested by posts to kill x11 and have only suceeded in occasionally rebooting the maching with them. I don't hear any sound or login window chime.

Many thanks to anyone who can shed light on my situation or provide help!!
mail_order_mini (Cam)

Edit: Using the live cd I mounted the linux file system and had a look around. The xorg.conf file contained nothing so I copied the one from the live cd's filesystem over to it and rebooted but the same blank screen occured

---

### Post by 3rdalbum on 2006-04-05
Usually when you open a file in Nano and it's "blank", it means that you've mis-typed the file path. Linux is case-sensitive, so the pathname should be: /etc/X11/xorg.conf. (uppercase X11)

---

### Post by mail_order_mini on 2006-04-05
I didn't open it in nano. I located it in Ubuntu Live after I mounted the drive  and opened it wiht the default text editor. The live version opened fine, the other showed nothing and was 0kb

---

### Post by linear on 2006-04-05
Well, if it works from the Live CD it should work from the installed version (unless there was a problem during the install).
 
Try this: boot Ubuntu. When you get to the blank screen, drop to a console (ctrl-opt-F1) and enter: **sudo dpkg-reconfigure xserver-xorg**.
 
With luck that will get you to working video.

---

### Post by stmiller on 2006-04-05
Did you press tab at the boot prompt to see install options? And try any of those?

---

### Post by mail_order_mini on 2006-04-06
Nope, puching tab in yaboot gives me a line of text saying "Linux         old". None of the key combinations have any affect at all (can't access console). Do you thing that it would work if I copied the filesystem from the live CD to the hard disc and tried to boot off that?

---

