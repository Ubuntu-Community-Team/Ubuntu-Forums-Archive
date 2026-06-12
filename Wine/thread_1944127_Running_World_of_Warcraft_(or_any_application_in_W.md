---
title: "Running World of Warcraft (or any application in Wine) through a SOCKS Proxy Server"
date: 2012-03-20
forum: Wine
---

### Post by skenmy on 2012-03-20
I have spent the better part of today experimenting with different solutions on how to get WoW running properly through a Proxy server with Wine. I have finally worked out a solution that actually works - and I am sharing it here in the hope that it will save others some time!

This procedure will theoretically work with any program under Wine - for reasons that will become clearer as we move on.

Just for reference: I am running Ubuntu 11.10 Oneiric.

[SIZE="4"]**Install Software**[/SIZE]
```
sudo apt-get install iptables git-core libevent-1.4-2 libevent-dev
```

This will install iptables (should already be installed, but doesn't hurt to try...), git (for the next section), and a couple of dependencies.

Then we need a piece of software called "redsocks":

```
git clone http://github.com/darkk/redsocks.git
cd redsocks/
make 
echo 'base{log_debug = on; log_info = on; log = "file:/tmp/redsocks.log"; 
       daemon = on; redirector = iptables;}
       redsocks { local_ip = 127.0.0.1; local_port = 1081; ip = 127.0.0.1; 
       port = 1080; type = socks5; }' > redsocks.conf
```

We also create a basic configuration for redsocks here - if you are truly interested in it's features you can read up on it - but this guide will just get you working.

[SIZE="4"]**Setup some scripts**[/SIZE]
The way that I have discovered works best is simply switching the entire system to redirect through a SOCKS proxy, until I tell it to stop. I have accomplished this with two launchers on my desktop - one to start, and one to stop.

**[FONT="Courier New"]/usr/bin/start-tunnel[/FONT]**
```
#!/bin/sh
cd /home/<USERNAME>/redsocks
./redsocks -c redsocks.conf
ssh -fqND 1080 <SSH USERNAME>@<SSH HOST>
gksudo iptables
sudo iptables -t nat -N REDSOCKS
sudo iptables -t nat -A REDSOCKS -d 10.0.0.0/8 -j RETURN
sudo iptables -t nat -A REDSOCKS -d 127.0.0.0/8 -j RETURN
sudo iptables -t nat -A REDSOCKS -d 192.168.0.0/16 -j RETURN
sudo iptables -t nat -A REDSOCKS -p tcp -o eth0 -j DNAT --to 127.0.0.1:1081
sudo iptables -t nat -A OUTPUT -p tcp -j REDSOCKS
sudo iptables -t nat -I REDSOCKS -d <SSH HOST IP> -j RETURN
```

The above script will start the tunnel. Replace the sections in <>s as appropriate (you may have compiled redsocks elsewhere (such as /usr/bin/redsocks) - update this script as appropriate). I have only included the IP ranges that work for me - most home networks are on the 10.x.x.x and 192.168.x.x range - if you aren't, you'll know, and can update accordingly.

Now for the stopping of the tunnel.

**[FONT="Courier New"]/usr/bin/stop-tunnel[/FONT]**
```
#!/bin/sh
gksudo iptables
sudo iptables -F
sudo iptables -X 
sudo iptables -Z
sudo iptables -t nat -F
sudo iptables -t nat -X
sudo iptables -t nat -Z
killall redsocks
```

That one's simple. Now do:

```
sudo chmod a+x /usr/bin/*-tunnel
```

To ensure we can execute them.

[SIZE="4"]**Desktop Launchers**[/SIZE]
I have two lovely icons on my desktop that I can double click to start / stop the tunnel. To set these up, you can create a Launcher by running 
```
gnome-desktop-item-edit ~/Desktop/ --create-new
```
and filling it out. The "Command" is one of either /usr/bin/start-tunnel or /usr/bin/stop-tunnel - depending on which one you are setting up!

[SIZE="4"]**Time to play!**[/SIZE]
That's it! Double click the Start Tunnel icon on your desktop - type in your SSH password (if necessary), and then type your system password for gksudo when it prompts you (for iptables). Navigate to something like [http://whatismyip.com/](http://whatismyip.com/) in a browser - and check you are running through the proxy. It should say "No proxy detected" - but your IP address will have changed.

Then give WoW a go! It should work flawlessly. ;)

[SIZE="4"]**Customisation / Ease of Use**[/SIZE]
[LIST]
[*]You could also launch WoW in the same Start script!
[*]Create an SSH key to prevent you having to type in your SSH password
[/LIST]

I hope this helps! I will try and check back to give support - but if I don't get back to you, drop me a PM!

---

### Post by xClueless on 2012-04-05
Hi, I've been trying to achieve a similar outcome however I'm struggling to follow exactly what's happening here. I've installed redsocks straight from the repositories (precise) and followed your steps however I'm having no luck. Currently I'm running iProxy and SSH to tunnel traffic through my iPod touch in a similar way to how you connect to your remote host. This works fine for Firefox and for most command line applications through Proxychains but unfortunately not for wine. This is the small script that enables my current tunnel:

```

iproxy 2222 22&
ssh -D 1080 -p 2222 root@localhost

```Would it be possible to redirect everything through this tunnel using redsocks? Thanks in advance.

---

### Post by CardexDave on 2012-11-28
You, sir, are genius!

Just wanting to note, for people who wants to use Your Freedom instead of using ssh like you do, here is the modified start_tunnel script to run after you started YF:

```
#!/bin/sh
cd /home/<username>/redsocks
./redsocks -c redsocks.conf
gksudo iptables
sudo iptables -t nat -N REDSOCKS
sudo iptables -t nat -A REDSOCKS -d 10.0.0.0/8 -j RETURN
sudo iptables -t nat -A REDSOCKS -d 127.0.0.0/8 -j RETURN
sudo iptables -t nat -A REDSOCKS -d 192.168.0.0/16 -j RETURN
sudo iptables -t nat -A REDSOCKS -p tcp -o wlan0 -j DNAT --to 127.0.0.1:1081
sudo iptables -t nat -A OUTPUT -p tcp -j REDSOCKS
sudo iptables -t nat -I REDSOCKS -d 127.0.0.1 -j RETURN
```

Beware, this script uses wlan0 because I'm using my wifi interface, but maybe you want to change it to set your own... :)
Thank you very much for this!

---

