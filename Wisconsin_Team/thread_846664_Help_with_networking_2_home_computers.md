---
title: "Help with networking 2 home computers"
date: 2008-07-01
forum: Wisconsin Team
---

### Post by Garyb1 on 2008-07-01
Hi, I Have 2 computers 1 is a Dell laptop with wi-fi and the other is a 
dell desktop which has a hp5610 printer connected to it.
 I have a Belkin wirless N router, the desk top is connected to it by hardwire and of course the lap top communicates by wireless. What i would like to do is share folders, files and print from my laptop to the printer that is connect to my desktop. Both computers have Ubuntu ultimate 8.04 installed on them. the name of my laptop is connie@connie-laptop it was connie-laptop but when i added the domain named workgroup the name of the comptuer changed, the same for my desktop it was gary-desktop now gary@gary-desktop.

My laptop ip is 192.168.2.4
My desktop is 192.168.2.2

broadcast address is 192.168.2.255
subnet mask 255.255.255.0
default route 192.168.2.1
primary DNS  192.168.2.1
secondary DNS 0.0.0.0
hardware address: 00:16:44:6D:FF:70 Laptop
hardware address: 00:0B:DB:CD:F7:E2 dessktop

I am new to Ubuntu but i have used it enough to know i want to stay with it, i like it very much i have set up every thing myself this is the last thing i need to do to make things complete. Please could someone out there take some time out of their day and help me or right a step by step procedure a dummy could follow. i have spent 2 days trying to get it to work with samba but i have failed to get it to work. 

Thanks

---

### Post by lisati on 2008-07-01
When talking networking, before long, you'll start hearing about things like SSH and "samba"

There's a good tutuorial [here]("http://http://ubuntuforums.org/showthread.php?t=202605") that talks about Samaba. Don't be put off by the reference to Windows - many of the basics still apply

---

### Post by ridgeland on 2008-07-13
For our home network we don't use Samba.  We use NFS and ssh.

My wife has a script to log her into the shared directories on my PC (Music, Images, HerFolderOnMyPC).  Once logged in she sees those directories in Nautilus.

I use that, but also Places->Connect to Server which connects to her whole file system by logging in my ID.  I also use ssh to log into her PC on the CLI and vncviewer to, with her click of OK, take over her screen to show her how to do some task.

I don't think any of that is required for printer sharing.  Just when you set up the printer under System->Administration->Printing (I think) you tell the system if you want to make the printer visible to the network.  She has the better printer so her printer is shared.  It shows on my PC as available just like my local printer.

---

### Post by Ek0nomik on 2008-07-20
> **ridgeland said:**
> For our home network we don't use Samba.  We use NFS and ssh.

My wife has a script to log her into the shared directories on my PC (Music, Images, HerFolderOnMyPC).  Once logged in she sees those directories in Nautilus.

I use that, but also Places->Connect to Server which connects to her whole file system by logging in my ID.  I also use ssh to log into her PC on the CLI and vncviewer to, with her click of OK, take over her screen to show her how to do some task.

I don't think any of that is required for printer sharing.  Just when you set up the printer under System->Administration->Printing (I think) you tell the system if you want to make the printer visible to the network.  She has the better printer so her printer is shared.  It shows on my PC as available just like my local printer.

I have yet to see a printer function in Linux.  What kind do you both have?

---

### Post by ridgeland on 2008-07-21
"I have yet to see a printer function in Linux."  That's shocking!

My wife's PC has a Canon i560.  The driver is something else like B7000.
I had an Epson ColorStylus 777 but replaced it in June with a HP all-in-one 5610v.  Mandriva and Ubuntu both did all the installation for me, very easy.  The printer and scanner work fine.  I doubt I'll ever try the fax feature.
My Mom's PC (Ubuntu 8.04) uses a Canon LBP1260 an ancient black only Laser via parallel port. ($10 at the Living Hope thrift store in Eau Claire)  Works great except photos in grey tone are unimpressive.
The PC I set up for our church uses Fedora Core 4 (latest release when I set it up) with an Epson Action Laser 1000.  Another old black only Laser that works fine.

The only printer I could not get to work was a Lexmark. 
[http://www.linux-foundation.org/en/OpenPrinting](http://www.linux-foundation.org/en/OpenPrinting)
called it a paper-weight.  Even that may have a driver now.

---

### Post by Ek0nomik on 2008-07-22
> **ridgeland said:**
> "I have yet to see a printer function in Linux."  That's shocking!

My wife's PC has a Canon i560.  The driver is something else like B7000.
I had an Epson ColorStylus 777 but replaced it in June with a HP all-in-one 5610v.  Mandriva and Ubuntu both did all the installation for me, very easy.  The printer and scanner work fine.  I doubt I'll ever try the fax feature.
My Mom's PC (Ubuntu 8.04) uses a Canon LBP1260 an ancient black only Laser via parallel port...

Well, to be fair I have only tried to setup my girlfriends Dell printer, but that seemed to be a lost cause.  Although it was over a year ago, so perhaps something came out for it.

> **ridgeland said:**
> ...($10 at the Living Hope thrift store in Eau Claire)...

I bought a coffee table there just a few weeks ago for my house that I will be living in once school kicks up again.  :)

---

### Post by ridgeland on 2008-07-23
Hi Ek0nomik,
Before I dared to gamble $10 on a thrift store printer I checked 
[http://www.linux-foundation.org/en/OpenPrinting](http://www.linux-foundation.org/en/OpenPrinting)
to see if it would be a winner or a loser.  It got good marks so I went back for it the next day. It doesn't say "Toner Low" or anything so I suspect it was donated because someone replaced a PC only to find the new PC didn't have a parallel port and they could no longer use the laser.
I thought you were in near-by Eau Claire. :)

---

### Post by doudar on 2009-03-15
I've had very good luck with brother printers. At work we have a 9840CDW and for the price it's an awesome machine. It servers 5 people working out of a small office. It doesn't work with Ubuntu out of the box, but just follow the linux directions on their website and it's cake. Scan, print and fax all work for me. 
 
The best feature we like about it is that you can scan directly to email. It also duplex scans and prints, but we don't use that much. The only issue I have with it is that full page color prints (photos) will streak and blotch, but that's not really what we got it for anyway.

---

