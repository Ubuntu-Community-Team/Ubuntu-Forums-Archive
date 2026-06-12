---
title: "Ubuntu Boot Issues on a G3 b&amp;w"
date: 2006-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by DrUbuntu on 2006-01-25
Hi all,

Hope you can help me.... I`ve installed ubuntu on my g3 b&w with 1gb ram and a radeon 7000 64mb card. The install went really smooth and generally the machine runs perfectly... One small problem tho... When i do a fresh install,install KDE and choose that as the default session with automatic login the machine will not boot after a restart. what happens is that it gets past the ubuntu startup screen then goes to a half white half black screen and stops, the pointer is still responsive on the screen but that`s about it?

Does anyone know how to startup the mac, goto a shell and change either the auto logon or change it back to gnome as it seems to be about the point that the kde startup screen appears when it stops booting?

Any help would be appreciated.
cheers,

---

### Post by beansbbq on 2006-01-25
DrUbuntu,


   Try the switchdesk command.  I've used the command in the past although it has been several years.  I remember the ability to quickly and easily switch back and forth between desktops.  Back then I use to switch between gnome, kde, and evolution.  Using a terminal, such as Putty, try the following command.  You may want to read the man page on it first since I"m not sure what all of the options are.  Research it, and best of luck to you.  

"switchdesk gnome"

---

### Post by DrUbuntu on 2006-01-25
hiya,

How can i get to the terminal when the mac boots as it seems to go straight into ubuntu...

cheers,

---

### Post by sulobanks on 2006-01-25
Can you network you mac and ssh to it from another machine?  If you can login to your account remotely, you could do the switchdesk thing.  Also, have you tried ctrl-alt-backspace?

---

### Post by DrUbuntu on 2006-01-25
hiya,

tried the ctrl+alt+backspace but nothing happens... Can you describe the procedure to ssh to this mac from say a linux booted pc?

cheers,

---

### Post by sulobanks on 2006-01-25
ssh -l <username on remote machine> <ip address of remote machine>

I don't recall if sshd is installed by default. :/

I wonder if the ubuntu boot cd has a rescue option.

[edit]  Indeed, you can boot from the cd and type rescue.
Once into the system, go to /etc/gdm/gdm.conf and change AutomaticLoginEnable=true to AutomaticLoginEnable=false.  Then reboot without cd and see if it just takes you to the gdm login.

---

### Post by DrUbuntu on 2006-01-25
hello again,

tried to type rescue from the botted install cd but it just goes to the installer. Is their a specific procedure that i need to follow?

cheers,

---

### Post by beansbbq on 2006-01-26
Dr Ubuntu,

If you are still having difficulties with the rescue option, perhaps you can use the Ubuntu Live cd as a rescue disk.  Mount the hard drive, and then manually edit the file that sulobanks suggests.  Reboot without the cd and see if you are all set.  

It not, try the Live cd again and undo the gdm.conf change.  (It's important not to make too many changes at the same time as this makes it difficult to troubleshoot).

Next, you'll want to change the boot process to runlevel 3. This will boot up your machine without the gui, since that appears to be where your problem lies, but will offer full networking capabilities.  See this link for details.  

[http://www.linuxquestions.org/questions/showthread.php?p=1995523#post1995523](http://www.linuxquestions.org/questions/showthread.php?p=1995523#post1995523)

Once you get past that, reboot.  You should come up to a text based screen.  Then try running the switchdesk command then.  

You'll want to install the SSH server so that way you can remote in from another computer in the future.  This was my first order of business on my Ubuntu machine.  
  
Here is another link that gives some additional background information.   
[http://www.howtoforge.com/forums/showthread.php?p=11551](http://www.howtoforge.com/forums/showthread.php?p=11551)

You should be able to piece together what you need from these links and a quick search on the Ubuntu Forums.  Let us know how it goes.

Best of luck...

---

### Post by hndrcks on 2006-01-28
Here's a quick something to try at the second stage boot prompt type

```
Linux video=ofonly
```

The boot process will look weird color-wise but you might just be able to get in then.

---

