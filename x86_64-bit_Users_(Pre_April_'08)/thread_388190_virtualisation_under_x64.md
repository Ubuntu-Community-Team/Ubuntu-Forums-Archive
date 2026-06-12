---
title: "virtualisation under x64"
date: 2007-03-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by nicolasdiogo on 2007-03-19
hi,

i am looking for a virtulisation application that would allow me to run virtual machines on top of ubuntu 6.10 desktop x64.
the hardware:
AMD x64 X2 4400+ L1
2gb DDR

i would like to find an Open source solution instead of VmWare if possible.
However, i would require to run Windows 32 and x64.

if someone with experience on this could share their experience, it would save me and others a lot of trial and error.

Many thanks for your assistance.

Nicolas

---

### Post by alamba on 2007-03-19
xen might be one option.

---

### Post by Kilz on 2007-03-19
> **nicolasdiogo said:**
> hi,

i am looking for a virtulisation application that would allow me to run virtual machines on top of ubuntu 6.10 desktop x64.
the hardware:
AMD x64 X2 4400+ L1
2gb DDR

i would like to find an Open source solution instead of VmWare if possible.
However, i would require to run Windows 32 and x64.

if someone with experience on this could share their experience, it would save me and others a lot of trial and error.

Many thanks for your assistance.

Nicolas

If you are looking at open source because of cost concerns be aware that the vmware server is free as in beer.

---

### Post by nicolasdiogo on 2007-03-19
thanks for your replies.

i am aware that VmWare is available for free for private use but i would like to seek other alternatives.
has anyone used vserver?

Nicolas

---

### Post by in_flu_ence on 2007-03-19
I am not sure if Virtualbox is opensource (I think it is) but it has been pretty popular in the ubuntu community.

If you ask me, I prefer vmware for its stability. I run my winXP under Ubuntu64 and even use it to do some simple simulation work. Very stable. Turn it on for days without much effect on the performance. Installation is fairly easy especially if you are not using a wireless network.

I think vmware has its name for virtualisation and I do have my confidence in it if you need stability. Better support for my cheap monitors as well.

Xen might be ok but abit of a learning curve for a lazy bum like me. I have not tested its performance so I don't put empty comments on it.

---

### Post by Quicksand on 2007-03-19
KVM ([http://kvm.qumranet.com/kvmwiki]("http://kvm.qumranet.com/kvmwiki")) works remarkably well and the kernel-module portion of it is integrated into kernel 2.6.20+.

But even without that bleeding-edge kernel, you can compile it yourself and install and run it very easily.  I'm running Windows XP on Edgy x64 myself, and it runs pretty well (I/O isn't super-fast, but it has been acceptable so far).

One advantage KVM has over Xen is that Xen guest operating systems (domU's, they call them) are limited to the same bitness (32 bit or 64 bit) as the host.  KVM doesn't have that limitation -- as I mentioned, I'm running 32-bit XP on 64-bit Linux.

I don't know how well 64-bit Windows runs or if it runs at all, but you could give it a shot.  If you don't like it, uninstall it!

Some simple instructions for compiling and installing KVM are here: [http://popey.com/Compiling_kvm_Under_Ubuntu_Edgy_i386]("http://popey.com/Compiling_kvm_Under_Ubuntu_Edgy_i386")

The HOWTO is for x86, but the procedure is the same for x64.  Because you have AMD instead of the author's Intel, look for the "svm" flag instead of "vmx".  Off the top of my head I'm not sure if your X2 4400 necessarily supports AMD hardware virtualization, so confirm that before you install anything.  KVM absolutely requires hardware virtualization support.

Read down into the comments on that page, and you'll note that someone observed you have to perform a "sudo modprobe kvm-amd" before you can run KVM; that has been my experience as well.

If it's working well for you, you can add the kvm-amd module to /etc/modules so it auto-loads.  And when you run KVM, you'll need to sudo it.

Good luck!

---

### Post by vargasman on 2007-03-19
> **in_flu_ence said:**
> I am not sure if Virtualbox is opensource (I think it is) but it has been pretty popular in the ubuntu community

Virtualbox is GPL'd but won't install on a 64bit system. Here's a quote from the top of the [FAQ]("http://www.virtualbox.org/wiki/User_FAQ") page.


> VirtualBox does not yet support 64-bit hosts. This is actively being worked on. (And no, you can't install the 32-bit version on a 64-bit host.) 

As for vmware, it's working great for me. I would suggest that you atleast try it to see if it meets your needs.

---

### Post by in_flu_ence on 2007-03-20
I didn't realise VirtualBox doesn't install in a 64bit host or i should say 64bit OS. Maybe when I was trying it some time back, I was still using 32bit ubuntu on my 64bit box.

Anyway, Vmware doesn't have such issue and works great.

---

### Post by noen on 2007-03-20
What is the performance like VMWare vs Xen?

I'm very hesitant to try because I really need the fastest possible performance I can get when I render. I have read and read, seems to me like it's just not a good idea for me.

---

### Post by flipybcn on 2007-03-21
> **vargasman said:**
> Virtualbox is GPL'd but won't install on a 64bit system. Here's a quote from the top of the [FAQ]("http://www.virtualbox.org/wiki/User_FAQ") page.




As for vmware, it's working great for me. I would suggest that you atleast try it to see if it meets your needs.

would it be possible to chroot the x86 version of the VirtualBox?
BTW, any good tutorial for xen?
I've tried qemu with kqemu, but it crashes a lot, and it's very slow.
In another computer I've VirtualBox and it works like it wasn't a hosted workstation.
And, VMWare, what's the point to make images to run? AFAIK, Ubuntu just have the Player version...

---

### Post by vargasman on 2007-03-22
I wouldn't know about chrooting Virtualbox, i've never tried. As for a good XEN howto, here's a [link to the ubuntu wiki for Xen on edgy.]("https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuEdgy?highlight=%28xen%29") As for VMWare, I use the server edition. It can make it's own images to run. You can downlaod it from [here.]("http://www.vmware.com/download/server/") They have tons of prebuilt enivorments to test or you can make your own. I made one from an edgy iso.

---

### Post by mjhb on 2007-03-22
A new how to was posted for Feisty using Qemu [https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo")  it also has a tip for 64bit users.

---

### Post by DKwhite on 2007-03-22
> **noen said:**
> What is the performance like VMWare vs Xen?

I'm very hesitant to try because I really need the fastest possible performance I can get when I render. I have read and read, seems to me like it's just not a good idea for me.

If you need to render in a Microsoft environment then a Dual Boot will be your best option.

---

### Post by mkgs on 2007-03-22
I'm planning to install Windows Vista ultimate edition(32 bit version) on Ubuntu Feisty 64bit version (after its release). VMware server seems to support this combination. Does anybody tried this before? Or anybody see problems with this combination ?

My Hardware - ASUS P5B-E, Core2Duo E6600, 2GB Memory, WD 250GB

Thanks for your help. Please let me know if this is not the right place to ask this question.

---

### Post by flipybcn on 2007-03-23
> **mjhb said:**
> A new how to was posted for Feisty using Qemu [https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo")  it also has a tip for 64bit users.

I've tried this one, but it keeps crashing a lot when the kqemu kernel module is loaded...

I'll try vmware server and xen, since I'm not sure how to chroot under a x86 enviorentment a virtualbox installation.

> **mkgs said:**
>  	I'm planning to install Windows Vista ultimate edition(32 bit version) on Ubuntu Feisty 64bit version (after its release). VMware server seems to support this combination. Does anybody tried this before? Or anybody see problems with this combination ?

My Hardware - ASUS P5B-E, Core2Duo E6600, 2GB Memory, WD 250GB

Thanks for your help. Please let me know if this is not the right place to ask this question.
I'm pretty sure that a core2duo supports virtualistation, so take a close look to the [KVM]("https://help.ubuntu.com/community/KVM")

---

### Post by nicolasdiogo on 2007-03-26
thanks folks,

i am interested in the KVM alternative, but i am confused with the hardware requirement.
my CPU is am AMD x2, see below my cpuinfo:

i tried to check for VT support and it does seem to support any.

i used the following command as explained at [http://kvm.qumranet.com/kvmwiki/FAQ?highlight=%28amd%29]("http://kvm.qumranet.com/kvmwiki/FAQ?highlight=%28amd%29")

egrep '^flags.*(vmx|svm)' /proc/cpuinfo

it is mentioned that maybe VT support has been disabled by the bios, and i believe that to be the case since it is listed here as supporting VT here:

[http://wiki.xensource.com/xenwiki/HVM_Compatible_Processors](http://wiki.xensource.com/xenwiki/HVM_Compatible_Processors)


thus i think i have a problem with my motherboard/BIOS disabling VT.

i would appreciate your views.

Many thanks,

Nicolas



#######################################################
> sudo cat < /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 35
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
stepping	: 2
cpu MHz		: 1000.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm cmp_legacy
bogomips	: 2011.82
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 35
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
stepping	: 2
cpu MHz		: 1000.000
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm cmp_legacy
bogomips	: 2011.82
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp

---

### Post by Quicksand on 2007-03-26
I think the "stepping: 2" entry in your cpuinfo suggests you have a relatively new socket-AM2 processor -- can you confirm?  If so, then it is almost certainly a BIOS issue.

Maybe someone more knowledgeable than I can verify that.  It might help if you posted what motherboard you have, if you know.

I have an Intel system, so I'm afraid I can't be much more help on specific configuration issues.

(There is one thing I can suggest, though, assuming you make it past this issue: make sure you try kvm version 18, which came out yesterday, or newer.  Versions 15 through 17 contained a bug that caused it not to compile with Edgy's default kernel.)

---

### Post by Betelgeuse on 2007-03-27
> **noen said:**
> What is the performance like VMWare vs Xen?

I'm very hesitant to try because I really need the fastest possible performance I can get when I render. I have read and read, seems to me like it's just not a good idea for me.

I'm using free (free as in free beer) vmware server on my web server. it's running 24/7 in ISP's datacenter and I did not have to go and see my server. it's running vmware server and have 4 virtual machines, 3 windows 2000 servers and one ubuntu 6.10 server edition and all working without problems. without vmware, I would need 4 seperate machines and pay 4 times to the ISP fo co-location service. Now I have one machine and 4 virtual machines and it's running 15 web sites with 5000 users avarega a day and e-mail service for 100 mailboxes. all is running fine except the host system running windows 2000. I'm planning to install ubuntu server 6.06 as host system but do not have time and courage to do something to a running system. 

wmware is good and ahead of all other solutions. I wish they GPL'ed their vmware server software but it's only a dream for now.

---

