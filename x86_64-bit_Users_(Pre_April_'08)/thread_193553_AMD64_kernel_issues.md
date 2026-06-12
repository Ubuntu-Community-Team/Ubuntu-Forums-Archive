---
title: "AMD64 kernel issues"
date: 2006-06-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by steabert on 2006-06-10
Hi All

I tried to install dapper 64bit on AMD64 X2 and the installation froze at "loading kernel". Some people got around this by using noapic and nolapic flags.

I however couldn't get this to work, so I decided to install the 32 bit dapper.
When I start the live CD, it indicates that there is only one processor.
I wonder if this will also eb the case when I install it, does i386 support dual
core? The live CD doesn't seem to.

If i386 doesn't support dual core, what 32 bit kernel does?
I know there are lots of threads about kernel versions, but sometimes they
say different things.
Can someone post some decent information on all kernel versions,
maybe in a separate thread or something?

Finally, In case the 64bit problem gets solved, where can I get a daily build?
I searched everything but I can't seem to find it.

Thnx!!

---

### Post by Patsoe on 2006-06-10
The install disc is single-core only, I think (quite sure of it). You can install an SMP kernel later, after the system has been set up completely (very sure of it). This is the same on amd64 and i386.

No idea about the freezing with amd64. It could be another hardware component?

---

### Post by steabert on 2006-06-10
[QUOTE=Patsoe]
No idea about the freezing with amd64. It could be another hardware component?[/QUOTE]

The fact is that I hardly know what the kernel parameters mean, or
how to give them as an option actually :)
So if anyone knows what other thing I could try...

AMD64 X2 3800+ cpu
MSI Neo4 FI motherboard
... if that is any help to someone?

I REALLY want to run the 64 bit version

---

### Post by bonzodog on 2006-06-10
You will need to install the SMP kernel after the main install. Like the other post said, It could be something else hardware related that is causing the freeze at 'loading kernel'. 
what are the specs of your system? List for us the following:
processor
Mainboard Chipset manufacturer (ATi, Nvidia, ???)
Graphics card

when you install Ubuntu it comes with one kernel on the install disc, then you can download a better kernel from the repo's and install it. In your case the best thing you could do is install the 64 bit version, then install the AMD-64-SMP-K8 kernel.

---

### Post by Patsoe on 2006-06-10
What seems to be most often the problem is the graphics card. What model do you have?

---

### Post by steabert on 2006-06-10
Hi, thnx for the help !! I really apreciate it.

AMD64 X2 3800+ cpu
MSI Neo4 FI mainboard (nForce 4)
XFX 7900GT 256MB graphics card

@ bonzodog
"In your case the best thing you could do is install the 64 bit version, then install the AMD-64-SMP-K8 kernel"

This is what I was trying, but how can I install the 64 bit version if the
installation freezes?

Also: on some other threads they say that smp is included in the kernels.

---

### Post by Patsoe on 2006-06-11
SMP is not enabled in the standard kernel, I'm sure. And I don't think it's on the install disk either (not enough room there for multiple kernels).
*!!!Edit: not so sure after all... :^o ...see wcmbrine's comment below...!!!*

Your hardware doesn't seem problematic. Can you describe where in the process the install hangs - what is the last thing you see? And how bad is the hang - just no screen output anymore, but still activity (can you screen get output by hitting Ctrl+Alt+F1)?

---

### Post by wmcbrine on 2006-06-11
[QUOTE=Patsoe]SMP is not enabled in the standard kernel, I'm sure.[/QUOTE]It is, in Dapper 64. Not only that, but there's no non-SMP K8 kernel in the repository! That shocked me, but it seems to be no problem on my uniprocessor system.

uname -a
Linux alanis 2.6.15-23-amd64-k8 #1 SMP PREEMPT Tue May 23 13:51:32 UTC 2006 x86_64 GNU/Linux

