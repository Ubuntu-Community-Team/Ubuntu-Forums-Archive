---
title: "Difficulties after installation..."
date: 2005-12-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by kufford on 2005-12-31
Hello all,
 
I recently built a new system comprising of the following components:

AMD 3700 64 bit processor
2 gigs corsair ram
Antec Sonata II Case
EVGA NFORCE SLI MOBO
EVGA 7800GT
WD SATA II 250 gig HD
Viewsonic 902b 19" LCD

I have my windows partition working well, however - I'm having issues with the breezy installation (note: I'm running 32 bit ubuntu, no need for 64bit ubuntu - especially with the lack of support). I can make it through the entire installation, up to the point for my initial log-in. After I login into the system, all I see is a blank screen with the ubuntu (nasty brown) background. I have a cursor and that is all. 

I think it may be a resolution problem as I can hear the "ubuntu chime" after I log in, but simply go no further afterwards. I then have to manually restart the machine, as no commands will work. 

I've been running ubuntu for several months now and am pretty comfortable with the OS, however, I was blessed with a system that installed without any trouble so I may have some initial issues with any suggestions that may be forthcoming. I ask for patience :) :)

For the record, I did try to google and use this site's search function to obtain the answer to my problem - however, this is one of those things that can't easily be explained in a search box. 

Thanks again, 

Ken

---

### Post by Atreju on 2005-12-31
Well I supose that if you do see a brown screen and hear some sounds, you must not be far from having a working system...

did you try to switch to another console by pressing Ctrl+Alt+F1 ? can you log in from there ?

if you can you could take a look at you x config file, or even run "ps ax" to see what's running....

Only suggestions, give it a try and give us some feedback :-)

> note: I'm running 32 bit ubuntu, no need for 64bit ubuntu - especially with the lack of support
what do you think we are doing here ? hehe, we're giving "support for breezy 64" ! :D

---

### Post by kufford on 2005-12-31
Actually, it was a problem with my video card - and to think i built my new system nvidia for the linux support. lol

future reference: 

the problem was fixed by the following...

boot into safe mode
sudo apt-get install nvidia-glx
nano -w /etc/X11/xorg.conf

find section that talks about GPU

change driver from "nv" to "nvidia"
ctrl + o
ctrl + x
sudo /etc/init.d/gdm restart

hope this can  help someone. This is the second time I've answered my own question here, I guess once I get frustrated enough to post up my problem - I always seem to find the answer...

---

### Post by Atreju on 2006-01-02
[QUOTE=kufford]hope this can  help someone. This is the second time I've answered my own question here, I guess once I get frustrated enough to post up my problem - I always seem to find the answer...[/QUOTE]

I think it's always a good thing when you find a solution even to one of your question the you post your answer: The post does not die stupidly, we know what you did to solve the issue :D

happy linux !

---

