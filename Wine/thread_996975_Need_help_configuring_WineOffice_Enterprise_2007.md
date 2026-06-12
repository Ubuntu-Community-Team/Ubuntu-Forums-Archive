---
title: "Need help configuring Wine/Office Enterprise 2007"
date: 2008-11-29
forum: Wine
---

### Post by zoner on 2008-11-29
I need some help figuring out how to set up wine to use Office Enterprise 2007.

I started out by following this guide: [http://samanathon.com/how-to-install-microsoft-office-2007-in-ubuntu-804/](http://samanathon.com/how-to-install-microsoft-office-2007-in-ubuntu-804/).

I went to the point of the install guide:

# Navigate to following folder: ~/.wine/drive_c/windows/system32/
You can do this via your Home folder (once at your Home folder, hit CTRL+H to display hidden files).
# We need to make a backup of a .dll file; rename rpcrt4.dll to rpcrt4.bak
# Download a new version of rpcrt4.dll and place it in the Wine system32 folder (from step 5)
# Open up the Wine Configuration tool again (ALT+F2, winecfg) and click the Libraries tab. In the New override for library field, enter in rpcrt4.dll and hit the Add button.

Well, here is where I screwed things up.  I deleted the rpcrt4.dll file and cannot figure out how to download and put it back in the system32 folder.

Now I am frustrated and was wondering what I should do.  Do I need to re-install wine?  If so, how do I do this?  Is there an easier way to install Enterprise Office 2007?  Thanks for any help.

---

