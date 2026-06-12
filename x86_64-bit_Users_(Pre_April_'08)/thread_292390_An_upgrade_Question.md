---
title: "An upgrade Question"
date: 2006-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Princey on 2006-11-03
I'm currently run Kubuntu Dapper and I'm thinking of upgrading to Edgy. What's the best way? Fresh install (I have home, usr, root all on separate partitions) or apt-upgrade? I read some posts of folks having problems with fglrx which I have running.

---

### Post by Azakus on 2006-11-03
The easiest way I found to do this was the update manager GUI updater. It was painless and went well.
Best way to force it to see the update is run "sudo update-manager -c -d" which will check for updated distros and distro upgrades, and needs both flags.
It will take a minute, ask to restart, and be ready to go.

---

### Post by Princey on 2006-11-04
Thanks for your contribution but I do know how to upgrade. I saw yours went smoothly but as stated earlier, I've read numerous threads where persons have had problems and went for a clean install. Just wanted to get feedback from both sides. Maybe I should have made it a poll.:-k

---

### Post by Princey on 2006-11-15
Ok, downloaded the Desktop version of both the i386 and AMD 64 isos, burnt to CD and booted up to see what's on before I could make my final decision. ](*,) starts up normally, then gets a text based screen with a log in prompt. I type > startX and a series of text flies through the screen with the final output saying something like X couldn't find any screens. Funny thing is that I tried it on my AMD 750 MHZ running an nVidia GForce 400 and it booted flawlessly. Just refuses to work on my new machine. Note, I had a similar problem with Dappper but chosing 'safe graphics mode' solved that problem. This time around, safe graphics mode does nothing. It does that on both the AMD 64 and x86 disc. Does anyone else with an ATI card experience the same problem and if so, how did you go about upgrading/installing to Edgy? 

P.S. I have an ATI X600 Express video card.

---

### Post by MST3Kakalina on 2006-11-15
I had this same problem when I tried to run a (I think it was 5.10) live disc on my HP pavilion zv5000us laptop.

Unfortunately, I was never able to figure out what that crap was, so I can't really help you. On the behest of another user here, I ordered a 6.06 disc from ShipIt, and that made all the difference.

---

### Post by RFScheer on 2006-11-15
Original post removed by idiot poster:)

---

### Post by Princey on 2006-11-16
> **RFScheer said:**
> I don't have an ATI card but consider this.  Edgy's Xorg looks for modules in /usr/lib/xorg/modules/ and your /usr directory is an old partition which won't be updated with the new install, right?    I don't think you're going to be able to use your old /usr partition without great care and at least renaming it.  What's the output of /var/log/Xorg.log.0 look like?  Maybe I've misunderstood your config.  Hope it helps.  Thanks MST3Kakalina for your input. I still can't for the life of me figure out why it's still doing that. I'm downloading the alternate CD to see if there'll be any differences.

RFScheer, thanks but I don't think you get my question. I'm still running Dapper. I booted off the CD just to see how edgy played with my system before doing a clean install. So, editing Xorg config is out of the question here. There are no messages in var log either. But seeing I'm running off the Edgy desktop CD, wouldn't it be looking on the cd's image for the configuration rather than my installation on my harddrive? As stated, I haven't as yet installed Edgy and just wanted to see what it was like for myself before doing a fresh install.

I'd really like to hear how those with ATI cards feared out.

---

### Post by Princey on 2006-11-20
Success!!! :) :D Finally got it working. This is what I did. 

I went back at it and this time, changed my screen resolution in the VGA settings prior to booting from the live CD to the highest my monitor supported, 1280 x 1024, and booted in safe graphics mode. Same problem. However, this time, when thrown back to the prompt, I could read the entire message. I had just finished writing out the entire message on screen and went to check the var log messages to post back on here. Alas!! :( var log was empty :( Nothing could be found in var log messages about X-server or xorg so I followed the crazy thought that popped into my mind, go check the xorg.conf file. 

Typed > sudo nano /etc/X11/xorg.confhit enter and scrolled through xorg.conf for any anormalities that might pop up.

Guess what I found? The 'safe graphics mode' is supposed to load the 'vesa' driver which works on any graphic card irrespective of the manufacturer. In this case from the Desktop Live CD, it doesn't. It still defaulted to 'ati'. I changed 'ati' to 'vesa', saved using CTRL and X and typed > startx and voila, after the momentary black and white screen, here I am posting from the Desktop Live CD. Isn't that a bug or something in the live CD?:-k:-k

---

