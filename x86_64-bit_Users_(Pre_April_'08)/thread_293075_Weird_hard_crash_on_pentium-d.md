---
title: "Weird hard crash on pentium-d"
date: 2006-11-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by bongoboi on 2006-11-04
Hi all,

I just got myself a new spiffy pentium-d 64 bit box a couple of weeks ago and i'm running into really annoying issues. For some reason, after i leave the comp running unattended for a few hours, it will hang hard, total lockup, and won't respond unless i turn it off... There are no error messages or panics in the log, the log just ends abruptly at the time the crash happens.

Since it's a new box assembled from components, I went step-by-step to locate the problem: I've ran memtest overnight, checked the disks, visual inspection of cpu+mobo for scratches/loose screws, thermal monitoring of cpu, bla bla. Long story short, I'm pretty confident the hardware's ok, my best evidence being that the hang won't happen when i leave the computer running windows xp for long hours ;)

So, i have now started to consider that something's borked in the software side of things. The mobo is a Gigabyte GA-8N-Sli Pro which comes with nvidia nforce4 chipset. I've done some googling and found no relevant links about similar problems with that mobo/chipset. I've also tried booting with kernel options noapic, nolapic and acpi=off and nomce but the problem persists.

Can someone give some advice on this? is there some known incompatibility with the nvidia chipset? I'm going nuts about this...

Boring system info dump follows, and output of dmesg is attached as dmesg.txt. Thanks in advance

-----

Distro:  edgy 
cpu:     pentium-d dual core 64bit 3.0GHz
mobo:    Gigabyte GA-8N-SLI Pro
chipset: NVidia Nforce4
mem:     1GB Kingston DDR2 533MHz
vcard:   NVidia Geforce 6600GS 256MB PCI-Express
hdd:     3x200GB Seagate SATA 7200RPM

---

### Post by hvidgaard on 2006-11-05
I have a similar issue, and found that disabling the screensaver have stopped the locks from happening :)

My hardware is similar to yours except that I have an Intel chipset...

---

### Post by confusimo on 2006-11-05
I have an ECS 915P-A v1.2 and Celeorn D 3.06 ghz and no issues so far.  At least no freezing or anything.

Thanks,
Confusimo

---

### Post by autocrosser on 2006-11-05
I was having something like that with my Pent-D 840--2G ram & a Asus P5P800-SE board--The system would crash in the middle of the night--had SETI running--Thunderbird--Gnome-PPP--downloading updates. No log info--nothing--I started looking like you at everything hardware I could--software too.... My problem was a slow thermal creep over 4/5 hrs with cpus at full load--The 840 seems to hard-lock with the curent kernel at about 120degrees core temp--changed my cooling system & got the core down to 105 average temp & no more lock-ups--best info I can do--are you running a 830 or a 930?

---

### Post by bongoboi on 2006-11-06
Hi all,

thanks for the advice. I have now disabled the screensaver and am leaving for work in a while, will leave the box running and check at night...

@autocrosser: Not sure what my cpu exact model is... dump of my /proc/cpuinfo if that helps:
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 6
model name      :               Intel(R) Pentium(R) D CPU 3.00GHz
stepping        : 2
cpu MHz         : 3013.008
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx cid cx16 xtpr lahf_lm
bogomips        : 6030.77
clflush size    : 64
cache_alignment : 128
address sizes   : 36 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 6
model name      :               Intel(R) Pentium(R) D CPU 3.00GHz
stepping        : 2
cpu MHz         : 3013.008
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 6
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx lm constant_tsc pni monitor ds_cpl vmx cid cx16 xtpr lahf_lm
bogomips        : 6026.50
clflush size    : 64
cache_alignment : 128
address sizes   : 36 bits physical, 48 bits virtual
power management:

---

### Post by bongoboi on 2006-11-06
just for the record, let me add that i just woke up and found the box crashed as usual, but with a difference: this time i left it with the console visible (ctrl+alt+f1) instead of X. And alas, I found a kernel panic had happened somewhere in the night. 

