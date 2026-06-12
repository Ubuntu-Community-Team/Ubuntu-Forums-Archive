---
title: "Networking between 1 OSX machine and 1 Ubuntu ppc."
date: 2005-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by tslager on 2005-10-25
Ok.  So I know that this is a common question, and I have read every thread here and elsewhere that I can find on it, but how the heck do you make this work?  I am somewhat new to Linux, as will soon become apparent, but have tinkered with UNIX in os x.  I cannot get samba to work, though it is on the G4 tower running os x and the G3 iBook running Ubuntu (both are wired through a D-link router)  In OS X I can see the Ubuntu machine in the network browser, but when I try to connect the finder freezes indefinitely.  In Ubuntu, when I browse the network it tells me that I have to log in to see 192.168.0.100, which is the os x machine's local ip, so i know it "sees" it, but no matter what I  enter it will not let me in.

Also, I tried the latest Netatalk, which just about killed me to install.  But I did get it to install with "./configure --enable-debian" which someone on the forums here suggested.  I can't tell that it is doing anything at all.  I don't even know if it started when I rebooted the machine.  Do I have to do something additinal after installation?

Basically, here is what I need:  A simple network between two computers through a router, with the ability to share a USB printer from one the machines.  I don't care about speed or anything.  Just a simple GUI through which to share files.  I could even pass on the printing if I had to.  If anyone can direct me to a tutorial, or to a program, I would be eternally gratefull.

Also, should something like this be this hard?  If Ubuntu is meant for the end user, should very simple networking tasks require a great deal of time in the terminal and on user forums?

Thanks in advance to anyone who responds.

---

