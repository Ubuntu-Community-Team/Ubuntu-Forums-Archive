---
title: "Problems with package installer."
date: 2007-05-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by burritomaster on 2007-05-20
I was installing a .deb and it didnt seem to be making any progresst, so I canceled on the window that said the package was installing. Then it brought me back to the package main window that said all the details and gives you the options to install it. I couldn't close the window so i used force quit. Now when I try to re-install it it gives me an error.

[B]A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'[/B]

Do I need to re-install the OS, or can  you save me?

Update: When I try to install any other .deb pacakge it gives me

**The package might be corrupted or you are not allowed to open the file. Please check permissions.**

Already checked permissions, everything seems OK.

---

### Post by John Jason Jordan on 2007-05-21
> **burritomaster said:**
> I was installing a .deb and it didnt seem to be making any progresst, so I canceled on the window that said the package was installing. Then it brought me back to the package main window that said all the details and gives you the options to install it. I couldn't close the window so i used force quit. Now when I try to re-install it it gives me an error.

[B]A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'[/B]

Do I need to re-install the OS, or can  you save me?

Update: When I try to install any other .deb pacakge it gives me

**The package might be corrupted or you are not allowed to open the file. Please check permissions.**

Already checked permissions, everything seems OK.
I'm sure you don't need to reinstall the OS. These problems sometimes take a bit of figuring out, but I've had problems like this when installing packages and I've always been able to resolve the problem.

The first step I would take is to launch Synaptic. It will probably say there is a broken package. Use Synaptic to see if it lists the package and if it will reinstall or uninstall or otherwise fix the problem. 

If that doesn't help, holler back.

---

### Post by WhiteSlash on 2007-11-24
Synaptic doesn't work, it returns "the package mercury-messenger needs to be reinstalled" and then it closes again.

---

### Post by WhiteSlash on 2007-11-25
I finally fixed it!
I used this command
sudo dpkg --force all -r mercury-messenger
sudo dpkg --force all -r <theconflictingpackage goes here>
Thanks anyway :D

---

