---
title: "OpenOffice 2.04, Edgy, AMD64: No drag-and-drop editing in OO Write!"
date: 2006-11-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by cogitordi on 2006-11-10
I have OpenOffice 2.04 in Edgy-64 on an AMD64 PC. In OO Write, I have no drag-and-drop editing capability.

On my Dapper-32 PC, I have OO 2.02 and I can drag and drop text. 

Is the problem with the OO 2.04 build?

---

### Post by cogitordi on 2006-12-11
> **cogitordi said:**
> I have OpenOffice 2.04 in Edgy-64 on an AMD64 PC. In OO Write, I have no drag-and-drop editing capability.

On my Dapper-32 PC, I have OO 2.02 and I can drag and drop text. 

Is the problem with the OO 2.04 build?

I still don't have an answer about OO 2.04 in Edgy-64. However, I've installed 32-bit compatibility and have also installed OpenOffice 1.1.5. Drag-and-drop editing works in OO 115 in Edgy-64.

---

### Post by jkwarras on 2006-12-11
Same here, can't drag and drop on my OOWriter amd64 Ubuntu.

---

### Post by John Jason Jordan on 2007-01-25
> **jkwarras said:**
> Same here, can't drag and drop on my OOWriter amd64 Ubuntu.
I just upgraded my Dapper amd64 with OOo 2.02 to Edgy amd64 with OOo 2.04. Drag and drop editing is now broken.

This thread started back in December. I'm hoping those who said they had the problem have a solution and that they will share it with me.

Thanks!

---

### Post by cogitordi on 2007-02-04
It's still broken,as described.

---

### Post by John Jason Jordan on 2007-02-04
> **cogitordi said:**
> It's still broken,as described.
It's weird. As far as I can tell, you, jkwarras, and I are the only three on the whole planet who have been bitten by this bug. I asked on the OpenOffice.org e-list, where I got lots of responses and suggestions, but no one else has the problem.

I also can't get the default tab settings to stick in Tools > Options > Writer > General. Might be a related issue.

Otherwise it works perfectly. No crashes, no other problems. I did a reinstall but it didn't change anything. I have a paper due tomorrow, but as soon as I finish it I'm going to do an uninstall first and then a regular install.

---

### Post by cogitordi on 2007-02-04
It's improbable that we're the only ones affected. However, we may be some of the few people who use OO on AMD64 and make regular use of drag-and-drop editing.

I doubt that a re-install will fix the problem. But let us know how it goes.

---

### Post by John Jason Jordan on 2007-02-14
I just filed a bug report here:

[https://launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/85248](https://launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/85248)

---

### Post by gajorro on 2007-04-01
i have the same with ooo2.0.4 64 bit. but i think that is not trouble with edgy. i've forced dpkg to install 32 bit polish [www.ux.pl](www.ux.pl) version of ooo and d&d worked fine...

---

### Post by cogitordi on 2007-04-13
See the first post. The problem does not seem to be present in the 32-bit builds.

---

### Post by bjchip on 2007-04-13
I am a newcomer to the forum but not to this sort of problem.   

My suggestion  - Check for similarities here... 


What chipset and motherboard combination are you all using?   


respectfully 
BJ

---

### Post by John Jason Jordan on 2007-04-13
> **bjchip said:**
> I am a newcomer to the forum but not to this sort of problem. My suggestion  - Check for similarities here... What chipset and motherboard combination are you all using? 
Of course, if we had the resources we could find the common element. The problem is that there are millions and millions of combinations of hardware, OSs, and installed applications, and any one of them could be the problem. I spent more time on this bug than I think anyone else and I can assure you that there are maybe a hundred people who have been bitten by it. That number is my guess based on the fact that I found about ten people who have reported it. I can also say that it occurs ONLY with Edgy amd64. It does not occur with 32-bit Edgy, nor does it occur with any other version of Ubuntu, nor does it occur with any other distro, regardless of version or architecture.

More important, I can assure everyone that it does not occur in Ubuntu Feisty amd64. Whatever the problem is, has been fixed. Except that it probably wasn't "fixed," it just went away because one of the thousands of changes to Feisty inadvertently fixed it.

The final of Ubuntu Edgy amd64 will be released in a matter of days. It was originally scheduled for April 19, but the release of the Beta was delayed about three days from its scheduled release, so I wouldn't hold my breath about Ubuntu meeting the April 19 date. Still, its release is imminent. Since it resolves the problem, I have stopped worrying about drag and drop editing of text in OpenOffice.org. I'll just upgrade to Feisty as soon as it comes out and that will be the end of the problem.

---

### Post by cogitordi on 2007-04-19
> **bjchip said:**
> I am a newcomer to the forum but not to this sort of problem.   
My suggestion  - Check for similarities here... 
What chipset and motherboard combination are you all using?   


BJ, this is a problem with drag-and-drop text editing. OpenOffice uses UNO and some Java, both highly abstracted from the hardware. It almost certainly has nothing to do with the chipset and motherboard, any more than it is likely to be caused by the mouse (PS/2 or USB).

---

### Post by John Jason Jordan on 2007-04-19
> **cogitordi said:**
> BJ, this is a problem with drag-and-drop text editing. OpenOffice uses UNO and some Java, both highly abstracted from the hardware. It almost certainly has nothing to do with the chipset and motherboard, any more than it is likely to be caused by the mouse (PS/2 or USB).
Cogitordi, have you upgraded to Feisty yet? I have a big exam on Monday and I need my computer intact, so I don't dare do the upgrade until Monday night. I am curious if Feisty amd64 fixes the problem for you.

---

### Post by cogitordi on 2007-04-20
I am about to install the Fawn. It will be a clean install, not an upgrade. I'll let you know. 

Off-topic: which is your exam?

---

### Post by jkwarras on 2007-04-22
In feisty drag and drop works :)

