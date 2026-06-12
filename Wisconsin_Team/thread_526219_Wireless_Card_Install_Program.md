---
title: "Wireless Card Install Program"
date: 2007-08-15
forum: Wisconsin Team
---

### Post by Ayuthia on 2007-08-15
As I mentioned in the Location thread, I am working on writing a script that will try to install wireless cards for Ubuntu.  The scripting is not too big of a problem, but the part that I have concerns with is with the downloading of the drivers.

Am I breaking any laws by supplying the drivers or if I use a wget to download the drivers for the user?  Is there a way to avoid this issue?

---

### Post by Ek0nomik on 2007-08-15
> **Ayuthia said:**
> As I mentioned in the Location thread, I am working on writing a script that will try to install wireless cards for Ubuntu.  The scripting is not too big of a problem, but the part that I have concerns with is with the downloading of the drivers.

Am I breaking any laws by supplying the drivers or if I use a wget to download the drivers for the user?  Is there a way to avoid this issue?

Assuming you are downloading Windows drivers for some network cards (my Dell 1500 Draft N' needed Windows drivers as an example) then I *think* you are violating a law in the United States, and probably a few other Western countries in Europe.  Don't hold me to this though, as I may be mistaken.

The reason why I am unsure is because I think this dispute is happening as we speak.  For an example, Ubuntu will now install video card drivers for you after a click of the button (Restricted Drivers Manager).  The drivers it installs aren't legal ones, at least to my knowledge.  It has installed propriety drivers onto all four of my boxes.

I do know that installing the Windows drivers via ndiswrapper isn't illegal as far as Linux "laws" are concerned.  There was a small push to make binaries illegal to install in Linux.  From an open source standpoint, if I am not mistaken, installing the binary drivers for wireless cards isn't legal.

You don't actually plan on supplying the wireless drivers though do you?  If it was in the package, it would inevitably make the release quite large.  If you hosted them on a website of yours, that would inevitably make bandwidth costs quite high.  Do you just plan to download them from the Dell or HP website (and other vendors)?

I don't know much programming, a little Visual Basic and PHP, but if you want help testing I have a laptop I can use to test with.  I'll have to do a little partitioning and install a second copy of Ubuntu though, in case your script ends my wireless life.  :)

---

### Post by Ayuthia on 2007-08-15
I originally was planning on downloading the drivers from the site because packaging them or hosting them would be too expensive.  If there are too many legal issues, I will not release it to the group.  I will have to look into that further.

I think I will continue on my adventure with getting a couple of cards working.  If you send me the pci id of your wireless card, I will get yours added you the script for testing.

---

### Post by Ek0nomik on 2007-08-15
> **Ayuthia said:**
> I originally was planning on downloading the drivers from the site because packaging them or hosting them would be too expensive.  If there are too many legal issues, I will not release it to the group.  I will have to look into that further.

I think I will continue on my adventure with getting a couple of cards working.  If you send me the pci id of your wireless card, I will get yours added you the script for testing.

So if you don't plan on releasing it why are you working on it?

It sounds like it could be a really good idea seeing as how it seems as though the Ubuntu developers aren't really supporting the wireless users all that much.  A lot of wireless cards don't work out of the box.

---

### Post by Ayuthia on 2007-08-15
Now that I have a family, I can't quite afford getting into any legal issues.  I am sure that there will be some way that I can get it out there so I am not giving up on it.  I just need to find the right way of doing it.

---

### Post by Ek0nomik on 2007-08-15
> **Ayuthia said:**
> Now that I have a family, I can't quite afford getting into any legal issues.  I am sure that there will be some way that I can get it out there so I am not giving up on it.  I just need to find the right way of doing it.

I'd suggest you create your original topic in the Community Discussion section.  This way you will get a lot of fresh faces throwing ideas on the topic rather than just mine.  :)

Rather than having the script automatically download the binary drivers, you could create a simple switch statement that follows something like:

```
If wirelessCard = ModelXXYYZZ
   echo "Please visit http://xxx.yyy.zzz"
```

This way you aren't actually providing the driver, you are simply saying where they can get it.

---

### Post by Ayuthia on 2007-08-15
It is going to head over there soon.  I wanted to start with the Wisconsin Team first to get some ideas and then work with the bigger crowd.

Your suggestion of having to go to the site might be where it ends up if I can't find a legal solution.  Then if someone wants to take my source and update it, they may do so.  It would not be too difficult to change that part.

---

