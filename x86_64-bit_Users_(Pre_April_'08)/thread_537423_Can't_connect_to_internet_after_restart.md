---
title: "Can't connect to internet after restart"
date: 2007-08-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by ikki_72 on 2007-08-28
When I got the internet connection(DSL) working, i "sudo apptitude upgrade" then "sudo apptitude update" succesfully. Installed Firestarter firewall then I restarted my PC. After I logged in, I couldn't connect. Why? And there're a few added entry on GRUB.

---

### Post by gimfred on 2007-08-29
regarding grub, that would be because you probably installed a new kernel; the new options probably are > Ubuntu, kernel 2.6.20-16-generic (recovery mode) or memtest etc. 

[Edit]
It is good to have the extra options there as if a problem occurs with your main kernel, you can still boot the old versions. 
[/Edit]

Now in regards to your connection, are you able to connect to the router? It will probably be an ip address such as 192.168.1.1 or 192.168.0.1. If you type that ip number in you should get the menu for your router. It may pop up and ask for your user name and password. It is not the same as your computer login. Think of the router as another (small) computer you are logging into. The manufacturer will have set the router's user name and password. I'm afraid you will have to look it up in the user manual. (The manual should tell you the ip address of the router too. 

Can you log in to the router?

---

### Post by Jouke74 on 2007-08-30
It's more likely that your firestarter firewall is now blocking your internet connection. 
You might want to check it's configuration.

---

### Post by gimfred on 2007-08-30
True, but if they work through eliminating "hardware" faults, people tend to be more dedicated to finding the software faults. I have often had it change my ip after trying out a firewall package. No reason that I can figure out but it does. So I always make sure I'm on the same domain as my router. (single machine/router here. no real networking)

---

