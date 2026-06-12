---
title: "I can't get an ip address!"
date: 2006-05-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by iMlazy on 2006-05-22
I was reviewing my schism with the internet with my compadre, and he pointed out that Ubuntu doesn't recognize an ip address for my internet connexion.

I am using SBC-Yahoo DSL connexion to the net, and it works fine when I choose to run windoze XP (using grub ;)). I selected Eth0 to have a dynamic ip address.

When I ran /sbin/ifconfig/ it returned:

eth0    [...]  inet6 addr: fe80::213:d3ff:fee7:9b6a/64 Scope:Link

[...]

lo    [...] inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
    
What do I have to do to get connected?  :???:

---

### Post by tonyr on 2006-05-22
You should provide some information about your hardware configuration, including
what ethernet controller you are using, if you know.  Run **lspci** in a terminal
and post the results.

---

### Post by iMlazy on 2006-05-22
I am using a NVIDIA nForce Networking Controller for my connection.

I'll edit in the results from running ispci :-|

I opened the terminal and typed in "ispci" it returns "bash: command not found" I typed in several variations of it, and it returned the same thing :(

---

### Post by tonyr on 2006-05-22
[QUOTE=iMlazy]I opened the terminal and typed in "ispci" it returns "bash: command not found" I typed in several variations of it, and it returned the same thing :([/QUOTE]

Darn fonts! That should be **lspci** (ell-ess-pee-see-eye) not 
**ispci** (eye-ess-pee-cee-eye).  It's in package **pciutils**, which should
have been installed by default, but may not have been.  Install it
if it's not already there.

---

### Post by tonyr on 2006-05-22
[QUOTE=iMlazy]I am using a NVIDIA nForce Networking Controller for my connection.[/QUOTE]

Is it a separate card, or integrated on the motherboard?  If on the motherboard,
do you know what the motherboard model is?

---

### Post by iMlazy on 2006-05-22
I am actually using an [emachine](http://www.amazon.com/gp/product/B000E1WN8W/103-1116087-5835028?v=glance&n=541966), so that's exactly what I have (nothing more, nothing less ;)).

I'll try the lspci in pciutils ;)

[edit] Here is the lspci ran from usr/bin/

0000:00:00.0 RAM memory: nVidia Corporation: Unknown device 02f1 (rev a2)

0000:00:00.1 RAM memory: nVidia Corporation: Unknown device 02fa (rev a2)

0000:00:00.2 RAM memory: nVidia Corporation: Unknown device 02fe (rev a2)

0000:00:00.3 RAM memory: nVidia Corporation: Unknown device 02f8 (rev a2)

0000:00:00.4 RAM memory: nVidia Corporation: Unknown device 02f9 (rev a2)

0000:00:00.5 RAM memory: nVidia Corporation: Unknown device 02ff (rev a2)

0000:00:00.6 RAM memory: nVidia Corporation: Unknown device 027f (rev a2)

0000:00:00.7 RAM memory: nVidia Corporation: Unknown device 027e (rev a2)

0000:00:02.0 PCI bridge: nVidia Corporation: Unknown device 02fc (rev a1)

0000:00:03.0 PCI bridge: nVidia Corporation: Unknown device 02fd (rev a1)

0000:00:04.0 PCI bridge: nVidia Corporation: Unknown device 02fb (rev a1)

0000:00:05.0 VGA compatible controller: nVidia Corporation: Unknown device 0242 (rev a2)

0000:00:09.0 RAM memory: nVidia Corporation: Unknown device 0270 (rev a2)

0000:00:0a.0 ISA bridge: nVidia Corporation: Unknown device 0261 (rev a2)

0000:00:0a.1 SMBus: nVidia Corporation: Unknown device 0264 (rev a2)

0000:00:0b.0 USB Controller: nVidia Corporation: Unknown device 026d (rev a2)

0000:00:0b.1 USB Controller: nVidia Corporation: Unknown device 026e (rev a2)

0000:00:0d.0 IDE interface: nVidia Corporation: Unknown device 0265 (rev a1)

0000:00:0e.0 IDE interface: nVidia Corporation: Unknown device 0266 (rev a1)

0000:00:10.0 PCI bridge: nVidia Corporation: Unknown device 026f (rev a2)

0000:00:10.1 0403: nVidia Corporation: Unknown device 026c (rev a2)

0000:00:14.0 Bridge: nVidia Corporation: Unknown device 0269 (rev a1)

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge

0000:04:07.0 Communication controller: Conexant: Unknown device 2f20

[edit 2] I found [Nvidia's Linux Driver](http://www.nvidia.com/object/linux_nforce_1.0-0248.html), installing that would solve the problemo; right? (Only it doesn't support Ubuntu!)

---

### Post by tonyr on 2006-05-22
[QUOTE=iMlazy]
[edit 2] I found [Nvidia's Linux Driver](http://www.nvidia.com/object/linux_nforce_1.0-0248.html), installing that would solve the problemo; right? (Only it doesn't support Ubuntu!)[/QUOTE]

I wish it were that simple.  What you actually need is the [nForce4 430/410 driver]("http://www.nvidia.com/object/nforce_nf4_430_410_winxp64_8.22.html") 
from what I can tell.  Unfortunately,  there is no Linux version
of that one, either.  Ubuntu handles this situation with **ndiswrapper**, which 
I believe allows Windows drivers to be encapsulated so as to look like loadable
driver modules.  I have never used it, but there is a lot of information around
about what it is, how to use it, and experience using it.  I'm not sure how
extensively it has been used with x64, but there should be plenty of references
for that, too.   I'm way outside of my area of knowledge now.  For what it's worth,
I believe your motherboard is a [MSI K8NGM-V]("http://www.msicomputer.com/product/p_spec.asp?model=K8NGM-V&class=mb"). Good Luck.

---

### Post by tonyr on 2006-05-22
Whoa Nellie!  Forget all that apologist bunk I just wrote. I think [this]("http://www.nvidia.com/object/linux_nforce_amd64_1.0-0310.html")
is the one you are looking for.  I googled **linux 430/410 driver** and came up
with a lot of hits.

---

### Post by ingo on 2006-05-23
Hi,

try 

dhclient eth0

to actively request an ip address.

HTH

Ingo

---

