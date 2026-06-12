---
title: "Why no &quot;clippy-the-LAN-wizard&quot; ?"
date: 2007-09-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by nss0000 on 2007-09-20
Gents:

We're all agreed that Lusr_land *nix admin tasks should NOT exceed a DOWNLOAD & INSTALL button ... and preferably be performed automagically with NO lusr input whatsoever. Just this morning, both my x32 & x64 Dapper kits got extensive automagic overhauls. I get a software list, say yes-to-everything ... zonk, the new stuff gleams as it should .

But Y-oh-Y is there no Ubuntu LAN autoconfiguration ? I can think of 3 reasons:

1) LAN is too high_value a function to be given away. It's CMA ...$$$ for the coders.

2) LAN is a rite-of-passage task ... the mad-dog Debiolian/Slackmolian mentality persists, so TABOO enforces among able coders.

3) {least likely IMHO} some needed interconnect information is actually not available to any one LANed system. That info must be known otherwise & manually entered.

So what's the truth?

---

### Post by tgm4883 on 2007-09-20
What?

---

### Post by Cappy on 2007-09-20
> **nss0000 said:**
> 

So what's the truth?

That you are smoking something really really strong.

Ubuntu supports DHCP. I assume this is what you're talking about. I don't know if you're saying it was working and now it isn't or if it isn't working on a new network. If it isn't working on a new network then that network doesn't support DHCP.

---

### Post by nss0000 on 2007-09-20
BigC:

Humm ... so it's (#2) answer you say. I have no idea what DHCP means, nor should I need to. 
I simply wish every hardware kit -- connected to my router -- to have promiscuously available the resources available to any.

---

### Post by John.Michael.Kane on 2007-09-20
> **nss0000 said:**
> BigC:

Humm ... so it's (#2) answer you say. I have no idea what DHCP means, nor should I need to. 
DHCP=Dynamic Host Configuration Protocol. Which is a set of rules used by devices such as a computer, outer or network adapter to allow the device to request and obtain an IP address from a server which has a list of addresses available for assignment.

> **nss0000 said:**
> I simply wish every hardware kit -- connected to my router -- to have promiscuously available the resources available to any.

From my understanding of what your asking. You want every data packet transmitted to be received and read by a network adapter or by every computer on the LAN.

To change your Ethernet adapter to work in promiscuous mode on a linux/unix environment. You can try the below method. You do so at your own risk as this is not tested.

As a root user please type the following command:  ifconfig ethx promisc

Being ethX the number of your adapter, for example if you want to do that on ethernet adapter 0 , then type: ifconfig eth0 promisc

---

### Post by dcstar on 2007-09-21
> **nss0000 said:**
> Gents:
.........
So what's the truth?

The "truth" is that there are other people in this forum other than "gents", and (IIRC) the Ubuntu install configures to use a DHCP server to save the user from any confusing Networking questions on install.

I do recall Networking questions being asked during Windows installs, but I'm not sure if the current Ubuntu install process does (I think that it doesn't).

In any case, the user still has to put in the manual network configuration if there is no DHCP, in Ubuntu it just has to be done after the install.

For the vast majority of Ubuntu users, using DHCP and not having a potentially confusing networking question during install is a benefit to them, and for the others they just have to do it a few minutes later via an easy GUI tool.

---

### Post by nss0000 on 2007-09-21
SDP:

No, not every data packet --- but on-request access to every file and application on every box attached to the LAN router. And why should I have to type something into the CLI ?  Configuring-the-system  is what I pay my OS to do.

As I remember, Dapperx64 asked precious_few questions while installing the 1st time - and basically nothing since. So an on-installation  QUESTION like ....

OH ALLWIZE RULER-OF-LUSRLAND YOUR HUMBLE OS SERVENT HAS INSTALLED AND CONFIGURED prudent_prunex64_LTS_2.8.4.2.67.4 AND ALL ALLIED APPLICATIONS. I HAVE ALSO IDENTIFIED TWO OTHER COMPUTERS CONNECTED TO YOUR ROUTER. MAY I ESTABLISH PROMISCUOUS RESOURCE SHARING AMONG THEM ? (y/n).  

... seems perfectly robust to me. And I expect it.

---

### Post by Mr_bleu on 2007-09-22
"*Configuring-the-system is what I pay my OS to do*.
[I]... seems perfectly robust to me. And I expect it.[/]
Ubuntu's free as far as I can tell.  Have you tried going back to windows?  Linux is NOT windows.
Most of the work done on the os is by volunteers.  I'm sure there are commercial versions out there, such as Suse/Novell that will be happy to take your money so you don't have to configure your os. <Or do minimal configuring>  Seems like you still want windows, though.:popcorn::lolflag::lolflag:

