---
title: "Changing folder permissions"
date: 2006-05-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by ravpaul on 2006-05-29
I have created a directory that only allows root to add or modify it. however this becomes annoying when trying to export music to it from gtkpod as permission is always denied. 

If anyone could tell me how to change permissions so that either only my user can modify it or anyone can it would be very helpful. Thanks.

---

### Post by frenchdm on 2006-05-29
gksudo nautilus

will open up the file manager (i.e. nautilus) as root.  You should be able to change the permissions from there.

---

### Post by olsonar on 2006-05-29
first, open a terminal and type

```
sudo nautilus
``` 
then, in the file browser that just opened, navigate to the folder. right-click, and choose properties, then the permissions tab. to make it so only you can access it, set 'file owner' to your username, then check all boxes in the 'owner' row, and uncheck the ones in the 'group' and 'others' rows. to make it accessible to everyone, check all nine boxes.

EDIT: using gksudo nautilus as frechdm suggests does the same thing, but also works from the 'run application' dialog (alt + F2)

---

### Post by ravpaul on 2006-05-29
Cheers guys. I've also discovered that creating a directory using the GUI gives me access as does making it from the terminal. It is only restricted to root if I use the sudo mkdir command. Incidently how do you guys get the box to appear when you are typing in a command on the forum?

---

### Post by olsonar on 2006-05-29
it's the little # icon. click it and put the contents of the box between the CODE tags that appear. for quotes, use the speech bubble.

---

### Post by thomasmilo on 2006-06-07
I followed the directions you have below and successfully changed one folder's ownership, but when I tried it on the mount point I had created for a USB drive, I tried the same routine and got the error message:

"The owner could not be changed.
Sorry, couldn't change the owner of 'usb'."

The usb drive on that mount point contains files for which I also would like to change ownership and or permissions.

Thank you for any advice.


From earlier post:

Code:  
sudo nautilus

then, in the file browser that just opened, navigate to the folder. right-click, and choose properties, then the permissions tab. to make it so only you can access it, set 'file owner' to your username, then check all boxes in the 'owner' row, and uncheck the ones in the 'group' and 'others' rows. to make it accessible to everyone, check all nine boxes.

---

### Post by gary4gar on 2006-06-09
hey guys pls help when i change file pernission on NTFS partion it displays it as read only.what to do

---

### Post by Torquemada28 on 2006-06-21
[QUOTE=gary4gar]hey guys pls help when i change file pernission on NTFS partion it displays it as read only.what to do[/QUOTE]

Ubuntu only has read-only access to NTFS partitions, regardless of ownership.

---

### Post by 2hot2touch on 2007-07-10
no worries gary4gar.....install ntfs-3g....u can find it in the list of available applications. Using it will give full read and write access to all ntfs partitions...:)

---

### Post by mskristinahall on 2007-12-31
Hello.

Firstly I am a brand new initiate to linux so I am completely clueless on how to do things.

I installed LAMPP last night, as my main reason for using linux is to create a testing server for websites. Plus I have discovered that Ubuntu is very pretty and I am falling in love with it.

Anyway, LAMPP works no problem. So I download drupal 5.5 which is a popular CMS right now. I try to extract the tar.gaz in /opt/xampp/htdocs but I get various permission denied messages. Ownership was set to nobody. I resolved that via the information at the beginning of this thread.

However now I was able to extract it and all is good on that front. When I check locahost/drupal and drupal is in the htdocs/drupal folder I get 

<cod>
The Drupal installer requires write permissions to ./sites/default/settings.php during the installation process.
</code>

I tried changing the permissions of the drupal folder to make sure. They seemed setup properly.

Any thoughts or guesses on this. I am learning towards a file permissions issue just not sure how to fix it.

---

### Post by Yellow Pasque on 2007-12-31
To see the permissions of files/folders, use:
```
ls -la
```

To change permissions of a file/folder:
```
sudo chmod 777 *filename*
```

777 gives read/write/execute access to all

---

