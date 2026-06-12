---
title: "No NIC detected and cant add manually"
date: 2005-09-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by flurdy on 2005-09-27
Bit embarresed to ask for help about this, as it something I should know, but here goes:

Ive installed the ubuntu server image of AMD64 Hoary on a celeron 64bit pc.
Install was fine and the machine is up and running, except:

The nic could not be detected during install.

The onboard network card this machine has is a gigabit intel pro, and thus the e1000 module is appropiate. The module is available, so it should be easy to add manually. This is were I get stuck, I probably cant see the forest for the trees.

I am not next to the machine now, so this is mostly off memory. But I will confirm everything later when I roll into the office.

  ifconfig
diplays that only the local interface is available
  modprobe e1000
is fine followed by
  lsmod | grep e1000
which confirms the module has been loaded by the kernel.
However the next step dont work:
  alias eth0 e1000
responds that eth0 and e1000 is unknown.
therefore this wont work either
  ifconfig eth0 blah blah

Any ideas? where to I specify to the system what eth0 is, in modutils?

Intel do have a download of the linux driver for the mobo, however it is dated march 05 and i presume the version of e1000 in ubuntu is the same version.

---

### Post by tonym on 2005-09-27
First,  add e1000 to /etc/modules to get the module loaded at boot up.

Then you need to add to /etc/network/interfaces

See "man interfaces" to get info on this file.

Regards

Tony

---

### Post by flurdy on 2005-09-27
Ah, didnt think that the map commands etc in interfaces would state what eth0 is. but that makes sense i suppose.

hadnt bothered with the interfaces file yet, as i though i need to get the system to recognise eth0 first, before i specified ip/dhcp etc. 

So I dont need to alias eth0 to e1000 anywhere then?

---

### Post by flurdy on 2005-09-27
No , think i need to do another step
This is my interfaces file

auto lo
iface lo inet loopback

mapping hotplug
        script grep
        map eth0

iface eth0 inet dhcp

auto eth0

however (post reboots etc) if I ifconfig eth0 or ifup eth0
the reply is no such device.
but lsmod | grep e1000 says e1000 is loaded. but i fail to see where i specify eth0 is e1000?

any more suggestions?
it could be the system and mobo just dont like each other, however i think imcompetance from me is more likely.

---

### Post by tonym on 2005-09-27
Can't help further I'm afraid.  Normally if you load the correct driver eth0 becomes active and networking works.  Looks as if there is a problem with the driver not matching your motherboard.

---

### Post by flurdy on 2005-09-30
Well this [Linux Test]("http://www.linux-tested.com/results/asus_P5LD2-VM.html") confirms that linux will work with this mobo(Asus P5LD2-VM). However it also states that the network card was not detected and needed downloading of the latest drivers.

It doesnt help that although the included cd comes with linux drivers, but they are Marvell ones, so I spendt a day testing to see if sk98lin is the driver I should load. But it seems the deluxe card uses the Marvell chipset, not the VM one.

So I have downloaded the latest e1000 driver of the Intel site. But since I have installed is the server image of ubuntu, compiling the driver is a pain. It complains about not being able to write to /var/cache due to catman mode !?!? 

Think Ill slap the whole ubuntu base system on, so that I have all the environment set up as normal, and then see if I can compile and install the module.

---