---

### Post by John Jason Jordan on 2007-04-26
> **jkwarras said:**
> In feisty drag and drop works :)
Yep, I ust finished upgrading to Feisty, and I'm happy to say that everything that was broken in OOo 2.0.4 in Edgy amd64 is now fixed. 

However, just in case this happens to someone else, there are definite problems with the upgrade. Evidently there is a bug somewhere in Synaptic or apt or some part of the package management system. The upgrade itself hung the computer and it took me almost all day to repair the damage -- had to boot a live CD, mount and chroot to the old partition and then use dpkg and apt-get over and over to finish the upgrade.

And once I finally had it fixed, the new OOo did not fix everything that was wrong with OOo 2.0.4 in Edgy:

No drag and drop editing of text
Some of the wizards (e.g., web page) would crash OOo
Half of the settings in Tools > Options would not stick

The new version on Feisty did fix the first two, but some of the settings in Options > Tools still refused to stick. So I decided to uninstall and reinstall the whole OOo 2.2 suite. The uninstall went fine, and I also renamed ~/.operoffice.org2, but after reinstalling I discovered that the remaining problems in Tools > Options were still there. Moreover, I noted that it used the same window size and the toolbar was floating off to the right where I normally have it. In other words, OOo was saving user data in places other than ~/.openoffice.org2. So I uninstalled again and then did "locate openoffice" from the command line, and then nuked every single file that had anything to do with OOo. 

Then I reinstalled from Synaptic. However, this time the Synaptic bug hit me again and the install hung the computer in the middle. After rebooting I found a godawful mess in Synaptic. I tried to resume the install, but it ended with a list of error messages, all pointing to a missing dependency on openoffice.org-hyphenation. The hyphenation module was installed, but it wouldn't uninstall or reinstall. I tried --purge and everything I could think of, but it was seriously stuck. 

Eventually I found the answer on a Debian list. Evidently this is a recent problem. The solution is to reinstall dictionaries-common. I don't know why it worked, but it did. I now have Feisty with OOo 2.2 and everything finally works properly.

---

### Post by cogitordi on 2007-04-27
> **John Jason Jordan said:**
> I'm happy to say that everything that was broken in OOo 2.0.4 in Edgy amd64 is now fixed. 

THAT is a bold statement, Sir. :^) At the same time, it's nice to have D&D editing back in OO. I was tiring of doing my editing in Gedit. 

> However, just in case this happens to someone else, there are definite problems with the upgrade. 

Doing an "upgrade" is a complicated process because not all eventualities can be accomodated, even if they can be predicted. In all the OSs that I've tortured, I've never seen an upgrade work consistently -- if it worked at all. Good data management and a fresh install will save your time in most cases.

---

### Post by John Jason Jordan on 2007-04-27
> **cogitordi said:**
> THAT is a bold statement, Sir. :^) At the same time, it's nice to have D&D editing back in OO. I was tiring of doing my editing in Gedit. 
Evidently the comment was a bit too bold. There is a problem with the video drivers. I hve to keep at least two OOo items running or I will be unable to restore a minimized instance from the panel. I am using the nv drivers, because the nvidia-glx drivers are broken at the moment. The problem is solved if you use the new nvidia-glx-new driver, but that driver won't work with the GeForce4 420 Go 64M in this laptop. I note that OOo was always a bit clunky with the video -- leaving floating toolbars on the desktop after the main window was minimized for example. But at least I can just keep at least two instances running until the bug gets fixed. There's something funky going on with OOo and the video because I don't have the problem with any other applicaion. When I have time later today I will research bug reports and see if it has already been reported.

I also learned from someone on the OOo e-list that there is a bug with the Document Converter wizard with Feisty amd64, which I was able to rerproduce. Luckily I have no use for the wizard so it doesn't affect me. The wizard is just a macro, so users might be able to fix it themselves.

---

