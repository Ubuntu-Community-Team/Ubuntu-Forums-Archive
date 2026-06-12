---
title: "FreeNX installed but some issues"
date: 2006-08-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by smpolymen on 2006-08-24
I have installed freenx and the libs from seveas' packages and have had some success but I now have the following problems-

I did a dpkg --force-arch and it installed the i386 stuff fine and nx worked perfectly :) but synaptic went crazy and refuses to do anything until I fix the broken "freenx" package. apparently I am missing nxagent but I see it is installed in synaptic (it's the i386 version of nxagent but the right version number) and it appears to be installed (it's working fine)

I tried an apt-get -b source and I guess it built an AMD64 version and I dpkg'd and they installed and apt was fine,  nxserver starts and runs, the client connects but does nothing no no machine logo and it errors with no response from remote machine.

So my question is either: how can I tell apt to ignore that package, or is there something I'm missing with building or using the amd64 versions?

Edit: in case it wasn't clear I have never built packages before so if I missed something, please point it out.

---

### Post by Kilz on 2006-08-24
> **smpolymen said:**
> I have installed freenx and the libs from seveas' packages and have had some success but I now have the following problems-

I did a dpkg --force-arch and it installed the i386 stuff fine and nx worked perfectly :) but synaptic went crazy and refuses to do anything until I fix the broken "freenx" package. apparently I am missing nxagent but I see it is installed in synaptic (it's the i386 version of nxagent but the right version number) and it appears to be installed (it's working fine)

I tried an apt-get -b source and I guess it built an AMD64 version and I dpkg'd and they installed and apt was fine,  nxserver starts and runs, the client connects but does nothing no no machine logo and it errors with no response from remote machine.

So my question is either: how can I tell apt to ignore that package, or is there something I'm missing with building or using the amd64 versions?

Edit: in case it wasn't clear I have never built packages before so if I missed something, please point it out.
If you remove the nxagent package do you get the error? Is it the only package that synaptic is complaining about? If so it might be possible to remove the package , then manualy install nxagent with dpkg -x package name Then copy it into place, just copy the contents in the extracted folders to the corasponding folders in the file system.

---

### Post by smpolymen on 2006-08-24
Ok problem solved. I read up on editing .debs and I wrote a quick script to change the arch in the i386 control files to amd64. They installed fine, it works and apt is happy. :)

---

### Post by kleeman on 2006-08-30
I need to do what you have done. Could you possibly provide the script or a reference for where you found how to edit .debs to change architecture?
TIA.

Edit: Found an answer. I used "deb-reversion -k bash" from the devscripts package and exited nano and then edited (in the shell) DEBIAN/control after exiting this shell it created the desired debs. Did not work for nxlient and I had to force installation using dpkg --force-architecture. I also had to convert the i386 package   libstdc++2.10-glibc2.2 using the method above. 

Luckily the last step did not bork apt and everything works great. I sent an email to Dennis Kaarsemaker suggesting he modify the erchitecture field of his debs (to all) for the convenience of 64bit users.

Further Edit:

Dennis does not want to add amd64 support because he says that nx does not play well with 64bit. I have seen no problems myself and suspect the issue is moot because the seveas packages are here being run in 32bit mode.

---

