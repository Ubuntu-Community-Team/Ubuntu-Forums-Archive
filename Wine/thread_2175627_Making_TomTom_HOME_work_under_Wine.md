---
title: "Making TomTom HOME work under Wine?"
date: 2013-09-20
forum: Wine
---

### Post by Lammis on 2013-09-20
Hi,
I am using Ubuntu 13.04 [64 bit] and Wine 1.4.1. 
I have a car navigation system called TomTom GO 750 that use a desktop application called TomTom HOME for map updates. I am able to install the software under Wine but it does not launch at all. I get the following error message: "TomTomHOMERuntime.exe failed with error 127: Procedure not found".

TomTom support department does not provide any help.

Does anyone know if it is at all possible to get this application up and running? Is it realistic to assume that any other software shell like e.g. VMware would work better?

---

### Post by SamTarling on 2013-09-20
Wine, although a good tool, can't run everything I'm afraid.

That being said, a quick search on [appDB]("http://appdb.winehq.org") shows that some versions of TomTom HOME **do** run under Wine. Have a quick look [here]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=3628") and see if your version is supported.

If not, using a VM running Windows would be your best bet.

Good luck! :)

---

### Post by ian-weisser on 2013-09-20
TomTom Home works quite well in a VM.
Never could get it to work with Wine. TomTom's fault, not Wine's fault.

---

### Post by johnd.jasper on 2013-11-20
Wine doesn't support access to the USB device so even though your TomTom will show connected within Ubuntu, Wine won't provide access to it, hence TomTom Home will not be of any use even if it loaded up. I haven't tried the VM route yet but probably will before long.

---

