---
title: "Dhclient not working with 2 wire gateway(sbc dsl)"
date: 2005-05-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by grinsystem on 2005-05-01
Im having a bit of an odd problem that I cannot find an answer to on google(unless Im searching something wrong here) 

Anyways, quick hardware specs(I doubt it will help, but noneless)I have a 3000+ with 1024 megs of ram(kingston hyperX)
The motherboard is an ECS 755-A2, which is an sis chipset. The Nic card is a linksys, (realtek 8139x based,I think), not the onboard one(sis). 

Anyways, I cannot connect to my dsl gateway, which is provided by  SBC, made by a company called 2wire. It acts as a dsl modem, and as a router with a firewall, and a dhcp server. I have 3 other active systems currently on the network that are working fine. 

Thing is, I guess its sort of connecting. Just that Ubuntu isn't exactly regonizing it. (oh btw- this problem has only occored within the 64 bit linux distros, including fedora 3, but with a 32 bit varation, in my case- slackware, it has not had any problems with dhcp, or windows xp for that matter)

On the gateway web setup, you see the machine being listed as connected(even the mac address match up to what it says in ifconfig to the gateways listing). But, whenever dhclient runs, it can never regonize the fact it was accepted. Dhclient just sends out the dhcp requests over(DHCPDISCOVER 255.255.255.0) and over again, then says their is no avalible ip leases. 
So I tried to do a quick hack by making it instead an static ip, that the dhcp server gave it. Then I made sure the route pointed to the dsl gateway. This only worked once and the network response was terrably slow when trying to just ssh or samba to other machines, or out to the internet. Now this will not work even if its manually done thru ifconfig. 

The next thing I did was tried to change nics, seeing if that what was causing the issue. So I enabled my onboard nic, and connected the network cable  to that. Same issue all over again. Tried another nic(an old winbond based nic), disabled the onboard again, and it reoccored. 

Thinking that my dhcp server does not like dhclient, I had a sempron 3000+ for my mythtv box that uses fedora(I know..I know) and it uses dhclient, and connected to the dhcp server/2wire gateway just fine. My slackware box doesn't seem to use dhclient, it use dhcpcd program instead, and it has no issues. Zeta(beos) doesn't have any issues eather.  

So I was wondering, if the dhclient, is 64 bit compiled native or is it 32 bit still? If this the case, my next step would try to apt-get the 32 bit version and any associated depencencies this program needs to run in order to get it up and going. 
Also, I was wondering if maybe there some changes to the dhclient.conf file I could try out in maybe dealing with timeout, or adding a certian setting. If anyone else uses this dsl gateway by 2wire, and its getting along just fine..let me know that too! 

Also, I will capture the verbose text of dhclient if nessary. 

Thanks!

---

### Post by ody on 2005-05-10
Have you tried switching to dhcpcd as you dhcp client.  I switched to Ubuntu from Suse linux about a week ago, suse uses dhcpcd and always worked fine.  When I use dhclient that comes with ubuntu I can no longer pick up IP addresses at the highschool I work at, but I can still obtain them from my linksys router.  I find dhclient to be very uncompatible with some networks.

---

### Post by stream303 on 2006-01-16
Sounds to me like dhcpclient is just picking up the dns server inside your sbc router/gateway rather than your isp's nameserver.

If you know your ISP's nameserver(s) are, you can force dhcp to look beyond your router's dns:

edit **/etc/dhcp3/dhclient.conf**

and just before the request line, add this:

**supersede domain-name-servers 123.45.678.90;**

for just one known isp dns address.  If you know a primary and a backup:

**supersede domain-name-servers 123.45.678.90, 456.78.901.23;**

Use a comma to separate and don't forget the semicolon at the end

You can now reboot, or bring the interface down and up again:
sudo ifdown eth0
sudo ifup eth0

---

### Post by aosmith on 2006-02-27
dhclient just doesnt like 2wire...im having the same probelm and i cant get an ip addr for the life of me.  It does however work on a "wired" computer running the same distro and the wireless...maybe dhclient isnt totally wirlessly compatable?

---

