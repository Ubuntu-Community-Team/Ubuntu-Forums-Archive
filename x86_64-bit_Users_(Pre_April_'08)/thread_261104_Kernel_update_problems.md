---
title: "Kernel update problems??"
date: 2006-09-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrw on 2006-09-19
My Kernel was just updated and now vmware won't run. Anyone else faced with this problem. Any solutions to suggest. This is really a bummer unless I can recover.

---

### Post by fr175 on 2006-09-19
Confirmed.  I also updated the kernel, and now cannot load into VMWare Server.  The programs starts to load, but shuts down after a couple seconds.

---

### Post by kuja on 2006-09-19
A part of the vmware configuration process is that kernel modules are built. A kernel upgrade would break those modules, so you have to rebuild them every single upgrade. I'll stop back later to tell you how, as my system is quite broken at the moment. (Using Knoppix for now)

---

### Post by mrw on 2006-09-20
I reinstalled vmware and it worked until I rebooted then I had the same problem again. It also made no difference booting from the earlier kernel version on Grub -- how come?

---

### Post by chrisccoulson on 2006-09-20
You shouldn't need to re-install vmware. Just re-run vmware-config.pl. I'm not sure why it still doesn't work for you though. i'll try it on mine later when I finish work.

---

### Post by mrw on 2006-09-20
We need the c-header files for the new kernel = where do we get that???

---

### Post by kick6 on 2006-09-20
there should be a package for them in aptitude/synaptics

```
apt-get install linux-headers-2.6.15-27-amd64-generic
```


or

```
apt-get install linux-headers-2.6.15-27-amd64-k8
```

depending on which kernel you are using.  If you're not sure do a 
```
 uname -r
``` first

---

### Post by mrw on 2006-09-20
When I run uname -r
I get:
2.6.15-27-amd64-generic

When I run sudo apt-get install 2.6.15-27-amd64-generic

I get: Couldn't find package 2.6.15-27-amd64-generic

Where do I go from here?

---

### Post by mrw on 2006-09-20
Sorry I see the typo.

---

### Post by stephensheppard on 2006-09-20
On the previous kernel upgrade I had to rebuild/reconfigure vmware. After running vmware-config.pl it ran just fine, and my previously setup virtual machines all ran as before.

I haven't installed the new (today) kernel updates for 2.6.15-27. Given the problems from the last update and my work needs I thought I would give it a day. I have two questions:

1. My "software updates" shows BOTH linux-image-2.6.15-27-amd64-generic and linux-image-2.6.15-27-amd64-k8. I am running the latter kernel, which I installed in quest of performance improvement to take advantage of my dual processor, dual-core Dell machine (Intel). Do I need to install all of these updates, or only the k8?

2. Is this a bug? In the software update dialog if I try to uncheck the kernel upgrades (to only install the gzip and libgnutls12 upgrades) I am autmatically logged off and returned to the signon screen. Surely that cannot be normal?

Advice?

---

### Post by mrw on 2006-09-20
The trick to getting vmware up was installing the new header C files by doing a sudo-apt-get install linux-headers-your version
mine was 2.6.15-27-amd64-generic.

Along the way however I've lost my network bridge. Vmware gives me the following warning:

The network bridge on device /dev/vmnet0 is temporarily down because the bridged Ethernet interface is down.  The virtual machine may not be able to communicate with the host or with other machines on your network.

Any ideas on how to correct this?

---

### Post by fr175 on 2006-09-21
Just wanted to say thanks for the tip on running the config to get this working again.  I didn't have to get the headers since I already had them (perhaps from the video card driver install), and I didn't lose my network bridge like mrw did, so I can't help with that problem.

Thanks again.

---

