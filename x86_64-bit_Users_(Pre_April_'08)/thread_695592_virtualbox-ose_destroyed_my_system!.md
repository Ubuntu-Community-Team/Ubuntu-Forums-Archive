---
title: "virtualbox-ose destroyed my system!"
date: 2008-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by enoughsaid05 on 2008-02-13
I am soooo fed up,

when i install virtualbox-ose and restart, I cannot use wireless, and my desktop now falls to primitive gnome! And it seems like my system has gone nuts!

Can anyone please help!

---

### Post by shane2peru on 2008-02-13
ok, we are going to need a bit  more information on this.  Did you install Virtual Box via the repositories?  Or did you download the deb from their web site?  There really should be no reason for this to happen.  I have installed both and not had a problem.  Did you get any errors?  The more info you can give us on this the more help we can be. 

Shane

---

### Post by impact on 2008-02-13
I had a similar problem (I think it was some permission problem, but I never really investigated it), just  uninstalling vbox and rebooting fixed it.

---

### Post by aochoa on 2008-02-13
Similar problem here:

My Ubuntu 7.10 installation had been running really well and very stable until 3 days ago when installed Virutalbox. I installed it using the Add/Remove option under the "Applications" menu. I followed the installation instructions and after that, it seemed to have changed or restricted access to everything on my system configuration:

1. I can't see the "Add/Remove" option under the application menu anymore.

2. I can't see many of the application on the "administration" menu under "system" including "Users/Groups"

3. I can't use the command "sudo" any more

4. The volume control has got a "red" mark and when I click on it I get the messages:

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured."

"No volume control GStreamer plugins and/or devices found"

5. The firewall "firestarter" doesn't run any more, I get the following message when I try to run it:
"Failed to run /usr/sbin/firestarter as user root.
The underlying authorisation mechanism (sudo) does not allow you to run this program. Contact the system administrator."

I don't know what to do. I have been looking for information on how to access the machine using root, but because I can not do "sudo" and I can't "access users/Groups" I'm confused about how to continue. I guess the only solution is going to be backing up all my files and reinstall.

Unfortunately, every time I have tried to move away from Windows to Linux, there is something that ruins the process. My idea was to use my best computer at home totally with Linux, and to have a virtual machine with Windows XP to use the applications we use at work that demand the use of Windows. Well, Virtualbox has messes up totally with my computer and my plans (5 months of a very smooth user Linux experience gone to the drainage). I have to admit that I'm not an expert on the operating system yet, I have read a lot and learn a good bunch of commands. I'm trying just to be a good user and to use my computer to organize myself and have my work done, but it seems to me that Linux hasn't achieved this "transparent" experience as the greedy Microsoft  has done with Windows.

Because I can't really do much with my Linux computer right now and I need to research if I can't do something to avoid reinstalling it again, I installed Virtualbox in my Windows XP machine, and there were not problems at all. I have installed Ubuntu and PCLinuxOS as virtual machines, and I can run them perfectly at the same time inside Windows. 

Well, I hope to find some advice here, but If you think that it is to complex to fix or to explain, do not worry too much. I needed to share a bit of the frustration I'm feeling right now.

---

### Post by enoughsaid05 on 2008-02-13
Hi,

ok, i sounded a bit to frustrated

i downloaded this virtualbox-ose from the repostories (should have installed it from source!) and the system requires me to restart

so when i restart, my compiz effects stops and falls back to primitive gnome, my sound couldn't be detected. Even when I type 'alsamixer' in the terminal, it says something like device not found. When I click on network manager, there is no wireless device found. So all in all, things that i need are not there.

Oh, and when I type in ps-aux, all of the processes has a ? at the side

After removing virtualbox from synaptic, the problem still persists. (using sudo apt-get remove virtualbox-ose)

Why????

(Sigh)

What could be the problem?

Thanks in advance!

---

### Post by rab4567 on 2008-02-17
HELP, HELP,HELP!!!!!!
I'm having the same problem no sound, no nvidia drver is lock out, and cannot correct the screen resolution. What the hell I just want to try virtualbox for the first time this is scary

---

### Post by aochoa on 2008-02-17
rab4567, try this post:

[http://ubuntuforums.org/showthread.php?t=697783]("http://ubuntuforums.org/showthread.php?t=697783")

---

### Post by rab4567 on 2008-02-17
Thanks for the help but I jumped gun before I looked, what was happing was the computer was  automatically booting into the server partition rather than the generic partition in the grub menu  duh and big duh! I really need to get rid of that xp partition. So for now how do i get it to auto boot into the generic partition?

---

### Post by enoughsaid05 on 2008-02-17
Sigh

If aochoa have replied sooner, I could have save my system from reinstalling!

Thanks Aochoa!

---

### Post by rab4567 on 2008-02-19
Maybe I can get Wine to work.

---

### Post by dulbirakan on 2008-04-28
> **rab4567 said:**
> Thanks for the help but I jumped gun before I looked, what was happing was the computer was  automatically booting into the server partition rather than the generic partition in the grub menu  duh and big duh! I really need to get rid of that xp partition. So for now how do i get it to auto boot into the generic partition?

This one worked for me under hardy, just boot to the generic partition. To set the generic as default you should tamper with variable called "default" in /boot/grub/menu.lst or you can just comment out the 386 kernels or move the generic ones up in the list.

Thank you rab4567

---

### Post by dulbirakan on 2008-04-28
BTW: I would like to detail the problem. It all occured when I installed the kernel modules for virtualbox-ose-2.6.24-386. I guess I should have chosen the generic version in the first place.

How do we thank the users?

---

