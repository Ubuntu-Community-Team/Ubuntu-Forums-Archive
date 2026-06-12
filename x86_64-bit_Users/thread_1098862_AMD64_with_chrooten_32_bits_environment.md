---
title: "AMD64 with chrooten 32 bits environment"
date: 2009-03-17
forum: x86 64-bit Users
---

### Post by AlexVader on 2009-03-17
Hi Forum

I Want to buy a laptop with 4Gb ram extendable to 8GB ;

I have the source code of several applications that are CPU intensive ( mostly engineering simulation application ), but I also have proprietary applications that wont run natively on a 64 bits environment;

So that leaves me with two options:

Either install an AMD64 version to compile and run natively my open source applications and run my 32 bits application in a chrooted environment,

Or just forget about the 64bits stuff and just install a 386 32 bits version of Ubuntu and run all in 32 bits.


My two questins are :

Does my 8.04 32 bits reach for all my 4Gb ram...?

Are there any performance degradations in running a 32 bits app in a 32 bits chroot environment over a 64Bits system, compared to running it natively over a 32 bits system....?

Thanks in advance

Alex

---

### Post by insane_alien on 2009-03-17
64-bit ubuntu can run 32-bit apps if you install ia32-libs. no need for a chroot.

---

### Post by AlexVader on 2009-03-17
Hi Insane_alien

This may be correct for a single executable... but is it valid for a complex and large program with several dozens of executables like Pro Engineer Wildfire 3 for Linux ? ( it exists only for 32 bits OS... )

How do i do... ?

I guess I must first type something like apt-get install ia32-libs in bash as root, but what after...?

Supposing I installed ia32-libs, installed Pro Engineer and symlinked the executable to /usr/local/bin...  If I type then proe in a bash shell ( like I do in my 7.10 x32 ) will it launch Pro Engineer in a 32 bit environment...? inside my 64 bits OS...?

Thanks in advance

Alex

---

### Post by insane_alien on 2009-03-17
as far as i know, yes it should work for more complex programs.

i just tried it with the 32-bit version of open-office(just for a larger multi executable program) worked fine.

---

