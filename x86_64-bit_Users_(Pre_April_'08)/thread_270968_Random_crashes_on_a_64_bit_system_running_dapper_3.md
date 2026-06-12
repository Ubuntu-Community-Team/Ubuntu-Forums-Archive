---
title: "Random crashes on a 64 bit system running dapper 32 bit"
date: 2006-10-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by sbecerra on 2006-10-04
Hello all, this is my first post so apologies if I am omitting any necessary information (or if this shouldn't go in the 64-bit forum).

I have the 32-bit version ubuntu dapper installed on an emachines T6410. It has a 64-bit Athlon processor and 512M RAM. It's running kernel 2.6.15-26-k7. It has a pci-express NVIDIA card with the latest NVIDIA drivers installed (1.0-8762).

The system would not complete boot up initially (and the system clock ran at twice the normal speed) until I added the following parameters to the grub entry (I had to add noapic and acpi=noirq): 

[FONT="Arial"]kernel    /boot/vmlinuz-2.6.15-26-k7 root=/dev/hdb1 ro noapic acpi=noirq quiet splash[/FONT]

So it runs now, perfectly fine except for some seemingly random lockups I've been experiencing. They seem to happen in two types of situations: 

1) The computer is idle, the screen has automatically turned itself off after a while. When I try to use the computer, the screen does not turn back on and the keyboard is unresponsive. If I press the numlock key, nothing happens (the numlock light on the keyboard stays on).

2) The computer is under a heavy CPU and network (but not hard drive) load. For example, watching videos on youtube. The difference in this crash is that usually I am still able to move the mouse around but the keyboard is still unresponsive.

The weird thing is that it just seems to be the display that's frozen, because I can ssh into the box without a problem and it continues to work as my router even after the display has frozen.

So I've looked in my /var/log/messages to see if there are any errors when the freeze occurs; there are none. Here's what the entries look like: 

[FONT="Arial"]
Oct  4 00:00:49 localhost -- MARK --
Oct  4 00:20:50 localhost -- MARK --
Oct  4 00:40:51 localhost -- MARK --
Oct  4 00:52:10 localhost syslogd 1.4.1#17ubuntu7: restart.
[/FONT]

As you can see above, the random crash happened at about 00:45, give or take a couple of minutes.

I have tried SSHing in and issuing a "sudo /etc/init.d/gdm restart" but all that does is kill the x-server (at this point the display goes black) and then the program reports that it is unable to restart gdm.

Here is the output of lspci:
[FONT="Arial"]0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge
0000:00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
0000:00:11.0 IDE interface: ATI Technologies Inc ATI 437A Serial ATA Controller
0000:00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 10)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 01)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: nVidia Corporation NV35 [GeForce PCX 5900] (rev a2)
0000:02:01.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:02:02.0 Communication controller: Conexant HSF 56k Data/Fax Modem
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)[/FONT]

My dmesg output is attached in gzipped form as dmesg.txt.gz

Does anyone have any ideas? Thanks in advance.

---

### Post by kuja on 2006-10-04
How very odd, but I've heard of similar issues regarding running a 32-bit linux on a 64-bit machine. Perhaps the ACPI thing could be a BIOS issue, but I'm really not sure. I wonder if the 64-bit dapper would give you any trouble or not, it'd be interesting to see if it ran stable whereas the 32-bit did not.

---

### Post by kleeman on 2006-10-04
It sounds like an X issue rather than a kernel issue since you are able to login and you are seeing no kernel error messages. Is there anything of interest in your /var/log/Xorg.0.log file after this happens? Login in remotely and check after you get another freeze.

---

### Post by sbecerra on 2006-10-05
> **kleeman said:**
>  Is there anything of interest in your /var/log/Xorg.0.log file after this happens? Login in remotely and check after you get another freeze.

Will do, thanks for the suggestion.

---

### Post by sbecerra on 2006-10-05
> **kleeman said:**
>  Is there anything of interest in your /var/log/Xorg.0.log file after this happens? Login in remotely and check after you get another freeze.

I got another freeze just now. There doesn't appear to be anything interesting in my Xorg.0.log file (but I attached it). I'm going to keep the machine in the frozen state so that I can keep trying any suggestions that you guys make.

Looking in my /var/log/messages, there is one interesting thing. The display froze at 18:54 (I know this because of the clock on my tray). There is only one line in my /var/log/messages for 18:54...

[FONT="Arial"]Oct  5 18:54:44 localhost kernel: [17252973.340000] NVRM: Xid (0001:00): 6, PE0000 0b04 ff5a5a5a 0000070c 00000000 ff5a5a5a[/FONT]

So it looks like it has something to do with the drivers for my Geforce PCX 5900.

I'm going to google around for solutions, but can anyone think of what to do? I'll report back with anything I find out.

---

### Post by kleeman on 2006-10-05
The following thread seems to be similar to your problem:

[http://www.ubuntuforums.org/showthread.php?t=270968](http://www.ubuntuforums.org/showthread.php?t=270968)

These guys think it is an nvidia driver issue. I would try two things:
1) Disbale agp (bios???) and see if this helps
2) Update to the latest nvidia driver using the manual howto in these fora.

---

### Post by JAPrufrock on 2006-10-06
Might be a glx problem.  Your NVidia card is installed, buy you may not have 3d acceleration.  You may have to install a new driver via Nvidia's [home page]("http://www.nvidia.com/object/unix.html").  I have the same problem, but am procrastinating.  It's not an easy push-1-button installation.  For now you might try using a non 3-D screen saver (the complex ones are 3d, while the simple ones are not), and turning off glx. Hope this helps.
   Oh year, I forgot- there was a very nice thread on Nvidia driver installation (including 64bit systems) on one of these fora.

---

### Post by sbecerra on 2006-10-08
Adding the following to the Screen section of my xorg.conf seems to have fixed it--I'll check back in a while to confirm whether this actually fixed it or not...

[FONT="Arial"]Option "NvAgp" "0"[/FONT]

---

