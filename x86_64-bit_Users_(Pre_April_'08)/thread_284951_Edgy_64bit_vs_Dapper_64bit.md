---
title: "Edgy 64bit vs Dapper 64bit"
date: 2006-10-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Pawel Stolowski on 2006-10-26
I've been using 32-bit Dapper on AMD64 machine as it was too much hassle to deal with 32bit software (I don't want to use chrooted environments). Now as I'm going to upgrade to Edgy I need to choose between 32 and 64 bit again. Is Edgy any better in terms of 32bit apps support than Dapper? Can I easily install 32-bit Firefox + flash plugin using official repos in Edgy? Could someone using 64-bit Edgy share his opinion about 64bit Edgy vs 64bit Dapper? Thanks in advance!

---

### Post by Apostata on 2006-10-26
Good question - I'm curious about what has changed (if anything - beyond app versions) in 64-bit since Dapper.

---

### Post by Kilz on 2006-10-26
> **Pawel Stolowski said:**
> I've been using 32-bit Dapper on AMD64 machine as it was too much hassle to deal with 32bit software (I don't want to use chrooted environments). Now as I'm going to upgrade to Edgy I need to choose between 32 and 64 bit again. Is Edgy any better in terms of 32bit apps support than Dapper? Can I easily install 32-bit Firefox + flash plugin using official repos in Edgy? Could someone using 64-bit Edgy share his opinion about 64bit Edgy vs 64bit Dapper? Thanks in advance!

The simple answer is no. The complex answer is that you dont have to use a chroot. 32bit firefox, and I am talking about the 2.0 reciently released is avilable from my howto (works with edgy), link in my signature. Also they are my .deb files, made from official mozilla binaries and not in the repos. But if you can double click on the install script, chose run in terminal, and answer yes or no to what plugins you want installed its very easy.
The reason its not any easier is because the developers do not want to put the effort into multiarch. Thats the ability to install 32 and 64bit applications. I know Debian has plans to get multiarch working. Perhaps when they get it in the Ubuntu developers will make it work here.
I had an extensive "discussion" with them on the developers mailing list. They say it wont help that many people. I tend to find that strange as nearly every processor sold today is a 64bit chip.

---

### Post by fabertawe on 2006-10-26
> **Kilz said:**
> [snip] I had an extensive "discussion" with them on the developers mailing list. They say it wont help that many people. I tend to find that strange as nearly every processor sold today is a 64bit chip.

I find that odd also. They should concentrate on the 64 bit version as before long, like you say, there will be hardly any (if any) 32 bit processors sold and the 64bit OS will be the norm. I'm sure Microsoft won't be so coy when the time is right, they will phase out 32bit Windows in an instant! It's a chance for Ubuntu to steal a lead really.

Paul

---

### Post by Kilz on 2006-10-26
> **fabertawe said:**
> I find that odd also. They should concentrate on the 64 bit version as before long, like you say, there will be hardly any (if any) 32 bit processors sold and the 64bit OS will be the norm. I'm sure Microsoft won't be so coy when the time is right, they will phase out 32bit Windows in an instant! It's a chance for Ubuntu to steal a lead really.

Paul

If you are interested in reading exactly what was said you can find [the whole thing here]("http://archives.free.net.ph/thread/20060923.055234.87fea1fd.en.html#20060923.055234.87fea1fd"). I also agree that it is a chance for Linux to expand on the great 64bit support that isn't available in Windows **yet**. IMHO they are letting an opportunity pass them by. Other distro's like SuSE are already multiarch. I want to see what 10.2 looks like in Dec. I also think when Vista is released 64bit Windows use will start to climb. It may be preinstalled on 64bit machines.

---

### Post by Bardia on 2006-10-26
Kiltz quick question for you while you're here.  Last night I ran your script to install 32bit Firefox 2.0 + plugins and everything worked fine, but after what looked like an install the terminal would just close.  I was unable to find any shortcuts (not sure if that's the official linux lingo, I'm still pretty new) or the actual program in the file system so I don't know if it installed.

I went ahead and used your manual installation instructions and they worked great, except that it installed the 1.5 version.  

I'm downloading 6.10 right now, going to reformat and try again, but if you can think of anything I'm doing wrong let me know.  

Thanks a ton man, I love the effort you're putting in the 64bit stuff.  I didn't buy a C2D to waste on 32bit applications.  :)

---

### Post by The Keeper on 2006-10-27
I hope that after Debian 4.0 (Etch) is released, Debian developers start working on multiarch for 4.1. After all, they need to rewrite most of the package management programs starting from dpkg to make it happen.

It is very disappointing that Debian and Debian derivatives are so far behind other linux distros and even Windows when it comes to multiarch support, but not all if any blame should be pointed towards Ubuntu developers.

---

### Post by earthfall on 2006-10-27
The only remarkable difference with Edgy 64bit is native openoffice. OO used to be really slow on Dapper 64 bit but is quite usable in terms of application response. For firefox browser, practically there is no other option but 32bit version.

---

### Post by jonah1980 on 2006-10-27
edgy seems much better to me. apart from all the packages being later versions there are more programs to install and choose from. A lot more it seems to me. Stuff like Xara (graphics package) and Wormux (Worms game) which weren't there when i tried installing under dapper. So I think the 64bit support has increased a little but has a long way to go...

---

### Post by Pawel Stolowski on 2006-10-27
Thanks for all answers. I still haven't choosen what version to install ](*,) . One more thing - do 64-bit Edgy repositories contain the same software as 32-bit repos (e.g. do I still have over 16.000 packages available in 64-bit repos)?