(This is for the K8 kernel; I don't know about the generic x86_64 kernel.)

---

### Post by steabert on 2006-06-11
[QUOTE=Patsoe]
Your hardware doesn't seem problematic. Can you describe where in the process the install hangs - what is the last thing you see? And how bad is the hang - just no screen output anymore, but still activity (can you screen get output by hitting Ctrl+Alt+F1)?[/QUOTE]

hi,

my install hangs at "loading kernel" about 83% in the install with
the alternate install cd.
nothing responds anymore, it's just frozen.

thnx

---

### Post by Patsoe on 2006-06-11
@ wmcbrine: thanks for correcting that. I found where my confusion comes from: when I installed the k8 kernel from the repositories, I could choose between two packages: linux-amd64-k8 and linux-amd64-k8-smp. However, on closer inspection, I now found that both virtual packages refer to the same kernel package, currently that is linux-image-2.6.15-23-amd64-k8. I will correct my earlier post.

@ steabert: that's a completely different place for it to stall than I had expected. I'm afraid I would have no idea how to fix that. It would be nice to be able to have a look at the installer logs, but I guess there's no real chance of getting to them (since presumably the real hdd file system hasn't been mounted at that stage).

By the way, is there a special reason why you're using the Live CD for i386 and the alternate CD for amd64?

---

### Post by steabert on 2006-06-12
Hi Patsoe,

I tried both live, but when live didn't work for amd64, i tried the alternate install.

So far: giving options "noapic nolapic" don't work

I tried again the live amd64: there it freezes at "Preparing restricted drivers"

any suggestions?

edit: I managed to install the i386 version fo ubuntu, but I would really try to contribute to 64 bit by running it on my pc

---

### Post by steabert on 2006-06-13
Hi, I installed the i386 version of ubuntu.

everything works fine until I tried  to compile something: complete system freeze :( 

I can reproduce it, but there are no logs indicating any error.

Could it be related to cpu activity while compiling??

---

### Post by Patsoe on 2006-06-13
This sort of errors makes me think you have a hardware problem. 
Do you have another OS running? Does that run reliably under serious load?

---

### Post by steabert on 2006-06-13
[QUOTE=Patsoe]This sort of errors makes me think you have a hardware problem. 
Do you have another OS running? Does that run reliably under serious load?[/QUOTE]

this little remark has saved my life :) thnx Patsoe!

On your advice, I tried to put some heavy load on my windows by playing oblivion, and it froze!
I just took out a memory module, and everything works fine.
After I installed ubuntu 64 bit, I tried to put the memory module back, but now
in dual channel, everything is ok!

The only question that remains is: my system should be able to work in single
channel ?? Why doesn't it??

Well, I'm happily running dapper 64 bit now :-({|= 

thnx **all** for the help, maybe my solution could be a help to some other people.
strange that this single channel gave me this probs?? It's supposed to work
according to the mobo manual.

summary:

MSI K8N Neo4 FI mobo
AMD Athlon 64 X2 3800+ cpu
XFX GeForce 7900GT graka
2x 1GB DDR400: works in dual channel, not in single channel, why?

also: when I put them in single channel, the speed is only 333MHz
in dual channel it is 400MHz
(according to MSI, this is normal?)

---

### Post by Patsoe on 2006-06-13
[QUOTE=steabert]I just took out a memory module, and everything works fine.
After I installed ubuntu 64 bit, I tried to put the memory module back, but now
in dual channel, everything is ok!

The only question that remains is: my system should be able to work in single
channel ?? Why doesn't it??[/QUOTE]

Just a question of curiosity first: why did you want to run it in single channel mode?

In all but the latest revisions, the S939 Athlon64s don't support more than two rows of memory running full speed (400MHz DDR) per controller. Since many DIMMs have two logical rows (I think they're called banks, but all that terminology is so confusing, since lots of people call the whole modules banks), putting two DIMMs on one channel means it is running four rows. AMD specifications say that the highest speed will then be down to 333MHz DDR. *EDIT: I'm not sure if I'm putting this quite right... I read somewhere else that it is a limitation that some motherboard manufacturers impose. One other thing to add: if you run four rows on one controller, the command rate must be 2T.*

Maybe you were running them in single channel mode, but still at 400MHz? Now that you've been moving the DIMMs around, the mainboard has reset the settings to 333MHz, which makes the setup stable again.

Still, there's a lot of advantages in running dual channel mode, so that's what I'd do. For one, you can run the DIMMs at 400MHz, which makes them synchronous with the CPU. Also, there's more bandwidth (almost double) and DMA masters (like graphics card and SATA drives) can access RAM while the CPU is accessing it too.

You might want to run the Memtest utility (it should be in the Grub boot menu) overnight to make sure it's really ok now. I'm glad you found the problem :)

---

### Post by steabert on 2006-06-13
[QUOTE=Patsoe]Just a question of curiosity first: why did you want to run it in single channel mode?

