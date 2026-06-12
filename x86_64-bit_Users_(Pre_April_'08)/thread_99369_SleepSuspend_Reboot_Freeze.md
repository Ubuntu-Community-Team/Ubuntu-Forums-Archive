---
title: "Sleep/Suspend Reboot Freeze"
date: 2005-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by yeti on 2005-12-05
Ok, so Im running Breezy on an iBook.  I generally run on a wireless network.  Its an old G3 700Mhz iBook and I installed Breezy about a week ago.  The problem is that I can get into suspend (using the <action> menu from bootscreen or System-->Logout-->Suspend works fine.  Also if I just close the top it goes into suspension.), however when I try to wake it up it always hangs and makes me do a hard reboot of the system.  When I reboot a list of acitons come up, that I presume is the readout from the wakeup operations.  At the Left in brackets are numbers (generally XXX.XXXXXXX) that I presume have something to do with time.  The number in the brackets changes, but the last operation (the one it hangs on) is always 

```
[750.2331831] eth1: New link status: Connected 0001
```

The order of the lines changes--the 2nd to last line is not always the same, but the last line is always the same.  

My limited noob problem analysis skills lead me to believe that the problem is somewhere involved in the ineteraction of setting up a connection to my wirless network and rebooting out of suspend, but I dont see why that is any harder than, say just rebooting and having to set up a new connection. 

Any Ideas?

*Update:*  When I try to reboot from suspension and it has both eth1 and eth0 active (my wireless and ethernet ports) then it gets past the above step and instead says :

```
 [XXX.XXXXXXX] eth0: Pause not enabled 
```

---

### Post by ssam on 2005-12-05
have you tried disconnecting from networks and unplugging all peripherals before sleeping?

---

### Post by yeti on 2005-12-05
Yeah-- Ive deactivated all network interfaces and peripherals and tried to reboot out of sleep and though the step that it hangs on changes, it still has something to do with eth1 or eth0... I dont know why it would though, since those are supposedly deactivated.

---

### Post by ssam on 2005-12-05
do you not get those boot messages on a normal start up?

you should probably shut down properly until this is fixed for you.

it is possible have scripts run before suspending and after resuming, so if the problem can be isolated then, we could work out a script.

have you used the lsmod, rmmod and modprobe tools before? you could try unloading the network driver modules before suspending and see if that helped.

---

### Post by yeti on 2005-12-05
I have not used those commands before-- Im a real noob. I get similar messages on startup, (I think) but frankly they whiz by so quickly that I cannot read them, and I dont know how to go back to check out the messages that are flashed up on the screen.  lsmod gives:

```
yeti@revenge:~$ lsmod
Module                  Size  Used by
ipv6                  300456  6
rfcomm                 45852  0
l2cap                  28356  5 rfcomm
bluetooth              60712  4 rfcomm,l2cap
cpufreq_userspace       5356  1
cpufreq_stats           6468  0
cpufreq_powersave       1888  0
cpufreq_ondemand        7580  0
cpufreq_conservative     8868  0
pcmcia                 33416  0
yenta_socket           27084  0
rsrc_nonstatic         13568  1 yenta_socket
pcmcia_core            58480  3 pcmcia,yenta_socket,rsrc_nonstatic
radeon                 90308  1
drm                    80440  2 radeon
af_packet              20840  4
tsdev                   9120  0
ohci1394               40436  0
uninorth_agp           10952  1
agpgart                38876  2 drm,uninorth_agp
dm_mod                 67124  1
evdev                  11936  5
sr_mod                 20964  0
snd_powermac           53700  1
snd_pcm_oss            65024  0
snd_mixer_oss          22048  1 snd_pcm_oss
snd_pcm               106020  2 snd_powermac,snd_pcm_oss
snd_timer              28388  1 snd_pcm
snd                    63668  7 snd_powermac,snd_pcm_oss,snd_mixer_oss,snd_pcm,s nd_timer
soundcore              11364  1 snd
snd_page_alloc         11880  1 snd_pcm
sbp2                   26024  0
scsi_mod              171488  2 sr_mod,sbp2
ieee1394              434320  2 ohci1394,sbp2
apm_emu                 7916  1
airport                 7392  0
orinoco                48308  1 airport
hermes                  8448  2 airport,orinoco
md                     53588  0
ext3                  143272  1
jbd                    70456  1 ext3
mbcache                11076  1 ext3
sungem                 37220  0
sungem_phy              9728  1 sungem
ohci_hcd               25188  0
usbcore               137972  2 ohci_hcd
ide_cd                 48548  0
cdrom                  47420  2 sr_mod,ide_cd
ide_disk               20544  3
unix                   31124  724

```

Which modules are the network drivers?  I suppose hermes, airport and orinoco have something to do with wireless networking, but which is ethernet and which is ppp?  is ieee1394 my ethernet?

---

### Post by yeti on 2005-12-05
So I used modprobe -r to remove airport, orinoco and hermes.  I could not remove ieee1394-- the machine said that it was being used by something.  I shut down the interfaces with ifconfig (both lo and eth0) but I still could not remove the module.  I tried to suspend it, but it still hung a some point in process to reboot from suspend.  

Any ideas?

---

### Post by er-ku on 2005-12-23
This is reported at [Ubuntu bugzilla as a kernel bug](https://bugzilla.ubuntu.com/show_bug.cgi?id=1940), and there's a fix for this problem there. And I just wrote a nasty comment out there, as they only fixed it for dapper, damnit!

However, [this thread](http://ubuntuforums.org/showthread.php?t=79301) may, or may not help you. Try searching these forums for "ibook wake up", you'll get lots of results.

---

