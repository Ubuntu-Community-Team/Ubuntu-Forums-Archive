---
title: "Stable socket 939 motherboard"
date: 2005-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by gereksiz on 2005-08-26
I'm planning to buy a Socket 939 motherboard by this weekend. As much as I searched google, I couldn't get any information about Socket 939 motherboards that are stable for Linux. From my experience (Asus A7N8X Deluxe), linux does not necessarly support latest chipsets/boards. So before jumping to a decision, I would like to learn about your experience. I'm planning to run Kubuntu 64. 

Which motherboards do you use and suggest? Even if your motherboard frequently freezes, please write the type so that we can avoid it. Perhaps, this thread will serve as reference for future buyers.

Thanks  a lot

---

### Post by gratefulfrog on 2005-08-26
I use an ASUS A8V delux, and have had no trouble with Hoary 64bit. In fact, the old story about linux not supporting the latest greatest isn't so true anymore (although it reamins true for webcams).

Also, check the hardware compatability post: 
[http://ubuntuforums.org/showthread.php?t=1651](http://ubuntuforums.org/showthread.php?t=1651)

---

### Post by DancingSun on 2005-08-26
I think most socket 939 mobo are generally very well supported.  You only tread into murky waters when your chipset has a really rare combination of chips or the chipset is very new.  For example, the MSI's nForce4 Ultra SLI mobo, it uses a soundblaster live! 24-bit sound chip instead of the more common AC97 CODEC chip, and that seems to cause a lot sound problems for many folks.

Beware of the new integrated ATI GPUs, they don't seem to work well with Ubuntu, not yet at least (ATI needs to step up in their driver support).

I have a Chaintech VNF-4 Ultra (nForce4 Ultra) mobo, and so far it is rock solid.  The only trouble that I had ever encountered have to do with Ubuntu's shutdown sequence (it does not seem to be mobo related), sometimes it just enters a kernel panic or just freezes when trying to unmount drives/partitions.  But with EXT3 partitions, I just manually shutdown and do a restart and it will recover file system without problems.

---

### Post by Corbelius on 2005-08-26
No problem with my MSI K8N Neo4 Platinum :D

---

### Post by liquidfire on 2005-08-26
My DFI lanparty nforce 4 board works great, for gaming and overclocking ;) Much options and very stable :D

---

### Post by earthfall on 2005-08-26
I am using ABIT AV8 motherboard without any problem. On board sound controller and gigabit ethernet works wonder too.

---

### Post by cholis on 2005-08-26
Cheap and complete motherboard, PCPartner RS480-A56. But remember, Ubuntu hasn't fully support 64 bit computing. The clock is running too fast.

---

### Post by DancingSun on 2005-08-26
[QUOTE=cholis]Cheap and complete motherboard, PCPartner RS480-A56. But remember, Ubuntu hasn't fully support 64 bit computing. The clock is running too fast.[/QUOTE]
My clock runs fine out-of-the-box....

---

