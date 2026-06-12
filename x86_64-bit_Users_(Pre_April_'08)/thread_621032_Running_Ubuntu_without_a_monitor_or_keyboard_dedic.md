---
title: "Running Ubuntu without a monitor or keyboard dedicated to it?"
date: 2007-11-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by william_hunter on 2007-11-23
I have a problem and I am looking for thoughts on it so I can try to figure out whats up. Here it is:

I run Ubuntu server on a box at home, and I have really been pleased with its performance, but I have a baby on the way and I want to move the box off the desk so I can put the desk away for baby room (-sigh- goodbye nice office). I have the server set up to allow VNC connections and have installed Webmin, both of which work nicely from outside my firewall. I can access either to control the server as long as I am not home. Problem is this: Inside the firewall, I cannot access them. That's not a good situation because I can't have the lack of control during the times I am home. Anyone have thoughts on how I can get around this? I suspect it is because of the router's NAT, but I cannot modify the settings so I am kinda stuck there. I tried setting the server on a DMZ, but that doesn't work either. Its maddening, because the server is literally 3 feet away when I am trying to log in from my laptop, but I can't make the connection!

---

### Post by eldragon on 2007-11-23
are you trying to connect to the server through the LAN ip? or through the WAN ip?

when accessing from the outside, you would use the WAN ip, but in your LAN, always use its LAN ip to connect to it.

thats all i can think of... besides that, see if you got your own lan blocked in /etc/hosts.deny  or if your router has some weirdo configuration.

check if both your client and server are in the same subnet.

---

### Post by mellowd on 2007-11-23
as above,  and how exactly is your network set up at home?

---

### Post by william_hunter on 2007-11-23
I put in the LAN ip and get an error message saying that the server is running in SSL mode and then  redirect to the DNS name I assigned to the server.  Should I do something to remove that DNS name? I don't really need it anymore, honestly. I had a forum set up that I have since removed.

---

### Post by william_hunter on 2007-11-23
> **mellowd said:**
> as above,  and how exactly is your network set up at home?

Internet is routed through a US Robotics wirelss router w/firewall. The Ubuntu server is hardwired as is one other desktop (for now). The rest of the computers in the house are Mac laptops (wireless).

I have ports open in the firewall for the server, including the proper port for VNC and for Webmin, AFAIK.

---

### Post by mellowd on 2007-11-23
Have you denied lan access to the server at any time? Or denied everything and just allowed wan access?

---

### Post by william_hunter on 2007-11-23
no, never.

I am finding that I can access the webmin if I go through the https address the error message gives me, but it is staggeringly slow.

---

### Post by mellowd on 2007-11-23
can you even ping the server internally?

---

### Post by william_hunter on 2007-11-23
yes, I can. My response times average out around probably 1.3ms.

---

### Post by daengbo on 2007-11-23
I had teh same problem a few years ago. There are elegant ways to solve it, but the quick-and-dirty way is to add the DNS name for the server into your LAN clients' host file.
Kind of like this:
168.126.63.1     ubuntu-server

When you are redirected, you'll stay on the correct IP.

Best of luck

---

### Post by xeth_delta on 2007-11-23
Do you have the same problems with ssh?

---

### Post by william_hunter on 2007-11-23
I have no idea, honestly. I am still learning a lot of this on the fly, and have not explicitly used SSH for anything. I am not even certain it is set up on the server yet.

---

### Post by william_hunter on 2007-11-23
> **daengbo said:**
> I had teh same problem a few years ago. There are elegant ways to solve it, but the quick-and-dirty way is to add the DNS name for the server into your LAN clients' host file.
Kind of like this:
168.126.63.1     ubuntu-server

When you are redirected, you'll stay on the correct IP.

Best of luck

Well now...I forgot all about the hosts file. I went and edited it, removing the *old* hosts references to the Ubuntu server, and suddenly things work faster. Now I feel dumb. I will restart now and see if it sticks, but I am willing to bet it does. I had the wrong internal IP assigned to the server in the hosts file (192.168.2.3 when it is now dedicated to 192.168.2.5)

---

### Post by xeth_delta on 2007-11-23
> **william_hunter said:**
> I have no idea, honestly. I am still learning a lot of this on the fly, and have not explicitly used SSH for anything. I am not even certain it is set up on the server yet.

I asked you because you should be able to make administration tasks on the server via ssh.

Xeth

---

### Post by william_hunter on 2007-11-23
> **xeth_delta said:**
> I asked you because you should be able to make administration tasks on the server via ssh.

Xeth

I think it working now that I modified the hosts file. I am checking now.

---

### Post by daengbo on 2007-11-23
If it is, please mark this post [Solved]

---

### Post by steveneddy on 2007-11-24
I run a headless server and I can access it both ways.

Usually I just use the internet address and it is just as fast locally as remotely.

Just for my personal info, what are you using the server for?

:popcorn:

---

### Post by william_hunter on 2007-11-25
I host a website, fileserver for my students, and a game server for Neverwinter Nights on the server. It is indeed solved, as it works just fine now. Now its time to start tweaking the interfaces.

---

