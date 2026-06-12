---
title: "Anyone esle trying GPUGrid?"
date: 2008-12-18
forum: x86 64-bit Users
---

### Post by thaumielx72 on 2008-12-18
GPUGrid is the DC project using Video cards to run scientific applications on.  (BOINC)

Since it only runs under Linux with 64 bit OS I figured this would be the place to ask.

(Although it will run under most Windoz platforms)

My take so far:  If you let it get started it can rapidly become a pain to get your system back.  I know, it supposed to run in background, but even changing the preferences to run only after X time of inactivity I still have to suspend it or even the cursor becomes very unresponsive.

There must be a way to give it less priority so any other program (X, for instance) will immediately suspend it until the user has left it alone for awhile.  Then you can check other things on your box without a long delay.

I'm gonna load Envy and see if the Nvidia utils it brings up will help here.  I'm letting another program run to completion now but will reboot and see if there is help there.

Not a complaint, just a question.

):P

---

### Post by theotherphil on 2008-12-18
I used the BOINC client last night to give the Seti@Home project a whirl using the new CUDA core. I was wanting to see what sort of performance my 9600GT would give but the system promptly hung. Not just slow to respond, I mean hung....I couldn't even ssh into the box to kill the process and had to resort to powering down the machine.

---

### Post by XCan on 2008-12-18
I wonder if they will add new boinc managers to the synaptics though. I'm kind of tempted to test the new version as well. But I guess I'm just too cowardly/stupid to install anything without synaptics. :p

---

### Post by thaumielx72 on 2008-12-19
Coincidently, Synaptic is what I was looking at for my solution right now.  I was searching the Ubuntu forums and thought I'd check out the responses I'd gotten so far.

The problem now is that Synaptic will install Boinc 6.2.12-1 and CUDA needs at least 6.4-2 and they recommend 6.4.5 since they have made an update to the code that fixes a problem with run times.

*However...*

By using /BOINC/run_manager in the terminal it immediately tells me I need to attach to a project.  I am already attached to GPUGrid and I have two wu's partially done somewhere in my system.

These are really *loooong* running execution times.  It is not reasonable to let only GPUGrid run on my desktop for God knows how long. I will be able to do virtually nothing else.

( I need my internet.....)

Well - I'm off to run some chores I'll try a few things when I get back.

Incidentally: the program I was referring to earlier was nvidia-settings.  It doesn't really allow me to change the settings I would need to change.

I have considered under-clocking it but several boards advise against this.  It would render the scientific results worthless.

This is sort of annoying as it already is niced to begin with but still grabs hold of my display and is very reluctant to surrender it.

---

### Post by coolbrook on 2008-12-26
> **thaumielx72 said:**
> it only runs under Linux with 64 bit OS
That's too bad. I was looking to upgrade my video card and get it crunching. Hopefully other projects will eventually support 32-bit Linux.

---

