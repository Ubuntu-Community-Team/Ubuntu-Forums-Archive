---
title: "[SOLVED] Hosts file"
date: 2008-08-01
forum: x86 64-bit Users
---

### Post by alt3rn1ty on 2008-08-01
Hi I have been following Stchman's tips and have a question regards his hosts suggestions [http://www.stchman.com/conf_host.html](http://www.stchman.com/conf_host.html)

He suggests our first line should be

127.0.0.1 localhost name-laptop

Which if linux hosts works the same as windows then I believe it is correct but my new Ubuntu installation has this

127.0.0.1	localhost
127.0.1.1	name-laptop
then a few more entries reference IPv6
followed by all my pasted entries from mvps.org hosts file .. (available here [http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm))

Is Stchman's advice out of date for Ubuntu 8.04.01 or should the 127.0.1.1 line and IPv6 entries be removed?

Also, in windows having a large hosts file could slow down internet access unless you disable DNSClient service, is there similar problem with linux?

---

### Post by redmk2 on 2008-08-01
I don't think 127.0.1.1 is a legitimate ip address.
  
Attempting ```
whois 127.0.0.0
``` returns > Unknown AS number or IP network. from the ARIN WHOIS database

The 127.0.0.1 address is an internal to the local host address. You can add your hostname here, but after reading from the forum, I would leave 127.0.1.1 as is.

Edit: I found [[COLOR="Magenta"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=388765") old forum discussion about the subject.

---

### Post by Jouke74 on 2008-08-01
According to some people on the internet it speeds up the loading of programs when you make the hosts file as 127.0.0.1 localhost name-laptop.

However developers of Ubuntu and Debian, if I remember well, have advocated against this hack as it bypasses some important stuff for internet connections and security (can't find it anymore on Google).

---

### Post by redmk2 on 2008-08-01
Yep, I have been reading.  I guess it was a big deal in feisty days and it was a Debian only (Ubuntu included) permutation.  I googled "127.0.1.1" and got tons of info.

---

### Post by alt3rn1ty on 2008-08-01
Thanks all,

@ Redmk2... Thank you for the link, cross referring with that and the fact that my install is completely mint and I dont perceive any slow down (terminals are instantanious) I believe my setup is correct.

Going to try and PM Stchman and ask if he can update his advice with reference to this post (possibly giving alternate advice for different instances of Ubuntu).

One further question, all entries from mvps.org hosts file start with 127.0.0.1, I am hoping that doesnt have to change... but do they now have to start with 127.0.1.1 under linux OS (please say no lol)

---

### Post by gsmanners on 2008-08-01
I think the only caveat is that if you are running a web server on your box, you'll need to use "0.0.0.0" instead of "127.0.0.1" (except for localhost of course).

---

### Post by redmk2 on 2008-08-01
[COLOR="Red"]**No**[/COLOR] the 127.0.1.1 is a additional address.  In all reality (pun) the only on needed is 127.0.0.1.  It is akin to your first nickname.  All of the others are also nicknames.  I don't think Ubuntu releases use it anymore.

gsmanners,

You do not need to run 0.0.0.0 in a hosts file .  That address is used in routers to mean "all" if I am not mistaken

---

### Post by dannyboy79 on 2008-08-01
my hosts file looks like this:

cat /etc/hosts
127.0.0.1 localhost.localdomain localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
**192.168.0.3 XXXXX XXXXX.xxxxx.com**

192.168.0.3 is my server's internal ip address which is linked to a FQDN using dyndns. Everything in my internal network and external connectivity works great! I have the ip's of the other machines in there but I removed them. I use my hosts file instead of setting up an internal dns server.

---

### Post by alt3rn1ty on 2008-08-01
@ Redmk2 <wipes brow> Phew, that would have been one major conversion.

@ Dannyboy79 noted in my useful stuff for future reference, thanks.

---

