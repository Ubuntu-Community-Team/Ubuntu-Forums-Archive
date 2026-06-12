---
title: "sudo won't work"
date: 2006-01-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by DrBob on 2006-01-07
Whenever I try to use sudo (for example, to run synaptic), it comes up with the "enter your password" dialog (which I do), then nothing else happens when I click "OK". Synaptic does not run; I cannot see it in any process list, neither is sudo running. This happens if I do it through the console, too: if I type (for example) "sudo apt-get update", it will ask me for my password, and then nothing will happen apart from a new command prompt appearing below the submitted one.
This might be because I had to restart my computer just as Ubuntu booted into X for the first time (after doing the remaining setup), as xorg.conf was wrong (it auto-detected my dual-core nVidia 6600GT as being in PCI:4:0:0 instead of PCI:5:0:0), but I've since upgraded sudo by booting up in recovery mode so I could work as root.

Any ideas? :confused:

---

### Post by DrBob on 2006-01-07
I am currently managing to do stuff as root using su, but it's certainly not an ideal solution.

---

### Post by DrBob on 2006-01-08
I've managed to fix this by adding myself to the sudoers file (/etc/sudoers) manually as root. I don't know why I wasn't on there, but if anybody else encounters this problem, that's how to fix it.

---

### Post by Mustard on 2006-01-08
Did you use expert install?

Expert install doesnt set up the first user account with sudo privileges.  It asks for a root password during the install procedure instead and its then necessary to add sudo privileges later on using the visudo command from a root prompt.

---

### Post by DrBob on 2006-01-08
Yes, I did.
It might be nice if this was documented somewhere easily visible, or if programs which use sudo from within a GUI would throw an error dialog if sudo errored, instead of dying silently.

---

### Post by GQed76 on 2006-01-10
I have the same problem ona  new install but did NOT do the expert install.

I have the 32 bit install running fine on another partition, but the 64 bit pretty much ignores me when i need to access a system that requires my password.

---

### Post by DrBob on 2006-01-10
Are you listed in /etc/sudoers?

---

### Post by ifunky2 on 2006-01-10
Same problem with no sudo password acceptance

And I would like to try this fix of editting /etc/sudoers
The problem I have is that I can not login to root  on any level.
This is compounded by: I am a total linux newb. While I am grovelling around,
trying to figure out simply how it is you boot to "recovery mode"
and once there, how to manually edit the file, I thought I would post and see If I got a little help with these basic commands before I figure it out...
(which I fear will be many hrs)

"Mustard" --> "Did you use expert install?"

"DrBob" -->  "Yes, I did.
It might be nice if this was documented somewhere easily visible,"

<--- (*"A frigg'n men"* I lost hrs finding out why this happens, 
I must have reinstalled a 1/2 dozen times, with hopes that would cure my noobness)

Anywho.. If anyone feels so inclined ?
How do I get to "recovery mode"
and once there how do I, using the text commands edit the file ?
TY ahead

---

### Post by DrBob on 2006-01-10
Recovery mode is as simple as rebooting your computer, and using the arrow keys on the boot menu (GRUB) to select the "recovery mode" option (it should be the one just below what's selected by default).
Once you've booted into recovery mode, it's a little more complex, as you have to know the root password. If you did an expert installation, this is no problem, as you chose one then and there, but I can't help you if you did the normal installation, as I think (I'm not sure though) that the root password is set to something random by the normal installer.
However, if you know the root password, you don't need to boot into recovery mode - you can simply open up a console, and type "su", then enter the root password - this will temporarily log you in as root (just type "exit" to stop doing things as root).
Regardless of your method, once you're logged in as root, you need to edit /etc/sudoers. If you type the command "nano /etc/sudoers", and then edit the file (I can't give you much help on that, but there are other forum topics on it), you can press Ctrl+O to save the file, and then Ctrl+X to exit. :)

---

### Post by Mustard on 2006-01-10
Recovery mode on a default install will drop you to a root prompt without the password.  If you don't see the GRUB menu at startup then you probably have to press the ESC key to view it, as its sometimes hidden and only revealed when you hit the ESC key.

Once at the root prompt you can use this command to edit the /etc/sudoers file..

```
visudo  #this command does on thing.  It opens the sudoers file for editing
```

My sudoers file looks like this.  Note the last line where I give my user sudo privileges.  This is the line that would need to be added by those who, for whatever reason, don't have sudo privileges.

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
mustard ALL=(ALL) ALL

```

Assuming the person who posted above had the user name 'ifunky', then the line that would need to be added would be..
```
ifunky ALL=(ALL) ALL
```

---

