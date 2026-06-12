---
title: "ytalk error?"
date: 2006-01-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by sanriofreak on 2006-01-12
Hi, I have Ubuntu successfully installed, running etc. on my mac mini. I ssh into it and use ytalk. Everything works ok at first, but mid conversation it freezes. I can only stop it with ctrl-z. If I fg it again, I get an error or two:

sendit: first select() failed Interrupted system call
house_clean: send_auto failed Interrupted system call

Not really sure what would be causing this. Internet searches have pulled up the code for things like socket.c but not much else. Any help is greatly appreciated (of course.)

EDIT:
A little more info..
My logs are throwing errors, this in /var/log/syslog:
Jan 13 07:36:39 localhost inetd[5739]: ntalk/udp: bind: Permission denied
Jan 13 07:36:39 localhost inetd[5739]: talk/udp: bind: Permission denied

---

### Post by sanriofreak on 2006-01-23
EDIT AGAIN:
Ok, the permission errors were evidently due to me starting the service as a user and I've cleared that up. However, ytalk still crashes. I've also updated to xinetd and removed inetd. 

I'm sorry to edit in a reply, but it's been over a week :( . Does this belong in a different category maybe?

---

### Post by ristosu on 2006-01-24
Could it be some kind of NAT/firewall problem at either end? UDP traffic tends to cause problems with those. Does it freeze after a minute's pause in the conversation? In that time, the router would forget your connection. You could test against another machine on the same LAN.

---

### Post by sanriofreak on 2006-01-24
It actually tends to freeze mid-typing. I'll try a test internally to see if I can get it to do the same, unfortunately it seems random. The machine is behind a router, could giving it specific UDP ports help matters?

---

### Post by ristosu on 2006-01-27
Yes, it could. Ytalk uses either 517/udp (talk) or 518/udp (ntalk). In addition, it may use other ports for the actual data connection. I had a book explaining it. I'll be back...

Yes, it uses random tcp ports negotiated with udp for the data, looks like every letter is sent over when typed. It should be almost impossible to get this to work through a NAT firewall. Anyway, it shouldn't stop afterwards. I cannot explain that.

---

