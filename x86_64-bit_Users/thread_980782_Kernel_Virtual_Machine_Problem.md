---
title: "Kernel Virtual Machine Problem"
date: 2008-11-13
forum: x86 64-bit Users
---

### Post by Iscariot.solia on 2008-11-13
I have been trying for the past 2 weeks to set up a KVM on a machine and I keep running into the same issue.

I have been following this guide to the T attempting to set it up.
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

Operating System: Hardy 64 bit Server.

Here are the steps I have been taking.

Format the computer.
Update
Upgrade
Install kvm libvirt-bin ubuntu-vm-builder qemu bridge-utils
Bridge the Network
Bridge Guests by Default

Then I attempt to set up the KVM using ubuntu-vm-builder

I make a file called vmcreator.bash and set this up
```

sudo ubuntu-vm-builder kvm hardy \
                  --domain app03vm \
                  --dest app03vm \
                  --arch amd64 \
                  --hostname solia \
                  --rootsize 130208 \
                  --swapsize 32768 \
                  --mem 7936 \
                  --user john \
                  --pass doe \
                  --ip 10.10.10.101 \
                  --mask 255.255.255.0 \
                  --net 10.10.10.0 \
                  --bcast 10.10.10.255 \
                  --gw 10.10.10.1 \
                  --dns 10.10.10.1 \
                  --mirror http://archive.localubuntumirror.net/ubuntu \
                  --components main,universe,restricted \
                  --addpkg vim openssh-server openssh-client mysql-server mysql-client php5-xcache php5-cgi php5-curl php5-dev php5-gd lighttpd \
                  --libvirt qemu:///system ;

```

At the end it says failed to define domain, it waits a few moments, then says done.

After I do this I go to /etc/libvirt/qemu/ to edit the XML file and there is no XML file there.  Any suggestions?

---

