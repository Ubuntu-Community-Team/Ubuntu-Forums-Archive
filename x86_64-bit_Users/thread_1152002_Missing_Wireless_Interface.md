---
title: "Missing Wireless Interface"
date: 2009-05-07
forum: x86 64-bit Users
---

### Post by microber on 2009-05-07
After two years of Ubuntu this is my first post; I found all other solutions on previously posted forums, but not for this problem (I guess I'm trying to say go easy on me if I missed something :)). The problem is that I am missing my wireless interface. I just updated to Jaunty from Hardy (in which wireless worked), my computer is an Inspiron 1525, wireless card is Broadcom 4312. In System -> Administration -> Hardware Drivers it says Broadcom B43 wireless driver is activated and currently in use. I have tried de-activating and re-activating, uninstalling and re-installing the fwcutter tool and then turning the driver on and off. The wireless switch on my laptop is on and wireless still works in Vista. Here's some more relevant information:

```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:5f:6d:9e  
          inet addr:132.236.1--.--  Bcast:132.236.1--.---  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe5f:6d9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19155 errors:2 dropped:2 overruns:0 frame:4
          TX packets:12403 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14142846 (14.1 MB)  TX bytes:2412065 (2.4 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1720 (1.7 KB)  TX bytes:1720 (1.7 KB)
```
```

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```

some relevant lines from dmesg:
```
[   20.404015] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.404023] pci 0000:00:02.0: setting latency timer to 64
[   20.416822] pci 0000:00:02.0: irq 29 for MSI/MSI-X
[   20.416866] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   22.302878] sky2 eth0: enabling interface
[   22.303584] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.892756] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   23.893451] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   34.032052] eth0: no IPv6 routers present
[  485.133247] b43-pci-bridge 0000:0b:00.0: PCI INT A disabled
[ 1423.866899] sky2 eth0: rx error, status 0x3c0052 length 60
[ 1478.301148] cfg80211: Calling CRDA to update world regulatory domain
[ 1478.327231] b43-pci-bridge 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1478.327255] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64
[ 1478.330286] cfg80211: World regulatory domain updated:
[ 1478.330290]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1478.330294]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1478.330297]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1478.330300]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1478.330303]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1478.330306]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1478.392205] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
[ 1478.396900] b43: Unknown parameter `ssb'
[ 1478.414196] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[ 1478.461216] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 6, Type 5, Revision 1)
[ 1478.461273] b43: probe of ssb0:0 failed with error -95
[ 1478.461303] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[ 2768.833073] sky2 eth0: rx error, status 0x3c0052 length 60
```
the relevant lines from lspci
```
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
```
```
~$ lsmod
Module                  Size  Used by
b43                   140168  0 
ssb                    42384  1 b43
mac80211              245624  1 b43
cfg80211               76568  2 b43,mac80211
input_polldev           4816  1 b43
i915                  186408  2 
drm                   189280  3 i915
i2c_algo_bit            7044  1 i915
binfmt_misc            10252  1 
ppdev                   8744  0 
bridge                 55552  0 
stp                     2948  1 bridge
bnep                   14912  2 
sbp2                   27052  0 
lp                     11716  0 
parport                42320  2 ppdev,lp
snd_hda_codec_idt      70124  1 
snd_hda_codec_intelhdmi    15680  1 
joydev                 13312  0 
snd_hda_intel          32232  3 
snd_hda_codec          78176  3 snd_hda_codec_idt,snd_hda_codec_intelhdmi,snd_hda_intel
snd_pcm_oss            46656  0 
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                94120  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            32544  0 
snd_seq_midi            8000  0 
snd_rawmidi            26368  1 snd_seq_midi
snd_seq_midi_event      8352  2 snd_seq_oss,snd_seq_midi
snd_seq                58688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8212  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    75592  18 snd_hda_codec_idt,snd_hda_codec_intelhdmi,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               65388  0 
soundcore               8960  1 snd
video                  23604  1 i915
sdhci_pci               8832  0 
videodev               41152  1 uvcvideo
snd_page_alloc         10768  2 snd_hda_intel,snd_pcm
sdhci                  21316  1 sdhci_pci
psmouse                55900  0 
dcdbas                  9104  0 
v4l1_compat            16260  2 uvcvideo,videodev
output                  3616  1 video
intel_agp              31792  1 
led_class               5320  2 b43,sdhci
pcspkr                  2944  0 
serio_raw               6660  0 
v4l2_compat_ioctl32    13056  1 videodev
iTCO_wdt               13584  0 
iTCO_vendor_support     4612  1 iTCO_wdt
ohci1394               34644  0 
ieee1394              101824  2 sbp2,ohci1394
sky2                   54436  0 
```/etc/udev/rules.d/70-persistent-net.rules
```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x11ab:0x4354 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1d:09:5f:6d:9e", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1f:e1:67:6a:1d", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
```

```
~$lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:5f:6d:9e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=132.236.142.39 latency=0 module=sky2 multicast=yes
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6a:09:aa:99:67:af
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```and a conspicuously short /etc/network/interfaces file:
auto lo
iface lo inet loopback

I have tried restarting the network, my computer, etc. I also tried adding eth1 to the /etc/network/interfaces file, to no avail. Any ideas? Thanks in advance.

---

### Post by Yellow Pasque on 2009-05-07
What driver did you use in Hardy? If you look at the b43 page, it explicitly lists your PCI ID as not supported: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
and your dmesg log confirms that the driver doesn't support that chip.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by microber on 2009-05-07
I removed the b43 and ssb drivers ("sudo modprobe -r b43 ssb" for anyone who would like to follow along), so now lshw -C network shows my wireless card is unclaimed. Is there a way I can tell which driver I had installed previously? Unfortunately I don't take notes when I do new installations (would save a lot of time in situations like these). I have been trying different things with ndiswrapper, will update if I figure something out. Thanks.

---

### Post by microber on 2009-05-07
Here's my solution:

I restarted into the 2.6.28-11-generic kernel, instead of 2.6.30-020630rc2-generic, which was my bootloader's default. Then I followed the instructions on [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) . I would post them all in detail, but it involves downloading the driver from the card manufacturer off of that page, so I assume if that link is broken then the instructions wouldn't be too useful. I think part of the problem was the ndiswrapper installation (despite reinstalling it several times). modprobe ndiswrapper kept returning an error about the module not being found. I may have just tried something different when I booted onto this kernel - not quite sure. I have tried following so many different suggestions about this that somewhere along the way I could have messed up the 2.6.30 kernel. At any rate, now that it's almost 6pm I can get to work!

---