### Post by tseliot on 2005-08-27
[QUOTE=cholis]Cheap and complete motherboard, PCPartner RS480-A56. But remember, Ubuntu hasn't fully support 64 bit computing. The clock is running too fast.[/QUOTE]
It's a kernel bug. PCLinuxOS doesn't have this problem because its kernel is patched. Fedora has the same problem (i.e. it doesn't have the right kernel patch) as Ubuntu.

---

### Post by tseliot on 2005-08-27
Please DON'T buy MSI RS480. It doesn't work with most distros and it is a bit Linux unfriendly.

---

### Post by ROUBOS on 2005-08-27
I've got the ASUS A8V Deluxw Socket 939 
and the AMD64 3500+ and running Ubuntu Hoary 5.04 AMD64 with no problems

---

### Post by DancingSun on 2005-08-27
[QUOTE=tseliot]Please DON'T buy MSI RS480. It doesn't work with most distros and it is a bit Linux unfriendly.[/QUOTE]
Yes, and the integrated GPU has some problems with the ATI drivers.  As far as I know, it can only work WITHOUT hardware acceleration.

---

### Post by front243 on 2005-08-27
[QUOTE=gereksiz]I'm planning to buy a Socket 939 motherboard by this weekend. As much as I searched google, I couldn't get any information about Socket 939 motherboards that are stable for Linux. From my experience (Asus A7N8X Deluxe), linux does not necessarly support latest chipsets/boards. So before jumping to a decision, I would like to learn about your experience. I'm planning to run Kubuntu 64. 

Which motherboards do you use and suggest? Even if your motherboard frequently freezes, please write the type so that we can avoid it. Perhaps, this thread will serve as reference for future buyers.

Thanks  a lot[/QUOTE]
 I second MSI K8N Neo4 Platinum, I have it and all I need is to get the sound working on my fresh ubuntu install. But I know sound works under Linux as I got it working with Fedora Core 4.

---

### Post by cholis on 2005-08-28
[QUOTE=tseliot]It's a kernel bug. PCLinuxOS doesn't have this problem because its kernel is patched. Fedora has the same problem (i.e. it doesn't have the right kernel patch) as Ubuntu.[/QUOTE]

Yeah...like you always said, it's a kernell problem. I tried to create new kernell xxx.12...xxxx) following your guidance in another post, booom... i've to reinstall my ubuntu.

I hope Ubuntu can release amd64 friendly OS. In September?

---

### Post by tseliot on 2005-08-30
[QUOTE=cholis]Yeah...like you always said, it's a kernell problem. I tried to create new kernell xxx.12...xxxx) following your guidance in another post, booom... i've to reinstall my ubuntu.

I hope Ubuntu can release amd64 friendly OS. In September?[/QUOTE]
Every user I helped with kernel compilation managed to make their kernel work in the end.

Have you followed every step of my HOWTO?

Why don't you ask me a question and post your problem with kernel compilation?

Ask it here in my guide's thread

[http://www.ubuntuforums.org/showthread.php?p=301048](http://www.ubuntuforums.org/showthread.php?p=301048)

---

### Post by cholis on 2005-08-31
[QUOTE=tseliot]

Have you followed every step of my HOWTO?

[/QUOTE]

Yessss.... also how to from wiki... both didn't work. I hope some day someone could put the ready to use xx12 kernel on synaptic.

---

### Post by cholis on 2005-09-02
finally, success in building kernel using 2.6.12.6
clock run normal
sound card run better

but... ntsf unaccessible

---

### Post by gereksiz on 2005-09-05
Thank you all guys. I think I will go with 
Update 	ASUS A8V DELUXE Socket 939. I will let you know my experience.

---

### Post by greyhound4334 on 2005-09-06
Late to the party, but... My A8N-E runs fine.  I've gone back to the 32-bit version for now since I found it a little too much work to get all the software I want running on 64-bit.  But the basic stuff all worked fine, and I really didn't try TOO hard to get it going.  I just figured that it seems to be getting better by the day, so I'd wait a few months for it to mature.

Good luck!

---

### Post by cholis on 2005-09-07
Finally there is a simple way to use ubuntu on 939 motherboard: Turn OFF the ACPI and APIC option motherboard BIOS.

Clock did't run too fast, etc. Ubuntu run out of the box. Don't have to comple any new kernel.

I found the tips somewhere in web, but forgot to bookmarks it.

I don't know wether Turn-Off-ing both ACPI and APIC will slowdown Ubuntu, but it does in WinXP.

Feel free to search for ACPI and APIC at google.

---

### Post by srss on 2005-09-07
I run an ASUS A8V Deluxe. It works like a charm out-of-box. By the way, the clock is running fine, never have trouble with it.

Also, I think its very stable. I have no complains.


=)

---

### Post by puppy on 2005-09-08
My K8N Neo2 Platinum MSI board (it has the NForce3 chip) runs fine - Ubuntu recognises the onboard ethernet controller, my sata drives etc with no issues.

---

### Post by crane on 2005-10-02
This is as good a thread as any for my post. I hate starting new threads when they are not needed.
My problem envolses a 939 mother board.
I recently  built a new computer using a gigabyte K8 Triton K8NS Ultra 939 mother board, AMD Athlon64 +3000 and two sticks of 256 ram. After building I had some problems with PSU but replaced with a new one and all is well there.
The major problem is this. I can't run linux on it. Windows runs fine.(XP) I have run test after test, Doom3, Qukae3, Battlefield2 demo, and many system/vid card tests under windows with no problems. I Boot to Ubuntu and it will freeze up, Normally it will freeze if left idle. I played Doom3 and quake3 with no problems. Left to eat dinner and computer was frozen. I have tested this over and over. Hoary freezes repeatedly. I tried updating by installing Breezy and if won't even run. I don't remember the errors now.
When I say freeze I mean freeze/ lock up. Nothing works other that the good old reset button on the case.
I have also tried installing Suse but same problem. This ticks me off. A motherboard that cant run Linux in truely an usless MoBo!:rolleyes: 
I'm going to try what cholis said:
[quote=cholis]
Finally there is a simple way to use ubuntu on 939 motherboard: Turn OFF the ACPI and APIC option motherboard BIOS.
Clock did't run too fast, etc. Ubuntu run out of the box. Don't have to comple any new kernel.
I found the tips somewhere in web, but forgot to bookmarks it.
I don't know wether Turn-Off-ing both ACPI and APIC will slowdown Ubuntu, but it does in WinXP.
Feel free to search for ACPI and APIC at google.
[/quote]
and hope for the best. Any ideas? Has anyone else seen this problem or run the MoBo?

---

### Post by Jiilik on 2005-10-02
[QUOTE=tseliot]Please DON'T buy MSI RS480. It doesn't work with most distros and it is a bit Linux unfriendly.[/QUOTE]

It works fine for me under breezy - accellerated ATI drivers, SATA, sound, everything.  And it supports dual core chips if you patch the bios.

Hoary is useless on it though, especially if you use SATA.

The RS480 is based on the ATI IXP chipset - so it should work with other boards as well (under breezy) that use the same chipset.

The problem with the RS480 is that the chipset is so new that kernel 2.6.12 was the first to support it fully - hoary came with 2.6.10

---

### Post by Jiilik on 2005-10-02
[QUOTE=DancingSun]Yes, and the integrated GPU has some problems with the ATI drivers.  As far as I know, it can only work WITHOUT hardware acceleration.[/QUOTE]

Works with the fglrx fully accellerated under breezy

---

### Post by tseliot on 2005-10-02
[QUOTE=Jiilik]It works fine for me under breezy - accellerated ATI drivers, SATA, sound, everything.  And it supports dual core chips if you patch the bios.
Hoary is useless on it though, especially if you use SATA.
The RS480 is based on the ATI IXP chipset - so it should work with other boards as well (under breezy) that use the same chipset.
The problem with the RS480 is that the chipset is so new that kernel 2.6.12 was the first to support it fully - hoary came with 2.6.10[/QUOTE]
I used that motherboard in Hoary with a Breezy kernel (2.6.12-8) and it solved many problems but one: the computer froze randomly.

After having tried several methods I gave in. Now My father uses my former computer (which runs Windows without any problem). I've bought a new computer with an Asus A8V Deluxe: EVERY DISTRO JUST WORKS with this computer, I LOVE IT! I'm not a fan of Asus, I'm just a fan of my current computer :p 

If MSI RS480 works for you then I'm happy for you. It was a hell for me (perhaps it's because of the crappy and idiot-proof bios from Compaq)

---

### Post by Ubunted on 2005-10-02
So is an Nforce-based board a better choice for Linux than one with VIA chipsets or not nowadays?

---

### Post by tseliot on 2005-10-02
[QUOTE=Ubunted]So is an Nforce-based board a better choice for Linux than one with VIA chipsets or not nowadays?[/QUOTE]
Which motherboard do you refer to?

---

### Post by rekstorm on 2005-10-04
how is with DFI NF4-ultra Infinity motherboard?
it has a nforce4-ultra chipset!

---

### Post by mdr on 2005-10-25
[QUOTE=crane]When I say freeze I mean freeze/ lock up. Nothing works other that the good old reset button on the case.[/QUOTE]

I have had this problem with an old Gigabyte 845 board (8I5GML i think) using embedded Intel graphics.  This board is a distro killer, none have ever got X working properly.  Tried disabling apic etc to no avail.  Linux or rather I should say X will not run on that board.  Got a new mobo instead.

So no help I'm afraid but it has happened to others.  and it is X rather than Linux btw.

---

### Post by darkjedi8359 on 2005-10-26
I have an Asus A8V Deluxe with an AMD 3100+, I had problems with hedgehog, but breeze works great :)

---

