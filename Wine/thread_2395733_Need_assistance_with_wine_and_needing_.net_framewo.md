---
title: "Need assistance with wine and needing .net framework 4 to run programs"
date: 2018-07-05
forum: Wine
---

### Post by maxthespy on 2018-07-05
So Ive been having this same problem for a little while, I thought it was just the one poice of software Im trying to use with wine but Its every windows software I guess. It keeps giving me the error message that I need to have .net framework 4 installed in order to continue. I went to t[his site]("https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-current") and used as a guide to install. I got all the way though the end until I got to the last step when it asks to "[COLOR=#000000][FONT=Menlo]sudo apt-get install aspnetcore-runtime-2.1"

I type that into the terminal and it gives me this output:

```

[/FONT][/COLOR]axthespy@Maxwell-Zorin:~$ sudo apt-get install aspnetcore-runtime-2.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 aspnetcore-runtime-2.1 : Depends: dotnet-runtime-2.1 (>= 2.1.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


[COLOR=#000000][FONT=Menlo]
```

How do I fix this to get wine running on my machine. Ive seen it done before and I dont know or am not sure of what I am doing wrong. [/FONT][/COLOR]

---

### Post by wildmanne39 on 2018-07-05
*Thread moved to **Wine for a more appropriate fit**.*

---

### Post by MikeCyber on 2018-07-12
net is not needed for wine. if at all I would use mono with winetricks

what you are trying to install doesn't use wine at all.-

google synaptic and how to fix broken packages

---

