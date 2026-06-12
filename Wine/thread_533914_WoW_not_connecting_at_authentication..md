---
title: "WoW not connecting at authentication."
date: 2007-08-24
forum: Wine
---

### Post by spikeblackwell on 2007-08-24
Thank you in advance for any help.

I have a fresh install of Ubuntu 7.4 and a fresh install of Wine on an older Alienware laptop. I followed the instructions in the HowTo to the best of my ability and I think everything there is as it should be. The game launches and seems to run fine except that at the point where I enter my account name and password and click 'Login', I get the little popup "Connecting..." window for a while and then I get the "Disconnected from server" popup. I have Verizon DSL with a brand new Westell 6100 modem that has a built-in router and I've watched it when I try to login to the game and the lights on it don't even flicker, so I'm assuming that the game either is not trying to talk to the network or it's being blocked on the PC itself. 

The PC has a good internet connection otherwise (I'm using it to post  this.) and I've had no other problems at all with the system running Ubuntu.

I have firestarter installed but I've tried it both with firestarter running and with it off and it seemed to make no difference. I've also set port forwarding on the router per the HowTo and again, it made no difference.

If you have any ideas, I sure would like to hear them. If I need to provide further details, please let me know. If I can't get WoW running, it'll be a major blow to my "No More Windows!" decision.

Thank you,
Spike.

---

### Post by MemoryDump on 2007-08-24
was it working fine under Windows? (if you are using the same system?)

are you able to to a traceroute to WoW's authentication server?

```
traceroute us.logon.worldofwarcraft.com
```
you might have to install traceroute since it's not installed by default.

---

### Post by spikeblackwell on 2007-08-25
Thank you for your help, I think I have discovered the problem.

I did not have WoW installed when I re-partitioned the drive and installed Ubuntu. Then I had issues with Ubuntu installing off my WoW/BC CDs, so to save time I just "borrowed" the entire WoW directory from a friend of mine who plays and copied it to my PC.

Well, apparently my friend's install was corrupted at some point and he made some modifications to some config and/or .ini files. I didn't know about that when I asked for the copy. I'm willing to bet this is the cause of my problem.

So, I've wiped that directory out and now I'm installing from the trial downloads off the Blizzard site Just to make sure that everything is current and standard. I'm pretty sure that will fix things. If not, I'll post again.

Thanks again,
Spike

---

### Post by angryforumreader on 2008-01-29
Honestly I see this as a real problem to lots of WoW players.
I just installed ubuntu 7.1 a few days ago, went on to install wine straight away and copied my WoW folder over from installed version on windows.
WoW started up properly to the login screen. When i enter my login and password i get a "disconnected from server" straight away. 

I tried:
traceroute us.logon.worldofwarcraft.com
gives:
traceroute: icmp socket: Operation not permitted

I tried:
sudo traceroute us.logon.worldofwarcraft.com
gives:
traceroute: unknown host us.logon.worldofwarcraft.com

I'm sure that is the reason why I get dc-ed straight away, there was no access to that server. (meaning there is no route to that server?)

I've been looking through every forum on google and all the various ubuntu forums regarding this but the thread always run into a dead end with no replies. I hope this very thread will lead to somewhere for all the wow players out there wanting to to play wow on linux.

Ubuntu does not block any traffic by default from what i read from this thread [http://ubuntuforums.org/showthread.php?t=43273&page=1](http://ubuntuforums.org/showthread.php?t=43273&page=1)

so why the inability to access the wow server?

---

### Post by Vadi on 2008-01-29
I think something might be wrong with that command - because it's not installed by default in Ubuntu (at least I don't have it, and I don't recall removing anything of that kind.. because it wants to uninstall "ubuntu-desktop" everytime and I sorta need that).

**sudo tracepath us.logon.worldofwarcraft.com** worked though, want to give that a try?

---

### Post by angryforumreader on 2008-01-29
sudo traceroute us.logon.worldofwarcraft.com
gives

traceroute: unknown host us.logon.worldofwarcraft.com

which to my understading means i cannot find a route to the server. This explain why I couldn't connect so anyone can help? I can surf the  net and go onto msn on ubuntu.

I don't see how when i can access so many things online just that i cannot connect to wow.

btw my sudo traceroute us.version.worldofwarcraft.com
actually gives me the routing so I'm really confused why
us.logon.worldofwarcraft.com just rejects me straightaway.

---

### Post by Vadi on 2008-01-29
> **Vadi said:**
> **sudo tracepath us.logon.worldofwarcraft.com** worked though, want to give that a try?

   ^^^^^

---

### Post by angryforumreader on 2008-01-29
woops sorry. I misread tracepath as traceroute
tracepath works to my surprise...

so it has nothing to do with ubuntu's access to the server. So it got to do with how i installed wine then. I'll try again tonight.

Thanks for pointing that out ^^

Edit: I'm lost at how I should install wine such that it let wow connects, If the problem doesn't lie with wine then where does it lie?

---

### Post by angryforumreader on 2008-01-30
now Im really lost and frustrated. almost 3 whole night browsing forums late into the night.

tracepath us.logon.worldofwarcraft.com
gives
gethostbyname2: Unknown host

it worked this morning. All I did was uninstall wine and reinstall.
Now i really lost all hope. Nothing recognise us.logon.worldofwarcraft
.com anymore.

ping says unknown host
tracepath says unknown host 
tracepath says unknown host

what the hell is wrong is wrong with the system.

Edit: I tried booting ubuntu from the Live CD. I notice 
tracepath us.logon.worldofwarcraft.com also doesn't work

Now I'm gonna do a thorough reinstall of ubuntu though I'm sure I'm going to be facing the same problem

---

### Post by hikaricore on 2008-01-30
Unknown host sounds like a problem with your ISP or at the very least your modem/router.

---

### Post by angryforumreader on 2008-01-30
The thing is whenever i switch back to XP (i have a dual boot) I play WoW fine.
I can type tracert us.logon.worldofwarcraft.com and get a route

when I log into ubuntu environment I'm cut from WoW totally.
tracepath us.logon.worldofwarcraft.com will just yield unknown host

I just finish doing a clean install of ubuntu again. Updated the components installed wine, got WoW to run to its login screen and the minute i enter my password it says disconnected from server.

It is like I'm totally blocked by ubuntu somehow. I read almost all the forums out there regarding this still no answers.

I've however had a freak case when I tried tracepath and it worked but going to run WoW immediately still doesn't connect me.

Please Please Please anybody out there solved this problem? I'm running Ubuntu 7.1 and newest version of wine too. I don't see why everyone can safely install and play right away and I have to go through such torture because of some strange network problem. Has it got to do with ubuntu 7.1?

---

### Post by ov3rcl0ck on 2008-01-30
when you install wine it doesnt include all of the windows components all you have to do is add some more dlls to wine.

---

### Post by angryforumreader on 2008-01-30
mm yea but i found the root of my problem.

I connected my laptop to the cable modem directly and wow works.
What had been preventing me from playing wow was my router after all. 
What I don't understand is why doesn't my router block me in XP but in ubuntu?

anyone?

---

### Post by Vadi on 2008-01-30
Give this guide a try:

[http://feeds.feedburner.com/~r/Fsckin/~3/203831103/](http://feeds.feedburner.com/~r/Fsckin/~3/203831103/)

---

### Post by angryforumreader on 2008-01-31
hate to say this but that guide was as useless to me as any other guides i've read through again and again.

My problem lies on the router as I said.

I tried connecting directly to the cable modem yesterday night and wow actually worked. I logged on and played fine.

Now the problem is I cannot have the modem to my own since theres like 2 more computer in my home that needs the router on the modem to get connection. Yet through the router I'm completely blocked.

Yes i know there will be ppl pointing me to port forwarding which i know how to do. Wow uses 6112, 3724, 6881-6999 on TCP

To port forward just set a static ip(just google setting static ip) and go to the router and add to the allow list (opening the port). Yes my ports are open i opened 6112, 3724, 6881. (my router has no range port opening so I used some kind of port triggering in the firmware of the router) 3724 to trigger 6881-6999.

Anyway I'm at wits end again. I know my router somehow cut my connection in ubuntu to wow yet I have no problem playing wow in XP. Obviously no logic in this. This definitely became a network problem in ubuntu

I've heard of the term SSH tunneling to bypass firewall. Someone have a good guide to that? I read a good ssh tunneling guide

[http://www.macosxhints.com/article.php?story=20060831091645414](http://www.macosxhints.com/article.php?story=20060831091645414) unfortunately it still doesn't work I dunno why
Is there any other way of making my router let me play wow? Only through the router do i experience problem with running wow on wine. namely cannot get pass login stage (disconnect immediately)


HELP!!

---

### Post by angryforumreader on 2008-02-01
summary what i want to know is what is the essential difference when i connect through a router as oppose to a cable modem

I played fine with my ubuntu linux box connected to the cable modem directly but I cannot get pass the log in screen when i go through the router. It just shows 'disconnected from server' without even showing connecting.

another thing is I play through router fine when Im on window xp on the very same laptop. And yes I portfwd 6112, 3724, 6881

help anyone!!

---

### Post by Vadi on 2008-02-01
Have you tried using Firestarter? Get it from Add/Remove, launch it. And try stopping your firewall and connecting again.

---

### Post by angryforumreader on 2008-02-02
erm I stopped firewall using firestarter and still no connections

I notice that my wow client has access to the breaking news whereever it came from.

So,,, anyone has any idea how my router is blocking my connection? What kind of information do i need to look at?

I'm using a static ip 192.168.0.121 and portforwarding 6112,3724, 6881 on both tcp and udp on the router.

I just tried putting my ip 192.168.0.121 on DMZ (demilitarized zone) on my router and putting down my firewall with firestarter. (yes very dangerous I'm essentially removing all blocks to outside traffic)

Still I couldn't connect to wow. It just says "Disconnected to server" like it was told the wrong address to connect to in the first place. I'm beginning to wonder if it is some kind of setting that is confusing my wow client on ubuntu. Then again I remind everyone that with this setting I could connect to wow when I connect directly to my cable modem instead of the router. What is wrong. I've been on this problem for almost 5 days now. I can run MSN, surf net, run MIRC on wine (with connection) just wow giving my trouble with connection.

---

### Post by angryforumreader on 2008-02-02
YES YES THE ANSWER IS HERE

Those that are on router and cannot play wow because you keep getting "Disconnected from server" once you type in your login and password I have the SOLUTION!

I'm not sure why this works (maybe someone can make it out but here goes)

Firstly go to manually configuration of your connection where you see 4 tabs Connection, General, DNS and Host

Go to DNS and you probably see the 192.168.0.1 (or something similar that is your default DNS for your router and your router's ip)

Now open a browser and type in 192.168.0.1 (or the DNS you use for router) This is to go into your router configuration place. Browse around for your WAN status

This is mine It will go something like this (It should probably be visible somewhere in your router configuration)
WAN
MAC Address: <MAC address of my router>
Connection: DHCP Client Connected  
IP Address: <my actual internet ip from cable modem>
Subnet Mask: <my actual subnet>
Default Gateway: <my actual default gateway>
DNS: 202.156.1.78 
        202.156.1.68 
        218.186.1.88

get that 3 DNS address and add them to your DNS list on your connection configuration. 

Now you should be able to play wow just like normal (like how you play on XP)

---

### Post by Vadi on 2008-02-02
Nice!

---

### Post by darthn00bius on 2009-05-28
That is obviously a DNS resolution issue.  I'd bet money that your Windows XP NIC is manually configured with a public DNS server that can resolve us.logon.worldofwarcraft.com successfully.  Your Ubuntu configuration probably did not have that... thus, when you configured the manual DNS servers in your router, it started working.

This is most definitely a problem with your ISP.  Your ISP's DNS servers don't have a correct route to the WoW servers.

I just experienced this problem today (I use verizon FiOS in NJ).  Adding the DNS server addresses you suggested to my Windows XP NIC Config resolved the problem.  This is just a work-around though.  If those DNS servers ever crash or change IP addresses, we will be SOL and possibly even worse off than square one if you don't remember you set those static DNS addresses.

You should contact your ISP and tell them what the problem is.  I plan on doing that for mine.

Cheers.

Aaron Cervasio
MCSE 2003

---

