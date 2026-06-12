---
title: "Sharing Wine with multiple users"
date: 2008-01-18
forum: Wine
---

### Post by dpharvey on 2008-01-18
I've looked through multiple posts which lead me to make a soft link for sharing Wine with other users.  I tried the ln command with the path from my wine directory to the other user account, but keep getting the error message "hard link not allowed for directory"  
    "ln ~/.wine /home/username"

Am I doing something wrong?   Or, is there a better method for allowing other users access to the Wine c: folder?

---

### Post by Onesimus on 2008-03-01
This would be really useful if it was solved.  I have Windows game(s) that take up ~1Gb of disk space.  I don't particularly want to install it for each user (5) - that would be a serious waste of hard disk.

---

### Post by Roryking on 2008-03-01
Well... permissions are going to be an issue. This is **[COLOR="Red"][SIZE="4"]really irresponsible[/SIZE][/COLOR]** but go to the home directory that has your stuff for wine and run:

```
chmod 777 -R .wine/
```

This will give everyone read, write, and execute permissions for everything in the .wine folder.
(I am assuming you are logged in as the user that has the wine directory we need to link to). 

then go to the directory for the other users that need access to the wine directory. You will probably need sudo for this:

```
sudo rm -rf .wine
sudo ln -s /home/[username]/.wine
```

The first line will remove the other users wine preferences, registry, etc. So use caution! The second line will create a link to the wine folder you wanted to use. This is why permissions need to be modified, because ordinarily Ubuntu doesn't like other people poking around in users home folders. Alternatively, there might be some setting to allow you to change your drive_c folder, in which case I'd just move it to someplace like /var/tmp where everybody can get to it.

---

### Post by MemoryDump on 2008-04-28
does wine's core libs/apps/etc "have" to be in the users home folder? Could we not just sym link all the users ".wine" directory to a  shared system folder?

ex:
shared wine would be installed in: /opt/wine
users wine config: "/home/<username>/.wine" would be a sym link to /opt/wine

would that work? I suppose the permissions on the /opt/wine folder could be set to a specific group. (like wineuser)

-MD

---

