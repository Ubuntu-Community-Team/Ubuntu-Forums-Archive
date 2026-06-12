---
title: "VirtualBox OSE"
date: 2008-04-25
forum: x86 64-bit Users
---

### Post by StrangeFreedom on 2008-04-25
I installed VirtualBox OSE and this is the error I get:

VirtualBox can't operate in VMX root mode. Please disable the KVM kernel extension, recompile your kernel and reboot.
VBox status code: -4011 (VERR_VMX_IN_VMX_ROOT_MODE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

I have had KVM installed, so that might be the cause of the problems.
How do I solve this?

---

### Post by StrangeFreedom on 2008-04-25
Solved by installing bum.
Then disabling kvm service in there.

How should I do it without bum?

---

### Post by your_gnu_spuddy on 2008-08-30
sudo /etc/init.d/kvm stop

---

### Post by randomAccess on 2008-09-20
> **your_gnu_spuddy said:**
> sudo /etc/init.d/kvm stop

how to make this permanent so it does not restart after reboot? or it is not safe to do that?

---

### Post by zmunson on 2008-09-22
Yes, I too would like to know how to tweak my system so I don't have to drop into a command line and issue this command before running VirtualBox.  VirtualBox gives me this error message *some* times that I load it, but not *every* time, and I haven't figured out what the trigger/cause is.  

Ideas for a relative ubuntu newbie, anyone?

Thanks!

Z

> **randomAccess said:**
> how to make this permanent so it does not restart after reboot? or it is not safe to do that?

---

### Post by randomAccess on 2008-09-23
Well, one can always make a shell script with sequential command to launch, but I know that there is a way to directly disable this module. Just don't know how. It seems that we'd have to wait for the "mercy of the gurus" :)

---

### Post by jespdj on 2008-09-23
kvm is another virtualization package which interferes with VirtualBox. You could uninstall kvm.

kvm isn't installed by default on Ubuntu as far as I know, so you must have done something in the past that installed kvm.

---

### Post by randomAccess on 2008-09-23
> **jespdj said:**
> kvm is another virtualization package which interferes with VirtualBox. You could uninstall kvm.

kvm isn't installed by default on Ubuntu as far as I know, so you must have done something in the past that installed kvm.

how to uninstall it? aptitude doesn't recognize it.
I think it's connected with Intel-based machine as Ubuntu install it by default on all intel machines.

---

### Post by randomAccess on 2008-09-24
> **randomAccess said:**
> how to uninstall it? aptitude doesn't recognize it.
I think it's connected with Intel-based machine as Ubuntu install it by default on all intel machines.

Hmmmm, a very funny thing. Kvm IS NOT installed on my machine (checked via apt-get), but it DOES EXIST in /etc/init.d/kvm. Can I just delete this file so it will not be restarted after reboot??? :confused:

---

### Post by randomAccess on 2008-09-24
SOLUTION:
[https://help.ubuntu.com/community/KVM#Removing%20KVM](https://help.ubuntu.com/community/KVM#Removing%20KVM)

---

### Post by Arabiest on 2008-11-08
This has helped me.

Thank you all.

---

