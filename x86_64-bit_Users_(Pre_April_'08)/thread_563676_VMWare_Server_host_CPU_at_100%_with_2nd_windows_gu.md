---
title: "VMWare Server host CPU at 100% with 2nd windows guest"
date: 2007-09-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by jharrop on 2007-09-30
Hi 

I'm running Ubuntu 7.04 x86_64 on Dell Precision Workstations 490 and 690.  Both boxes contain a single dual core Xeon.  

I'm running VMWare Server on both boxes.  1.0.2 and 1.0.4 respectively. 

I've found that things work fine with a single Windows XP Pro guest, but when I so much as start a second guest, host CPU utilisation immediately goes to 100% (and basically stays there)  and the guests become unresponsive.  

This happens on both boxes.  I've chosen to post to this forum since I suspect this problem is attributable to the X86_64 distribution.

Happily there is a workaround.  The workaround is to configure the Virtual machine settings to have 1 processor rather than 2.  CPU utilisation then reflects (the in my case very light) load, and the guests are easy to work with.

There are postings around to the effect that VMWare performs poorly on 7.04 (with its 2..6.20 kernel), [http://www.vmware.com/community/message.jspa?messageID=642486]("http://www.vmware.com/community/message.jspa?messageID=642486")
but I think this is a different issue.  

That post links to a bug report about disk write performance:  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/113532]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/113532")

Given the commonalities with this post [http://communities.vmware.com/thread/83605]("http://communities.vmware.com/thread/83605") 
:
- 2 windows guests
- Ubuntu 7.0.4 X86_64
- dual core CPU
- workaround
(even though their symptoms were with Workstation 6 beta)
I reckon it may be X86_64 distribution which is causing the problem here.  But I don't have a machine running 32-bit Feisty to see.

cheers

Jason

---

### Post by jpkotta on 2007-09-30
You should also make sure that the guests aren't using all of your RAM.  I think the default is 1/2 of total RAM is allocated to each guest, so when you run 2 ...

---

### Post by jharrop on 2007-09-30
Each VM is using 512MB RAM.  The machines have 3GB and 2GB respectively.  I don't think RAM is the problem.

It'd be good if others running VMWare on X86 64 could try starting 2 windows guests, and report results.  

thanks

Jason

---

### Post by Jouke74 on 2007-10-01
You indeed should assign one cpu per windows vm machine. Otherwise each windows assumes it has control over 2 cpu's. Windows will balance the load between the two virtual cpu's. Which it basically can't because your second virtual pc is doing the same. Your host system starts to balance 4 virtual cores (while each windows balances two) over two cpu's and that takes some calculation power, and probably causes a loop here and there.

This probably won't happen if you assign a single CPU to 4 virtual windows machines because there is no balancing in the virtual machines, each windows sees only one CPU. 
(Might also be a windows issue).

---

### Post by tribaal on 2007-10-01
Also make sure you have up-to-date VMware tools installed on your guest system, they help with CPU and disk access throttling.

Hope this helps

- trib'

---

### Post by veloce on 2007-10-01
> **Jouke74 said:**
> You indeed should assign one cpu per windows vm machine. Otherwise each windows assumes it has control over 2 cpu's. Windows will balance the load between the two virtual cpu's. Which it basically can't because your second virtual pc is doing the same. Your host system starts to balance 4 virtual cores (while each windows balances two) over two cpu's and that takes some calculation power, and probably causes a loop here and there.

This probably won't happen if you assign a single CPU to 4 virtual windows machines because there is no balancing in the virtual machines, each windows sees only one CPU. 
(Might also be a windows issue).

Jouke is right, the problem is in allowing a windows machine control of the smp.  Windows doesn't do smp well to start with.  On a vm it grabs both processors and doesn't let them go.

Try two ubuntu vms with dual processors and you'll see the difference.

---

### Post by kamermans on 2008-04-02
I also noticed this problem - I'm running ubuntu 7.10 server with vmware server 1.0.5 on a dual core Opteron system.  I have two Windows 2003 Server VMs (one Domain Controller and one Exchange Server).  When I have dual processors setup on the VMs and they both try to do something at the same time the CPU skyrockets to 100%.  I was able to get through an installation by suspending one VM and letting the other have the CPUs, then shutting it down and resuming the other VM.  Then I switched both VMs off and set them up with 1 processor each.  Now everything is running just fine. 

:)

Steve

---

