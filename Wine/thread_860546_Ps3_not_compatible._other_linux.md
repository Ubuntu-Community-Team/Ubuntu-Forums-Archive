---
title: "Ps3 not compatible. other linux?"
date: 2008-07-15
forum: Wine
---

### Post by hoagtech on 2008-07-15
I was wondering id anyone with a ps3 has found a wine program to run off of x86 proccessors. I know there not compatable with ubuntu 7.10 ppc edition, but are there other linuxes that might be able to handle wine. That i could run on my ps3. Thanks in advance.

---

### Post by hoagtech on 2008-07-16
Does no one know what im talking about when im i say im using on a ps3? I cant be the only one here using ubuntu on the ps3? does anyone know cool stuff to try like emulators and such that run on x86 processors (specifically ps3?) thanks again

---

### Post by Steveway on 2008-07-16
Since you are running another processor-architecture you need a virtual-machine that simulates a x86 pc.
You should try looking if virtualbox, qemu or vmware is avaiable for your architecture.

---

### Post by ReFuSeD88 on 2008-07-16
hehe, yeah try that! :lolflag:

---

### Post by Drk Guy on 2008-07-16
Wine can run on any architecture, but you have to compile off by hand, just do this:
sudo apt-get build-depend wine
mkdir wine
cd wine
apt-get source wine # This will download wine's source and patch it with ubuntu-specific stuff, you can patch it with 3DMark as you wish
ls # This will list all dirs, cd to the wine's dir
cd wine-1.1.1 # Assuming the source is in there
debuild # Compile a DEB
This last command will generate a DEB, if everything goes fine, just double-click it and enjoy ;)

---

### Post by hoagtech on 2008-07-17
Ok thanks for all the suggestions. Im theinking of trying qemu, because ive heard good things about it from the youtube community. Evry one there has it running off od yellow dog though but im not sure if that will amke a difference. Im dedicated to ubuntu because it is much faster and has a gui that im getting more and more familiar with. Is there anyone else here who has tried something similar? Im sure with enough heads together we could do some pretty cool stuff with this expensive machine.

---

### Post by h4mx0r on 2008-07-18
well wine won't work with the ppc64 cpu because it processes differently however you can use qemu. A hack I've been wanting to try out is that you might even be able to use a wrapper between wine and qemu to transition the processor calls but you'll need a sandboxed 32 bit environment like how some 64bit kernel people do. That way you won't be running a secondary OS in memory just translating wine calls to ppc64.

---

### Post by articpenguin on 2008-07-19
what arch is ps3? Is it new since its a cell processor?

---

### Post by Steveway on 2008-07-19
> **articpenguin said:**
> what arch is ps3? Is it new since its a cell processor?

AFAIK, Linux on the PS3 doesn't really use the Cell-processor but it instead uses the co-ppc-processors.
So he uses basically a ppc.

---

### Post by wu-stix on 2008-08-22
I thought yellow dog is supposed to use the cell processor.

---

