---
title: "OpenOffice on 64bit Dapper - Network access"
date: 2006-07-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Raedwald on 2006-07-16
I have a small home network, so that all the family can access reources such as printers, certain data files & so forth from a central data server (which is a WinXP box to keep things simple for wife and children!).

I have two main systems that I use - a laptop (64bit Dapper build) and a desktop (32bit Dapper build).

On both systems there is a permanent connection to the data server shares (SMB). Both systems are configured the same way. I can access the server shares, copy files across, etc. and the server shares are listed (and accessible) within the Network browser.

However, within OpenOffice, on the 64bit build, there is no option to load or save a document across the network, and attempts to open a document directly fromn the file share start OpenOffice, but the app then closes without opening the document.

It works perfectly under the 32bit build for both saving and opening from the server ](*,)

Is this an issue with OpenOffice under 64bit, or have I missed something stunningly obvious?

---

### Post by Kilz on 2006-07-16
> **Raedwald said:**
> I have a small home network, so that all the family can access reources such as printers, certain data files & so forth from a central data server (which is a WinXP box to keep things simple for wife and children!).

I have two main systems that I use - a laptop (64bit Dapper build) and a desktop (32bit Dapper build).

On both systems there is a permanent connection to the data server shares (SMB). Both systems are configured the same way. I can access the server shares, copy files across, etc. and the server shares are listed (and accessible) within the Network browser.

However, within OpenOffice, on the 64bit build, there is no option to load or save a document across the network, and attempts to open a document directly fromn the file share start OpenOffice, but the app then closes without opening the document.

It works perfectly under the 32bit build for both saving and opening from the server ](*,)

Is this an issue with OpenOffice under 64bit, or have I missed something stunningly obvious?

Have you tried mounting the shares with smbfs?

---

### Post by Raedwald on 2006-07-17
That's how they're mounted, yes.

As I said, works perfectly under 32bit............

---

### Post by Kilz on 2006-07-17
> **Raedwald said:**
> That's how they're mounted, yes.

As I said, works perfectly under 32bit............

I have a few questions. First are you mounting these shares manually, or are they in fstab? Second, why are you trying to save/open the files in the network browser? 
If they are mounted you should be able to open them at the mount point and save them there. The changes will happen on the server. I have one windowsXP home box for the wife(god I'm tired of cleaning out the spyware)on the network with a similar share, its mounted in /mnt/smbfs/files. Here is the fstab entry
```
//192.168.0.108/files    /mnt/smbfs/files      smbfs    username=Guest,password=,fmask=777 0 0
``` 
Maybe by posting this it will help figure out whats going on. I get an error every once in a blue moon when saving a file there. But I just save it again.

---

### Post by Raedwald on 2006-07-19
Shares were created using the "Connect to Server" option from the Places menu (working on the "if there's an easy way to do it....."). Were created exactly the same way on 32bit as on 64bit.

Ideally, what I want to be able to do on the 64bit box is to access/open/update the file share copy of a file from within OOo(exactly like I can on the 32bit box). But that option isn't there!

---

### Post by Kilz on 2006-07-19
> **Raedwald said:**
> Shares were created using the "Connect to Server" option from the Places menu (working on the "if there's an easy way to do it....."). Were created exactly the same way on 32bit as on 64bit.

Ideally, what I want to be able to do on the 64bit box is to access/open/update the file share copy of a file from within OOo(exactly like I can on the 32bit box). But that option isn't there!

Then mount the shares in fstab, it will mount them automaticly. It will look like the files are on your computer. You will be able to edit, create, and save all kinds of files. It will look like you are only doing it localy but the changes will happen on the server. You will have to install the smbfs package to do it. Its not part of a normal samba install. You will have to create the folders they mount to on the 64bit box. Then use the line above as a guide when editing fstab.

---

### Post by Raedwald on 2006-07-23
That works and the shares can be accessed.

Still doesn't explain though why they access fine under 32bit without all that being necessary.

Oh the joys of 64bit...... ](*,)

---

### Post by Kilz on 2006-07-23
> **Raedwald said:**
> That works and the shares can be accessed.

Still doesn't explain though why they access fine under 32bit without all that being necessary.

Oh the joys of 64bit...... ](*,)

Im told that in Edgy that Open Office on the amd64 version will be  64bit unlike the current 32bit. Maybe that will make a difference.

---

