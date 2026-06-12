---
title: "[SOLVED] remote desktop usage"
date: 2008-01-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2008-01-26
I have several systems on my home router.  I would like to have a remote desktop connection to some of them.  I want to the system>preferences>remote desktop on each of the computers I want to connect to.  I enabled the remote connection service.  I told it that confirmation was not needed. I set a password.

Then, I typed

```
charles@MSI-K8N-Neo4-SLI-Platinum:~$ rdesktop 192.168.1.103
Autoselected keyboard map en-us
ERROR: connect: Connection refused
charles@MSI-K8N-Neo4-SLI-Platinum:~$ sudo rdesktop 192.168.1.103
[sudo] password for charles:
Autoselected keyboard map en-us
ERROR: connect: Connection refused
charles@MSI-K8N-Neo4-SLI-Platinum:~$
```

What am I doing wrong here?

---

### Post by XplOzIOn on 2008-01-26
Ok lets do a Check list:

1. Remote Desktop access active on ever computer?
2. Any firewall aplications on the host side?

Remote desktop should not give any problems as i even use it from WAN.

Tell us what OS is running the host - client.

---

### Post by crjackson on 2008-01-26
> **XplOzIOn said:**
> Ok lets do a Check list:

1. Remote Desktop access active on ever computer?
2. Any firewall aplications on the host side?

Remote desktop should not give any problems as i even use it from WAN.

Tell us what OS is running the host - client.

1. Yes
2. Firestarter - Perhaps I need to open a port or something?  Which one?

---

### Post by crjackson on 2008-01-26
Just hanging out for a guruish answer...

---

### Post by XplOzIOn on 2008-01-26
> **crjackson said:**
> Just hanging out for a guruish answer...

Default port is 3389

Add a rule to open that port in firestarter :guitar:

EDIT: Let me know if it worked

---

### Post by crjackson on 2008-01-27
> **XplOzIOn said:**
> Default port is 3389

Add a rule to open that port in firestarter :guitar:

EDIT: Let me know if it worked

Thanks, I'll do that today...

---

### Post by crjackson on 2008-01-27
No still not working.  Even with firewall turned off.

---

### Post by crjackson on 2008-01-27
Okay, lets start from scratch.  All my systems have active IP Tables as per standard confutation by Firestarter.  Can you please tell me step by step how to connect to my remote workstations (connected wirelessly), I will be physically operating from my wired workstation.

I need exact firewall settings (do they go in the inbound or outbound tabs) for both hots and client machines.  I assume the machine I'll be using in the client, and the ones I want to connect to are the hosts.  If that's wrong let me know.

Step by step commands to enter...  I need it all so I can get this up and running.  I have seen that there is the rdesktop commad and also the Remote Desktop GUI told me to email a custom command and enter that one.  I've tried both without luck.

Thanks...

---

### Post by crjackson on 2008-01-27
charles@MSI-K8N-Neo4-SLI-Platinum:~$ vncviewer emachines-m6809:0

VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 16:58:22
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Sun Jan 27 17:30:07 2008
 main:        unable to resolve host by name: Connection timed out (110)
charles@MSI-K8N-Neo4-SLI-Platinum:~$ rdesktop 192.168.1.101
Autoselected keyboard map en-us
ERROR: connect: No route to host
charles@MSI-K8N-Neo4-SLI-Platinum:~$

---

### Post by crjackson on 2008-01-27
[SIZE="4"][COLOR="Red"][FONT="Comic Sans MS"]Anyone wanna take a crack at this?[/FONT][/COLOR][/SIZE]

---

### Post by crjackson on 2008-01-28
So no one knows how to make Remote Desktop Connections work.  I'm very surprised.  Is it ONLY the 64-bit OS that this won't work on, or is it the 32-bit as well?  Perhaps they will come out with a working solution in the next release.

---

### Post by crjackson on 2008-01-29
[SIZE="5"][COLOR="Red"][FONT="Comic Sans MS"]Bump for help...[/FONT][/COLOR][/SIZE]

---

### Post by XplOzIOn on 2008-01-29
Sorry  i missed this threat!

Ok so all system has default firestarted setting?

Now you need to add a RULE to allow the remote desktop port be open

Here is an example for port 80 (HTTP)
[IMG]http://www.techotopia.com/images/a/ab/Ubuntu_linux_firestarter_inbound_rules.jpg[/IMG]

Now you need to add the policy for the Remote desktop port 3389 that its standard.

This should work it has to work! :)

Remember that if you are running firestarter and you havent set and policy for remote desktop you will never be able to connect

---

### Post by crjackson on 2008-01-29
Great, thanks for the info.  I actually turned off (disabled) all firewalls and it still wouldn't work.  I'm thinking my router firewall is blocking it and I need to open up a port there, but I haven't figured it out yet.

---

### Post by crjackson on 2008-07-02
Issue was resolved by upgrading to Hardy

---

### Post by lesbillbell on 2008-07-24
I have Hardy Heron but (using ufw not firestarter to allow port 3389) I get this connection refused error message. In one terminal I do ssh tunnelling using plink, in another terminal window I try to run rdesktop.

---

