---
title: "vmware-player won't update!"
date: 2007-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Butthead on 2007-10-18
Hi,

Hope I'm posting this to the right place!  I have a AMD 4600+ F2 system that I am curently running Dapper 6.06 LTS on.  Yesterday, the Adept package manager claimed there was one update available via the repositories (a vmware-player upgrade), but when I went to try installing it under Adept, it locks up on me at 16%.  The "show details" tab (when pressed) shows a blue text box with an "OK" box on it that I assume needs to be pressed for the upgrade to continue, but it doesn't seem to work when I attempt pressing it in Adept package manager.  Can anyone on the forum here tell me how to go about correcting it (maybe performing the upgrade using the command line somehow?), so I can finally get rid of the stupid "upgrade available" icon on the bottom window bar?  Thanks!

BTW, I think I managed to finally (permanently? :shock: ) turn off the "upgrades available" icon in the window bar.  Is there any way I can bring it back up again after (hopefully?) finally fixing the vmware-player update problem I'm having?  Thanks 2X! :guitar:

---

### Post by yellowbread on 2007-10-19
If I remember correctly, you select options with the tab and arrow keys, enter key  when your choice is selected. Hope this does it for you.

---

### Post by Butthead on 2007-10-19
Hi,

Thanks for the assistance!  I THINK??? I managed to fix it using the "apt-get dist-upgrade" command in terminal (even though I got an error message telling me the upgrade was unsuccessful, Adept package manager claims it did in fact upgrade). :confused:

Now I got to wait and see if the upgrade icon shows up again in the bottom toolbar the next time upgrades are released.  I sure hope vmware-player doesn't cause Adept to lock up on me again. :( :mad: ](*,)

---

