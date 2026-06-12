---
title: "Question about ssh"
date: 2005-09-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tux_army on 2005-09-01
Hello i just started using ssh to try and log into my step dad xp computer. I have openssh-client & openssh-server installed. Everytime i try to ssh into his computer all i get his conncection refused. He doesn't have any firewall install on his system.

Here are my questions

1. My dad computer name is Dustin but his username -- the one he use to log into his xp computer is "insane". When i want to ssh to his computer do i type in 

ssh Dustin@hisipaddress or ssh insane@hisipaddress. 

2. Do both computers have to have ssh install? i have ssh install on my system but does he have to have ssh install on his computer?

3. Where do i exactly add his ip address in /etc/hosts? When i open ssh this is all i see is this.

> # The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

So i'm guessing i add his ip address in the ip6-allhosts, so now it would look like ff02::3 hisipaddress

Please help! :?

---

### Post by amohanty on 2005-09-01
Does _your dad's machine_ have an ssh _server_ installed?

Basically to be able to ssh _into_ a machine, the destination machine needs to have an ssh server installed and running.

Take a look at some windows servers here:
[http://www.jfitz.com/tips/ssh_for_windows.html#SSH_Servers](http://www.jfitz.com/tips/ssh_for_windows.html#SSH_Servers)

HTH
AM

---

### Post by Tux_army on 2005-09-01
Well i install PUTTY in his computer and i think i almost have ssh working i keep getting this error when i type in my password. I'm sure i type it in right.
> 
Permission denied (publickey,keyboard-interactive).

---

### Post by amohanty on 2005-09-02
Take a look at this:
[http://web.arizona.edu/~consult/win-ssh.html](http://web.arizona.edu/~consult/win-ssh.html)

AM

---

### Post by PaganHippie on 2005-09-03
You're trying to log into a WinXP system?  Does his computer have "remote assistance" enabled?  If so, then you should be able to telnet into his system (try a telnet client), but "ssh" may not work.

---

