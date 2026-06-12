---
title: "i386 --&gt; 64-bit Ubuntu advice requested"
date: 2006-07-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by IoCaster on 2006-07-13
I've gotten the i386 version installed and running fine. Everything from xgl+compiz to all of my multimedia apps are installed, configured and operating smoothly. The problem is that I've got an AMD 64 X2 4400+ and I've got that itch. Some of you know what I mean I'm sure. I just can't leave well enough alone. I must tinker and tweak until I hit the wall. I'm compelled to install the 64-bit Ubuntu. 

Here is my hardware list as I posted it in the hardware compatibility list thread.....

[I]MSI K8N Neo4 Platinum
AMD 64 X2 4400+
Sapphire GeForce 7800GTX
Dell 2405FPW
Audigy 2 Platinum
HP-dvd640 DL DVD/RW
Generic DVD-ROM Drive
PATA 120GB HDD
PATA 160GB HDD
SATA 250GB HDD
Linksys WRT54G router as 10/100 switch
Chilibox CB160W - NAS/Server/Router/Wireless
HP Photosmart 3310 AIO Printer w/wireless 

Dual booting WinXP Pro + Ubuntu[/I]

Would any of the hardware listed be problematic with the 64-bit version? Should I reformat and start from scratch or simply install over my existing i386 version as a kind of upgrade? What would be the preferrred method to use? My /home is on a separate partition, but I don't know how that would affect a transition.

Any and all advice would be greatly appreciated.

Regards -- Joe

---

### Post by DiamondX on 2006-07-13
From what I have heard, if it works in 32bin, theres drivers for 64bit (linux only, not true with winxp). I had the same delema as you, everything installed, but using 32bit with an AMD64. I just switched last night. I cant help tinkering with it. I cant cound how many times Iv reinstalled ubuntu (or windows, but that was my fault only half of the time).

Edit: Forgot to answer the rest of your question:
I think you should backup, then upgrade. If it doesnt work out, reinstall.

---

### Post by Kilz on 2006-07-13
My advice to you is to setup 64bit on a seperate partition if you have the room. That way you can tinker and get it just right. You can probably mount your existing home partiton in the 64 install. If you have any issues you can just boot into the 32bit partition. 
Once its as you want it, you can delete the 32bit partition

---

### Post by IoCaster on 2006-07-13
> **Kilz said:**
> My advice to you is to setup 64bit on a seperate partition if you have the room. That way you can tinker and get it just right. [B]You can probably mount your existing home partiton in the 64 install. If you have any issues you can just boot into the 32bit partition. 
Once its as you want it, you can delete the 32bit partition.[/B]

Excellent advice and just exactly what I was seeking. It's certainly something I hadn't even considered. Sounds like a workable solution and hopefully non-destructive.

Thanks and best regards.

-- Joe

---

### Post by IoCaster on 2006-07-13
snip....

[QUOTE=]I cant help tinkering with it. [/QUOTE]

Believe me, I know the feeling. It's an incredibly strong compulsion and I'm helpless sometimes in my efforts to resist it.  :twisted:  

I guess I'm a tech junkie or something. :mrgreen: 

Best regards -- Joe

---

### Post by RAOF on 2006-07-13
I don't think you can actually "upgrade" as such from the 32bit version to the 64bit version.  They're implemented as different architectures, and apt doesn't (yet) deal very well with that sort of stuff.

But if you just keep your /home unformatted, you will at least have all your (personal) settings preserved.

---

### Post by lin_uxsprout on 2006-07-14
I'm a newbie and I use simply mepis (similar to ubuntu)I also could not resist the urge to try 64bit processing.That is where this begins.I have an intrest in music and 64studio looked like a good place to start.I do not think the problem i had was caused by the software directly but my lack of knowledge to properly set it up.The program uses kernal 2.6.17 and it loads and boots quite fast.Yesterday I was in a program called "hydorgen",it is a drum machine.granted the room temp was warm I got a message about the cpu overheating.Initiallyit did not worry me however I decided that because I had found that some things did not work like totem a movie player and now this.I decided to remove and install kanotix64 wich took forever(cpu still hot)It installed and did not boot.the grub loader asked for permission on install it recognized windows and ubuntu 6.06 wich I don't have(mepis 6.0rc5)when I booted it said I still have 64studio instead of 64kanotix.It went from bad to worse.i tried to install again no help then on reboot no boot(panic)I put mepis in the rom and booted to kde and then to install and grub.installed boot in mbr,all better now and I did not loose my main drive.There are less packages in synaptic for 64 bit and it seems to make the processor work harder.I give,back to i386 32 bit mepis.

---

### Post by DiamondX on 2006-07-15
> **lin_uxsprout said:**
> I'm a newbie and I use simply mepis (similar to ubuntu)I also could not resist the urge to try 64bit processing.That is where this begins.I have an intrest in music and 64studio looked like a good place to start.I do not think the problem i had was caused by the software directly but my lack of knowledge to properly set it up.The program uses kernal 2.6.17 and it loads and boots quite fast.Yesterday I was in a program called "hydorgen",it is a drum machine.granted the room temp was warm I got a message about the cpu overheating.Initiallyit did not worry me however I decided that because I had found that some things did not work like totem a movie player and now this.I decided to remove and install kanotix64 wich took forever(cpu still hot)It installed and did not boot.the grub loader asked for permission on install it recognized windows and ubuntu 6.06 wich I don't have(mepis 6.0rc5)when I booted it said I still have 64studio instead of 64kanotix.It went from bad to worse.i tried to install again no help then on reboot no boot(panic)I put mepis in the rom and booted to kde and then to install and grub.installed boot in mbr,all better now and I did not loose my main drive.There are less packages in synaptic for 64 bit and it seems to make the processor work harder.I give,back to i386 32 bit mepis.

That is weird. I have heard ubuntu doesnt work with laptop fans, but Im assuming your using a desktop (idk why, probably because I am right now). Also, next time please use more spaces, maybe make paragraphs, and use correct punctuation (and capital letters). Thanks.

---

### Post by Lil_Eagle on 2006-07-15
I can tell you why it said you had Ubuntu instead of Mepis 6.0... 

Mepis 6.0 is actully a revamped Kubuntu.  There are minor differences, but they both use the same repositories.  One thing that bothers me about this is that if you use Mepis, every time you install something with apt-get, you receive a message about how the authenticity of the package couldn't be verified and installing the said package could damage your system.  Certainly that is true if you change from the 386 kernel that it comes with and replace it with the 686 version that is more likely the one you should be using, but not so with the other packages.

Since the Mepis kernel is modified differently than the Ubunutu one, you would be changing to ubuntu if you did it, but you'd still be getting the stupid messages.

Perhaps this issue will change in the final release, but somehow I don't think so.  I actually like Mepis, but since there is no 64-bit version of it, and the aformentioned problem exists, I run Kubuntu AMD64.

---

### Post by lin_uxsprout on 2006-07-15
Yes Sir,I will try to use punctuation sir.Yes sir it is a desktop and no sir it is not Ubuntu.Both of the fans were running.The cpu was probably running 100%. If you would please correct my spelling and give me a grade.I was in a hurry when I posted.
 It is 64 studio wich is Debian as is Ubuntu,Mepis and many other distro's .
 I have never been attacked about spelling, punctuation,capitalizing or lack of paragraphs. 
 I was replying to the post by loCaster.It was my intention to help,since I do not use the same distro I suppose I do not belong here.I like linux and they are all related.
 I would assume that this might get me banned but I did not originally intend to offend anyone until I read the post by diamondx undoubtedly a scholar and a gentleman:twisted:

---

