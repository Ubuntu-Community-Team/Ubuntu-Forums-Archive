---
title: "How do I get an app running in Wine to connect to Win2000 server"
date: 2008-10-05
forum: Wine
---

### Post by nuke on 2008-10-05
Hi!

I've been searching the forums here and at WineHQ.  So far no luck.  But maybe I don't know the proper terms to search for???

Wine version:
I am running the version of wine that is installed using Synaptic in version 8.04.1.

What I'm trying to do:
I am trying to install a program (Canadian Automated Export Declaration - CAED) that is an MS Access runtime.  The database for this program is on a server running MS 2000 Server Edition.

In Ubuntu, the server folder share where the CAED database is saved is available.  The mounted share can be seen in Nautilus.  It is shown as 192.168.1.1/CAED.  The server is being accessed using smb (I think) using the "Connect to Server" command in Places menu.

Help Request:
Is there a trick to get WINE to find the mounted network shares of Ubuntu?  I can only get c:\ to show up.  How do I get the network share to show up as a drive in Wine?

Thanks in advance for your help and suggestions.

---

### Post by nuke on 2008-10-07
Hi!

Is there anyone who can guide me to how to mount win2000 server shares in WINE?  I am still trying but having no luck.

Thanks in advance.

---

### Post by izar on 2008-11-26
did you try oppening the folder, right cliking the installer and telling it to run through wine?
you might also want to use wintricks - see wineHQ

---

### Post by hikaricore on 2008-11-26
Open up winecfg and add the drive there under the Drives tab.
It's really quite painless.

---

### Post by nuke on 2008-11-27
Thank you.  I'll give that a try and report back if it works.

---

### Post by nuke on 2008-12-01
I have tried to set up a network share using winecfg.  But I can't find the mount point to put in winecfg.

I have a network samba connection to the server.

I'm using Hardy 8.04.1

I have tried to put in <\\server\share> and </server/share/> in the path.  I would have figured that the samba share has a mount point somewhere but I can't find it.

/mnt is empty
/media has only cdrom, cdrom0, floppy, floppy0

On the desktop I have "share on server" listed.  

Could you suggest where that network connection is mounted?

Thank you.

---

### Post by izar on 2008-12-03
look in home/.gvfs

---

