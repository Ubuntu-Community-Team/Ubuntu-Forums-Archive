---
title: "New to linux on my next computer"
date: 2006-08-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by jeremyn on 2006-08-07
Hi everyone.  I downloaded Ubuntu 6.06 and tried it out (very briefly..planning on playing with it more) on my current laptop.  I'm considering switching over to linux permanently when I build my first desktop computer in a few months.

However, I'm a little concerned:

Most of the new hardware seems to be migrating toward the 64-bit architecture.  Since I'll be buying all new components, this is probably what I'll get.  I'm leaning towards the low end of the intel Core 2 line.  Will this work with Ubuntu 6.06?  People seem to have a lot of issues making 64-bit chips work with everything.

Where can I find a motherboard that will fit this cpu and "just work" (mostly) out of the box?  ie I want onboard sound, network, etc to be detected out of the box.  I want it to detect a dual-core chip and do whatever it needs to do to get that to work.  Alternatively, I don't mind following some instructions to get something working as long as I can understand them!

I'm a little concerned since I'm a total linux newbie and I want to build my own computer for the first time.  Is it too ambitious to try both of these at the same time?

I'm really looking for some advice on how to choose hardware and a guide for getting everything up and running.  Some references to places I can look for info on this would be a great help too.

Let me know if you can help me!

Thanks!!
Jeremy

---

### Post by John.Michael.Kane on 2006-08-07
jeremyn I would advise you do reseach frist on all the parts you want to include in your build. 

where xxx is the model you want 
Intel Core 2 Duo E6xxx 

there maybe others that you like.
ASUS P5B Socket T (LGA 775) Intel P965 Express
MSI 975X Platinum Socket T (LGA 775) Intel 975X 

Memory 1 to 2 gig ddr2 should work

Videocard can be ATI or Nvidia pci-e

Sata or ide Notice some users have had issues with mixing sata and ide

Any old gneric Case to hold your parts



This is a rough list for you. you have make some kind of list of the parts would want to use for any of us here to give concrete advice. **take your time. **

---

### Post by jamesford on 2006-08-07
i have no experience with intel dual cores. but amd 64 x2 is no problem at least.
personally ive had problems with ati graphics cards (hopefully amd can sort out their drivers now amd has bought ati). for now id get nvidia if it was me

---

### Post by Kilz on 2006-08-07
> **jamesford said:**
> i have no experience with intel dual cores. but amd 64 x2 is no problem at least.
personally ive had problems with ati graphics cards (hopefully amd can sort out their drivers now amd has bought ati). for now id get nvidia if it was me

Ati can be a pain some times, but all video drivers can. That also isnt something that is specific to 64bit either.


[QUOTE=jeremyn] 	
Hi everyone. I downloaded Ubuntu 6.06 and tried it out (very briefly..planning on playing with it more) on my current laptop. I'm considering switching over to linux permanently when I build my first desktop computer in a few months.

However, I'm a little concerned:

Most of the new hardware seems to be migrating toward the 64-bit architecture. Since I'll be buying all new components, this is probably what I'll get. I'm leaning towards the low end of the intel Core 2 line. Will this work with Ubuntu 6.06? People seem to have a lot of issues making 64-bit chips work with everything.

Where can I find a motherboard that will fit this cpu and "just work" (mostly) out of the box? ie I want onboard sound, network, etc to be detected out of the box. I want it to detect a dual-core chip and do whatever it needs to do to get that to work. Alternatively, I don't mind following some instructions to get something working as long as I can understand them!

I'm a little concerned since I'm a total linux newbie and I want to build my own computer for the first time. Is it too ambitious to try both of these at the same time?

I'm really looking for some advice on how to choose hardware and a guide for getting everything up and running. Some references to places I can look for info on this would be a great help too.

Let me know if you can help me!

Thanks!!
Jeremy[/quote]

As long as you dont mind following a few howto's. You should have no problems getting a 64bit system up and running. Doing the work of checking out the hardware before buying is a good idea. Moving to linux may not be as hard as you think if you come with an open mind.

---

### Post by fistfullofroses on 2006-08-07
I would not get an Intel 64bit chip. From what I have seen there are not many programs that are compatable with their architecture. Also, I am not sure for the Intel, but I know that the AMD64 is backward compatible with 32bit software. ATI graphics cards on PCIe also have compatability issues, thus I would choose Nvidia. For sound, if your sound is not integrated into your board, I would go with SoundBlaster. For your motherboard I know that Gigabyte is extremely good. If this is your first time building a computer, I think that using Linux to run it is a good idea. There is no better way to learn Linux. Though, I would suggest dual booting between Ubuntu and a harder system. Ubuntu is the best Linux to start with, but using a harder distribution such as Gentoo will help you learn more about how Linux works underneath the pretty visuals that Ubuntu provides.

Good luck.

---

