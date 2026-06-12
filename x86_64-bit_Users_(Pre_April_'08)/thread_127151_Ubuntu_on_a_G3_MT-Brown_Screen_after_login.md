---
title: "Ubuntu on a G3 MT-Brown Screen after login"
date: 2006-02-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by threephase on 2006-02-08
greetings.
after a week of trying to get ubuntu running on this oldworld mac-i finally cracked it last night. which made me very happy.

the second part of the install process took sooo long that i had to go to bed.

woke up to find lovely looking ubuntu login screen.

entered name & password

brown screen of death!

nothing happens at all. i can move my cursor but thats it.

so its force restart and either back to 9.2 or try ubuntu again...

and its brown screen of death all over again.

im definately a linux newbie-but i've been tinkering with the terminal in OSX for over two years. usually when i have the right & correct information i get what i need done. but any deviation from that usually means i'm stuck. (well, that happened with the ubuntu install, but i fixed it ie. at the bootloader warning: opt-f2 to copy over the initrd and vmlinux files to the ubuntu partition resulted in dev/sda6 not existing/wouldn't mount until i tried hdd6 and then yup-all was ok).

so, can anyone help? i've seen other posts about this brown screen, but that appears to be specific to G5's.

is this to do with the screen resolution? i cant remember what i set it to, which is no help (i know). it may have been 1280x960 but i have a feeling it could be 1024x168 as i have a black border around the login & brown screen.

i want to try out ubuntu on this machine because panther is too much of a nightmare (on the beige G3)...if i don't get anywhere with ubuntu i think i'll just give up and install jaguar and have done with it!

thanks.

oops before i submit this here are the specs of the machine.

G3 266mhz, 192mb ram, 8gig ide, no pci cards (yet), on a network.

---

### Post by dombleu on 2006-02-08
Many folks did report that behaviour.

I did experienced that trouble.

Make sure that the local loop is running.

You might do so by getting to a VT by pressing

```
ctrl-alt-1
```

log in.

And then 

```
ifconfig
```

if a device called "lo" do show up, move on it's something else

otherwise you'll have to make sure a few lines like 

```
auto lo
iface lo inet loopback
```

do exist in /etc/network interfaces

and reboot

Alternatively you might want to do
```

sudo ifconfig lo up
```

if you don't want to reboot.

And by the way, on my side, the brown screen only stayed for a long time (let's say 5 minutes) and then gnome would finish loading properly.

Hope it helps.

---

### Post by linear on 2006-02-08
Sounds like the Ubuntu Date Bug:
 
[https://wiki.ubuntu.com/UbuntuDateBug](https://wiki.ubuntu.com/UbuntuDateBug)

---

### Post by ssam on 2006-02-08
i think it might be this
[https://wiki.ubuntu.com/UbuntuDateBug]("https://wiki.ubuntu.com/UbuntuDateBug")

happens to macs when their PRAM batteries get old and they forget the date.

update:
linear, you must have beaten me by a second

---

