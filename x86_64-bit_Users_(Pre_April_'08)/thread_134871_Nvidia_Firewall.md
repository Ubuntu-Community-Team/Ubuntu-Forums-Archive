---
title: "Nvidia Firewall"
date: 2006-02-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by xinix on 2006-02-22
Is there any way to use the nvidia firewall built into some motherboards?

---

### Post by spydirweb on 2006-02-22
the nvidia "hardware firewall" is there, but it can only be used to proper drivers.  meaning it's fine on windows but us linux folk are left out to dry.

On and off I hear rumors that nvidia is gonna put support in some version of the nforce drivers, but most knowledgable people say it'll never happen.

Ultimately it's pointless on linux, and even pointless on windows.  For ideal security what you should have is a NAT router, which will help block incoming connections.  A proper "personal firewall" on windows, or proper firewall settings for iptables in linux, will help block outgoing connections (meaning "OMFG I GOT TEH H4X3D AND THERE'S A ROOTKIT CALLING HOME!" is less likely to fumble out of your mouth).

---

### Post by s1gnAl on 2006-02-24
[QUOTE=spydirweb]the nvidia "hardware firewall" is there, but it can only be used to proper drivers.  meaning it's fine on windows but us linux folk are left out to dry.

On and off I hear rumors that nvidia is gonna put support in some version of the nforce drivers, but most knowledgable people say it'll never happen.

Ultimately it's pointless on linux, and even pointless on windows.  For ideal security what you should have is a NAT router, which will help block incoming connections.  A proper "personal firewall" on windows, or proper firewall settings for iptables in linux, will help block outgoing connections (meaning "OMFG I GOT TEH H4X3D AND THERE'S A ROOTKIT CALLING HOME!" is less likely to fumble out of your mouth).[/QUOTE]

I'll second that, and based on my experiences with it in a windows environment, my opinion is that it is pure crap. I had all kinds of problems with it and I'm not sure if it was hardware or software. I would like to see it mature as I did like the interface and features however. If you have a NAT router you should be ok, if you still want a firewall in addition to that for your box, take a look at shorewall or iptables. Either one should fill your needs.

---

### Post by spydirweb on 2006-02-24
oh, I forgot to mention...

iptables can be a bit confusing to properly configure.  I really, really, really recommend ipkungfu.  google it, I'm not sure if there's an ubuntu package avail.  It's one config file...and you're done...and it's probably the best I've used in forever.  Great.

---

### Post by TestUser on 2006-02-25
Hi

I used nvidia firewall some time ago and I am sorry to tell you but it is easily fooled. I am now talking about windows so I refer to IE.
Make a rule for any software, ie IE then take another program and change name to same as internet explorer then try get online with it...
At least this worked in he version I used, so any trojan named after a already allowed program wil have full access...

I think it is a good idea and all but if it is that easy it does not matter how safe and fast the rest of the futures are.

TU

---

### Post by woland on 2006-02-28
Just like s1gnAl, I had problems with nvidia firewall in windows on my sister's nforce4 m/b.
At first I was getting BSOD when windoze loaded and when I tried it on a clean install, it was sluggish and buggy. Nice idea, but "get it back to the oven, 'cause it's not done yet!"

---

