---
title: "wine not functioning"
date: 2011-07-19
forum: Wine
---

### Post by madhavhmk on 2011-07-19
I tried installing wine for the upteenth time but is getting nowhere....

I included the software sources ppa wine(bla bla bla) and tried installing both wine 1.2 and wine 1.3  to no avail.

when I try winecfg in terminal, I get the following error:

winecfg
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
err:ole:apartment_createwindowifneeded CreateWindow failed with error 126

--------------

I am desperately trying to switch over completely (sort of :) to ubuntu and that long avaited transition can happen only if I can run some windows programs through linux :P

someone pls help..!!!

---

### Post by Surendil on 2011-07-19
try crossover!!!
for me it worked much much better than wine

---

### Post by ajgreeny on 2011-07-19
According to your user CP you are still on 8.04.
> Join Date: Feb 2009
 				 				 	  					Beans: 57 				
 			       Ubuntu 8.04 Hardy Heron  				 				 				 				 				Is that so?  If so, I suggest you update to the latest LTS version 10.04, as 8.04 is no longer supported, which may account for wine not working any more.

---

### Post by madhavhmk on 2011-07-20
Oops..!!! I hadnt updated the user cp......... I have 10.04 installed...,and also, I have included the software source ppa which is supposed to contain the correct version of wine.

---

### Post by Elfy on 2011-07-20
Please do not post duplicates.

---

### Post by cwwilson721 on 2011-07-20
> **madhavhmk said:**
> I tried installing wine for the upteenth time but is getting nowhere....

I included the software sources ppa wine(bla bla bla) and tried installing both wine 1.2 and wine 1.3  to no avail.

when I try winecfg in terminal, I get the following error:

winecfg
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
err:ole:apartment_createwindowifneeded CreateWindow failed with error 126

--------------

I am desperately trying to switch over completely (sort of :) to ubuntu and that long avaited transition can happen only if I can run some windows programs through linux :P

someone pls help..!!!
Either:
[LIST]
[*]You have a borked up X11 install
[*]or you have a borked up video driver install.
[/LIST]

Install your drivers (if there are any), and try again.

---

### Post by madhavhmk on 2011-07-20
I think  I had messed up with wine installation some time back, by quiting the installation midway or something.

It seems there is a conflict between the improper installation.

even after I give the following command,
sudo apt-get remove wine 1.3,
i get an output of current version wine 1.1.14 when I type wine --version in the command prompt.

how I can ensure that wine is completely uninstalled?

---

### Post by gandaran on 2011-07-20
> **madhavhmk said:**
> I think  I had messed up with wine installation some time back, by quiting the installation midway or something.

It seems there is a conflict between the improper installation.

even after I give the following command,
sudo apt-get remove wine 1.3,
i get an output of current version wine 1.1.14 when I type wine --version in the command prompt.

how I can ensure that wine is completely uninstalled?
use synaptic package manager.

---

### Post by ajgreeny on 2011-07-21
> **gandaran said:**
> use synaptic package manager.
And check for any hidden .wine folder in your home which may be corrupt, and remove it completely.

---

### Post by drs305 on 2011-07-21
Moved to Wine forum.

---

