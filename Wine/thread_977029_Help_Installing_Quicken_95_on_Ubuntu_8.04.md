---
title: "Help Installing Quicken 95 on Ubuntu 8.04"
date: 2008-11-09
forum: Wine
---

### Post by andreab35 on 2008-11-09
Hey guys! I'm totally new with the Linux OS, so feel free to call me a total noob! :)

On my father's computer, it is running Ubuntu 8.04. He loves the Quicken 95 Financial Suite and does not want another software. 
So, I downloaded Wine and installed it. I booted the setup.exe off the Quicken installation CD. Got through that part fine until it tells me the Setup Directory and the Program Group.

I have not gotten past this point and I have worked hours trying to install this thing. I don't know where to setup the software's directory, and nor do I know which program group to choose. 

Whenever I hit the ok button, it says: **You have too many programs groups. To continue, you need either to use an existing group or delete a group.**

I have Windows XP on this computer also... however currently the BootMgr is not working since I downgraded him from Vista since he hated it. I cannot boot into XP. So, I am stuck with Linux.

He'll stick with Linux as long as he can get his Quicken on there.

I appreciate all the help I can get. I'm desperate at this point!
Thanks again! :biggrin:

---

### Post by cogadh on 2008-11-09
I don't wish to discourage the use of Linux, but in order to fix the machine so that XP will boot, just put in the XP installation CD, boot the computer and select "Recovery Console". when you get to the Recovery Console command prompt, just type "fixmbr" and it will restore Windows default boot record, thus allowing XP to boot again. That will leave Linux off-limits, but you can get that back by re-installing Ubuntu.

As for getting Quicken 95 to work with Wine, the first thing you should probably do is set the Windows version in Wine at least as low as Win 98. You may need to set it to Win 95 or even lower. IIRC, that version of Quicken was actually made for Windows 3.1, so it will not be easy to make it work.

---

