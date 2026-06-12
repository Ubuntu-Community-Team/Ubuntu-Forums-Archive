---
title: "Wifi"
date: 2006-04-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by string on 2006-04-02
I have an iBook G4.

I installed breezy on it and upgraded to Dapper (via dist-upgrade).
That's all I did.
What do I need to do now to make the wifi work ?
Thank you

---

### Post by aimislame15 on 2006-04-02
Here are the exact steps (worked for me multiple times on 3 different machines. (iBook, G5, and TiBook)). 

First, you need to use Synaptic or apt-get to get:

subversion
gcc
g++
make

Then, go to terminal and enter each one of these codes separate from eachother.

```

svn checkout svn://svn.berlios.de/bcm43xx/trunk/fwcutter
cd fwcutter
make
wget http://www.ghostcorp.net/AppleAirPort2
./bcm43xx-fwcutter AppleAirPort2
sudo make installfw
```

You might want to reboot for fun. Sometimes, I didn't have to, sometimes, I did. 

Now you're ready to set it up with a script. Easy way to make it in is gedit (Text Editor).

```
#!/bin/bash
interface=eth0 # interface of your wireless card
# Turning off wired network...
ifconfig eth1 down
modprobe bcm43xx
# Starting up wireless network...
ifconfig $interface up
iwconfig $interface essid MY_ESSID
iwconfig $interface mode managed
iwconfig $interface key off
dhclient $interface
```

Now that you have this script, you need to make it read/write-able. So go back to console and type this:

```
chmod 777 myscript
```

Make sure you set the script up to par. My script is basically the sam as the one aforementioned, with only a few tweaks. When I go back down the hall to my iBook, I'll post my script. To run the script, do the following command.
```
./myscript
```

The script should hook you up with an IP from your wireless router.

All credit goes to spaceballl for making the original tutorial.

For the record, can we get someone to sticky this so the question doesn't keep coming up?

---

### Post by aimislame15 on 2006-04-02
Here is my script direct from my iBook G4.

```

#!/bin/bash
interface=eth0
ifconfig eth1 down
ifconfig $interface down
ifconfig $interface up
modprobe bcm43xx
iwconfig $interface essid "Apple Network 7dafac"
iwconfig $interface mode managed
iwconfig $interface key off
echo "Setting up DHCP"
dhclient $interface

```

To make it even easier on myself, I created a custom application launcher on my menu bar. (Right-click or F12) and then click "Add to panel". After that, click "Custom application Launcher".  Name it whatever you want. The command should be something like

sudo /home/eric/myscript

Then, make sure you click run in terminal.

---

### Post by JackosKing on 2006-04-02
Hello, does it work with WEP 128 Bits key?
Airport is the only limit :/

---

### Post by string on 2006-04-02
Thank you... a lot..

I'll try this as soon as I have a couple of minutes to spend on my mac.

Couple of questions though:
- why 777 mode for the script ? is there a specific reason, or is it just a brutal way to say "dont bothert me with rights", because 777 is not safe, 755 or 711 could do the trick already (even 111 :p), but maybe I am missing a good reason to give 777...
- this iis probably because of my crappy english, but what do you mean by "Make sure you set the script up to par." ?

Last question, if the network I want to connect to is protected by WEP, what will happen, and where should I enter this key ?

Thanks again, you are my savior (and yes, a sticky would be cool ^_^)

---