### Post by EXCiD3 on 2007-08-15
Wouldn't it be a program kind of like ENVY? Wouldn't the legality of it be close to using ENVY to install your graphics drivers?

---

### Post by Ek0nomik on 2007-08-15
> **Ayuthia said:**
> It is going to head over there soon.  I wanted to start with the Wisconsin Team first to get some ideas and then work with the bigger crowd.

Your suggestion of having to go to the site might be where it ends up if I can't find a legal solution.  Then if someone wants to take my source and update it, they may do so.  It would not be too difficult to change that part.

Understandable.  I just wanted to suggest the broader community it all.  :)

By the way, here is my lspci output:

```
0b:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)
```

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

This was the HOWTO that got my wireless working in Edgy and Feisty.

If you want more information feel free to ask.

---

### Post by Ayuthia on 2007-08-15
> **EXCiD3 said:**
> Wouldn't it be a program kind of like ENVY? Wouldn't the legality of it be close to using ENVY to install your graphics drivers?

I actually have not looked at ENVY as of yet.  I would assume that they would be the same.  I'll go check it out.

By the way, great work on the dv9000 threads!

---

### Post by Ayuthia on 2007-08-15
> **Ek0nomik said:**
> Understandable.  I just wanted to suggest the broader community it all.  :)

By the way, here is my lspci output:

```
0b:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)
```

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

This was the HOWTO that got my wireless working in Edgy and Feisty.

If you want more information feel free to ask.

Can you post the lspci -nn for it?  I am looking for the pci id and the rev for the card.  With the n-draft cards out, there have been some new install issues associated with it.

---

### Post by EXCiD3 on 2007-08-15
> **Ayuthia said:**
> I actually have not looked at ENVY as of yet.  I would assume that they would be the same.  I'll go check it out.

By the way, great work on the dv9000 threads!

It was just a thought, but ENVY downloads the Nvidia Linux driver from nvidia's website and then compiles it for you. It is along the same lines as your program would be, I just thought you might like to check it out first. 

Oh and thanks for the compliment on the threads. I feel sorry for everyone with Broadcom wireless cards, since they take so much work to get going and mine works out of the box (intel 3945). If you do make this program please let me know. If add support for the Broadcom 43xx cards that would be incredible, I'll add it to my Howto asap. ;)

---

### Post by Ayuthia on 2007-08-15
I just downloaded the source for ENVY and I am going to talk to tseliot about how he deals with it.

Have you checked out gutsy yet?  I have a dv6338se and found that the USB ports no longer work in gutsy but worked in feisty.  It is because of the IRQ 7 issue and noapic.  I am currently testing out noapic noirqdebug on it to see if it is stable and it appears to be working well so far.

---

### Post by Ek0nomik on 2007-08-15
```
0b:00.0 Network controller [0280]: Broadcom Corporation Unknown device [14e4:4328] (rev 01)
```

I was going to mention that it was very close to Envy.  However, I don't think Envy is legal either if it is automatically fetching binary drivers and compiling them for you.  The legality of some issues is irrelevant to some people.  I must say I am guilty quite often.

---

### Post by EXCiD3 on 2007-08-15
> **Ayuthia said:**
> I just downloaded the source for ENVY and I am going to talk to tseliot about how he deals with it.

Have you checked out gutsy yet?  I have a dv6338se and found that the USB ports no longer work in gutsy but worked in feisty.  It is because of the IRQ 7 issue and noapic.  I am currently testing out noapic noirqdebug on it to see if it is stable and it appears to be working well so far.

Lemme know how it pans out for you, i have yet to try out Gutsy, (downloading atm ;)).

---

### Post by rowanrook on 2007-08-25
> **Ayuthia said:**
> As I mentioned in the Location thread, I am working on writing a script that will try to install wireless cards for Ubuntu.  The scripting is not too big of a problem, but the part that I have concerns with is with the downloading of the drivers.

Am I breaking any laws by supplying the drivers or if I use a wget to download the drivers for the user?  Is there a way to avoid this issue?
Hmmm... props to you for tackling the challenge. Certainly, lack of proper driver support would be a deal-breaker for most people (non-techies) interested in an alternative to Windows. I know my Targus Bluetooth Mouse doesn't seem to work in Feisty. And that sucks, a lot. What if your program prompts the user to choose to download the proper drivers, would that relieve you of liability? It is difficult to believe that either the device manufacturer or the open source community would want to punish anyone for writing code to ENABLE THEIR PRODUCTS TO FUNCTION PROPERLY!!! But I have seen some pretty stupid litigation before...

