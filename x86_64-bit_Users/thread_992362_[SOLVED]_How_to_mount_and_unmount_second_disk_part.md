---
title: "[SOLVED] How to mount and unmount second disk partition"
date: 2008-11-24
forum: x86 64-bit Users
---

### Post by Oldcowboy on 2008-11-24
I recently emigrated from years of openSUSE to UBUNTU and am attempting to do tasks the UBUNTU way.

Formerly, I had a Backup program which I called (as root) from a shell script which mounted the backup drive as rw, did the daily backup from CRON, and then remounted the drive as read only (to prevent any accidental deletions.)

Now, in UBUNTU I am not familiar enough to successfully mount the second HD partition from the terminal, before I put the commands in a shell script. Do I need to manually edit fstab to put the second drive there first or?

I have two physical HD's, and it only makes sense to keep the Simple Backup files on another HD, for if a drive fails and the backups are on the same drive, all is lost.

For the moment, I am mounting the second HD manually from Nautilus each day which chances the human element of forgetting.

Thanks for any good suggestions to point me in the right direction.

---

### Post by cdtech on 2008-11-24
> **Oldcowboy said:**
> before I put the commands in a shell script. Do I need to manually edit fstab to put the second drive there first or?

I have two physical HD's, and it only makes sense to keep the Simple Backup files on another HD, for if a drive fails and the backups are on the same drive, all is lost.

For the moment, I am mounting the second HD manually from Nautilus each day which chances the human element of forgetting.

Thanks for any good suggestions to point me in the right direction.

I do the same thing with my /backup partition. Mounted externaly via scritp. You need an entry within your /etc/fstab file:
```
/dev/sda1 /backup ext2 defaults 0 0
```
This will mount it on boot and then using the scripts below you use the mount/unmount command:
```
	# mount partition to read-write	   

	   echo -n "Remounting backup partition read-write ... "
	if ( mount ${backuppart} -o remount,rw &> /dev/null ) then
	   echo "done."
	   else
	   echo "Failed to remount ${backuppart} in read-write mode!"
	   echo "Aborting Incremental System Backup."
	   exit 1
	fi
```
And:
```
 	
           echo -n "Remounting partition as read-only ... "
        if ( mount ${backuppart} -o remount,ro &> /dev/null ) then
	   echo "done."
	   else
	   echo "Failed to remount ${backuppart} in read-only mode!"
	   echo "Aborting Incremental Backup."
	   exit 1
	fi # end if statement
```

Hope this helps ya....

---

### Post by Oldcowboy on 2008-11-30
I am embarrased to report that I am still failing to be able to mount my backup drive from the command line.

Now, I have put the backup drive into fstab:
# /dev/sdb2
/mnt/sdb2 /backup  ext3 defaults 0 0

But, when I attempt to do:
sudo mount /mnt/sdb2 /backup

It returns: mount: mount point /backup does not exist

If I am missing something, I would appreciate some more guidance. Thank you.

---

### Post by drs305 on 2008-11-30
> **Oldcowboy said:**
> I am embarrased to report that I am still failing to be able to mount my backup drive from the command line.

Now, I have put the backup drive into fstab:
# /dev/sdb2
**/mnt/sdb2 /backup**  ext3 defaults 0 0

But, when I attempt to do:
sudo mount /mnt/sdb2 **/backup**

It returns: mount: mount point /backup does not exist

If I am missing something, I would appreciate some more guidance. Thank you.


You identify the device as " /dev/sdb2 " , not as /mnt/sdb2, so your fstab entry should read:
```

/dev/sdb2 /backup ext2 0 0

```

In either command, the mountpoint **/backup** has to exist. Create it with the following command; the second will make you the owner, the third will give only you access (which you can change by changing 700 to some other value, such as 750):
```

sudo mkdir /backup
sudo chown -R *yourusername:* /backup
chmod -R 700 /backup

```

To manually mount the device, you can use either the first command (if you have added it to fstab), or the second:
```

sudo mount -a 
*OR:*
sudo mount /dev/sdb2 /backup

```

Note: By convention, removable/external drives are usually mounted on either /mnt or /media (e.g. /media/backup) but the way your are doing it will work fine.

---

### Post by Oldcowboy on 2008-12-06
Thank you for your help. :D

---