---

### Post by nss0000 on 2007-09-22
MRB:

Ubuntu may be "free-as-beer", but otherwise is quite expensive. I've used UBUNTU since v_5.x, and conservatively estimate my UBUNTU "opportunity costs" ( at $60/hr )  as :

                        $60*200 = $12000. 

For twelve-thousand dollars I rightfully expect a good deal of service from my OS. In particular going_forward I expect -- by superior Ubuntu innovation : 

1) polynomial increase in my own computing power
2) rapidly growing market share of fellow OS users
3) competitors ( M$ ) to be marginalized,

What haven't I made clear ?

---

### Post by a9k on 2007-09-22
$12,000 on installs? Are you driving one of those Geek Squad VW's yet?

Your original communication is opaque as to specific bits of software and functionality you think are missing. I'm still having a hard time understanding what you want. This could be because linux land is a vast area with many ways to do things. Choice is part of being free.

Are you asking for automatic Windows File Sharing? (like samba?) I hate it, almost never install it and would NOT want that automagically shoved on machines I'm installing.

Do you want something like Apple's BonJour (mt-daapd/firefly)? or UPNP? or to be able to name all the computers on your network (dnsmasq)?

What is it you want - be specific, precise and pretend we are all children that speak a foreign language - talk slowly. I think people are really curious about what you want but our brains exploded while reading the first post.

---

### Post by GavinZac on 2007-09-22
> **nss0000 said:**
> MRB:

Ubuntu may be "free-as-beer", but otherwise is quite expensive. I've used UBUNTU since v_5.x, and conservatively estimate my UBUNTU "opportunity costs" ( at $60/hr )  as :

                        $60*200 = $12000. 

For twelve-thousand dollars I rightfully expect a good deal of service from my OS. In particular going_forward I expect -- by superior Ubuntu innovation : 

1) polynomial increase in my own computing power
2) rapidly growing market share of fellow OS users
3) competitors ( M$ ) to be marginalized,

What haven't I made clear ?

for something like $125, cannonical do tech support. if you value your time at $60/hour, perhaps you should look into it.

---

### Post by nss0000 on 2007-09-22
GZ:

So ... your answer is (#1).  I believe you. 

A9K:

I had no idea "file sharing" had anything specifically to do with Window$. I do wish to be able to transparently "share" them ( read/write/modify/store ...) among all Ubuntu boxes  hooked to my router.

I wish to transparently access  hardware peripherals ( webcam/printer/scanner/external drives ...) ported to any Ubuntu box from any other Ubuntu box attached to the same router.

Sounds concrete to me , and surely LAN enabled somewhere for the last 20 years.

---

### Post by Cappy on 2007-09-22
I'm using Feisty and you can enable file sharing at System --> Administration --> Shared Folders. It isn't turned on by default because it would be a security threat if someone hooked up a box to the internet to get updated and it was infected. That is what happens if you install Windows.

---

### Post by Total_Biscuit on 2007-09-23
> **nss0000 said:**
> MRB:

Ubuntu may be "free-as-beer", but otherwise is quite expensive. I've used UBUNTU since v_5.x, and conservatively estimate my UBUNTU "opportunity costs" ( at $60/hr )  as :

                        $60*200 = $12000. 

For twelve-thousand dollars I rightfully expect a good deal of service from my OS. In particular going_forward I expect -- by superior Ubuntu innovation : 

1) polynomial increase in my own computing power
2) rapidly growing market share of fellow OS users
3) competitors ( M$ ) to be marginalized,

What haven't I made clear ?

I'll have a pint of whatever you're drinking!  It takes about 30 minutes to install Ubuntu.  So, at no point between the first and four-hundredth install did you ponder some more profitable use for your time?

---

### Post by nss0000 on 2007-09-24
T_Biscuit:

OOps my blunder. I started with RH_5 & SuSE, but UBUNTU 2.4.x ... so that's approx $12000 opportunity costs for all LINUX installs. A "hobbiest" ( which I am NOT ) would figure his/her costs differently. 
Yes, I ran my own business for years -- between teaching stints at university -- and know how to squeeze a $0.05 . Semi-retired now, but still teaching I roll-my-own kit. That saves money too.

As for the three (3) items ... who would not expect all three in a successful, growing concern ?  3% market penetration is not even a statistical fluctuation, so in the market *NIX has been doing something fundamentally wrong. 
IMHO Ubuntu strives to improve ... its' lusrs should NOT let "tradesmen" ( coders)  set their information processing agenda, but push hard for transparent function. 

Now  for the pint -- galpal prefers martinis, but they are not to everyones taste.

