---
title: "Internet Not Working"
date: 2006-10-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Virtunate on 2006-10-03
I just booted up the 64 bit CD on my new system and the interent doesn't seem to want to work. I'm wondering if it's just a Live CD issue or is a hardware issue. The system is an Athlon 64 3200+ with intagrated 10/100/1000 ethernet. It's an MSI K9N NEO mobo.

---

### Post by dimis on 2006-10-04
Do you mean your problem is your Ethernet card? And what's wrong with it? Under System>Administration>Networking, can you pinpoint ethernet? If yes, try to De-activate and then Re-activate it. Does it work now?
If not, how do you want to connect to the internet? ADSL/Dial-up? Are you using a router? Are you using a modem? Is the modem USB?

---

### Post by Virtunate on 2006-10-05
I tried your suggestion of finding the Ethernet and turning it off and then on again. That did nothing. I'm on a DSL connection. I'm using a D Link router which has wireless capabilities, but I'm hocked in via an Ethernet cable. The router is a D Link DI 524 if that helps.

---

### Post by kopilo on 2006-10-05
Try putting the external DNS address as the address to connect to, **not** the ip of your modem (10.1.1.1).

Generally you can find the external DNS address off your ISP's website. Take for example if you were with [aapt]("http://www.aapt.net.au/network_setting.php"), it would be 203.8.183.1

Hope this helps... Also you have to watch the network settings as they can reset themselves which is very annoying. There is a solution which has been covered in ubuntuforums, however I don't have the link handy because I am not at home.

---

### Post by Virtunate on 2006-10-05
I don't know where the External DNS is on the website. The tech support sucks there. If you could help me find it the site is Aliant.net

---

### Post by kopilo on 2006-10-06
Well I'm not sure about the version of modem but if it has a similar web interface to the one I have, if you click "status" it might tell you the DNS it connects to, which (in my case at least) is the external DNS.

---

### Post by Virtunate on 2006-10-10
The DNS is 192.168.0.1

---

### Post by kopilo on 2006-10-11
Awesome does it work if you set it as the DNS for your ethernet card?

---

### Post by Virtunate on 2006-10-13
I tried it. Still no luck. I also tried installing Nvidia ethernet drivers, but that didn't work either.

---

### Post by kopilo on 2006-10-14
Damn, hmm can you even ping the modem?
Maybe try typing "ifconfig" into a terminal window, to find out the modems IP, if it shows at all.

If the router/modem can't be pinged then it is definatly your home network, ensure that there are no kinks or breaks in your network cable and that both ends are plugged fully in (there should be some sort of light on your ethernet card or router/modem to show this).

---

### Post by Virtunate on 2006-10-14
Here's the thing. It works fine under Windows. I'll try pinging the modem and get back to you.

---

### Post by NeoLithium on 2006-10-14
It may also help if you display what is written in /etc/network/interfaces

Sometimes accidental oopsies can be written in there, and a user doesn't even notice without looking. (Personal experience)

---

### Post by craiglarry on 2006-11-24
Here is a very simple solution that worked for me, running AMD 64 Ubuntu 6.06 64, if you are on adsl pppoe and don't need ipv6. This does not remove but disables ipv6. Don't remember link where I found this, was just running through a bunch of things and writing down the solutions. In Firefox type in "about:config" Push enter, add ipv6 in top blank, forget what they call it, then double click on results to change boolean from false to true. I'm a real newbie but this has my internet booming, I mean booming! Good luck.

---

### Post by incubus on 2006-11-24
Yeah, it would be very helpful if you could post your /etc/network/interfaces.  If you don't mind, also post the output of:
```

$ ifconfig

```

But delete information like your MAC address.  I suspect you're just not running the proper script to get an IP.  That happened to me in my fresh 64bit installation.

incubus

---