### Post by RAOF on 2006-08-08
> **fistfullofroses said:**
> I would not get an Intel 64bit chip. From what I have seen there are not many programs that are compatable with their architecture. Also, I am not sure for the Intel, but I know that the AMD64 is backward compatible with 32bit software. 
...
The Intel (x86-)64bit architecture is **the same as** the AMD (x86-)64bit architecture.  Intel call it EMT64, AMD call it AMD64 (or x86-64).  They're the same thing.  You might be confused with Intel's entirely separate (and pretty much dead) **IA64** (also called Itanium, or some such) architecture, used by their big-super-server chips that no-one uses.

Intel chips are (almost) **completely equivalent** to AMD chips.  If you can run it on an AMD chip, you can run it on an Intel chip, and visa versa.  There are some differences, but these are only in the SIMD extensions (sse1/2/3/4 (intel), 3dnow/ext/etc).  Almost all programs that use these extensions detect them at run time, so you don't need to care.

---

### Post by jeremyn on 2006-08-08
Thanks everyone for the replies.  

Eventually I'll choose hardware and post here.  Will the people here be able to warn me about possible problem I'll have?  Give suggestions?

Do you think it is best just to build it and start up with the installation and then post the problems I get here?  The reason I'm nervous is because I'm TOTALLY new to both linux and building comptuers.  I don't think I'll be able to diagnose the problems that arise (and I KNOW there will be problems).  

When does the next Ubuntu release come out?  I could  wait for that and hope that better hardware support comes out to relieve some potential problems.

Thanks again,
Jeremy

---

### Post by jeremyn on 2006-08-08
Another question:
does anything special need to be done to make ubuntu utilize a dual-core chip correctly?  I've gotten mixed impressions reading about this.
Jeremy

---

### Post by John.Michael.Kane on 2006-08-08
jeremyn All that would need to be done is to install ia64 smp kernel.this will take full advantage of the two cores. as for any hardware issues that depends on what you will add to machine. for the most part decide on the parts you want, and list them here for us to look over, and the next Ubuntu release comes out in september i believe though there's no reall need to wait till then,however. If you did wait it would give you more time to research to get to get as headache free a setup as you can :mrgreen: .

---

### Post by jeremyn on 2006-08-08
Hi again snake.  You mention installing the ia64-smp kernel.  Again, I'm totally new to this, so I'm not entirely sure what is entailed here.  If I get the amd64 distribution, would this simply be an installation option?  Or do I need to do something else?

I think I'll likely wait until the first week in January to do this.  I'm a graduate student and I'll have a couple of weeks off at that time.  You mentioned a new version in September.  Could this mean a new version in January also?

Jeremy

---

### Post by John.Michael.Kane on 2006-08-08
jeremyn After you downloaded the 64bit version,and installed it you would going into synaptic,and look for the kernel that pertains to your architecture. In this case that would be EM64T install it,and reboot. After all is in the clear you could then remove the generic kernel using synaptic.as for the new ubuntu version in September i beleave this is to get distro back on their 6-month release cycle (don't quote me on this as it's just a guess) most likely you should just recive security updates ect. then in another 6-months you would get another version bump.


Hope this helps.

---

### Post by Cynical on 2006-08-13
I have a core 2 duo setup myself and I'm going to tell you now, you'll have a hell of a time trying to get an cdrom using ide to be recognized. I think it has to do with the fact that intel removed ide support from the p965 express chipset, and motherboard manfacturers had to include it themselves. I would either suggest waiting until nforce/ati chipset boards are out or buying a sata connector for your cdrom drive. One workaround that I used was instlx, which installs on your windows partition and when you reboot, allows you to install ubuntu over the internet.  (still doesnt recognize the drive afterwards of course)


After you get it working though, its blazing fast. You'll notice it most during compiling. I still don't regret purchasing mine after the trouble I've been through.

---

### Post by fireboxtester on 2006-09-02
> **Cynical said:**
> I have a core 2 duo setup myself and I'm going to tell you now, you'll have a hell of a time trying to get an cdrom using ide to be recognized. I think it has to do with the fact that intel removed ide support from the p965 express chipset, and motherboard manfacturers had to include it themselves. I would either suggest waiting until nforce/ati chipset boards are out or buying a sata connector for your cdrom drive. One workaround that I used was instlx, which installs on your windows partition and when you reboot, allows you to install ubuntu over the internet.  (still doesnt recognize the drive afterwards of course)


After you get it working though, its blazing fast. You'll notice it most during compiling. I still don't regret purchasing mine after the trouble I've been through.

Cynical, how does Instlux work?  I tried using it but nothing happened, it just said it had to restart my computer, and then after restart it said uninstalling instlux"

For the P965 issue I made a wiki page to put all of the information about it in one place:
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

As you can see it's a pretty major issue.  There are already 3 bugs and at least 9 forum threads regarding this.  Hopefully we can get this fixed for Edgy.  (I'm going to test Knot 2 later tonight)

---