### Post by Yellow Pasque on 2009-03-18
> Does my 8.04 32 bits reach for all my 4Gb ram...?
No, 32-bit systems can only address 3.2GB of RAM, unless you install the server kernel with PAE, in which case, the OS can address 64GB, and a single app 4GB. 64-bit systems can theoretically address a large amount (can't remember the exact number) of memory, but it depends on a properly implemented BIOS.

> Are there any performance degradations in running a 32 bits app in a 32 bits chroot environment over a 64Bits system, compared to running it natively over a 32 bits system....?
No, you're not emulating or virtualizing anything, so the code still runs natively. Running a 64-bit OS would probably give a nice little performance boost for your open-source scientific apps.

---

### Post by AlexVader on 2009-03-18
Thx Temujin

I will most certainly install the 64 bits thing...

I Have also heard that the Feisty 7.04 was a lot faster than 7.10, 8.04 and 8.10... guess it was in a phoronix benchmark...

Is 9.04 stable release ready yet...? Do you know if it will be faster than 7.04...?

BRGDS

Alex

---

### Post by 3Miro on 2009-03-18
My 2 cents,

I myself am running 64-bit 8.10 and running fluid flow simulations on it. The instance you put double something in your code, you want 64-bit machine.

I run skype 32-bit directly under my 64-bit machine as well as other simple code. I guess it is possible for your app to fail to run, but it i unlikely (also if it is an Engineering software, they should make a 64-bit version of it).

If you run into trouble, you are probably better off dual-booting 64-32 bit rather then sacrificing the ram and speed on the full 32-bit system.

---

### Post by 3Miro on 2009-03-18
I had 7.04 long time ago and I don't remember if it ran faster, I wouldn't think it did. 9.04 should be ready in a month or so, but I for one wouldn't migrate at once (mostly because I would be very busy with other stuff for the next couple of months).

---

### Post by Slim Odds on 2009-03-18
> **AlexVader said:**
> Is 9.04 stable release ready yet...? Do you know if it will be faster than 7.04...?


Sir, may I give you a genuine and heartfelt LOL

9.04 means April 2009, so no, it is not a stable release yet (but soon).

---

### Post by AlexVader on 2009-03-18
Hi 3Miro

What do you use for CFD...? OpenFOAM or Fluent...? ( those are the ones I work and feel more comfortable with...)

I also do a lot of FEA, and genetic design optimization, but as you most certainly know, all these require meshing, and meshing requires a 3D solid modeler... meaning a  3D CAD...  In Linux, Pro Eng Wildfire 3 is my only option... but ...   :-( exists only in 32 bits...   :-((   

About the Feisty Fawn speed thing check this...

 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1)

They say that Ubuntu has been losing speed with the successive versions...

Is this processor dependent... ?  My CPU will be an Intel Core Duo P8600, and most of my apps are written in C++ and will be compiled using GCC...

What can you tell me about the performance of PC BSD 64 bits for high end scientific computation, "exotic" ( this would be the correct word ... lol ) CFD, like Deflagration analysis within an engine Cylinder with a moving mesh, or Deflagration to Detonation Transition in an air-fuel aerossol, like it happens in a Fuel Air Explosive... This kind of CFD is one order of magnitude slower to run than "standard" compressible turbulent analysis : In each iteration you solve a chemical kinetics problem, probably involving dozens of ordinary differential equations, and a thermal multispectral radiation transport problem involving a diffusion equation for each wavelength in the thermal spectrum under analysis...

Meaning that 4GB and an intel Core Duo at 2.4 GHz are not that much....  Probably not even a Cray, if you want to analyse things straight ( Rayleigh-Taylor instabilities in interfaces in shock propagation in condensed matter ...  )

Does Unix ( PC BSD Fibonnaci X86-64) speeds up things compared to Linux ( Ubuntu 8.10 AMD 64 ) ?

Thanks in advance

Alex

---

### Post by 3Miro on 2009-03-18
I have never used BSD and I will read the entire article, but it seems that they were running the test on 32-bit version.

My CFD is directly written in C++ with the only use of Matlab distmesh for meshing (I do mostly 2D). My study is more theoretical and I am using the code to experiment with theory more then anything else. I am trying to compute optimal feedback control law for Navier-Stokes and large PDEs in general.

In either way, I recently did incompressible flow pass a cylinder simulation (you have probably seen that example), having total of 27000 unknowns in less than 17 hours (on an AMD X2 2.3 Ghz CPU). Nothing exotic, however, just the standard turbulent wave that forms behind the cylinder. My code is definitely not optimal, I expect your apps to work better.

If your mesh generation is build for Linux, you should be able to just run it without glitches. I am running 32-bit windows games on my 64-bit Linux machine without problems (there is no slow down dues to 32-64 bit).

---

### Post by 3Miro on 2009-03-19
I don't know about those Phoronix tests, on one side you kind of expect that newer versions of the OS would have more features and those will have an overall impact on the system. If you need huge performance, you should look at an optimized system (turn unnecessary stuff off and so on). When I was running my  program I was at the same time browsing Internet and listening to music.

If there truly was such a big drop in performance, IMHO the community would have noticed.

Furthermore the tests were performed on a laptop, a desktop is a much better place for testing heavy performance. Laptop hardware is very tricky sometimes. Drivers could be another issue, KDE on pre 1.80 NVIDIA driver runs as fast as a crippled turtle.

If you want great performance from your machine, boot a different run level, no X, no apps, no Network, just the program that you want. Now that would be the fastest.

---

### Post by AlexVader on 2009-03-19
Hi 3Miro

I also have this experience... redirecting shell output to /dev/null, something like :

nohup nice -19 #myApp [argList] > /dev/null

Generally boosts up performance quite a lot... specially it you do it after init 1 as root...

Once I did that while running an "exotic" CFD-FEA coupled problem ( The impact of a high altitude shock wave resulting from a blast in an underlying building structure and its collapse analysis ( eigen value problem) ... ) took all night to run... but in the morning, the results were there... but then again, I used a "trick" ( only works with structured 2D-3D meshes though...) : Adaptive mesh refinment trigered by gradients of pressure in the fluid mesh, meaning:

The mesh was globally coarse, and locally fine, being that the "local" captured the shock wave and its reflections and interactions...

Anyway...  bought my lappy this morning, will backup MicroBulshit OS so as not to void warranty in case i need to reinstall Vistugh ( it is an HP ) and will start in ascending order trying those :

7.04 AMD64, 7.10 AMD64, 8.04 AMD64 and 8.10 AMD64,

I will use the Live DVD installers so as to watch how my hardware is recognised...

Once I decide which one to install I will  go to the lower ( more stable, thinner, and faster ) version, and install it with the Alternate installer allows me to have strong encryption at Filesystem level, I do not want any North Korean dude to steal my lappy and learn about unifocal spherical implosion systems; instability mitigation in shock compression devices, pulsed detonation engines, chemical lasers... u know...  those kinds of "grown up kids play toys"...  :-D

Just kiddin here :-)

Anyway, Ill keep in touch on how does Dv5 1170 behaves with Ubuntu...


One more trick to boost tings up in Ubuntu... ( Have a smaller memory footprint ) Dump Gnome, and KDE ( at least do not use it...   try something like WindowMaker, of FluxBox...


Best regards

Alex

---

### Post by 3Miro on 2009-03-19
I have used Windows Maker and it does rock. If you want a boost in performance, it is the next best thing to booting under another run level (3 I think was the right one).

If you encrypt the HD you will suffer a performance hit (well better that than a hit from NK).

Post results on your tests, I am wondering if older versions are indeed faster.

---