Maybe you were running them in single channel mode, but still at 400MHz? Now that you've been moving the DIMMs around, the mainboard has reset the settings to 333MHz, which makes the setup stable again.
[/QUOTE]

Well, they came from the shop in single channel mode :cool: 

I don't understand this second thing though?
They came in single channel mode and the mobo indicated 333MHz as speed.
When I put them in dual channel mode, the mobo indicates 400 MHz as speed.

So I never ran single channel in 400 MHz?
And I didn't change it back to single channel to check if things froze up
again. Maybe I should test this :)

---

### Post by Patsoe on 2006-06-13
[QUOTE=steabert]Well, they came from the shop in single channel mode :cool: 

I don't understand this second thing though?
They came in single channel mode and the mobo indicated 333MHz as speed.
When I put them in dual channel mode, the mobo indicates 400 MHz as speed.
[/QUOTE]

Hmmm... some shop :-( 

Well, things should be stable in single channel mode, but I'm not sure if that's true for any bank/row configuration - that is, it might depend on the type of modules.

Also, the temperature at which the CPU is running may influence controller stability. So you might want to check the temps (in BIOS, or through "acpi -t" in a terminal) - wonder if that shop can apply thermal grease properly? :rolleyes:

By the way, the correct story about the RAM channels for the Athlon64 is here (but it's not in English... do you read Dutch?): [http://gathering.tweakers.net/forum/list_messages/649229///#ramcompatibiliteit](http://gathering.tweakers.net/forum/list_messages/649229///#ramcompatibiliteit)

---

### Post by steabert on 2006-06-13
[QUOTE=Patsoe]Hmmm... some shop :-( 
Also, the temperature at which the CPU is running may influence controller stability. So you might want to check the temps (in BIOS, or through "acpi -t" in a terminal) - wonder if that shop can apply thermal grease properly? :rolleyes:

By the way, the correct story about the RAM channels for the Athlon64 is here (but it's not in English... do you read Dutch?): [/QUOTE]

Hey, it's a fine shop :o 
Today, I bought a new cooler for the cpu in that same shop :D
strangly the thing doesn't cover the entire cpu-surface (I don't have a lot of experience with coolers) but it seems to work ok.
acpi -t gives 22C, which is impossible, as my room is 29C :confused: [-X 
I'll check the bios and report back.

As for the dutch, I don't think my native language will give me any problems :rolleyes:


edit: BIOS gives 38C for cpu and 41C for system
my windows distro gives 37 for cpu

is there a way to get acpi -t right?

(we're getting heavily off-topic, or not? guess this can also be called "kernel issue")

---

### Post by Patsoe on 2006-06-14
Yeah, I had sort of guessed it would be your native language :)

The cooler being smaller than the cpu's heatspreader is less than optimal (the cpu-cooler interface often is the limiting factor in cooling), but the temps are ok I suppose.

No idea how to calibrate the acpi temps... but I'm sure it's possible :razz:
*EDIT: you might want to take a look at the package lm-sensors. Haven't tried it myself but it might just be what you need. There's also a Gnome applet for it, I think.*

---

### Post by fragos on 2006-06-15
I installed the 6.06 RC which upgraded it self to the final on a Sempron 2800+ and my "uname -a" looks similar except -generic instead of -k8.

Linux Geo 2.6.15-23-amd64-generic #1 SMP PREEMPT Tue May 23 13:45:47 UTC 2006 x86_64 GNU/Linux

I've had no problems other than some 32 Bit applications and browser plugins.

---

### Post by geezerone on 2006-06-15
[QUOTE=steabert]Hey, it's a fine shop :o 
Today, I bought a new cooler for the cpu in that same shop :D
strangly the thing doesn't cover the entire cpu-surface (I don't have a lot of experience with coolers) 

edit: BIOS gives 38C for cpu and 41C for system
my windows distro gives 37 for cpu

[/QUOTE]

Is the cooler an Arctic freezer 64 or 64 pro? That doesn't fully cover the chip surface (about 1 to 2mm on each edge visible) but provided you have thermal paste it will be ok. Good cooler that BTW!!

---

### Post by steabert on 2006-06-16
It's an Arctic Freezer 64 Pro :D 

I don't have thermal paste however, just the bit that came attached
to the cooler.

I got lm-sensors working and it indicates about 42C on heavy load
(both cores compiling stuff).

Idle, it indicates around 30C for the cpu.

I'll check back in the bios

---