---

### Post by rplantz on 2006-10-27
> **Kilz said:**
> 32bit firefox, and I am talking about the 2.0 reciently released is avilable from my howto (works with edgy), link in my signature.


I once installed 32-bit firefox under dapper and yelp went away. Would this happen again? I see from your howto that I can leave 64-bit firefox installed. Perhaps this is a good compromise: can still use yelp and live with email, etc. launching 64-bit.

> 
They say it wont help that many people. I tend to find that strange as nearly every processor sold today is a 64bit chip.

The good news is that the x86-64 architecture also runs x86-32 code. The bad news is that developers don't have to support x86-64. Well, I guess if you're a developer, that could also be good news.

---

### Post by The Warlock on 2006-10-27
> **Pawel Stolowski said:**
> Thanks for all answers. I still haven't choosen what version to install ](*,) . One more thing - do 64-bit Edgy repositories contain the same software as 32-bit repos (e.g. do I still have over 16.000 packages available in 64-bit repos)?

Yes. There are maybe five or ten packages that don't compile properly to x86_64, the rest are there.

---

### Post by Pawel Stolowski on 2006-10-27
Thanks again for sharing your experience. I decided once again to go 32bit route (just installed it, looks very nice, no problems at all, even my Planet wireless nic works fine as it worked before in Dapper). Although I consider myself as experienced user (I've been using Linux for ~8 years), I prefer simpler solutions and all the benefits of synaptic (that's why I stopped using Slackware a few years ago ;)). I hope multiarch will be supported in Edgy+1 or Edgy+2... In the meantime, I'll maybe give the 64-bit release a try in QEMU to see how much tweaking it needs. What I need now is firefox, flash, wine, acrobat, realplayer etc. from apt-get repos to benefit from automatic updates.

---

### Post by pony-tail on 2006-10-27
Edgy is not without it's issues !
xorg 7.1 does not play nice with "fglrx" radeon drivers (this has been a Major issue for me )
I am not sure if the issue is with "fglrx" or xorg 7.1 there have been bug reports filed for the various issues for a couple of weeks (before 6.10 was put on the mirrors) but although there are work arounds none fixes all the issues and mostly they cause something else to break .
I had to keep my Dapper instal because of this and at present dual boot with Edgy (6.10 final)

---

### Post by rplantz on 2006-10-28
> **pony-tail said:**
> Edgy is not without it's issues !

I had to keep my Dapper instal because of this and at present dual boot with Edgy (6.10 final)

I'm thinking of reinstalling Dapper in dual boot. I have a separate partition for home. Can simply cross-mount this partition so that both Edgy and Dapper use the same home?

---

### Post by pony-tail on 2006-10-28
It is not a good idea to share the home partitions between to distros that are that different - a lot of settings and the like stored there have very different values - You may get away with it but it could break something .
I have mine on a completely separate drive but that is most likely overkill !
All I can say is that in "edgy" Radeon (fglrx) + xorg7.1 = Disaster in either 32bit or 64bit :(

---

### Post by rplantz on 2006-10-28
> **pony-tail said:**
> It is not a good idea to share the home partitions between to distros that are that different - a lot of settings and the like stored there have very different values - You may get away with it but it could break something .

Thanks for your words of wisdom. It was late last night, and I did not think about the settings files. (I confess to doing dumber things.)

My Edgy works quite well, except for compiling 32-bit C code. They lost some header files (at least) from Dapper to Edgy. I don't do a lot of that, and the programs are very simple. I may install Dapper on another partition or my other disk, then hand mount and copy files as needed. Hopefully, there will be an upgrade that fixes the problem.

---

### Post by FewClues on 2006-10-29
> **Kilz said:**
> If you are interested in reading exactly what was said you can find [the whole thing here]("http://archives.free.net.ph/thread/20060923.055234.87fea1fd.en.html#20060923.055234.87fea1fd"). I also agree that it is a chance for Linux to expand on the great 64bit support that isn't available in Windows **yet**. IMHO they are letting an opportunity pass them by. Other distro's like SuSE are already multiarch. I want to see what 10.2 looks like in Dec. I also think when Vista is released 64bit Windows use will start to climb. It may be preinstalled on 64bit machines.

I too agree with you both. However 64bit users are now battling the same inertia that has hampered Linux from the start: the vast number of 32bit Windows computers already deployed.  A software developer is going to address the largest market segment first.  The free thinkers who have bleeding edge systems are also going to have to adjust to the gravity of that inertia.

---

### Post by RAOF on 2006-10-29
> **FewClues said:**
> I too agree with you both. However 64bit users are now battling the same inertia that has hampered Linux from the start: the vast number of 32bit Windows computers already deployed.  A software developer is going to address the largest market segment first.  The free thinkers who have bleeding edge systems are also going to have to adjust to the gravity of that inertia.

Only poorly written code doesn't work on x86-64.  Well written code doesn't care what size an **int** is, or where it does it uses the C types **guaranteed** to be the right size (eg int32_t).

I can very much see where the developers are coming from: Multi-arch is almost exclusively to make using proprietry software easier.  Since they don't consider that a priority, they don't see the point in expending the (enormous) effort required to do a sensible, multi-arch dpkg/apt.

---

### Post by rockets on 2006-10-29
Except, that you forget that some developers (like me) do cross-compile to other architectures. In my case, I run 64 bits, compile for 32 and release.

Now, can someone tell me whiche header files were lost on Edgy ?

---

### Post by rockets on 2006-10-29
Care to mention the lost header files ?

---

