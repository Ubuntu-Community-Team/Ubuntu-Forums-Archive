---
title: "hardware drivers for 64 bit OS"
date: 2007-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by vinceZZZZ on 2007-06-01
[Hello forum people,

please can you tell me how UBUNTU 64 bit.....will get HARDWARE drivers for my computer hardware?...

my video chip is a via pm800 chip....what about router drivers?...etc...

does UBUNTU 64...simply use it's own system drivers....to drive my hardware?

also, does all 32 bit LINUX software work on a 64 bit platform?.

thanks

Vince.

---

### Post by tgm4883 on 2007-06-01
> **vinceZZZZ said:**
> [Hello forum people,

please can you tell me how UBUNTU 64 bit.....will get HARDWARE drivers for my computer hardware?...

my video chip is a via pm800 chip....what about router drivers?...etc...

does UBUNTU 64...simply use it's own system drivers....to drive my hardware?

also, does all 32 bit LINUX software work on a 64 bit platform?.

thanks

Vince.

Let me answer your question with a question.  How does UBUNTU 32-bit get hardware drivers for you computer

Drivers for most things are built in.  Sometimes a driver must be installed for added functionality (like 3d drivers)

Whats is a router driver?

Alot of the 32-bit software has been compiled for a 64-bit processor.  The few that aren't can usually be made to work on a 64 bit OS.

---

### Post by vinceZZZZ on 2007-06-01
Hello,

thanks for your quik reply.

Well i am new to LINUX...but i believe that LINUX normally has many generic hardware drivers built in.

So presumably this is also true for UBUNTU 64...

You see my hardware is 2 years old...but it is 64 bit compatable. When i look at the DRIVE disc that comes with my computer board..it only has 32 bit drivers...for video chips...sound chips....ethernet etc...

I do not understand much too much about 32&64 bit software....i think it is all FORWARDS compatable isn't it....so like you say..most 32 bit applications will work on 64 bit hardware and operating systems....(this is what i understand happens with the Mosft windows world of software.....but i was not sure about LINUX software)

at the end of the day....i am just trying to decide if it is better to BUILD a 64 bit computer or a 32 bit....

it seams that if you do not use much hardware peripherals...then drivers are not a problem....and most 32 bit software will run faster on a 64 bit system.....(this is what i read)

any more advice welcome

thanks

ps...what i don't understand is how rare 64 bit software seams to be....i have only found one TOOL for windows64...an art tool called POVRAY...(but it still seams that there is no LOSS in building and using a 64 bit system)

thanks

V



V

---

### Post by vinceZZZZ on 2007-06-01
Hello,

thanks for your quik reply.

Well i am new to LINUX...but i believe that LINUX normally has many generic hardware drivers built in.

So presumably this is also true for UBUNTU 64...

You see my hardware is 2 years old...but it is 64 bit compatable. When i look at the DRIVER disc that comes with my computer board..it only has 32 bit drivers...for video chips...sound chips....ethernet etc...

I do not understand too much about 32&64 bit software....i think it is all FORWARDS compatable isn't it....so like you say..most 32 bit applications will work on 64 bit hardware and operating systems....(this is what i understand happens with the Mosft windows world of software.....but i was not sure about LINUX software)

at the end of the day....i am just trying to decide if it is better to BUILD a 64 bit computer or a 32 bit....

it seams that if you do not use many hardware peripherals...then drivers are not a problem....and most 32 bit software will run faster on a 64 bit system.....(this is what i read)

any more advice welcome

thanks

ps...what i don't understand is how rare 64 bit software seams to be....i have only found one TOOL for windows64...an art tool called POVRAY...(but it still seams that there is no LOSS in me building and using a 64 bit system)

thanks

V

---

### Post by jamesford on 2007-06-01
just download the desktop/live cd iso, fire it up and see if everything works before you install

---

### Post by vinceZZZZ on 2007-06-01
hello,

thanks, that is a good idea....try the LIVE ubuntu 64 CD disc first...and if the machine works(web etc)...then fine..

thanks

V

---

### Post by tgm4883 on 2007-06-01
> **vinceZZZZ said:**
> 
at the end of the day....i am just trying to decide if it is better to BUILD a 64 bit computer or a 32 bit....


Go with 64 bit.  There are a few things wrong with what you said, but lets take a look at that.

> it seams that if you do not use many hardware peripherals...then drivers are not a problem....and most 32 bit software will run faster on a 64 bit system.....(this is what i read)

Actually the opposite.  Running 32-bit software on a 64-bit system is actually a little slower.  Not much and may not even be noticable.

> ps...what i don't understand is how rare 64 bit software seams to be....i have only found one TOOL for windows64...an art tool called POVRAY...(but it still seams that there is no LOSS in me building and using a 64 bit system)

Wrong.  There is lots of 64-bit software available (maybe not for Windows).  Most things that are compiled for 32-bit are also compiled in 64-bit.

> 
I do not understand too much about 32&64 bit software....i think it is all FORWARDS compatable isn't it....so like you say..most 32 bit applications will work on 64 bit hardware and operating systems....(this is what i understand happens with the Mosft windows world of software.....but i was not sure about LINUX software)

Yep.  In the rare case that the software you need isn't compiled in 64-bit, all you need to do is satisfy some dependencies usually.  Check the forums, most of this has already been figured out.

> 

Well i am new to LINUX...but i believe that LINUX normally has many generic hardware drivers built in.

So presumably this is also true for UBUNTU 64...

You see my hardware is 2 years old...but it is 64 bit compatable. When i look at the DRIVER disc that comes with my computer board..it only has 32 bit drivers...for video chips...sound chips....ethernet etc...


ehh, I wouldn't say they are generic drivers.  They are open source, and for the most part fully functional.  Certain drivers sometimes need to be installed that are not open source (restricted drivers)  but this is a fairly easy thing to do.

You wouldn't be able to use your driver disk anyway (most likely has Windows drivers only).  Even if it did contain linux drivers too, there are most likely newer drivers available for it.

Pop the live cd in and boot it up.  At the terminal do "lspci" and see if anything comes up unknown.  Those may take a little setup but everything else should work.

---

### Post by ronocdh on 2007-06-01
> **tgm4883 said:**
> Pop the live cd in and boot it up.  At the terminal do "lspci" and see if anything comes up unknown.  Those may take a little setup but everything else should work.
I just wanted to point out that this is a good method, but additionally the **sudo update-pciids** command will grab more info for your hardware, thus helping the troubleshooting.

---

### Post by tgm4883 on 2007-06-01
> **ronocdh said:**
> I just wanted to point out that this is a good method, but additionally the **sudo update-pciids** command will grab more info for your hardware, thus helping the troubleshooting.

hmm, haven't heard of that before, what does that do?

---

### Post by vinceZZZZ on 2007-06-04
Hello again,

thanks for your good advice....it is only a little more dollars for me to get a 64 bit cpu....which can always be run on a 32 bit OS if needed...

It is good to know that Linux may have more 64 bit software....proper 64 bit...

my hardware here... is probably going to be just fine for UBUNTU 64....it's very popular brands of hardware...and it is all NEW...

To be honest....it is certainly not so nice to have to pay so much dollar for Vista 64....so this decision of miine.... to go with linux... is not too tough...

I wonder if any of you can offer me good advice about ROLLING BACK changes in Linux....a method of almost putting your LINUX into a shadow session....so no matter how much mess you create you can always ROLL BACK or dump the entire user session and changes....

I have found similar software for SHADOW working in windows...and it's super....i have never had a single window problem in a long time (1 year).....since using SHADOWUSER....and shadowsessions....(it is a kind of GHOST feature on drives)

thanks then

V

---

