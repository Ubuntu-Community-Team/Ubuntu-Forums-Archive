---
title: "ssh: cannot ssh into machine behind firewall"
date: 2008-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by professor-g on 2008-03-04
i provide as much info as possible ... 

ubuntu 7.10 
small cluster we set up
can ssh out to net and anywhere from server - no problem
cannot ssh in to machine from outside since behind firewall

ssh: connect to host 211....  port 22: No route to host

/etc/nsswitch.conf:
hosts files dns

/et/ssh/ssh_config:
GSSAPIAuthentication no
GSSAPIDelegateCredentials no


machine seems to be a 10.10.* (internal network)
and internal we can use ssh as long as it is coming from a 10.10.* host
and going to the 10.10* interface on the machine

but if we go from a 10.10.* host to the external interface
211... i get connection refused on port 22.  in this case there
is a route to the host but it does not seem to want to talk to me.  i
did an nmap on the machine itself and it seems that the port is open, as
well as from another machine.  so i imagine that is a firewall issue,

we also tried to use a different port rather than 22; tried port 80 but that also
failed.  i am wondering however if a VPN might solve the problem

it seems fundamentally to be a routing problem, in which external
packets get dropped on the floor if they go anywhere that is not
configured.  so perhaps even with a vpn we would need to do some tweaking

---

### Post by hvc123 on 2008-03-04
ok are you ready??----


this is how i do it. ssh to my home machine from work .

i setup ssh on port 443 (https) because that is a trusted port on the squid at work 

now for the command --

i wrote a small script to do this for me 

#! /bin/sh
konsole -e ssh -p 443 <YOURTARGETIP> -X -o "PROXYCOMMAND connect -H <YOURPROXYADDRESS> %h %p"
exit 0

this script will forward X as well so if you dont need x forwarding then remove the -X 
oh yer the other thing is this is for konsole (kde term) but i suppose you could change that easy enough

---

### Post by hvc123 on 2008-03-04
hmm after re-reading your problem its the other way around



you need to forward whatever port you use for ssh on your proxy to the ssh server 

ie ssh = 22 

proxy:22>ssh server:22
so that your proxy knows where to direct that ports traffic. if you do not have access to the proxy then you wont be able to do it

---

