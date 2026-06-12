---
title: "So many threads on &quot;minimum ubuntu installs&quot;, help?"
date: 2009-08-10
forum: x86 64-bit Users
---

### Post by binskipy2u on 2009-08-10
there's many threads on minimal ubuntu installs.. ie: using the 11mg iso to install basics , then add what you want for a truely streamlined system..
my question(s) are.. does someone have an updated be all , end all how-to to install and setup a minimum ubuntu setup? with screenshots or command line instructions?

I'm sorry if i'm rehashing a subject with multiple threads.. but just wondering if someone put them all together , with updated info, or knows a better way then all the rest..

thanks for any help, information

---

### Post by kerry_s on 2009-08-10
minimal is really easy, just grab that mini.iso & install the base:
[http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-amd64/current/images/netboot/mini.iso)

then just install enough to get you into the gui:
**sudo apt-get install xorg gdm synaptic your-wm-or-de**

"sudo apt-get install xorg gdm synaptic" is actually enough to get you into the gui failsafe terminal, where you can use synaptic to get what you want, most of us already know what window manager or desktop we want, so it's easier just to work in there.
for example on mine i do:
**sudo apt-get install xorg gdm synaptic xfce4 mousepad iceweasel**

cause i know thats already what i want to use.
so as long as you know what wm/de you want the rest can be installed from there.

say your doing a mini gnome:
sudo apt-get install xorg gdm gnome-core synaptic

is enough to give you a desktop, you just open synaptic an select whatever else you want.

---

### Post by snowpine on 2009-08-10
Here is another good one: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

But no, there is no "be all, end all" tutorial on the subject, because there are millions of different ways to customize your own minimal install... :)

---

### Post by binskipy2u on 2009-08-10
say your doing a mini gnome:
sudo apt-get install xorg gdm gnome-core synaptic
**************

is there one more thing to add so i have a log in screen? so i dont have to type startx every time?

also, I have a printer mp210 i have to force install (using 64bit) the 32bit drivers for.. will the gnome core have "cups" or do i just search for CUPS in synaptic and itll give me all i need?
thanks

---

### Post by kerry_s on 2009-08-10
> **binskipy2u said:**
> say your doing a mini gnome:
sudo apt-get install xorg gdm gnome-core synaptic
**************

is there one more thing to add so i have a log in screen? so i dont have to type startx every time?

also, I have a printer mp210 i have to force install (using 64bit) the 32bit drivers for.. will the gnome core have "cups" or do i just search for CUPS in synaptic and itll give me all i need?
thanks

"gdm" is the log in screen. once you do this:
**sudo apt-get install xorg gdm gnome-core synaptic**
you just reboot(ctrl+alt+delete) & you'll be at the gdm log in screen just like a normal install.

no, you'll have install what you want.

---

