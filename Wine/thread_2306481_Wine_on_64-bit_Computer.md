---
title: "Wine on 64-bit Computer"
date: 2015-12-15
forum: Wine
---

### Post by wagb278 on 2015-12-15
Problem in a nutshell - Winetricks installing DLL or Windows components - I get a message that the installer does not support 64-bit architecture and Winetricks exits. 

On a 64-bit computer running Ubuntu-MATE 15.10 I installed Wine 1.6.2 using the PPA method and that process seems to have worked - "wine --version" reports wine-1.6.2, the current stable version.  The Applications Menu now has a Wine entry with Configure Wine and Winetricks, along with other items.  The included Notepad application runs Okay.  So I figured all is well with Wine. I did notice during installation of Wine it was fetching 64-bit and 32-bit versions of many files. 

The one Windows application I need is Ancestral Quest; which runs fine in Wine (1.6.2) on a 32-bit Linux Mint 17 computer - I just want to use that application on this 64-bit computer and thought installation of that application would go smooth; wrong!  Ancestral Quest requires Windows components &#8220;jet40&#8221; and &#8220;mdac28&#8221; I believe, at least those were needed on the 32-bit computer for a Collaboration feature to communicate with a database server. So I try to install those using Winetricks - Install a Windows DLL or Component, but that wont work because I am on a 64-bit computer.  

Is there a 64-bit version of Winetricks or what do I have to do to get those installed? 
Shouldn't Wine accommodate both architectures and pick the right one automatically? 

I haven't tried to install the Ancestral Quest application in Wine yet because I believe I first need to get those Windows components.  How do I get those components into the Wine environment on a 64-bit computer? 

I have searched for answers, but I could not find anything recent pertaining to Wine and Ubuntu-MATE. Wine documentation is no help and does not include anything about 64-bit computer differences.

Any suggestions are welcome or if more information is needed I will try to provide it.
Thanks

---

### Post by qyot27 on 2015-12-15
[This is probably relevant.](http://askubuntu.com/questions/136714/how-to-force-wine-into-acting-like-32-bit-windows-on-64-bit-ubuntu)

---

### Post by wagb278 on 2015-12-16
Thanks qyot27,

I was able to get that to work.  Seems strange to me that WINEARCH needs to be set and a new configuration for wine established, but hey I got Ancestral Quest running in Wine on 64-bit computer and the Collaboration feature works, too.

---

### Post by yoshii on 2015-12-21
how did you guys set the WINEARCH variable?  How is that accomplished?

---

### Post by ndricsimarmata on 2016-02-10
> **qyot27 said:**
> [This is probably relevant.]("http://askubuntu.com/questions/136714/how-to-force-wine-into-acting-like-32-bit-windows-on-64-bit-ubuntu")

Thank you qyout it's help me..

---

