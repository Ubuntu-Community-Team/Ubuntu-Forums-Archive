---
title: "backburner or ubuntu security hole?"
date: 2008-01-12
forum: Wine
---

### Post by JohnLM_the_Ghost on 2008-01-12
I got a funny behavior in backburner.

I am a bit of CG artist, and use 3ds Max in Windows. It has the network render manager known as backburner.

The thing is while running it in Ubuntu with Wine it occationally shows some unknown IPs to connect to backburner manager. Those never appear in Windows.

I suspect they are network attacks from WAN side (internet) what happens "hit"  the port backburner is using. My Antivirus software probably blocks those in Windows.
Of course not that anything bad happens cause of network attacks (nothing i know of at least) in Ubuntu, but I want to be really sure.

Or it may be a security hole? What I find to be less likely.

Could you suggest me any workaround?
Or at least reliable and lightweight antivirus?

---

### Post by david3d on 2008-01-14
Well first off this is not a Ubuntu security problem.  It may be a security issue or a bug in backburner or caused by running backburner under wine.  One thing to keep in mind is that Backburner was never made with security in mind.  It was designed to operate on a trusted network so I would avoid running it on any computer that is directly attached to the internet.  If the computer is behind a router that has NAT then I would expect that computers from the internet would not be able to access Backburner unless you have forwarded the ports used by Backburner.

Most likely this is just a bug caused by running Backburner under wine.  Running "sudo lsof -i" will list all the open connections to your computer so you can see if the connections are showing up there as well.

If you need to block these connections you can always use iptables to block any connections to that port that's not part of your local LAN.
--
David

---

### Post by JohnLM_the_Ghost on 2008-01-17
While I had a good idea about problem already, your post really helped me understand the problem.

Actual situation is:
I really have the port forwarded. That's because some of my friends contribute to rendering by running Render server from their homes.
Makes stuff really fast.

I will try to allow connection only to Local Network and those few internet friend PCs.

Thank You!

---

### Post by david3d on 2008-02-05
John,
  You may want to setup a VPN for that sort of thing.  I would suggest OpenVPN.  It's what we use here at work although we use Deadline for rendering farm management here the idea is the same.
--
David Miller

---

### Post by JohnLM_the_Ghost on 2008-02-06
Thanks David! I will have a look into that!

---

### Post by tyk on 2008-04-04
hey john,
i too am using max for my work. difference being that i'm running it on a xpVM on my quadbox (host=Xubuntu gutsy). i would highly appreciate it if you could tell me how to get backburner running properly on wine. when i run server on the host on wine, it gives me a sharing violation output but starts up. my VM manager registers it and the VM server but at the submittal screen it shows only the latter.

when starting server on wine, i get
ERR:cannot acess ......\backburner\Network\nrapi.conf: Sharing violation (0x20).

i should also say that wine is directly running server and i haven't 'installed' it.

many thanks also for anybody who can help.
regards,
tyk.

---

