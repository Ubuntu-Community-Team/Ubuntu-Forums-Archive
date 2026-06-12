---
title: "HOW-TO: Get Aiport Extreme Working on Dapper Dekkar(sp?)"
date: 2006-03-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by slooksterpsv on 2006-03-22
EDIT: EDIT: EDIT:
Ok you guys, I found out how to do this. Here's how I got mine working (see siggy). This works with my iBook so I hope it works with yours. It works 100% with mine now. So try it on yours, let's hear the results.


1 - Download and Install either Dapper Dekkar Ubuntu or Kubuntu (WILL NOT WORK WITH Breezy). You must partition your hard drive cause you have to get some utilities for Dapper.

2 - Once it is installed use OS X (or burn a cd) with bcm43xx-fwcutter.tar.gz - google for this or find it here maybe: [http://www.fisica.unipa.it/~lavaget/ubuntuae/](http://www.fisica.unipa.it/~lavaget/ubuntuae/) - and AppleAirport2, you get this by going here on OS X System/Library/Extensions/AppleAirPort2.kext/Contents/MacOS/AppleAirPort2 so go to your terminal and type in 
cd /System/Library/Extensions/AppleAirPort2.kext/Contents/MacOS
then 
cp AppleAirPort2 ~/Desktop/

3 - Go back to (K)Ubuntu and put your files on the Desktop (the bcm43xx-fwcutter-003.tar.gz and AppleAirPort2). Go to a terminal there (it's under accessories under Ubuntu and with Kubuntu you can type in xterm using Run in the start bar). Type in: cd Desktop/
This sets your current directory to the Desktop. Now type in tar -xvf bcm43xx-fwcutter-003.tar.gz or whatever the file was called. Now this will extract everything you need to there.

4 - Next go to Synaptic or Adept, Ubuntu and Kubuntu respectively. Install make and all the GCC and G++ programs.

5 - Back in the terminal after those have installed type in: cd bcm43xx-fwcutter-003/
then
make

6 - Next type in bcm43xx-fwcutter ../AppleAirPort2  this will create a bunch of .fw files.

7 - Type in: sudo cp *.fw /lib/firmware/ this copies all the fw files to that place.

8 - Type in modprobe bcm43xx

9 - Reboot

10 - Now that you have that done we'll start on enabling and getting wireless access. You need to know a few things. Well... the only thing you need to know is your channel and WEP, WPA, etc. Key.

---------Breathe, we're almost done---------------

10 - Now that we've breathed let's continue. Go to a terminal and type in these commands:

```

sudo ifconfig eth0 up -- replace the 0 with the # for your wireless card
sudo ifconfig eth0 192.168.0.15 -- replace 192.168.0.15 with the IP you need, so it may be 192.168.11.5 for the ip you want to use
sudo iwconfig eth0 channel 5 rate 11M essid ACTIONTEC key FAFAFAFAFA ap 00:15:05:03:E5:FA  -- Replace channel with the channel you are on, rate keep at 11M, essid is the name of the connection so I connect to ACTIONTEC Router, key if you have WPA or WEP keys, ap then the mac address, mine is shown above.
sudo route add default gw 192.168.0.1 -- the router is my gateway, so 192.168.0.1 is mine, yours may be different like 192.168.2.1, it's the same as the first three numbers of your IP address. 

```

You now have internet access.
[b]THIS WORKED FOR ME AND I HOPE IT WORKS FOR YOU.

---

### Post by slooksterpsv on 2006-03-23
Ok let's continue with this. I finally got it to work on a new installation. Here's how you do it:
Go to a terminal (xterm) and type in the following, putting in the info you have:
sudo iwconfig eth0 channel 5 rate 11M essid ACTIONTEC key FAFAFAFAFA mode Managed ap 00:15:05:03:E5:FA

EXCEPT change the channel to your channel, yes set the rate to 11M, set the essid as the ID of the wireless, our's is ACTIONTEC, key is your 64-bit or 128-bit encryption key, mode is Managed, ap mac:address:of:the:router

Next type in this:
sudo route add default gw 192.168.0.1

replace 192.168.0.1 with the router address, so yours may be 192.168.11.1


Finally, go into System Settings and go into Network Settings. choose eth0 configure it as DHCP now, and finally you can connect to the internet. I also added the DNS's in the DNS tab.

---

### Post by AlphaMack on 2006-03-23
Negative.  The FTP site for the bcm43xx snapshots is a bad link.

And I still get:

$ modprobe bcm43xx
FATAL: Module bcm43xx not found.

I guess the next question is:

What do I need to delete, edit, redo if I want to start over from scratch as if I never attempted this?  It seems there is something that is conflicting with the install.  Mind you, I did everything in this thread, the other thread, and that blog link.  Something is borked somewhere.

---

### Post by staticdisaster on 2006-03-23
Thanks man. this how to actually worked :D

---

### Post by slooksterpsv on 2006-03-24
[QUOTE=alphasubzero949]Negative.  The FTP site for the bcm43xx snapshots is a bad link.

And I still get:

$ modprobe bcm43xx
FATAL: Module bcm43xx not found.

I guess the next question is:

What do I need to delete, edit, redo if I want to start over from scratch as if I never attempted this?  It seems there is something that is conflicting with the install.  Mind you, I did everything in this thread, the other thread, and that blog link.  Something is borked somewhere.[/QUOTE]

Here's the file

---

### Post by AlphaMack on 2006-03-24
[QUOTE=slooksterpsv]Here's the file[/QUOTE]

Nope; no dice.  I'm suspecting that the softmac install outlined in that blog page did something to Dapper to make it no longer recognize or install bcm43xx.

---

### Post by AlphaMack on 2006-03-24
All right.  Reinstalled Dapper.  Everything working except for the WEP key.  Typing sudo iwconfig eth0 key (my 13 char key) is returning an error (invalid argument).  It must not like my selection of characters (there's a # sign in there at the end).

Edit:  I used iwlist eth0 scan to find my ap and used that for sudo iwconfig ap XX:XX:XX:XX:XX:XX.  I have an access point and the scan correctly identified my Airport Express.  I used Wifi-Radar and it saw all of the networks.  The thorn in the side continues to be WEP.  In System->Admin->Networking I used the default Hexadecimal option (is it supposed to be Plain?).

Maybe I need to test this on an open network.  Unfortunately, everyone with a router around here is smart and restricted their access.  I need to find a sucker with a linksys. ;)

I'm going to bed now.  I've spent enough hours tackling this.

---

### Post by slooksterpsv on 2006-03-25
The key has to either be 64-bit or 128-bit, which 64-bit is: FAFAFAFAFA
I think it has to be an even number. Try limiting your key to 5 pairs or 10 numbers instead of 13 characters

---