---

### Post by EXCiD3 on 2007-08-25
> **rowanrook said:**
> Hmmm... props to you for tackling the challenge. Certainly, lack of proper driver support would be a deal-breaker for most people (non-techies) interested in an alternative to Windows. I know my Targus Bluetooth Mouse doesn't seem to work in Feisty. And that sucks, a lot. What if your program prompts the user to choose to download the proper drivers, would that relieve you of liability? It is difficult to believe that either the device manufacturer or the open source community would want to punish anyone for writing code to ENABLE THEIR PRODUCTS TO FUNCTION PROPERLY!!! But I have seen some pretty stupid litigation before...

I agree. What if in your program, it asks for the Windows driver .exe, it then proceeds to extract it and install it. Have the user supply the drivers, your program can just do the rest.

---

### Post by Ayuthia on 2007-08-25
> **EXCiD3 said:**
> I agree. What if in your program, it asks for the Windows driver .exe, it then proceeds to extract it and install it. Have the user supply the drivers, your program can just do the rest.
That is most likely going to be my fall back plan because if I can't download it automatically, then I want to make sure that they have an easy way to get the drivers.

---

### Post by EXCiD3 on 2007-08-25
I guess the other thing of doing it that way would allow for easy use of different drivers. The only problem being if the drivers require unique setups.

---

### Post by Ek0nomik on 2007-08-25
> **EXCiD3 said:**
> I agree. What if in your program, it asks for the Windows driver .exe, it then proceeds to extract it and install it. Have the user supply the drivers, your program can just do the rest.

I *believe*, although I am not certain, that this would actually still be illegal in the United States.  My reason for saying so is I know the Supreme Court ruled that P2P software creators are **not** free of guilt for creating the software which *can* (although much more frequently not) be used for legal purposes.  (9-0 Decision | MGM v. Grokster)

I think we are all aware there is a slight difference in operation here, but if *Ayuthia* is actually concerned of U.S. law then I think he is probably on the short end of the stick.  Again, that's just my conclusion though.

That being said, I think this fine line in law is something Ubuntu developers, and many others are taking advantage of.  They offer the binary drivers after a fresh install of Ubuntu.  So you may be fine until Linux developers actually start taking heat for some of their actions.

If you didn't plan on hosting your software in the repository, you could always move overseas.  Perhaps where the Pirates in the Bay live?  :)

---

### Post by EXCiD3 on 2007-08-25
> **Ek0nomik said:**
> If you didn't plan on hosting your software in the repository, you could always move overseas.  Perhaps where the Pirates in the Bay live?  :)