### Post by aimislame15 on 2006-04-02
777 because I just dont like being bothered with rights... so I'm willing to risk a bit of security. If you want security that bad, don't use wireless (or connect to the internet for that matter, then you're unstoppable :P). There are too many ways to steal peoples bandwidth and traffic with wireless. I have no idea how WEP/WPA codes work with the airport but here is (I believe) how to input them.

Add this line to your script:

```
iwconfig $interface key KEY_HERE
```

By the way, none of the thanks should go to me. The thread which I used as a template to make a template (how ironic) is buried a few pages back, created by spaceballl. You should look him up and thank him.

---

### Post by string on 2006-04-05
[QUOTE=aimislame15]777 because I just dont like being bothered with rights... so I'm willing to risk a bit of security. If you want security that bad, don't use wireless (or connect to the internet for that matter, then you're unstoppable :P). There are too many ways to steal peoples bandwidth and traffic with wireless. I have no idea how WEP/WPA codes work with the airport but here is (I believe) how to input them.

Add this line to your script:

```
iwconfig $interface key KEY_HERE
```

By the way, none of the thanks should go to me. The thread which I used as a template to make a template (how ironic) is buried a few pages back, created by spaceballl. You should look him up and thank him.[/QUOTE]

OK. Si I did all the stuff I was told to do.
The Wifi os obviously working ... up to a point :/ :
-The MAC address of the card is fine. So it means the system knows at least a bit the hardware.
-When I launch some software like wifi-radar, the networkd are detected : I see my own network as much as other networks from my neighbours. I see my is locked by a key.
- I ask to get a IP address but DHCP gives me nothing while it works fine on OSX (== the network is fine). I copied the WEP key in the appropriate section , nut it doesn't change a thinf.
I also tried to enter my own IP with mask, gateway and dns but it doesn't seem to be any more efficient

---

### Post by aimislame15 on 2006-04-05
You've got to remember that this is the bleeding edge of technology. I'm sure it's not easy to just reverse engineer a piece of hardware. That said, there is no application (that I know of) that will hook your airport up to a network. I'm not sure what to do abuot WEP/WPA as I never use/have used it.

---

### Post by nargilamonster on 2006-04-05
[QUOTE=aimislame15]Here are the exact steps (worked for me multiple times on 3 different machines. (iBook, G5, and TiBook)). 
[/QUOTE]
Have you tried this solution only with Airport Extreme Cards? I want to utilise my Aiport card, it seems to be partially supported already, but almost all of the code/solutions I've seen to enable full functionality seem to be for the Airport Extreme

---

### Post by aimislame15 on 2006-04-05
As far as I know, the regular airport is fully supported in the Networks control panel. I don't use gnome (xfce4 instead)on my file server (iMac Graphite 500mhz upgraded to 80gb HD) but it hooks up with my network right off the bat. I haven't had a single issue yet.

---

### Post by string on 2006-04-06
[QUOTE=aimislame15]You've got to remember that this is the bleeding edge of technology.[/QUOTE]

Don't worry. I know that already. And the fact that on my example it is "not working in such a way" ensures me that it will work someday, and it is great to know alrerady.

[QUOTE=aimislame15]That said, there is no application (that I know of) that will hook your airport up to a network.[/QUOTE]

So how to connet to soomething ? only the script ? but let's be honest, the script lanuches dhcp, and software do nothing different, just graphically ... am I wrong ?

[QUOTE=aimislame15]I'm not sure what to do abuot WEP/WPA as I never use/have used it.[/QUOTE]

No problem...thanss a lot

---

### Post by NodlezFodlez on 2006-04-18
[QUOTE=aimislame15]
```

svn checkout svn://svn.berlios.de/bcm43xx/trunk/fwcutter
cd fwcutter
make
wget http://www.ghostcorp.net/AppleAirPort2
./bcm43xx-fwcutter AppleAirPort2
sudo make installfw
```[/QUOTE]

I have subversion, but when I try "svn" it said "command not found"

---

### Post by AlphaMack on 2006-04-19
[QUOTE=JackosKing]Hello, does it work with WEP 128 Bits key?
Airport is the only limit :/[/QUOTE]

Yes.  But you should be following the steps outlined in the thread "Exact steps to getting Airport Extreme working."  Use WiFi Radar (can get from Add/Remove) to find your network and connect up with it.  The key (passphrase) must be preceded with a 's:' (without the quotes).  Ditto your profile in Networking (System>Admin>Networking).  You'll need to reboot.

WiFi for me has been iffy.  Often I could just reboot and I'll be connected to one of my preferred base stations.  Other times I have to switch profiles and reboot.  When I sleep my machine, I lose networking and have to reboot to get it back.

Yup, it is indeed bleeding edge.

---