### Post by pauljwells on 2005-10-25
Actually, if you poke around a bit on these forums you'll find that samba is a real pita  on ubuntu. That said, I obviously got lucky with my setup (well, one of them) which is a Mac PB running OSX and a PC running Breezy, (I think the fact that your ubuntu machine is also ppc shouldn't make any difference). The mac is just set with windows sharing from the control panel and the PC has samba running with smb.conf posted here [http://ubuntuforums.org/showthread.php?t=79763](http://ubuntuforums.org/showthread.php?t=79763) in dapper developer  (make sure you pick my smb.conf, not vvlist's)

I can then see my ubuntu machine in 'Network' in Finder, and the mac in 'Network Servers' in Nautilus

I always found that you can avoid a lot of problems by shutting down all your machines and the router. then restart the router and each machine in turn, allowing each one to start and settle down before going to the next one. Maybe just superstition?!

There is an excellent site that explains how to print from your mac osx on a windows printer and this setup worked straight away for the ubuntu printer. [http://www.ifelix.co.uk/tech/index.html](http://www.ifelix.co.uk/tech/index.html)

Good luck

---

### Post by evil-boweevil on 2005-10-26
There is a problem with the version of samba included in Ubuntu.  You will not be able to connect to a shared folder from Tiger.  You need to upgrade it to 3.0.20.  I did that by adding a debian testing repository to aptitude and then upgraded samba to 3.0.20.  Works great now.  I'm not sure about PPC specific repositories though.

---

### Post by ipn1nj4 on 2005-10-27
I often connect my Tiger laptop to my ubuntu SMB server. Setup takes just a few minutes. 

One thing I think people forget about is the fact that you need to create a samba user for authentication
```

smbpasswd -a joeblow
```

Then use those creidentials when you map to a share through finder

```

smb://ip-of-server/sharename

```

---

### Post by tslager on 2005-10-27
Alright, so last night I went through and followed everyone's advice, and then my internet went down and I went out for a few drinks and just shut everything down: computers, modem, router, everything.  This morning I started everything up and suddenly I can connect both computers to each other.  Oddly, I think I am using samba to connect Ubuntu to OSX and Netatalk/Appletalk to connect OSX to Ubuntu.  Unfortunately I tried about 10 sollutions with very little testing in between so I don't know what exactly did the trick : (

Anyway, thanks for all your help.  And, re-reading my original post, I came off as a bit of an ass hole.  Sorry about that:???:

---

### Post by pauljwells on 2005-10-27
hi tslager

can you elaborate on this a little? Do I just type this at a terminal? can I include it in smb.conf? how does it all work?

thx

---

### Post by BloGTK on 2005-11-01
I've had the very same problem. Hoary worked fine, but after I upgraded to Breezy every time I try to make a Samba connection, the Finder completely locks up. Sadly, I thought that 10.4.3 would take care of it, but no luck there.

From what I've heard, upgrading Samba does fix the problem, but I'd rather not add packages from other repositories unless I have to.

---

### Post by yjsoon on 2005-11-11
I'd just like to confirm -- Samba sharing is broken between OS X Tiger 10.4.3 (running samba 3.0.10) and Breezy (samba 3.0.14a-Ubuntu), yes? I'd just been trying for a while to get sharing working between the two before stumbling upon this thread.

Any idea which versions of Samba on each would actually be compatible? I'm not averse to mucking around with foreign packages on either of my computers.

---

### Post by peter taffs on 2005-11-14
I use OS X Tiger 10.4.3 and have just dist-upgraded my headless server to Breezy. It seems to have broken browsing the Ubuntu machine from the mac, ie picking Network, browsing my Workgroup (Cactus) to the server and pressing "Connect" causes a hang in finder.

I have since found using the Apple key-K option (Go, Connect to server) and using the URL smb://icecube/peter works (my machine is icecube and mount-point is my user's home directory). Also, smb://peter: password1@icecube/peter makes the connection. the machine is defined in /etc/hosts so an IP address might be required otherwise. The icecube machine has other shares defined in smb.conf, so I'm used to browsing.

---

### Post by ssam on 2005-11-14
If you want to avoid typing ip addresses try this.

[https://wiki.ubuntu.com/HowToZeroconf](https://wiki.ubuntu.com/HowToZeroconf)

it should be uptodate, but let me know if you find any bugs in it (or just fix them :-) )

---

### Post by rplantz on 2005-11-30
[QUOTE=peter taffs]I use OS X Tiger 10.4.3 and have just dist-upgraded my headless server to Breezy. It seems to have broken browsing the Ubuntu machine from the mac, ie picking Network, browsing my Workgroup (Cactus) to the server and pressing "Connect" causes a hang in finder.

I have since found using the Apple key-K option (Go, Connect to server) and using the URL smb://icecube/peter works (my machine is icecube and mount-point is my user's home directory). Also, smb://peter: password1@icecube/peter makes the connection. the machine is defined in /etc/hosts so an IP address might be required otherwise. The icecube machine has other shares defined in smb.conf, so I'm used to browsing.[/QUOTE]

I have the same experience.

One of the problems I had was that the names used in the various posts varies. For example, computername, host, sharename, etc. I finally figured out that in the command:
```

smb://hostname/sharename

```
I need to use the hostname command on my ubuntu machine to get hostname. Then sharename is the word I invent for a section in my /etc/samba/smb.conf file.

For example, if I do ```

bob@abc:~$ hostname
abc
bob@abc:~$ 
```

and ```

[ijk]
       comment =  whatever you want here
       writable = yes
       path = /home/bob/cars
       public = yes
       create mask = 0664
       directory mask = 0775

```
then as user bob I can mount the /home/bob/cars directory on my Mac (OS X 10.4.3) by using Go-->Connect to Server and entering ```

smb://abc/ijk

```

I was having lots of trouble figuring out where the names came from: which ones are perhaps keywords, which ones do I invent, where do they get declared, etc.

---

### Post by talz13 on 2005-12-19
So updating to a new version of samba fixes the problem?  I just discovered this last night when I tried to access my ubuntu shares from my mini (10.4.3) and finder just kept locking up hard.

---

### Post by athena on 2005-12-23
mind if I jump in here?
I am trying to set up a Mac running OSX (10.3.9) and a pc running Ubuntu 5.10 to share files on a simple home LAN, but I keep running into glitches.  I am just learning Ubuntu and know even less about file sharing, so I am sure the problem is mine and not the machines I am working with.  Is there somewhere I can find detailed step by step instructions for this?  All the info I can find is either specific to a different version of OSX, is for Mac/pc networking, or is way to technical for my skill level.  Can someone help? 

thanks

---

### Post by dombleu on 2005-12-23
I'm not a linux networking specialist, but for me, little just-user, ssh have been the easiest solution since many years. And it is gracefully handled by nautilus and konqueror. 

Install openssh, set host name on each machine and type in nautilus for instance, after a ctrl-L:

ssh://usernameonthatmachine@hostnameonthatmachine

NFS and Samba might have nice features wich I don't know. But for me ssh did the trick...

edit: but is ssh available on osX? It seems so...
[http://www.ocf.berkeley.edu/~phlee/ssh-osx-howto/ssh-osx.html](http://www.ocf.berkeley.edu/~phlee/ssh-osx-howto/ssh-osx.html)

---

### Post by yjsoon on 2005-12-24
[QUOTE=athena]mind if I jump in here?
I am trying to set up a Mac running OSX (10.3.9) and a pc running Ubuntu 5.10 to share files on a simple home LAN, but I keep running into glitches.  I am just learning Ubuntu and know even less about file sharing, so I am sure the problem is mine and not the machines I am working with.  Is there somewhere I can find detailed step by step instructions for this?  All the info I can find is either specific to a different version of OSX, is for Mac/pc networking, or is way to technical for my skill level.  Can someone help? 

thanks[/QUOTE]

What kind of glitches are you running into? As far as I know, Samba support on 10.3.9 is pretty similar to that on 10.4. Try connecting with the Finder's "Connect to" feature (Go->Connect To Server..., then smb://hostname/sharename), that seemed to work for me even in the old 10.2 machine.

---

### Post by athena on 2005-12-27
Hi, sorry about the delay in my response.  Just been very busy.  
What happens is that after I make sure samba is set up on the Ubuntu box, I set up a folder for sharing, then I go to system preferences/sharing on the OSX machine and make sure that personal file sharing is turned on,  and then I go back to system prefs and click the Network icon.  I select network status from the drop down list box, and then I am supposed to make sure I am on the same network as the Ubuntu box.  That is where it all comes to a screeching halt, because it does not show that I am connected, and when try to configure it, I don't know how to find out the router address.  That is as far as I have gotten with this.  So how do I find out that router address? and thats not all, because now there is a new MacOSX server icon on my desktop that I did not put there.  I have no idea how that happenned, but if I click on it, it opens up to a folder with a bunch of .dmg files for open office.  That seems strange because when click on go to server in Finder, it opens up to a connect to button box with an open office ftp server address already pasted in.  I have no idea what that is all about, because I rarely use open office on this Mac, and I have never even tried to use it to transfer files.  So what is going on?

thanks

---

### Post by yjsoon on 2006-01-02
Sorry about my delay in responding, too. I'm not entirely sure what to make of your situation, but here goes:

[QUOTE=athena]
What happens is that after I make sure samba is set up on the Ubuntu box, I set up a folder for sharing, then I go to system preferences/sharing on the OSX machine and make sure that personal file sharing is turned on,  and then I go back to system prefs and click the Network icon.  I select network status from the drop down list box, and then I am supposed to make sure I am on the same network as the Ubuntu box.  That is where it all comes to a screeching halt, because it does not show that I am connected, and when try to configure it, I don't know how to find out the router address.  That is as far as I have gotten with this.  So how do I find out that router address?
[/QUOTE]

First, check if your Mac is online (since you say it "does not show that you are connected"). If it's a wired connection, is the wire fully plugged in? Is your wireless on if you're using AirPort? If connected, it should tell you that your wired or wireless connection is connected to the internet. Click on that and it will give you your IP address.

Next, check your router's home page (you mentioned you're running a home network). If you don't know what it is, look up your router's manual and look for information on the router home page.

> 
 and thats not all, because now there is a new MacOSX server icon on my desktop that I did not put there.  I have no idea how that happenned, but if I click on it, it opens up to a folder with a bunch of .dmg files for open office.  That seems strange because when click on go to server in Finder, it opens up to a connect to button box with an open office ftp server address already pasted in.  I have no idea what that is all about, because I rarely use open office on this Mac, and I have never even tried to use it to transfer files.  So what is going on?


That looks like you (or someone else) connected to a fileserver (FTP) site to download OpenOffice. When you click on "Go to server" in the Finder, it will default to the last address that's opened. Don't worry about it. This problem should have been solved if you've just rebooted your Mac since posting this message a few days ago; otherwise, you can drag the server icon to the Trash to disconnect.

Hope that helps.

---

### Post by lobo on 2006-02-09
I had the same problem as allot of people when trying to connect Tiger 10.4 to Ubuntu Breezy, OSX would freeze up, good old beach ball of death I think its called.
Any way while Samba definately seems broken for Breezy it only seems to be browsing which is affected so while my attempts to connect to ubuntu using 

smb://192.168.1.10

did not work connecting directly to the share like this:

smb://192.168.1.10/music

did work, bringing up the authentication window, I have it set for guest so just hitting return with no credentials did the trick.

I can live without being able to browse until Dapper and this solution was not spelled out for me in earlier posts - I had thought there was no way to connect at all without upgrading Samba - so hope this helps someone get connected.

---

### Post by WelterPelter on 2006-02-20
upgrade to the new samba. This fixes the problem. I connect to my ubuntu machine with a couple of boxes running osx, and couldn't make it work until I got samba 3.0.21

Add this line to your synaptic sources and you will be able to upgrade:

[http://us5.samba.org/samba/ftp/Binary_Packages/Debian](http://us5.samba.org/samba/ftp/Binary_Packages/Debian)

Then open your keychain in the osx machine and delete any references to samba. Then try to connect and it should work fine.

---

### Post by jclark on 2006-02-26
[QUOTE=WelterPelter]

Add this line to your synaptic sources and you will be able to upgrade:

[http://us5.samba.org/samba/ftp/Binary_Packages/Debian](http://us5.samba.org/samba/ftp/Binary_Packages/Debian)

Then open your keychain in the osx machine and delete any references to samba. Then try to connect and it should work fine.[/QUOTE]

What does this look like in your /etc/apt/sources.list file?  I'm running server without X so don't have synaptic.  There's no dists/breezy at the above URL, and I can't quite figure out the sources.list entry I need.

Thanks,
Jason

---

### Post by WelterPelter on 2006-03-09
Here's a sources.list entry I believe will work for you: 
deb [http://it.samba.org/samba/ftp/Binary_Packages/Debian](http://it.samba.org/samba/ftp/Binary_Packages/Debian) sarge samba

---

### Post by jclark on 2006-03-09
Cheers, WelterPelter.  That worked perfectly for me.  Upon updating my samba  install, I can browse my shares from the OS X finder without issue.

Jason

---

### Post by WelterPelter on 2006-03-09
[QUOTE=jclark]Cheers, WelterPelter.  That worked perfectly for me.  Upon updating my samba  install, I can browse my shares from the OS X finder without issue.

Jason[/QUOTE]

You're welcome. Glad to be of service.

---

### Post by CeeJayCee on 2006-03-10
I can confirm that this works too. 

Thanks everyone, I spent about two hours last night playing with the config and master browser settings trying to get this to work :)

---

### Post by jamerson on 2006-04-12
Hi all!
I seem to have the same problem here.
But the sources.list line does not work. Anyone knows what to do?
It just says: Couldn't stat source package list...

---

### Post by dpny on 2006-04-12
[QUOTE=jamerson]Hi all!
I seem to have the same problem here.
But the sources.list line does not work. Anyone knows what to do?
It just says: Couldn't stat source package list...[/QUOTE]

I'm having the same problem: there is no PPC binary. Is there a solution for this?

---