---

### Post by nss0000 on 2007-09-25
Oh yeah ...

This morning UBUNTU prompted, DLoaded , configured and installed the new v_2.6.15.x Dapperx64. Automagic. Flawless. Everything just works. Years ahead of M$. As it should be.

Perhaps the new Gnome is not far behind. 

Now about the LAN ... why isn't this point manifest and evident to all with concern and  affection for *NIX ?

---

### Post by kiwisparkles on 2007-09-27
OK, this is an internet forum. First off you need to understand a few basic rules.

Internet forums such as this one are frequented by people on a voluntary basis. We do not need to answer questions, and do it for fun/learning/whatever other reasons. If you come here and jump up and down screaming that something is terrible and needs to be fixed immediately, you will be offending many people who feel a personal allegiance/affinity to Ubuntu/Linux. This is perhaps a strange response from people, however this is what happens. You feel as if you have invested time into learning the system - how do you think the people who wrote it feel? When people feel offended and on the back foot, they will frequently strike back, as has happened in this thread. This is even more so the case when you come across as demanding that the Open Source Community bow to your demands immediately; I am sorry to say it but it makes you come across as a rather angry teenager (right or wrong). 

My advice is first off to take a deep breath. The people here do in fact want to see Ubuntu become a better OS, and for it to grow in market share. These two goals are complimentary, and require feedback such as yours for this to happen. This feedback needs to be somewhat more concrete, as networking in general is a very broad subject which involves many aspects. 

It appears as if you wish to be able to have access to all resources (data, webcams, printers etc) inside your network from each machine. I will go forward using this as an assumption.

Now, to get into more specifics. As a general rule most Linux (including Ubuntu) Distributions will turn off virtually all network services as standard. This is done so that people can bring their laptop or whatever to work or a foreign network and not be open to any forms of attack or data theft. I certainly wouldn't want other people to be able to access my data or resources without me specifying it as being OK. This is however a valid thing to want inside a known and trusted network. I just hope for your sake that you don't have wireless ;)

As was previously mentioned, data sharing is something which is commonly done inside a network, and for this you can do it through the "Shared Folders" option in the Administration submenu. There is a similar option for sharing installed printers across the network, but for the same reasons this is disabled by default.

So as a short answer, I guess that what you want is:
4. Leaving everything open by default is not secure and so is not done.

---

### Post by nss0000 on 2007-09-28
BigK:

Well stated points ---  for a particular class of UBUNTU users. Yet IMHO they miss the target. I think you're saying the answer is #2. That is, no Ubuntu LAN CLIPPY for SLUDs ( single lusr unsupported desktop ) so corporate_type IT admins can lax on their own security efforts. 

Oh the poor poos ... here's UBUNTU, a distro specifically "marketed" to SLUDS, and yet defaulting to corporate flavored behavior. No automagic LAN? Gee - maybe we should all compile our own kernels! Think I'm gonna gag. No wonder *nix can get only 3% of the home-desktop, a market where galpals access everything and security is insured by S@W only.

Make no mistake, CLIPPY-the-Ubuntu-LANWIZARD would immediately triple (x3) the number of home Ubuntu lusrs. I think that scares lots of byteboyz.

---

### Post by kakalaky on 2007-09-28
GUI for LAN configuration - It's in the system tray.
GUI for file sharing - System -> Administration -> Shared Folders
Gui for printers (including network printers) - System -> Administration -> Printing

Anything else you think there isn't a GUI for?

---

### Post by kiwisparkles on 2007-09-28
There are individual GUI's available for the configuration of individual options, but I think that the point here is that there should be another option given which will completely open your box up to the outside world including all functions that are available (be it printers, files etc).

I think that this is certainly an interesting one... Not really very responsible, but then few people in this world are. 

@nss0000: I am not sure if you realise this or not, but what you are suggesting here would not just open these functions up to other machines on your network, but to every computer on the internet. There is no means by which your computer can distinguish between other "trusted" PC's on your network and, for example, my one. This is the real reason that there is no such option available. It would give "hackers" (by the media definition) very easily the ability to access and control your machine. As such botnets are used for undesirable functions as spam, I can't see many developers lining up to give such an option.

I believe that you have a point in that there are some improvements that can be made in terms of sharing data inside a network. I have recently put together a box to be used as a file server to my Mac Mini (htpc), and franky getting shares from an Ubuntu box -> Mac has been anything but easy. It turns out that with CIFS sharing not only do you have to share the directory (using the pretty GUI), you also have to enable particular users to be able to login and access the data (which can only be done through the command line as far as I can see). This is something that I would like to see improved upon...

---

