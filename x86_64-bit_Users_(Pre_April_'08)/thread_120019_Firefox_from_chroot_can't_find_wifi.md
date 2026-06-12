---
title: "Firefox from chroot can't find wifi"
date: 2006-01-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-01-20
I installed chroot in order to get Adobe Reader 7.0 and RealPlayer installed. They worked fine as standalone appsm but I couldn't get Firefox to see them. Eventually I installed Firefox in chroot also, and that did the trick.

Then I went to the university and discovered that 32-bit Firefox cannot see the wifi. However, it does see my home ethernet connection via cable modem and it works fine there. So it's just the wifi that it does not see. And everything else can see the wifi and use it, including the old (original) version of Firefox, which is still installed.

Today I went to a cafe and used their wifi. Same problem. Everything goes online without a problem except 32-bit Firefox. When I look at System Monitor while 32-bit Firefox is trying to find a page the monitor is flat-line. If this were a hospital we would pull the sheet up over the patient's face. :)

So now I have islated the problem. I know it is not the wifi (working with ndiswrapper). I know it is not the university. I know it is not 32-bit Firefox because it goes out to the internet just fine at home via ethernet and cable. The problem is getting 32-bit Firefox to realize there is wifi. 

I suspect it may have something to do with the 64-bit Windows driver that ndiswrapper is using. I got it from Linuxant.com. It is a Broadcom, although I don't remember the model number. I don't think the wifi module itself is the problem because it works just fine with everything except things running in chroot.

Right now I can use the original Firefox with wifi, in which case I get no RealPlayer. Or I can use 32-bit Firefox from chroot, in which case I get RealPlayer but can't connect by wifi.

Anyone have any idea how to tell 32-bit Firefox where to find the wifi?

---

### Post by John Jason Jordan on 2006-01-20
And now I have discovered something else. I wondered if other apps installed in chroot would be able to see the wifi. So I opened Synaptic32 and proceeded to install kmail (first thing my eyes lit on). But the download did not proceed. So I unmarked kmail and marked the mozilla mail and news suite. Same results. Then it dawned on me that Synaptic32 is inside chroot. That is the proof of the theory right there. Evidently nothing installed in chroot can see the wifi. No problem with ethernet at home, but as far as the chroot environment is concerned, the wifi does not exist.

So the question is, how to get chroot to see the wifi. Any suggestions at all?

---

### Post by John Jason Jordan on 2006-01-22
OK,  yesterday I discovered that it is a DNS problem. I don't have wifi at home, and Fireforx32 from chroot goes out to the net just fine over ethernet and my Comcast cable modem. It's only when away from home and dependent on wifi when I can't go anywhere.

Yesterday I was at a local Linux hangout (Free Geek in Portland -- awesome) and connected to their wifi. I launched 32-bit Firefox and still couldn't go anywhere. So then I opened a regular terminal window in the 64-bit world and pinged my university. It returned the IP address. Then I went into chroot and tried pinging my university by name again. This time it went nowhere. But when I replaced the name with the IP address, bingo!

So now I know the whole problem getting 32-bit Firefox in chroot to work with wifi is a DNS problem.

Someone local told me to look at resolv.conf. I opened resolv.conf in /chroot/breezy/32bits/etc and it says:

search comcast.net
nameserver 216.148.227.79
nameserver 204.127.202.19

Then I opened the resolv.conf file in /etc and it says exactly the same thing.

I'm too dumb to know what that means. All I know is that nothing from the chroot environment can go anywhere unless I specify the IP address. That includes Synaptic32, because I tried to install other apps via Synaptic32 while connected with wifi.

Does anyone know how to fix this?

---

