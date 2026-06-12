---
title: "Dapper Grey Screen on G4"
date: 2006-04-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by godard on 2006-04-25
I updated to Dapper this evening on my G4 w/ GeForce2 card using the 'gksudo update-manager -d' command. Everything seemed to go fine, but upon restart i got through the textual boot screens and then dropped into a grey screen with no further disk activity and an unresponsive keyboard (so far as i can tell). Any help greatly appreciated.

---

### Post by Rxke on 2006-04-25
a whitish grey screen, like when you boot OSX?

---

### Post by godard on 2006-04-25
Yes, it looks like one and the same, sans logo and activity widget.

---

### Post by jono.carnie on 2006-04-25
Godard,
Are you able to do a safe mode start and check logs etc??


JC

---

### Post by godard on 2006-04-25
I'm a noob on Ubuntu, Jono, how do I safe mode start?

---

### Post by jono.carnie on 2006-04-25
Godard,

On X86 easy... on PPC I'm not sure.. I've not got my hands on one of them at the moment.

Anyone else able to help??

On X86 the boot screen lets you choose a kernel... normal/safe/memtest etc.

Sorry..

JC

---

### Post by Rxke on 2006-04-26
No, I think what he's seeing is bootprocess hanging, I used to have that in the early days w/ OSX too... Problem is I forgot how... Maybe booting up keeping the 'command-v' button pressed, puts you in verbose mode? (doubletake: no that's for OSX...)

You're not dualbooting, it's just plain Linux?

---

### Post by godard on 2006-04-26
I am dual-booting, but the grey screen is after i get through the second boot prompt screen.

---

### Post by Rxke on 2006-04-26
this is not a fresh install? I mean, before this you had Dapper running and did apt-get or another way to upgrade? If not, did you do a repartitioning of your drives?

---

### Post by godard on 2006-04-26
Before this i had Breezy running, i just did a  'gksudo update-manager -d' through the terminal - download and install seemed to run fine. After the reboot the grey screen appeared as discussed above.

---

### Post by Rxke on 2006-04-27
I'm stumped. (But then again, I'm quite a noob...)
You got important stuff on your machine? (The Ubuntu part)

---

### Post by jono.carnie on 2006-04-27
You could always pop a live cd in, boot up and go looking at the logs etc....
You'd feel much better knowing why it's stopped booting if you have to wipe it.

JC

---

### Post by godard on 2006-04-27
I downloaded the beta install disk and tried doing a fresh install. After getting the grey screen again after the initial prompt, i tried the 'install video=ofonly' option, sadly it was back to the grey screen again. Jono, which logs should i be looking for, and what would you recommend keeping an eye out for within them? 

At the moment, i'm just pitching here, but i'd say there was something up with the video driver for beta one. I'm wondering if i should just hang out for beta two.

Rxke, There's nothing important on the machine that i haven't backed up or can't replace later.

Postscript: I decided to have a play with the installer on my old B&W G3 which has an ATI card in it - sure enough, the installer, briefly, goes to a grey screen, but then pushes on through to the installer. At this stage i'm going with that particular installer not liking nvidia for the moment. Unhappily for me, the installer keeps failing at around the 74-75% mark. The good news is that beta 2 is out today and one of the things they mention is the installer has had some work, not to mention the developments since beta 1 - i'll download, give it a go and report back.

---

### Post by godard on 2006-04-30
<deep breath> Okay, here's an update on beta one on my G4. I redid a clean install of breezy and did a dist-upgrade using the Dapper beta one cd. The upgrade seemed to go well and i played around for a while with the new look and then logged out. Logging in gave me a bunch of messages and warnings to restart but everything looked good and semed to be functioning fine, thinking everything was looking okay, i restarted. Sure enough, back to the grey/white screen after the yaboot boot choices and the boot: prompt is back again.

The good news is that i know there is a working install there, sadly i just can't get to it.

**Update Two**

I downloaded the Dapper beta 2 live CD. Same problem with beta 2 on the G4 with the nvidia - a couple of boot prompts and then the grey/white screen which doesn't change at all.

On the old B&W G3 with the ATI card, the cd loads up, punches through the grey/white screen section of the install, but then when nautilus is loading it complains about an error 3 with the bonobo-server. I can get to the command line from there, but have no knowledge of where to go from there.

I'd really like to take my old B&W out of the equation entirely and concentrate on getting Dapper working properly on my G4, but if i can help with testing and stuff on that for anyone - i'm happy to do that.

I'm pretty confident about filing a bug on this now that it's up to beta 2, yes?

---

