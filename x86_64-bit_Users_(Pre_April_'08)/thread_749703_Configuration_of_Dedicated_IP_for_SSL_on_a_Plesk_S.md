---
title: "Configuration of Dedicated IP for SSL on a Plesk Server Running 7.10..  How?  (n00b)"
date: 2008-04-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by jdjustice on 2008-04-08
Hi, I run Plesk 8.3.0 on a Xen-managed VPS using Ubuntu 7.10 as the distro.
I have read about how to enable SSL support by manually editing the Apache2 config / vhosts files and could get that part accomplished.

But I am a newbie at this whole thing and since I use Plesk to manage my server, I would like to do everything through Plesk that is possible (and yes, I've been over to the Plesk forum).

My main question is how do I use a DEDICATED IP for the SSL support?
I've requested an additional IP for my VPS for this purpose, but I will be wanting both the IPs to serve mixed (HTTP / HTTPS) content on ONE domain.  I have a GeoTrust SSL Certificate for my domain and generated the Cert request in the Domain-specific section of the Plesk interface.

I have uploaded the Cert and everything is working fine but Plesk expects a dedicated (or 'exclusive') IP for any site or subdomain running SSL / HTTPS.  Since I already have another SSL cert securing my Plesk Control Panel (Port 8443), it is not an option to NOT use a dedicated IP for my specific domain.

Plus, I want in the future to be able to buy more SSL certs for other uses.

This is turning out to be a long-winded first post here, but I need advice or suggestions on how to configure not only the Plesk interface but specifically also the DNS so that both HTTPdocs and HTTPSdocs can be served from the same domain on the same server (But with DIFFERENT IPs).

Am I crazy and do I have no idea what I am talking / asking about?  Possibly.
But I am still waiting for my Hosting Provider to supply the secondary IP so I thought I would ask for tips and any help would be appreciated greatly.. Then I will be better prepared to not totally hose my server when I attempt to enable (further) SSL configuration(s).

Thanks In Advance and great forum here!!

JD

---

### Post by pseudo-random on 2008-04-08
Why not use your existing SSL certificate and stick with 1 domain, 1 IP and 1 certificate like most sites?
You don't need two!

---

### Post by jdjustice on 2008-04-08
Well, my Plesk Server runs on a dedicated host, and the SSL cert I purchased for it is a lower-end product not suitable for potential e-commerce applications.

The SSL cert for the Plesk Server is installed on the server itself.  Because my first certificate is for a specific subdomain that matches my system hostname, I need another cert for another domain.

If I were only running 1 site this would be an option but I am managing 5 sites of my own and have a client on my Plesk server as well who runs 3 sites.  The SSL cert I initially bought was for the Plesk Control Panel only and cannot be configured or changed to my custom domain that I wish to use for more intensive purposes.   But then again, I know very little about all of this -- I just know I need a seperate SSL cert for every specific domain I wish to enable HTTPS on.

So basically it's SEVERAL sites, not just one.  :)

> **pseudo-random said:**
> Why not use your existing SSL certificate and stick with 1 domain, 1 IP and 1 certificate like most sites?
You don't need two!

---

