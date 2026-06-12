---
title: "PCMCIA card recommendation and wireless help"
date: 2005-10-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Adam Boettiger on 2005-10-15
I am (understandably) frustrated with the fact that broadcom has not or will not release the Airport Extreme card specs so a driver can be developed.

In lieu of this, and in the interim, I am looking for someone to recommend the best out-of-the-box PCMCIA card that I can plug into a PowerBook G4 PCMCIA slot and have work for wireless net connectivity with Ubuntu 5.10.

"Any card using the Prism chipset works well as they have released their specs and drivers are available."

(love it when I talk to myself, but just saving time...)

I realize that Prism chipsest cards are likely the best option. But is there a list or compillation somewhere online that states which models use the Prism chipset in their cards?

Also. I have a D-Link AirPlus DWL-650+ wireless cardbus adapter.

I no nothing about using ndiswrapper or reconfiguring a kernel. 

A) Is there any newbie documentation on how to do this online?

B) Is there anyone willing to talk me through it by phone if I pay for their time, to get this card to work?

Thanks in advance for any suggestions.

Off-list I may be contacted at adam AT linuxmojo DOT org

/AB

---

### Post by pingswept on 2005-10-15
[QUOTE=Adam Boettiger]
I realize that Prism chipsest cards are likely the best option. But is there a list or compilation somewhere online that states which models use the Prism chipset in their cards?[/QUOTE]

Like this? [http://wiki.personaltelco.net/index.cgi/Prism2Card](http://wiki.personaltelco.net/index.cgi/Prism2Card)

> Also. I have a D-Link AirPlus DWL-650+ wireless cardbus adapter.

A) Is there any newbie documentation on how to do this online?

From [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) :

# Card: D-Link Airplus DWL 650+

    * Chipset: ACX100
    * pciid: 104c:8400
    * Driver: Windows drivers from [http://www.dlink.com/](http://www.dlink.com/) . "Native" acx100 Linux driver available at [http://lisas.de/~andi/acx100/](http://lisas.de/~andi/acx100/) ; requires Firmware from Windows drivers. Please read README for details.
    * Other: Tested on Slackware 10 with Ndiswrapper 0.8. acx100 supports WEP (only tested 128bit).
    * Other: Works Perfectly with Ndiswrapper 1.1 in Ad-Hoc mode ( 2005.05.12 ). Howto: Craig's ACX100/111 Guide for Linux <http://www.houseofcraig.net/acx100_howto.php> 

There is an ndiswrapper package that you can install through Synaptic. I've used it once, and it was not painful (but maybe I was just lucky).

---

### Post by oswaldkelso on 2005-10-15
Check this first :)

[http://ubuntuforums.org/showthread.php?t=76416](http://ubuntuforums.org/showthread.php?t=76416)

---

### Post by Adam Boettiger on 2005-10-15
> 2005.05.12 ). Howto: Craig's ACX100/111 Guide for Linux <http://www.houseofcraig.net/acx100_howto.php> 

There is an ndiswrapper package that you can install through Synaptic. I've used it once, and it was not painful (but maybe I was just lucky).

Thanks. I tried running through Craig's tutorial. Query: Does 5.10 have the GCC package installed by default, along with a wireless package?

If yes, thanks for confirming it.

If no, how am I supposed to obtain it if I do not have net access in Linux?

Thx

---

### Post by Adam Boettiger on 2005-10-15
[QUOTE=oswaldkelso]Check this first :)

[http://ubuntuforums.org/showthread.php?t=76416](http://ubuntuforums.org/showthread.php?t=76416)[/QUOTE]

I did. Thanks! Yeah all it says is that Airport Extreme is not supported yet, but that there is an ongoing project. The project site says they took it offline for legal reasons but are still working on building a driver.

This is actually irrelevant to me. I've accepted the fact that I won't be able to use the internal card in my PowerBook G4 for some time; so I went out and bought a used external card and am trying to configure that one, not the Airport Extreme internal card.

Thanks for the info.

AB

---

### Post by pingswept on 2005-10-15
[QUOTE=Adam Boettiger]Thanks. I tried running through Craig's tutorial. Query: Does 5.10 have the GCC package installed by default, along with a wireless package?[/QUOTE]
I don't know, but if it is, it should be in /usr/bin/gcc.
> 
If no, how am I supposed to obtain it if I do not have net access in Linux?

Try "sudo apt-get install gcc" with the install disc in your CD drive. Even if it's not installed by default, I'd be shocked if it weren't on the CD.

---

