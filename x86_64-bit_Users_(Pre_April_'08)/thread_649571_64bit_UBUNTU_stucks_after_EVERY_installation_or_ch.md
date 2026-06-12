---
title: "64bit UBUNTU stucks after EVERY installation or change"
date: 2007-12-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by S3irios on 2007-12-25
Goodmorning and Merry Christmas. I have a 64bit AMD processor, 2 gigs of 800Mhz Ram and a MSI mainborad with dual lan. Since i installed 64bit Gutsy Gibbon Ubuntu, i have a specific problem.... 
After ANY change or ANY installation (drivers or simple programms) when i restart ubuntu , in the loading screen the orange bar stucks like 3 boxes before it becomes full.Then it changes screen and it shows the code.
 The line which it stucks in the code is somethin for "HP printers cpud"  then after one minute it says ......{OK} and it continues loading other stuff till it gets me on the login screen.I put my user and pass and log in. BUT nothing works well, it takes like 4 minutes to become usable as it is loading the desktop environment, first it shows the bars up and down with the menus on it, then the menus disappear and the desktop picture appears, then the menus appear again with the wallpaper as well, BUT menus don't work (i click them and nothing happens), so... i wait for about 1-2 mins and they become "click-able".
 Even then i can't access the internet or really work ubuntu.  When i restart and all of this repeats  for about 3-4 times with restart after restart it fixes and nothing of this happens, everythings works normally. No stuck on the loading screen and everythnigs works really sweet. Well this is not normal and i have really difficulty using ubuntu if every time i need to restart it like 5 times to work.  I want to stop using winndows us much us i can and really learn how to "fix" those problems, so plz if anyone can telle me what to check or anything i'll be really thankful.

---

### Post by tgilber1 on 2007-12-25
You need to see where you're hanging up and you need to get rid of the splash screen to view messages while booting.

1.  First of all when you boot up, hit the ESC key to get to the boot up prompt
2.  Arrow down to the kernel line,  the line that has the word splash
3.  Type the letter 'e' from the keyboard to edit the kernel line
4.  Move the right arrow to get to the word, splash 
5.  Erase the word splash with backspace or delete key
6.  Hit the Enter key
7.  Type the letter 'b' to boot into system

Post the line where the system is hanging along with any error messages while booting

You can also view what happened during the last boot up by check the following files

/var/log/dmesg
/var/log/debug
/var/log/messages
/var/log/daemon

You can use gedit from the GUI or 
nano or vi from the CLI (terminal)

---

### Post by S3irios on 2007-12-25
Thnks mate for your help, but the problem fixed by itself... :confused:

Now something else occured . Everything were going great, i installed progs and stuff and restarted with no problem, but at some point system crashed, and from then the icon up and right that shows the ethernet card has disappeared.. Can't access to the Internet except when i  use "Configure Network Card" (thank God i installed it) and manually  enter ip addresses every time i login.  I tried and run on the dual boot loader, the option (recovery) it shows all good until it shows it cant find any ethernet devices so [fail] on that. Nevertheless the dual lan i have shows right on "Hardware information".......

---

### Post by tgilber1 on 2007-12-25
> **S3irios said:**
> Thnks mate for your help, bu the problem fixed by itself... :confused:

Now something else occured. everything were going great, i installed progs and stuff and restarted with no problem, but at some point system crashed, and from then the icon up and right that shiws the ethernet card has disappeared.. Cant access to the Net except when i  use "Configure Network Card" (thank God i installed it) and manually  enter ip addresses every time i login.  I tried and run on the dual boot loader, the option (recovery) it shows all good until it shows it cant find any ethernet devices so [fail] on that. Nevertheless the dual lan i have shows right on "Hardware information".......

It's sounds like the module is not loading.  Check to see what kind of Ethernet card you have and place its associated module in the /etc/modules file.  Leave the .ko extension off.  Populate the module name as you would when loading it using modprobe.

---

### Post by S3irios on 2007-12-25
Well i probably found the problem but i don't exactly know what i must do exactly to fix it :S

In recovery mode it brings 2 [fail]        ( i was wrong saying that it cant find any ethernet devices i'm posting the right failures now)

1st) can't read interfaces file "etc/network/interfaces"      [fail]

2nd) Configuring Netwrok interfaces    [fail]

I searched for the "interfaces" file, i fond it being exactly there, so i suppose something inside it isn't right written.
This is it:



```
auto lo
iface lo inet loopback


address 192.168.2.8
netmask 255.255.255.0
gateway 192.168.2.1


address 192.168.2.10
netmask 255.255.255.0
gateway 192.168.2.1

auto eth0
iface eth0 inet static
	address 192.168.2.30
	netmask 255.255.255.0
	gateway 192.168.2.1
auto eth1
iface eth1 inet static
	address 192.168.2.40
	netmask 255.255.255.0
	gateway 192.168.2.1
```


192.168.2.(8,10-30,40) are various Ips that i entered while i had to enter manualy ip after any login....

---

### Post by S3irios on 2007-12-25
hmm.. well i deleted 

```
address 192.168.2.8
netmask 255.255.255.0
gateway 192.168.2.1


address 192.168.2.10
netmask 255.255.255.0
gateway 192.168.2.1
```

and it's ok now, no problems, and no need of manually putting ip..

BUT still there's no icon up-right for ethernet device (well stupid problem but if it has simple solution.. why not? :P)

---

### Post by S3irios on 2007-12-26
Network Icon fixed via sessions->startup programs. It had "disabled" written beside, maybe because of the earlier network problems...

I want to check something more because i had the issue with ubunty stucking on loading again.. I just disabled dual lan through Bios and it booted up correctly, hope this was the problem, but till i certify it i'm not closing this thread , just to be sure

---