Hahah, I would have loved it if they would have purhcased that country... Remember that? [http://arstechnica.com/news.ars/post/20070115-8618.html](http://arstechnica.com/news.ars/post/20070115-8618.html)

Thats forunately not a problem at the moment, but unfortunately inthe near future it most likely will be. What exactly is the reason this would be illegal in the US? I dont see that you are passing off this program as your own...Is there any possiblity of contacting Broadcom, or whomever and seeing if you could get permission to do this if it is deemed illegal? I really doubt that they would even reply, but its worht a shot as Linux is gaining market share... I'm not really up to par with the laws, etc, just some random ideas i had floatin around... ;)

---

### Post by Ek0nomik on 2007-08-26
> **EXCiD3 said:**
> Hahah, I would have loved it if they would have purhcased that country... Remember that? [http://arstechnica.com/news.ars/post/20070115-8618.html](http://arstechnica.com/news.ars/post/20070115-8618.html)

Thats forunately not a problem at the moment, but unfortunately inthe near future it most likely will be. What exactly is the reason this would be illegal in the US? I dont see that you are passing off this program as your own...Is there any possiblity of contacting Broadcom, or whomever and seeing if you could get permission to do this if it is deemed illegal? I really doubt that they would even reply, but its worht a shot as Linux is gaining market share... I'm not really up to par with the laws, etc, just some random ideas i had floatin around... ;)

Yeah I remember reading about that a few months ago.  I don't care what anyone says, I love TPB, even though I never use it.  I like them being a political icon for the online copyright battle.

The reason this would be illegal in the United States (again, this is only my judgment, but based upon the voting history of this countries legislative and judicial branch I feel rather confident in my assessments) is because his software would be aiding in the installation of binary drivers on an unintended operating system.

I suppose *Ayuthia* could just send a letter or e-mail to Broadcom and see what their response it.  It would definitely give a final answer to the situation, as their legal representatives would definitely be taking a side on this issue to cover their own companies trail.

---

### Post by EXCiD3 on 2007-08-26
> **Ek0nomik said:**
> I suppose *Ayuthia* could just send a letter or e-mail to Broadcom and see what their response it.  It would definitely give a final answer to the situation, as their legal representatives would definitely be taking a side on this issue to cover their own companies trail.

I just thought that this would clear up any questions on legality, and therefore he could begin deciding on whether or not this is worth making.

---

### Post by Ayuthia on 2007-08-26
From what I have been reading through the info that the driver's hosting websites, most seem like it might be ok.  I will need to ask them though.  Acer does not have legal info on their site, but HP does.  I forgot what Dell says.  I will also be asking Broadcom and the bcm43xx developers.  I did look at ENVY and they do get permission from Nvidia.

As for option two, I am pretty close to that "country" as we speak so maybe I should have a talk with Roy of Sealand and see if we can work something out.  Maybe I can install Ubuntu on his machine for him and he can give me his country...

---

### Post by EXCiD3 on 2007-08-26
Isnt it terrible that we might have to get things running in a different country in order to benefit a free operating system? Laws these days...This is terrible.

---

### Post by lifewithryan on 2007-08-28
> **Ek0nomik said:**
> ```
0b:00.0 Network controller [0280]: Broadcom Corporation Unknown device [14e4:4328] (rev 01)
```

I was going to mention that it was very close to Envy.  However, I don't think Envy is legal either if it is automatically fetching binary drivers and compiling them for you.  The legality of some issues is irrelevant to some people.  I must say I am guilty quite often.

I don't see anything wrong with the legality here...nVidia provides these drivers on their website... they are linux drivers, all ENVY is doing is retrieving them for you.  

What you may be thinking about is running a binary driver on ubuntu "taints" the kernel and the spirit of "open source" software since the binary driver is closed source.

---

### Post by Ayuthia on 2007-08-28
> **lifewithryan said:**
> I don't see anything wrong with the legality here...nVidia provides these drivers on their website... they are linux drivers, all ENVY is doing is retrieving them for you.  

What you may be thinking about is running a binary driver on ubuntu "taints" the kernel and the spirit of "open source" software since the binary driver is closed source.
What about the wireless network drivers?  Are they made for linux?  The other part is that if you go to the HP website to download the driver, you have to agree to the HP terms but if you go directly to ftp the driver, you miss it.

---

### Post by lifewithryan on 2007-09-04
> **Ayuthia said:**
> What about the wireless network drivers?  Are they made for linux?  The other part is that if you go to the HP website to download the driver, you have to agree to the HP terms but if you go directly to ftp the driver, you miss it.

Well I haven't read HPs terms of use, what exactly are you downloading from the ftp site?  is it source code that you have to compile?  Is it some sort of EXE file that we're ripping apart/reverse engineering?  Or is it a linux compatible binary driver?

If its source code, I guess it would depend on the license with which it is being released.  If its just a binary linux driver that your are extractin from a tar.gz file and copying some place, I don't see a legal issue there...though I am NOT a lawyer...

---

### Post by EXCiD3 on 2007-09-04
Its actually an executable windows driver which we are extracting the driver out of... so technically it may not be quite legal.

---

### Post by lifewithryan on 2007-09-05
> **EXCiD3 said:**
> Its actually an executable windows driver which we are extracting the driver out of... so technically it may not be quite legal.

Ahhh, I see now...plus you're sort of disrtibuting it then...that's a good question, perhaps a gray area...though I still maintain that if their terms of service don't say anything about it and since they offer it up on the web...you may be able to fight if you got "in trouble"  again, IANAL... :)

What process are you using to "extract" the driver?

---

### Post by Ek0nomik on 2007-09-05
> **lifewithryan said:**
> Ahhh, I see now...plus you're sort of disrtibuting it then...that's a good question, perhaps a gray area...though I still maintain that if their terms of service don't say anything about it and since they offer it up on the web...you may be able to fight if you got "in trouble"  again, IANAL... :)

What process are you using to "extract" the driver?

I presume he will be using ndiswrapper for the Windows Drivers, although I could be mistaken.

---

### Post by EXCiD3 on 2007-09-05
I'm not sure what else he would use other than ndiswrapper. We should definitely wait until the Gutsy release before anything happens because I read somewhere that Broadcom wireless cards would be supported in the Restricted Drivers Manager...can anyone confirm this?

---

### Post by Ayuthia on 2007-09-05
I am currently starting with ndiswrapper and bcm43xx-fwcutter although I would like to cover other options also.  From what I understand, ndiswrapper uses the Windows driver as is, but has the code to make the Windows driver work.  bcm43xx-fwcutter actually takes a portion of the firmware from the Windows driver but bcm43xx takes care of the rest.

I have seen Broadcom supported under Gutsy in the restricted drivers under Ubuntu but I am right now using Kubuntu and I have not seen the restricted drivers show up at all.

I know that my card (4311)is supported in the linux kernel (2.6.20.6 or greater) and I have gotten it to work but I recently ran into some interference issues where my wireless connection has to keep retransmit packets (my terminology might be off).  The antenna received stronger signals than ndiswrapper.

---

### Post by EXCiD3 on 2007-09-05
Hopefully the RDM will take care of all the problems and we wont need this script...Unfortunately then it takes your project away!

---

### Post by lifewithryan on 2007-09-05
> **Ek0nomik said:**
> I presume he will be using ndiswrapper for the Windows Drivers, although I could be mistaken.

Okay so your not "extracting" the driver in anyway, just wrapping with ndiswrapper...(sorry never messed with ndiswrapper before, my cards have always been supported with other, easier to deal with drivers).

In that case...I don't see a major legal issue with that...I could be wrong, but if really all you are doing is writing a script that goes and grabs the HP driver, I don't see how that can be a legal issue....again, IANAL and perhaps I should read the HOW-TO's for the Broadcom stuff just to familiarize myself with the process...

---

### Post by Ayuthia on 2007-09-05
> **EXCiD3 said:**
> Hopefully the RDM will take care of all the problems and we wont need this script...Unfortunately then it takes your project away!
According to the bcm43xx website, there are still some cards that are not stable as of yet (4309, 4318, 4319) so there will still be people that will want to use ndiswrapper.  Also, the n-draft cards are new so I don't think that they are ready yet either.

---

### Post by EXCiD3 on 2007-09-05
> **Ayuthia said:**
> According to the bcm43xx website, there are still some cards that are not stable as of yet (4309, 4318, 4319) so there will still be people that will want to use ndiswrapper.  Also, the n-draft cards are new so I don't think that they are ready yet either.

Yay! That's right, I forgot about the wireless N cards, those are starting to come on the new high-end laptops. I'm looking for some kind of open source project to start myself...Any ideas?

---

### Post by Ayuthia on 2007-09-05
> **EXCiD3 said:**
> Yay! That's right, I forgot about the wireless N cards, those are starting to come on the new high-end laptops. I'm looking for some kind of open source project to start myself...Any ideas?
You could always create an apt-on-windows.  That could be used for those who don't have the high-speed access at home or those who have already exceeded their bandwidth usage.  It would need to fit on a portable storage device so they can go to an internet cafe and download what they need and be able to sync it back to their computer.

---

### Post by EXCiD3 on 2007-09-05
Hmm, im not quite sure i understand, but it sounds like a pretty cool idea...PM me a little more info on that idea, I dont wanna get off topic on this thread.

---

### Post by EXCiD3 on 2007-09-06
:( [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

Did someone already beat us to it?

---

### Post by Ayuthia on 2007-09-07
> **EXCiD3 said:**
> :( [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

Did someone already beat us to it?
He does have working well for the Broadcom drivers.  I was thinking about trying to do other ones along with Broadcom.  I will still continue with my project just for practice and check with bmartin to see hor far he plans to go with his project.  No sense in releasing the same product.

Besides that, it will give me time to work on the next project. :)

---

### Post by EXCiD3 on 2007-09-07
> **Ayuthia said:**
> He does have working well for the Broadcom drivers.  I was thinking about trying to do other ones along with Broadcom.  I will still continue with my project just for practice and check with bmartin to see hor far he plans to go with his project.  No sense in releasing the same product.

Besides that, it will give me time to work on the next project. :)

Yeah, thats too bad that he's already done that. Unfortunately we couldnt have been like tseliot and gotten our program done ahead of time and gotten all popular. ;) Anyways, I'm sure his doesn't work for all the wireless cards, and a guy i tried helping used his program but it wouldnt work for him...if he actually did it right. Its pretty neat that there are all these people out there writing scripts and apps to make it easier for newcomers to use Ubuntu. This is one of the biggest reasons why I like Ubuntu the best, the community.

---

