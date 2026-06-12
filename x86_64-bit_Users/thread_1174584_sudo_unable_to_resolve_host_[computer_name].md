---
title: "sudo: unable to resolve host [computer name]"
date: 2009-05-31
forum: x86 64-bit Users
---

### Post by Neverest on 2009-05-31
Hewwoh!

I was following this guide :[http://ubuntuforums.org/showthread.php?t=772490&highlight=flash](http://ubuntuforums.org/showthread.php?t=772490&highlight=flash)

... to install flash 10 on my 64 bit Hardy 8.04. When issuing the command "sudo getlibs -p libcurl3" I get the error "sudo: unable to resolve host [computer name]" when trying to download.

I also got this earlier:
(entry:) sudo apt-get -y purge mozilla-plugin-gnash
sudo: unable to resolve host [computer name]

I think I surpassed the missed purge with "apt-get autoremove"

My search for help was unsuccessful whereas the inquiry.
I've had similar messages earlier since my upgrade from Gutsy 7.10, but it hasn't been a problem until now. 

what's my problem!? Is my PC ruined!?
just kidding.

thanks in advance

---

### Post by nikgare on 2009-05-31
Please post your **/etc/hosts** file

---

### Post by Neverest on 2009-05-31
"127.0.0.1 localhost
127.0.1.1 Newponk.MSHOME

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts"

---

### Post by dcstar on 2009-05-31
> **Neverest said:**
> "127.0.0.1 localhost
127.0.1.1 Newponk.MSHOME

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts"

There is no entry for your machine name or your local IP address, have you been playing with the Network Manager?

---

### Post by drs305 on 2009-05-31
> **Neverest said:**
> "127.0.0.1 localhost
**127.0.1.1 Newponk.MSHOME**

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts"

A piece of software has probably changed your computer's name in the highlighted line above. Sometimes the computer name is appended with an additional title (don't ask me why).

If your computer's name is "Newponk" change the highlighted line back to:
> 
**127.0.1.1 Newponk**


Do this by opening the /etc/hosts file with:
```

gksudo gedit /etc/hosts

```

---

### Post by ddales on 2009-06-03
Mshome is appended to the host name for Windows/Samba.  That's the default name of the Windows Workgroup to which it thinks it belongs.  The default workgroup name in Vista is also mshome instead of the old "workgroup".

You don't need to remove the .mshome portion, just add the computer name after that as an alias.  Also, 127.0.1.1 isn't a real address anyway.  It's just the IPV6 capable localhost address.

Check your DNS settings under /etc/resolv.conf.

If you are trying to use a static IP address, add it to the /etc/hosts.

If you're using the network manager, I can't help.  The first thing I do after a new install is remove it and set my network settings by hand.

---

### Post by drs305 on 2009-06-03
> **ddales said:**
> 
You don't need to remove the .mshome portion, just add the computer name after that as an alias.  Also, 127.0.1.1 isn't a real address anyway.  It's just the IPV6 capable localhost address.

Like this:
> 
127.0.1.1 Newponk.MSHOME Newponk


---

### Post by Iowan on 2009-06-03
I doubt it changed, but verify that **hostname** is still Newponk.

---

### Post by doas777 on 2009-06-03
I had this problem a lot in gutsy. it may come back everytime a change is made in the gui network config utility. it kept appending the dns name, even if a fqdn was already in there. thank goodness gksu still worked.

---

### Post by Neverest on 2009-06-11
Thanks a lot! Problem fixed and I learned something new. =)

---

### Post by Horomancer on 2009-08-18
Hey there. I'm running into a simular problem with getting an 'unable to resolve host' error message

I went into /etc/hosts with gedit and it says-
127.0.0.1 localhost
127.0.1.1 Time Control

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

i then opened up a file in /etc called hostname and it had-
Time Control

I've not been monkeying around with the network manager, so what gives?

---

### Post by drs305 on 2009-08-18
Horomancer,

Don't know how you ended up with "Time Control", but edit (gksudo gedit) both files and change the name back to the name of your computer.
Example /etc/hosts:
127.0.0.1  localhost
127.0.1.1  mycomputer
Example hostname:
mycomputer

---

