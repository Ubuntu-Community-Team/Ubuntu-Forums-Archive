---
title: "[SOLVED] VNC into Ubuntu from XP with Secure SSH"
date: 2008-12-02
forum: x86 64-bit Users
---

### Post by mattman85 on 2008-12-02
I have a dual-booting XP/Ubuntu installed on a wired laptop that is behind a router at my house.

I'd like to be able to remote into the laptop from my fiance's XP box at her house while it is booted into Ubuntu. I can do this fine when I have it booted into XP, but I can't get the settings right or something in Ubuntu..

What I have done so far:
1. registered with dynDNS
2. configured ddclient to update the dynDNS info
3. configured port forwarding of VNC (port 5900) the router to point to my laptop

This is where it doesn't work (VNC side..  XP Remote Desktop worked fine)
1. I've installed openssh server, and tried to connect through Putty...Putty was able to see the ip address of router but does not connect ... i get a "Network Error: Connection time out" message

2. I turned on remote desktop via System > Preference > Remote Desktop, and set up a password.
3. I set up port forwarding for SSH to be a port other than 22 for more a more secure port.

I have a couple vnc programs, but none have worked..  any ideas?

---

### Post by cariboo on 2008-12-02
Have a look here:

[http://members.shaw.ca/nicholas.fong/vnc/](http://members.shaw.ca/nicholas.fong/vnc/)

This may help you with your vnc problems.

Jim

---

### Post by mattman85 on 2008-12-10
Woo!  That worked!  What I was doing wrong was trying to launch vncviewer from the SSH Bash..  I wasn't opening the vnc program from my local machine...  sometimes I overlook the most obvious part...  Thanks!

---

### Post by bodhi.zazen on 2008-12-10
Solved:

Woot ... :guitar:

Please mark this thread as solved, it saves the time of many volunteers looking to help 
[indent]... and users looking for solutions.[/indent]

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

