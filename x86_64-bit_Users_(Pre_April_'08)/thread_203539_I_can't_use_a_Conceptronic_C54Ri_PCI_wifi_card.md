---
title: "I can't use a Conceptronic C54Ri PCI wifi card"
date: 2006-06-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Surething on 2006-06-25
Hello everybody:

First of all: sorry for my bad english language.

My C54ri is not working on Ubuntu 6.06 64 bit.

Well, let's see. Once installed Ubuntu, the pci card appears on the networking configuration window, but when I clicked on "properties" nothing happened.

So, then I thought "it's time to try with ndiswrapper".

So, I installed ndiswrapper-utils using Synaptic.

I got the latest Windows XP 64 bit drivers for the card. Then:

```
sudo ndiswrapper -i rt2500.inf
```

Then:

```
ndiswrapper -l
```

And it printed:

```
rt2500 driver loaded
```

¡But do not displays "hardware present"!

So, I unistalled that driver and tried with the rt61.inf included in the same Windows XP 64 bit driver package.

Then "ndiswrapper -l" returns "rt61 driver loaded hardware present".
8
¡Ok! Then:

```
sudo depmod -a
```

Returned nothing: that's ok.

Then:

```
sudo modprobe ndiswrapper
```

Returned nothing: that's ok too.

Then:

```
iwconfig ra0 scan
```

(ra0 is my card)

Returned something like "scan didn't find any AP".

Then i tried:

```
iwconfig ra0 essid ESSID
```

And returned something like "error. can't do that".

Mmm... I am a newby... and now I do not know what to do. I have tried to go to System > Administration > Networking and nothing happens when I clic on properties. I have tried with a ralink 64 bit driver but there is no "hardware present" when "ndiswrapper -l".

What can  I do? Can someone help me?

Thanks in advance.

Postscriptum: Again sorry for my bad english.

---

### Post by potroclo on 2006-07-05
I've got the same problem. But, of course, I don't know so much of unix systems like you.
same distribution & same conceptronic pci card.
everywhere i look tell me that the drivers are already intalled whit this distribution 6.06, but when i try to acces to the options it hang on.

as i've said i don't know much. there is somthing called terminal, but i'm not sure what it's for... (Joking) but i really don't know how to use it. and not, i don't really want to compile anything to use the system...

any easy help would be aprecieted.
thank you.
sorry for not solve your problem. but now you know you're not alone...

---

