---
title: "VMWare Performance"
date: 2008-01-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by syyid on 2008-01-29
I've recently switched from 32bit to 64 bit ubuntu with my upgrade from 7.04 to 7.10. Besides finally being able to see/use all my memory (4GB+) I have an issue with VMWare. I transferred over the images I was using previously and the performance is now significantly slower. For example using a Centos 4 image (32bit) I frequently get points where the system freezes completely and it takes a few seconds to catch up and become responsive again (for example simply running ls on a large folder). 

I never experienced this on the 64bit version. Are there any settings I need to modify or any other reason that this could be happening?

Also on a related note, I don't think VMWare supports the SVM extensions? (AMD AM2 Dual core Cpu), couldn't find anything on their site to that effect. Is that correct? If not how do I verify if they are being used.

Thanks in advance for any help.

---

### Post by mwolfer1 on 2008-02-03
I had similar problems. What appeared to make a lot of difference was setting the subsequent parameters in the vmx file:


sched.mem.pshare.enable = "FALSE" 
mainMem.useNamedFile = "FALSE" 
MemTrimRate = "0" 
MemAllowAutoScaleDown = "TRUE"

Hope this helps, 

Martin

---

### Post by bhaverkamp on 2008-02-04
I started noticing this after I upgraded to th 2.6.22 kernels. Large IO loads try DDing a gigabyte within the VM. If your seeing what I am seeing the system load index will go very high (over 20). As soon as the IO settles and SLI drops below 10 things start to smooth out. I have not found anything that fixes this yet. I will try the above suggestions.

---

### Post by bhaverkamp on 2008-02-05
It does seem to do something. Where did you get this suggestion?

---

### Post by mwolfer1 on 2008-02-08
VMWare Knowledgebase if I recall correctly. It all started with me trying to put VMWare images on a USB drive (just for kicks and grins). It didn't work and I started reading up on it and stumbled over an interesting discussion on how VMWare handles memory. The suggestions came from that discussion, they mainly prevent disk IO when accessing memory.

Martin

---

### Post by dcstar on 2008-02-09
> **mwolfer1 said:**
> VMWare Knowledgebase if I recall correctly. It all started with me trying to put VMWare images on a USB drive (just for kicks and grins). It didn't work and I started reading up on it and stumbled over an interesting discussion on how VMWare handles memory. The suggestions came from that discussion, they mainly prevent disk IO when accessing memory.

Martin

It seems to improve the performance of my VMs (although I probably shouldn't have all 7 running simultaneously.......)

---

