---
title: "Major Internet Lag after upgrade to 9.10"
date: 2009-11-06
forum: x86 64-bit Users
---

### Post by crazy dave on 2009-11-06
Can anyone advise if they've experienced lags with webpage impressions after upgrading to 9.10.  I have major delays, and have tested Firefox, Opera, and Epiphany, all with the same result; there is a significant delay in loading fresh webpages, either through clicking on links, clicking bookmarks, or through searches.  This is not a problem with the ISP as other PC's and devices do not suffer this problem.  Also ADSL speedtests show all is fine.

I've read some threads suggesting it might be IPV6, does anyone know for sure.

---

### Post by Ve6jhc on 2009-11-06
Yes I have the same issue....feels like dialup on my cable connection with 9.10! I checked my wife's windows box and it is nice and snappy. I hope this is fixed asap.

---

### Post by DodgeV83 on 2009-11-06
This 100% fixed my problem! Posted by mikio at

[http://ubuntuforums.org/showthread.php?t=1283146](http://ubuntuforums.org/showthread.php?t=1283146)

1. In /etc/dhcp3/dhclient.conf add the following line:

prepend domain-name-servers 208.67.222.222,208.67.220.220;

2. In /etc/nsswitch.conf edit this line

hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

to this

hosts: files dns

I'm not sure which one of these did it to be honest, but it's fixed!

Note:  To edit those files, open a terminal and type "sudo gedit" then the file:

```
sudo gedit /etc/dhcp3/dhclient.conf
```

```
sudo gedit /etc/nsswitch.conf
```

Edit:  Then reboot the machine.

---

### Post by crazy dave on 2009-11-06
no luck with that suggestion but thanks anyway

---

### Post by tomcat025 on 2009-11-06
Completely shutting down IPv6 helped a bit for me. However, there is still a good deal of lag left.

---

### Post by sgosnell on 2009-11-06
Reverting to 9.04 works.  I don't know if anything else does.

---

### Post by crazy dave on 2009-11-06
what did that invlove? with IPv6 I mean?

---

### Post by sgosnell on 2009-11-06
[This](https://store.opendns.com/setup/device/ubuntu/) worked for me.  The problem seems to be connected to DNS, and using openDNS made pages load immediately on my system.

---

### Post by PhilGil on 2009-11-06
There is a large thread in Launchpad about this problem: [https://bugs.launchpad.net/bugs/417757](https://bugs.launchpad.net/bugs/417757)

My layman's understanding of the bug is that Karmic's DNS resolver tries to do an IPv6 lookup before IPv4.  If your modem/router is not configured to respond to the IPv6 request the resolver has to wait until the query times out, causing the delay.

There's talk in the thread about a patch, but in the interim what has worked for me is to bypass my router when doing DNS lookups.  I have had success using DNS servers from my ISP as well as Open DNS.  Instructions for manually entering a primary and secondary DNS server are here (these are instructions for Open DNS, but should work for your ISP's DNS server - if you know the IP addresses): [URL="https://store.opendns.com/setup/operatingsystem/ubuntu"]https://store.opendns.com/setup/operatingsystem/ubuntu
[/URL]

---

### Post by DodgeV83 on 2009-11-06
> **PhilGil said:**
> There is a large thread in Launchpad about this problem: [https://bugs.launchpad.net/bugs/417757](https://bugs.launchpad.net/bugs/417757)

My layman's understanding of the bug is that Karmic's DNS resolver tries to do an IPv6 lookup before IPv4.  If your modem/router is not configured to respond to the IPv6 request the resolver has to wait until the query times out, causing the delay.

There's talk in the thread about a patch, but in the interim what has worked for me is to bypass my router when doing DNS lookups.  I have had success using DNS servers from my ISP as well as Open DNS.  Instructions for manually entering a primary and secondary DNS server are here (these are instructions for Open DNS, but should work for your ISP's DNS server - if you know the IP addresses): [URL="https://store.opendns.com/setup/operatingsystem/ubuntu"]https://store.opendns.com/setup/operatingsystem/ubuntu
[/URL]

I think that's essentially what the instructions I gave above do.  Set DNS to OPENDNS and bypass the router or something.

Dave, did you reboot the machine after making the changes in my previous post?

---

### Post by PhilGil on 2009-11-06
> **DodgeV83 said:**
> I think that's essentially what the instructions I gave above do.  Set DNS to OPENDNS and bypass the router or something.

Dave, did you reboot the machine after making the changes in my previous post?

DOH, you're right.  New to Ubuntu, I'm still more GUI-oriented.

I think a reboot is necessary with your method.  With the GUI method you can hit the "Apply" button after making the changes.

---

### Post by crazy dave on 2009-11-06
Thanks for tha, I did indeed reboot but maybe I didn't edit the files correctly I'll try again.  Any examples of the text files would be welcome.

---

### Post by sgosnell on 2009-11-06
No, using the network manager GUI, you still have to reboot for the settings to take effect.

---

### Post by crazy dave on 2009-11-06
OK thats fixed it Thanks a lot everyone.  I inserted the DNS Servers with those from my routers firmware as advised and its done the trick.  Many Thanks.

---

### Post by crazy dave on 2009-11-06
I had sucess with the DNS server workaround here:> Quote:
Originally Posted by PhilGil View Post
There is a large thread in Launchpad about this problem: [https://bugs.launchpad.net/bugs/417757](https://bugs.launchpad.net/bugs/417757)

My layman's understanding of the bug is that Karmic's DNS resolver tries to do an IPv6 lookup before IPv4. If your modem/router is not configured to respond to the IPv6 request the resolver has to wait until the query times out, causing the delay.

There's talk in the thread about a patch, but in the interim what has worked for me is to bypass my router when doing DNS lookups. I have had success using DNS servers from my ISP as well as Open DNS. Instructions for manually entering a primary and secondary DNS server are here (these are instructions for Open DNS, but should work for your ISP's DNS server - if you know the IP addresses): [https://store.opendns.com/setup/operatingsystem/ubuntu](https://store.opendns.com/setup/operatingsystem/ubuntu)

---

### Post by cybrsaylr on 2009-11-07
I was having a similar problem with serious lag but only when using Opera browser with 9.04 and 9.10 Ubuntu. FF and SeaMonkey ran fine. Turned out for me to be an IPv6 issue that was corrected by using Beta Opera 10.10 version. Now with Opera 10.10 Karmic flies very fast again.

Another thing, this slowness only happened when using wireless on my Toshiba laptop. When hardwired the laptop was very fast and speedy along with my desktop! The led me to believe it was something in my router but Beta Opera 10.10 took care of that and everything is nice and snappy with Karmic now.

---

### Post by heldal on 2009-11-08
> **PhilGil said:**
> My layman's understanding of the bug is that Karmic's DNS resolver tries to do an IPv6 lookup before IPv4.  If your modem/router is not configured to respond to the IPv6 request the resolver has to wait until the query times out, causing the delay.


There are multiple issues that contribute to the overall perception of slow networking.

1. Incomplete/incorrect ipv6 configuration. The system tries/prefers ipv6 but fails and falls back to v4.

2. Some DNS-servers, and most notably broadband-routers with built-in DNS-forwarders not handling IPv6 information properly.

3. Incorrect or missing NXDOMAIN responses.

The behaviour of the dns-resolver has changed in Karmic and it now tries to add the local or search-domains on all requests even when applications specify a FQDN. E.g. it first looks for "google.com.yourlocaldomain" when you type "google.com" in a browser. That doesn't make much difference with a fast DNS-server giving immediate NXDOMAIN (not found) responses, but causes delays with some DNS-forwarders which fail to pass these responses to the clients. Even worse is if you've got a provider whose CPE's tell clients (via DHCP) to use a certain domain and implements DNS-wildcards on that domain. One way to avoid this when using DHCP on the client is to either remove the "domain" and "search" lines from /etc/resolv.conf after connecting, or modify the configuration of the DHCP-client so that it doesn't ask for these options at all. This workaround still uses the broken DNS server/resolver though. A better solution is to use a proper local resolver/cache that queries the root itself.

---

### Post by servio on 2009-11-09
Much thanks - worked most excellently.

---

### Post by Arup on 2009-11-09
To disable ipv6 in Karmic edit /etc/default/grub 

Change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"

Do a sudo update-grub 

Also in Firefox about:config set network.dns.disableIPv6 to true.

It works with my karmic here. All credit goes to Joe Hacker [http://www.joehacker.com/index.php?title=Ubuntu_Tips#Disable_IPv6_on_Karmic_9.10](http://www.joehacker.com/index.php?title=Ubuntu_Tips#Disable_IPv6_on_Karmic_9.10)

---

