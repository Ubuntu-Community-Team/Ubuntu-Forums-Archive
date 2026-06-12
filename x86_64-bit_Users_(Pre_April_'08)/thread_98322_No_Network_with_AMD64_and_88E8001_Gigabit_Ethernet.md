---
title: "No Network with AMD64 and 88E8001 Gigabit Ethernet"
date: 2005-12-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by Buchuki on 2005-12-02
Hello,

I got Kubuntu installed from the Breezy Badger 5.10 DVD install for AMD 64. Sadly, I'm not getting the 'just works' functionality that my acquaintances have been bragging about in Ubuntu. I think I may have bad karma! :-)

Its refusing to detect my network. I'm not familiar enough with the tools to see why yet. ifconfig -a shows eth0, but I am unable to get it to come up no matter how hard I try. The network card is Marvell 88E8001 Gigabit Ethernet card, and works fine under Arch Linux using the sk98lin module.

I noticed this module wasn't in the output of lsmod, so I modprobed it. Now it shows up in lsmod. I ran ifup eth0, but it failed with something about ignoring interface eth0=eth0 (I don't remember the exact error atm, sorry). I tried /etc/init.d/networking restart, but that didn't bring it up either.

Forum search came up with this thread:

[http://www.ubuntuforums.org/showthread.php?t=47615&page=9](http://www.ubuntuforums.org/showthread.php?t=47615&page=9)

I haven't read through the whole thing, but it seems like the problems brought up in the thread are supposed to have been fixed in Breezy Badger.

Now, two things I have thought of doing:
* install the sk98lin driver as described in the first post of the above thread
* try to upgrade my install to the 2.6.14 kernel somehow (without network)

Both of these seem like kind of invasive procedures, so I was hoping for a hint that would prevent me from having to do either, or at least a hint saying which was more likely to give results, and perhaps the easiest way it can be done given that I have no network in Kubuntu but am still able to boot Arch.

My main problem is I don't have a lot of time right now -- this is the main reason I am switching to ubuntu, to be honest -- I need a distro that provides me with more support than Arch is giving me. I'm hoping this network thing will be the only headache I will have.

Thanks for any advice,

Dusty

---

### Post by Buchuki on 2005-12-03
Sorry, one other thing I have already tried is the skge module. It didn't seem to make a difference unless I am pulling a 'stupid' in trying to get the network to come up.

Dusty

---

### Post by Buchuki on 2005-12-03
Hmm.... I've done a more invasive forum search. It looks like this particular card has caused a lot of grief for other users in the past, but from what I read this was supposed to be fixed with breezy? Am I wrong? The only thing I can think of is maybe its not fixed with the AMD64 version.

I've got the 2.6.14.3 kernel sources and am going to try to build according to the HOWTO I found in the wiki. Been a while since I've built a kernel the Debian way. :-) Am I on the right track?

One other minor point, I should perhaps have posted this to the 64 bit forum instead of here... would appreciate a move if a moderator has the time. :-)

Thanks again,

Dusty

---

### Post by Buchuki on 2005-12-05
Well, I got tired of repeated recompiles to even get the kernel to boot. Probably a simple thing, but I don't really have time to experiment, especially since I don't even know if its going to solve the network problem. I think for now I'll stick with arch and see if maybe the 'it just works' promise comes true with the next Ubuntu release. :-(

Dusty

---

### Post by guice on 2005-12-05
You try to alter your IPs and such through the network control panel? Then you need to set your route: route -r
Should see a default route. If you don't, you need to set it. If you're on a normal LinkSys network just use: route add default gw 192.168.1.1

---

### Post by Buchuki on 2005-12-05
No, that's not it, I need to use dhcp. The network control panel can't even seem to find the card (can confirm with lack of output from ifconfig). I'm pretty sure its at the module level, somehow.

Thanks,
Dusty

---

### Post by jon_z on 2005-12-15
dusty, I'm using the same motherboard, processor as you...the only thing i did different.. I installed mandriva 2005 first... Mandriva loves our motherboard and configures dhcp flawlessly....installing packages for us....not so much.... At this point as soon as i do a barebones install on mandriva, i pop the kubuntu disk in, reboot, install kubuntu, and wala when detecting dhcp comes up, SUCCESSFUL! and i always smile :-) Ive re-installed kubuntu now about 5x without having to install mandriva once now, and it gets dhcp every time...just an odd tip, try doing that and see if it works for you.

---

### Post by Buchuki on 2005-12-17
Hi jon, thanks for the info.

That's interesting, why would this work? Is it that Ubuntu installer queries the existing system for DHCP information? If this is the case, why doesn't it query my Arch setup? OR, why doesn't it let me configure it myself?

Are you installing the 64 bit version of kubuntu? I suspected that had something to do with it. :( I don't really feel like downloading and installing mandriva to get ubuntu installed, the ubuntu install process as long enough already. :-)

Dusty

---

