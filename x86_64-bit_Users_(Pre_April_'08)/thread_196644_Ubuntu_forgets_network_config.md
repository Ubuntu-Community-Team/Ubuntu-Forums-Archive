---
title: "Ubuntu forgets network config"
date: 2006-06-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by xerman on 2006-06-14
Hi there,

I installed dapper64, and instead of installing kde apps into gnome, i decided to install kde and switch desktop manager depending on the app.

What I found is that, as I use Gnome as base system, I set the network settings in Gnome and after installing "kubuntu-desktop" Gnome never remembers the settings, forcing me to modify them every time I boot Gnome.

The weird thing is that I have already set a network location, and everytime I log in, I choose that location, which remembers the DNS, gateway and so on, but between boots again forgives that location.

This did not happen before installation of Kubuntu-desktop. 

Regards

---

### Post by ljoris on 2006-06-15
Do you have sufficient diskspace left on your partition(s) ?

as root, type 

df -h



regards,

Joris

---

### Post by Lil_Eagle on 2006-06-15
I ran into the same problem.  

While I was trying to fix it, another problem surfaced.  I was editing my dhcp configuration because my stupid router won't do the DNS correctly.  I already had the prepend domain-name-server setting to bypass the dhcp settings, but for some reason the resolv.conf kept resetting itself to only use my router.  Not looking at all at the dhclient.conf like it should.

So, I made some changes in that file, and left out a semi-colon.  When I tried to re-open it (with sudo) I got a timestamp error and it wouldn't let me edit the file.  There was nothing wrong with my clock.

Needless to say, my DNS still doesn't work right, although my router does eventally make the connection, it should just go right to the DNS that I have configured.  I'm sure there is a script error somewhere with the init.  I'll keep digging.

---

### Post by xerman on 2006-06-16
[QUOTE=ljoris]Do you have sufficient diskspace left on your partition(s) ?

as root, type 

df -h



regards,

Joris[/QUOTE]

Hi Joris,

For sure I have enough space on my partitions:
/boot  - 1GB (used 5%)
/        - 55 GB (used 16%)
/home - 40 GB (used 3%)

so I don't think this is the issue.

I have the location stored and keeps the location saved, but I have to select it every time I boot to get nektwork working. Ubuntu does not keep the preferences from boot to boot. And this just since I have Gnome and KDE installed.

So I'm pretty stuck.

Regards.
Xermán

---

### Post by Lil_Eagle on 2006-06-17
Are you using DHCP?  If so, and your DHCP server works like mine, you'll need to edit the /etc/dhcp/dhclient.conf file.  That file is very well commented.

For me it was just adding the line:

```
prepend domain-name-server 62.251.0.6;
```

which is the closest one to me.  I could of course have my own DNS, but with a less than 50 ms response from the above, why should I bother maintaining one.

---

### Post by xerman on 2006-06-19
[QUOTE=Lil_Eagle]Are you using DHCP?  If so, and your DHCP server works like mine, you'll need to edit the /etc/dhcp/dhclient.conf file.  That file is very well commented.

For me it was just adding the line:

```
prepend domain-name-server 62.251.0.6;
```

which is the closest one to me.  I could of course have my own DNS, but with a less than 50 ms response from the above, why should I bother maintaining one.[/QUOTE]

Nope, I don't use DHCP either. I'm starting to think about filling a bug. I'll try with Ubuntu 32 and see if this issue is 64bit related or Ubuntu related.

---

### Post by axel-vpk on 2006-08-05
Hello!

i dont use 64-bit Dapper, but this is the same problem as mine. 

I installed ubuntu, then kubuntu-desktop, then xubuntu-desktop, and then uninstalled kubuntu-desktop.

now i have the situation that i have to reset the DNS servers everytime i start GNOME, which is annoying. 

i changed my resolv.conf to comment out the parts about 

```

#request subnet-mask, broadcast-address, time-offset, routers,
#       domain-name, domain-name-servers, host-name,
#       netbios-name-servers, netbios-scope;
```

as i dont really use DHCP at all and really dont want it to mess up my  manual settings. 

this didnt seem to help though.

---