Pity is that since the box was locked for good i couldn't scroll up or use the mouse to cut'n'paste, but the final lines of the dump were something like this (quickly written down to paper as i have my coffee):

tcp_v4_rcv
ret_from_intr
ip_rcv
netif_receive_skfo
net_rx_action
call_softirq
do_IRQ
cpu_idle
_sinittext

Kernel Panic: Oops, not syncing
<Something about IRQ timer here>

Hope that helps ](*,)

---

### Post by autocrosser on 2006-11-06
OK--I do have something you don't--I'm on ubuntu-develop-list & there has been a bit about a problem with Nvidia drivers causing hard lock-ups--I installed the "new" drivers & at the same time did the cooling mod--I'll post the Nvidia stuff for you--NOTE: if you have ANY problems with the new drivers--there is a open report on LaunchPad--Please report anything strange--this updates the drivers to 8776

In your /etc/apt/sources.list:
#Nvidia driver Testing
deb [http://people.ubuntu.com/~kees/test-lrm-2.6.17.6-1/](http://people.ubuntu.com/~kees/test-lrm-2.6.17.6-1/) ./

and do a sudo apt-get update/sudo apt-get upgrade

---

### Post by bongoboi on 2006-11-06
Yhanks for the help.

I just came back home from work and the box is still up, reporting 12 hours uptime. That's good news -- I left it running at the console and basically sitting idle, so i guess the problem is either nvidia driver-related or cpu-load (ie heating) related. 

Gonna try those drivers now, will keep you updated

Cheers :-D

---

### Post by bongoboi on 2006-11-06
BTW, i'm checking those nvidia packages and they seem to be linked against kernel 2.6.17.6-1, my current kernel is 2.6.17-10 and my nvidia-glx package is already 8776, should i really install those? do they have any specific bugfix not in the ubuntu official package?

---

### Post by autocrosser on 2006-11-06
The drivers will work with whatever kernel you are using--I'm with the -10 kernel also--they are slated to be released as a bug-fix as soon as the test period is over(note: if yours is 8776--you already have the "new" drivers)--Glad to see you box is better--what are you using to keep a eye on temp?? I have dual screens, so use Gkrellm with the lm-sensors package--the older how-to for lm-sensors works very well in Edgy.

---

### Post by bongoboi on 2006-11-06
I'm not using any software to monitor temp -- i set the BIOS to beep annoyingly past 70ºC... I'm currently booting with acpi, apic, and lapic turned off cause those are suspicious of crashing the kernel as well. Not that i really trust the bios, but anyway...

I haven't totally grokked your last post wrt nvidia drivers, you mean if i have 8776 then i don't need to install those other packages? or do those packages have some specific bugfix the upstream packages don't have?

---

### Post by autocrosser on 2006-11-06
The best I can say is to monitor the updates to see if there is a Nvidia driver update--I know we are moving to the 9xxx serives drivers as soon as they exit beta--you can still upgrade via the path I posted--I'm sure that there is some code in the "testing" drivers I'm using that has not made it to main, but I have not been notified of that yet.

As far as cpu temps--it looks like the 8xx Intel pent-D cpus like it as cold as possible--I know you have a 830 due to the cache report--2048= 1024 per cpu. The 9xx series had 4096= 2048 per cpu--the 830/840/845/50 series are good units--I'd say if you are running more that 50c--you're too hot.

---

### Post by bongoboi on 2006-11-07
$ uptime
 21:04:55 up 1 day, 13:19,  3 users,  load average: 0.00, 0.00, 0.00

:D 

Well, at least the box seems to not crash when on idle state -- i'll leave it downloading stuff with resource-hogging and cpu-intensive stuff overnight and see if it stands the load...

will keep you updated

---

### Post by autocrosser on 2006-11-11
So how is the box doing?? I just installed the non-beta Nvidia 9xxx series drivers & my erratic crash problems "seem" to have gone------They should show up in the repositories soon.....

---

