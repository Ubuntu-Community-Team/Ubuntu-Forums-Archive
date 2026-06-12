---
title: "Help, problems after installation"
date: 2005-08-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by lancaster on 2005-08-11
I'm sorry to make my first post on these forums a cry for help, but I have just installed Ubuntu on my Athlon64 machine and am experiencing a few problems. When I login to the system with the user name I created during the setup procedure I am presented with a warning dialogue which says "Could not look up internet address for kubuntu.  This will prevent gnome from operating correctly.  It may be possible to correct the problem by adding ubuntu to the file /etc/hosts.".

I have tried adding ubuntu to the list of known hosts in /etc/hosts, however when I try to use sudo to edit the file I get the error "sudo: unable to lookup ubuntu via getbyhostname()
Password : postdrop: warning: unable to look up public/pickup: No such file or directory"

I am also unable to configure any network interfaces as when I go to System > Administration > Networking the program loads for a while then seems to crash without producing an error message. I assume this has something to do with the above problem?

Thanks in advance for any assistance you can provide. :)

---

### Post by varunus on 2005-08-11
Can you boot into recovery mode from the grub prompt, issue a "sudo nano /etc/hosts", and replace the contents of the file with the following:

```
127.0.0.1 localhost.localdomain localhost yourhostname here

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

You can find your hostname by typing "cat /etc/hostname" in the prompt.

---

