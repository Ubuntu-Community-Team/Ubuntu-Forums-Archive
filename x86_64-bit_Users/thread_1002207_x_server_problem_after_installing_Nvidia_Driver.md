---
title: "x server problem after installing Nvidia Driver"
date: 2008-12-04
forum: x86 64-bit Users
---

### Post by skoleon on 2008-12-04
Hi I was installing nvidia driver for my GF6 card and I had to stop the x server to install it and after I finished the install the GUI did not start up.

This is what I did:

[I]/etc/init.d/gdm stop 
ctrl alt f1[/I]

Intall the driver.
The only thing that happend in the installation was:
"Unable to performe the runtime configuration check for library libGL.so.1

[I]/etc/init.d/gdm start
ctrl alt f7[/I] <= Still a CLI

*/etc/init.d/gdm restart* <= Still a CLI

Now I went to google.

after a little while of no detailed help I wrote:

*startx*

Following info came up (hope I wrote the right info):

[I]Primary device is not PCI
(EE) No Devices detected.

Fatal server error:
no screens found
giving up.
xinit: Connection refused (erno 111): unable to commect to X server
Xinit: No Such process (errno 3): Server error[/I]

I found in my google search this command:

*sudo dpkg-reconfigure xserver-xorg*

but I didn't find any real tutorial to finish the reconfigure.


I haven't many years in Linux just the basics, If you know the solutions to this problem please help me and just explain it like I am a five year old just step by step if it will be some complex solution because I have dyslexia an I get often confused when I'm in CLI :D

If u need more info just say so and I will post it.

Thx Skoleon ;D

---

