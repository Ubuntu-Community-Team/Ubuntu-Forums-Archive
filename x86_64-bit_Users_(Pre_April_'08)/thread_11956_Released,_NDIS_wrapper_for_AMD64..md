---
title: "Released, NDIS wrapper for AMD64."
date: 2005-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by blinksilver on 2005-01-20
On the 17 of January, the ndis wrapper version 1.0rc3 was released with supported for amd64. It was tested with the broadcom wireless drivers found in the latest RC for Windows XP x64 Edition, and KNOWN to work.

it can be downloaded from [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

now for the bad news, although it will compiles on Gentoo x86_64, at least according to some posts made on their forum, it sadly  does not on ubuntu, (well not for me anyway), here is the error message:

soganess@M6805:~/Installation Files/ndiswrapper-1.0rc3$ make all
make -C driver
make[1]: Entering directory `/home/soganess/Installation Files/ndiswrapper-1.0rc3/driver'
Can't find kernel sources in /lib/modules/2.6.10-2-amd64-k8/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/soganess/Installation Files/ndiswrapper-1.0rc3/driver'
make: *** [all] Error 2
soganess@M6805:~/Installation Files/ndiswrapper-1.0rc3$

As far as i know the kernel directory listed above is the proper one, but i have only recently started to use ubuntu.

If there is a way to fix this every emachines m68XX user will be very greatful.  =D> 

Also is there way to get this onto one of the ubuntu servers as a deb file?

not bad for my first post, i hope  :D 

Blinksilver

---

### Post by Mr. Coconut on 2005-01-20
That would be good news for the Gateway 74xx users out there as well. Tell me, though, why would it be looking for kernel sources in /lib/modules? You would be more likely to find them in /usr/src

Hope that helps. I'll give this a shot myself.

---

### Post by blinksilver on 2005-01-20
I really would have no idea, i just did a make all, but i will give it a try

---

### Post by blinksilver on 2005-01-20
no luck /usr/src/ does not work, here is the output

root@M6805:/home/soganess/Installation Files/ndiswrapper-1.0rc3 # make all KSRC=/usr/src
make -C driver
make[1]: Entering directory `/home/soganess/Installation Files/ndiswrapper-1.0rc3/driver'
Can't find kernel sources in /usr/src;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/soganess/Installation Files/ndiswrapper-1.0rc3/driver'
make: *** [all] Error 2
root@M6805:/home/soganess/Installation Files/ndiswrapper-1.0rc3 #

---

### Post by Psy on 2005-01-20
First of all, it's /usr/src/linux.

You will need the linux-headers package for your kernel installed first.

If it still doesnt work, then get the linux-source package. It will install the source as a .tar.bz2 in /usr/src so you have to decompress it first. Then enter the directory that was extracted and type make oldconfig and make a symlink from /lib/modules/kernel-blabla/build to /usr/src/your-kernel-dir.

---

### Post by blinksilver on 2005-01-20
thank you very much, I got it to work, i am nowhere near a wireless network right now so i can check it, but it complied and load the the broadcom drivers,

---

### Post by Mr. Coconut on 2005-01-20
I just tried it myself. I already had the kernel headers installed, so it compiled without a problem. It also seems to take the broadcom drivers alright.

However, I get a serious kernel error when the drivers load, as follows (from dmesg):

---- QUOTE
ndiswrapper version 1.0rc3 loaded (preempt=no,smp=no)
ndiswrapper: driver netbc564 (,10/01/2002,3.70.17.5) added
ACPI: PCI interrupt 0000:00:0c.0[A] -> GSI 18 (level, low) -> IRQ 18
ndiswrapper: using irq 18
wlan0: ndiswrapper ethernet device 00:90:4b:c0:bd:2e using driver netbc564
wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP
ndiswrapper (register_devices:844): couldn't register ndiswrapper pci driver
Trying to vfree() nonexistent vm area (ffffff00046dd000)
Badness in __vunmap at mm/vmalloc.c:294

Call Trace:<ffffffffa031cb61>{:ndiswrapper:register_devices+1249}
       <ffffffffa031cbbf>{:ndiswrapper:wrapper_ioctl+63} <ffffffff8017ad0b>{sys_ioctl+507}
       <ffffffff80168a0e>{filp_close+126} <ffffffff8011162a>{system_call+126}

ndiswrapper (wrapper_init:1508): loadndiswrapper failed (1792); check system log for messages from 'loadndisdriver'
ndiswrapper: device wlan0 removed
Unable to handle kernel paging request at ffffff00046df118 RIP:
<ffffffffa0325697>{:ndiswrapper:miniport_halt+71}
PML4 3c4063 PGD 2facc067 PMD 2a149067 PTE 0
Oops: 0000 [1]
CPU 0
Modules linked in: ndiswrapper fglrx powernow_k8 proc_intf freq_table cpufreq_userspace cpufreq_powersave ds button ac battery ipv6 af_packet ohci1394 via_rhine mii crc32 snd_via82xx snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd_page_alloc gameport snd_mpu401_uart snd_rawmidi snd_seq_device snd soundcore ehci_hcd usbhid uhci_hcd yenta_socket pcmcia_core md dm_mod capability commoncap parport_pc lp parport sbp2 ieee1394 tsdev joydev evdev ide_cd rtc mousedev psmouse sr_mod scsi_mod cdrom ext3 jbd mbcache ide_generic via82cxxx ide_disk ide_core unix fan thermal processor font vesafb cfbcopyarea cfbimgblt cfbfillrect
Pid: 4466, comm: modprobe Tainted: P   2.6.8.1-4-amd64-k8
RIP: 0010:[<ffffffffa0325697>] <ffffffffa0325697>{:ndiswrapper:miniport_halt+71}RSP: 0018:000001001e139df8  EFLAGS: 00010212
RAX: ffffff00046df108 RBX: 0000010021eb2c18 RCX: 0000000000000100
RDX: 000000000012a00a RSI: 000001001e139db7 RDI: ffffffffa033d360
RBP: 0000010029383360 R08: 0000000000000000 R09: 000001002ec6b000
R10: 0000000000002000 R11: 0000000000000100 R12: ffffffff802e9840
R13: 0000002a9556a000 R14: 0000000000000000 R15: 0000000000508d70
FS:  0000002a95fe3380(0000) GS:ffffffff803c0a40(0000) knlGS:0000000000000000
CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
CR2: ffffff00046df118 CR3: 0000000000101000 CR4: 00000000000006e0
Process modprobe (pid: 4466, threadinfo 000001001e138000, task 000001001f9ac0f0)Stack: ffffff0004790b20 0000010029383360 0000010021eb2c18 ffffffffa0326619
       000001001d49a538 0000010001f77000 0000010001f77070 ffffffffa031bbf0
       000001001dbc6cb8 0000010001f77070
Call Trace:<ffffffffa0326619>{:ndiswrapper:ndiswrapper_remove_one_dev+425}
       <ffffffffa031bbf0>{:ndiswrapper:ndiswrapper_remove_one_pci_dev+48}
       <ffffffff801be58c>{pci_device_remove+44} <ffffffff801fff1e>{device_release_driver+94}
       <ffffffff801fff5f>{driver_detach+31} <ffffffff802003aa>{bus_remove_driver+42}
       <ffffffff80200829>{driver_unregister+9} <ffffffff801be82d>{pci_unregister_driver+13}
       <ffffffffa031cd06>{:ndiswrapper:loader_exit+70} <ffffffffa0327889>{:ndiswrapper:module_cleanup+9}
       <ffffffffa033f0ee>{:ndiswrapper:wrapper_init+238} <ffffffff80149385>{sys_init_module+245}
       <ffffffff8011162a>{system_call+126}

Code: 83 78 10 05 75 23 48 8b bd b8 03 00 00 48 8b 5c 24 08 be 03
RIP <ffffffffa0325697>{:ndiswrapper:miniport_halt+71} RSP <000001001e139df8>
CR2: ffffff00046df118
----- END QUOTE

I have no idea why it does this. It compiles without a problem, it installs without a problem and I can register the broadcom driver with ndiswrapper as well. But it does not appear to work for me at this point.

Since you have an M6805, you have essentially the same machine as I do (7405GX); i'd be interested in seeing if you can upload the binaries you created ...

---

### Post by blinksilver on 2005-01-20
Beyond essentally the same machine, i am using the gateway bios, so it is the same machine, ok i also have no idea what that mean, but i am using the k8 kernel and have all the updated, as well as am using hoary, maybe your configuration differs in some respect(IE using warty, or something) and that is it, otherwise I am really sorry.

Oh and i see you got the ati drivers to load, would you my telling me exaclly how you did it, i was following the instruction in one of the other forums and kept getting an error. 

best of luck
blinksilver

P.S. I made this post on wireless, it is the best feeling in the world, now if i can get those darn ati drivers to load i would have no reason for windows, well maybe FFXI, man i love the game.

---

### Post by Mr. Coconut on 2005-01-20
I fixed it. I updated my kernel to the hoary version and presto, instant wireless. 

How did I get the ati drivers to work? I unpacked them, compiled the module, did make_install.sh and presto, it just worked. I did, however, have to set the useinternalagpgart to NO for Xfree not to crash.

But since you're using hoary, I don't see how it matters. The driver has been made available under restricted modules for you.

---

### Post by blinksilver on 2005-01-20
pardom my noobness now would access and then install, the module, sorry, really new to linux, system, mainly using solaris and that is just for coding, never tinkered with the settings

---

### Post by Isengrim on 2005-01-23
I get this error with rc4


root@ubuntu:/home/anne/ndiswrapper-1.0rc4 # make
make -C driver
make[1]: Entering directory `/home/anne/ndiswrapper-1.0rc4/driver'
make -C /lib/modules/2.6.8.1-3-amd64-generic/build SUBDIRS=/home/anne/ndiswrapper-1.0rc4/driver \
        NDISWRAPPER_VERSION=1.0rc4 \
        EXTRA_VERSION= modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.8.1-3-amd64-generic'
  CC [M]  /home/anne/ndiswrapper-1.0rc4/driver/hal.o
/bin/sh: line 1: gcc: command not found
make[3]: *** [/home/anne/ndiswrapper-1.0rc4/driver/hal.o] Fout 127
make[2]: *** [_module_/home/anne/ndiswrapper-1.0rc4/driver] Fout 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.8.1-3-amd64-generic'
make[1]: *** [default] Fout 2
make[1]: Leaving directory `/home/anne/ndiswrapper-1.0rc4/driver'
make: *** [all] Fout 2


Does someone know what I do wrong?

---

### Post by Psy on 2005-01-23
You have to install the gcc package first with the command 'sudo apt-get install gcc'.

---

### Post by blinksilver on 2005-01-23
thanks for the reply, yeah i figured it out,  finally figuring out what the heck the error messages mean, lol, anyway, 

I have a question, everytime your computer turns on does your wireless get set to static IP and the network your on get reset???, It keeps happening to me,

also how is your battery life, mine went down from like 3:20 minutes in minimal mode in windows to 2:20 in minimal mode in linux, what is with the discrepency???

---

### Post by Psy on 2005-01-23
I have no such problems with my wireless card.
I recommend configuring the card with the gnome system utility 'Networking' found in the Computer -> System Tools menu. If the card isn't listed click Add, and follow the instructions (the driver must be loaded first).

---

### Post by blinksilver on 2005-01-23
I am using that networking program, but every time i turn i on my PC i have to into that applet, choose my lan Wlan card, hit properties, then couse a network  and change Static IP to DHCP, its really annoying.

---

### Post by hitch on 2005-01-29
I'm having problems with rc4 - everything compiles alright, but when I try to load the module, I get "FATAL: Error inserting ndiswrapper (/lib/modules/2.6.8-9-amd64-k8/misc/ndiswrapper.ko): Invalid module format"

Any suggestions?

---

### Post by blinksilver on 2005-02-06
sorry for the delay, been waiting for array 4 to hit so i can give a try, as for you , make sure your header files match,  i don't see why the woudn't, but check, the rc4, spinlock implementation is a bit (and by a bit i mean alot,) buggy, so try the 1.o which actually came out the day you made this post, also what drivers are you trying to wrap?? some drivers will just refuse, ndis is good, its not perfect,

oh this maybe silly, but did you do a 
> ndiswrapper -i XXXXX.inf 
before trying to modprobe them in

---

### Post by Psijudge on 2005-03-04
Hi, I am a new user to Hoary and I am trying to get the NDIS Wrapper installed as well, but I am having problems with installing the Kernel Source required, where do I get it from? I am currently running, 2.6.10-3-amd64-generic. When ever i do APT-GET for the Linux-sourece-2.6.10-3-amd64-generic , it can't find it. 

Thanks.

---

### Post by blinksilver on 2005-03-04
okay no big deal, alot of new user to debian find apt-get a little less then user friendly, so don't worry.

my solution is try syanptic, search the gnome menus you will find it, and use the search function to find two things build-essentials and kernel header (searching headers will do, make sure you get the right version, same as your kernel) install them and you should be set to complie

have fun

oh as a side not if you are going to comple them make sure you use either 1.0 or 1.1rc4, most other version fail for me and cause a kernel panic

---

### Post by Psijudge on 2005-03-04
Thanks for your help.

I searched Synaptic and I couldn't fing the Kernel source of header for the version of my linux core, 2.6.10-3-amd64-generic. I could find then for 2.6.9 and below...

This frustrating.. not that it would stop me from hammering it out...  :mrgreen: 

Any other suggestions?

---

### Post by blinksilver on 2005-03-04
i know its in there, i have them installed, make sure you into the respoitores and turn on select the bottom two and check all the boxes for both then do an update, i will put like 1000 dollar that they are there,

---

### Post by kubla on 2005-03-05
[QUOTE=Psijudge]Thanks for your help.

I searched Synaptic and I couldn't fing the Kernel source of header for the version of my linux core, 2.6.10-3-amd64-generic. I could find then for 2.6.9 and below...

This frustrating.. not that it would stop me from hammering it out...  :mrgreen: 

Any other suggestions?[/QUOTE]

psijudge: sometimes the graphical interface isn't the best for finding or doing things quickly. Try this from a shell:

sudo apt-get update

sudo apt-cache search amd64-generic

The first result:

linux-headers-2.6.10-4-amd64-generic - Linux kernel headers 2.6.10 on x86_64

and the third result:

linux-image-2.6.10-4-amd64-generic - Linux kernel image for version 2.6.10 on x86_64.

You could then simply do: 

sudo apt-get install linux-image-2.6.10-4-amd64-generic linux-headers-2.6.10-4-amd64-generic

Good luck!

Ian

---

### Post by BjoernVDM on 2005-03-07
Hi, since this thread helped me a lot, I just wanted to let people know that I got my broadcom wlan working in my emachines 6805.

All konsole commands of course in root shell.

0. checked that wireless-tools are installed in synaptic
1. got the broadcom *.inf from linuxant
2. got ndiswrapper source from sourceforge
3. installed newest kernel and headers:
 3.1 apt-get update
 3.2 apt-cache search amd64-k8
 3.3 apt-get install linux-image-2.6.11-1-amd64-k8 linux-headers-2.6.11-1-amd64-k8
4. reboot into new kernel
5. install GCC using synaptic
6. untar, unzip ndiswrapper, change into ndiswrapper directory, make, make install
7. ndiswrapper -i netbc564.inf 
8. ndiswrapper -l
9. modprobe ndiswrapper
10. check if wlan is activated (blue "e" on laptop, otherwise press Fn+F2)
11. iwlist wlan0 scan 
12. use network config from System menu, enter SSID and key, activate interface
14. deactivate Ethernet
13. ping [www.google.com](www.google.com) - yay!
14. ndiswrapper -m


Worked great. Thanks again to all the posters in the thread.

Cheers, B.

---

### Post by yippy on 2005-03-08
By the way, the most recent package from apt-get source ndiswrapper is ndiswrapper-0.12+1.0rc2, and it will not work for me.  It will compile and add the driver, but modprobe fails.  However the old version, ndiswrapper-1.0, does work.  I recommend if the new one fails to download it from sourceforge, or just start from sourceforge and do it right :)

Joejoejoe

---

### Post by Psijudge on 2005-03-09
Thanks for the help.

I have upgraded the kernel and downloaded the source and header. I tried to run make and I get the following error

```
make -C driver
make[1]: Entering directory `/home/psijudge/My Downloads/ndiswrapper-1.1rc4/driver'
Can't find kernel sources in /lib/modules/2.6.11-1-amd64-generic/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/psijudge/My Downloads/ndiswrapper-1.1rc4/driver'
make: *** [all] Error 2
``` 

Any other suggestions?

---

### Post by ortizeg on 2005-09-17
Okay...I think I've run through all of the steps.

I typed:
ndiswrapper -l

The output is:
Installed ndis drivers:
netbc564                driver present, hardware present

However, in the Network Settings (System > Administration > Networking Men) my device does not show up.  Any suggestion as to what's wrong?

Thanks,
Enrique

---

### Post by boobytrapped on 2005-10-10
[QUOTE=ortizeg]Okay...I think I've run through all of the steps.

I typed:
ndiswrapper -l

The output is:
Installed ndis drivers:
netbc564                driver present, hardware present

However, in the Network Settings (System > Administration > Networking Men) my device does not show up.  Any suggestion as to what's wrong?

Thanks,
Enrique[/QUOTE]

Make sure that you have the ndiswrapper module loaded (run 'sudo modprobe ndiswrapper')

---

### Post by Protostar on 2005-10-12
> **Psijudge]Thanks for the help.

I have upgraded the kernel and downloaded the source and header. I tried to run make and I get the following error

```
make -C driver
make[1]: Entering directory `/home/psijudge/My Downloads/ndiswrapper-1.1rc4/driver'
Can't find kernel sources in /lib/modules/2.6.11-1-amd64-generic/build said:**
> : *** [prereq_check] Error 1
make[1]: Leaving directory `/home/psijudge/My Downloads/ndiswrapper-1.1rc4/driver'
make: *** [all] Error 2
``` 
 
Any other suggestions?

That's the same error I got. Hopefully someone will have an answer though. :KS

---

