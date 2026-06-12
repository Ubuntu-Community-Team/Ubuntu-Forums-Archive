---
title: "How to install NewAtlanta BlueDragon Server"
date: 2005-12-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by linoox on 2005-12-30
I'm getting the following error when i tried executing the BlueDragon_Server_62-Linux.sh (this noobie doesn't know what .sh extension stands for).

"line 2180: /tmp/install.dir.7241/Linux/resource/jre/bin/java: cannot execute binary file"

What does it all mean? I tried chmod +x to the /tmp directory. That doesn't work too.

Followed instructions from here - [http://www.we3geeks.org/?p=4](http://www.we3geeks.org/?p=4)

---

### Post by linoox on 2006-01-02
Anyone seen this error? have a fix? Thx:KS

---

### Post by ethan@xmlstandards.org on 2007-03-25
Hi there,

I would suggest that first you download another instance of the installer just to be sure that you have not received a corrupted download (unlikely) and then further suggest that you try out the 7.x instead of the 6.x for BlueDragon (this shouldn't affect the installation but will give you more features inline with the current offering from Adobe).

Navigate to where you downloaded the installer and change the permissions as such:

chmod 744 BlueDragron_Installer.sh

This will allow you to execute the installer for BlueDragon (can't think why before you had to change permissions for the /tmp directory).

Once you have changed permissions, then execute the installer:

./BlueDragon_Installer.sh

The *.sh extension is simply an agreed upon file extension for a shell script. You could just as easily strip off the extension and it should still work the same. Think of it along the lines of how Windows will respond when you execute a *.exe file (same convention).

The installation should be installed to:

/usr/local/NewAtlanta

by default, I would go with the default location although /opt seems like a more fitting location (personal preference).

Once you have installed you'll then need to navigate (via terminal) to:

/usr/local/NewAtlanta/{BlueDragon_Version)/bin


and execute:

./StartBlueDragon.sh

to stop:

./StopBlueDragon.sh

Make sure you check the correct paths, since I am writing from memory?

If all is well at this point, you can then browse to:

[http://localhost:8080/bluedragon](http://localhost:8080/bluedragon)

Update your port number if you chose different from the default (8080), and enter your password (entered during setup).

Also note that the installation is a graphical one, the installer spawns a GUI to perform the installation (at least it did for me) guess it reads the environment (must be command line based without X present?).

Let me know how you get on?

---

