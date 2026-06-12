---
title: "X86_64 NIC Bonding"
date: 2008-07-21
forum: x86 64-bit Users
---

### Post by andyd34 on 2008-07-21
I know its a question that's prbably being asked a thousand times before but here is my scenario anyway.

I ordered the Ubuntu 8.04 Desktop CD and loaded it on a box I want to use as a gateway for my network to access the internet. The box has an MSI motherboard with onboard NIC (Realtek) also install are 3 other NIC's 2 more realtek and an Intel NIC. Here is what I am hoping to achieve. 

***Ignore the pfsense as I couldn't get it to load this is the gateway***


[img]http://www.awksdesigns.com/images/mysetup1.jpg[/img]


I have searched the internet but can only find a write up on the howtoforge website which shows how to bond IC's in Ubuntu 6.10. Sadly this doesn't with on Ubuntu 8.04 because when you reboot the system you cannot access the internet through bond0 also the 3 Internet NIC's do not have static IP addresses.

Can someone please help because I am fast running out of options

---

### Post by inphektion on 2008-07-22
I followed [this.]("http://www.astroshapes.com/information-technology/blog/archives/21-port-bonding-with-linux-ubuntu-server.html?/archives/21-port-bonding-with-linux-ubuntu-server.html")
Except I use mode=4 cause I have cisco switches.  Chose the mode that works best for your needs.

---

### Post by andyd34 on 2008-07-22
Thank you for your suggestion but sadly it didn't work. 

I added the following to /etc/modprobe.d/arch/x86_64

> alias bond0 bonding
options bond0 mode=5 miimon=100 max_bonds=5

I added the following to /etc/network/interfaces
> 
auto bond0
iface bond0 inet dhcp

up /sbin/ifenslave bond0 eth0 eth2 eth3
down /sbin/ifenslave -d bond0 eth0 eth2 eth3

As you can see bond0 has to be dynamic as the ip address for my modems are assigned by my ISP, I think this is where I am having the trouble getting it to work.

eth1 is my LAN NIC card just in case your wondering

---

### Post by inphektion on 2008-07-22
so is bond0 not getting an IP? or it is and just not routing to the internet correctly?

---

### Post by andyd34 on 2008-07-22
Its not doing anything and in Network Tools its saying unknown device. I know its not the cards because I've had it working in Widndows using WinGate and InterGate but I am trying to get away from the Microsoft OS's

---

### Post by inphektion on 2008-07-23
Oh right i forgot you were using a GUI.  I've had the gui net manager step on my toes before.  if you run ifconfig do you see your interfaces?  can you stop that network manager from running?  I've never done bond on desktop OS so not sure if it is messing it up.  Just did it in non gui server os.

---

### Post by andyd34 on 2008-07-24
I am totallty new to Ubuntu but do have a little experience with programming. If someone can point me to the right reading I would like to see if I can create a work around myself.

I also have a basic knowledge of networking. I understand that anything transfered via a network is btoken down into packets, and are transfers as dots and dashes through the network cable (Digital). Packets are sent through one wire and recieved through the other. What I need to do is route each packet sequentially to a different NIC.

---

