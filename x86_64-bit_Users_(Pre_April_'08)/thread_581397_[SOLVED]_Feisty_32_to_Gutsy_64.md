---
title: "[SOLVED] Feisty 32 to Gutsy 64"
date: 2007-10-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Inxsible on 2007-10-19
I am thinking of installing Gutsy 64 bit. Now I know I cant upgrade from 32 bit to 64 bit, but since 64-bits have come a long way, I think I should use it since my machine supports it.

Of course the only way to go about it would be to install it in a different partition. How do I go about it ?

1) Will I have to create a separate home drive for it or can I use the same as that of Feisty 32bit?
2) What problems, apart from the Flash, will I have in 64-bit?
3) I currently dual-boot with Feisty and Vista. Will triple boot of Feisty-32, Vista and Gutsy-64 be easy enough?
4) Any other info that you think might be helpful

---

### Post by ubuntu dave on 2007-10-19
1) You should be able to use the same /home partition.
2) There might be a few but it's unlikely. Flash shouldn't be one.
3) Should be easy enough - more OSs = more potential for complications, though.
4) 64bit really is similar to 32bit. Personally I found the idea of 64bit being a bit 'behind' 32bit or 'incompatible' in some areas (flash etc) to be incorrect these days.

---

### Post by John.Michael.Kane on 2007-10-19
> **Inxsible said:**
> I am thinking of installing Gutsy 64 bit. Now I know I cant upgrade from 32 bit to 64 bit, but since 64-bits have come a long way, I think I should use it since my machine supports it.

Of course the only way to go about it would be to install it in a different partition. How do I go about it ?
That is not the only way,however. it's one way to go if you are looking to test the 64bit waters first.

> **Inxsible said:**
> 1) Will I have to create a separate home drive for it or can I use the same as that of Feisty 32bit?
If you are planning on running dual 32bit, and 64bit then yes you should make new partitions,however. According to some members you can upgrade from 32bit to 64bit Ubuntu while keeping your one home folder.

I have not test this method fully, and can't vouch for it so will have to wait for those who have done so to chime in on that method.

> **Inxsible said:**
> 2) What problems, apart from the Flash, will I have in 64-bit?
Flash should no longer be an issue while using 64bit, As Gutsy 7.10 now allows for the installation of flash through synaptic, and feisty 64bit has a script written that install flash.

> **Inxsible said:**
> 3) I currently dual-boot with Feisty and Vista. Will triple boot of Feisty-32, Vista and Gutsy-64 be easy enough?
I'm not sure on this. For the most part it should be a simple matter of allocating space for it, and installing the next OS you want to use.

> **Inxsible said:**
> 4) Any other info that you think might be helpful
You may want to have a look over the thread below.
[Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")

hope this helps.

---

### Post by Octagonal on 2007-10-19
Just wanted to post my experience as I moved from Feisty 32-bit to Gutsy 64 bit and then to Gutsy 32 bit.

w/ 64 bit Gutsy the problems I encountered were:
1. No splash screen on boot up (works fine w/ 32bit)
2. Gdesklets for 64 bit in the repository doesn't work (had to download a diff. deb)
3. adesklets didn't work either from the repository (there's probably a fix I didn't take the time to resolve it).
4. HD WMV movies don't work w/ sound-- that is the w32codecs equivalent for 64 bit gutsy (w64codecs) don't seem to work for me...  if you're running a Gutsy 64bit and can view either of the two high quality movies from this site: [http://www.halowars.com/trailer.html](http://www.halowars.com/trailer.html)
then I would love to know about it.  These play just fine in 32bit Gutsy.

---

### Post by holomorph on 2007-10-21
they play ok for me w/ 64 bit gutsy - don't know what's different but it seems you have hope; at least it's possible ;)

---

### Post by steveneddy on 2007-10-22
64 bit is the way to go if you ask me.

Everything works very well on my Core 2 Duo machine, even the upgrade from Feisty 64 bit to Gutsy 64 bit went flawlessly.

:popcorn:

---

### Post by Inxsible on 2007-10-22
Seems like things shouldn't be too difficult. 

SD-Plissken, I intend to keep Feisty 32 only because I do not want to be without Ubuntu, in case Gutsy-64 does give me problems. After a couple of weeks, once I have the G-64 to be the way I like it, I would probably remove F-32.

1 last thing. My parents run F-32 too. They use the computer for basic things like surfing, email, messengers, printing etc. The machine is pretty decent too with Intel Core 2 Duo, since I bought them a new one recently. Should I upgrade them to G-64 too?

Remember that they would NOT want any "additional" hassles to install things and such and they would also probably want everything to work ( meaning whatever should and would work on Windows ).

I am probably gonna go with G-64 on my machine. I think, I would love the challenge of getting everything working on a 64bit OS. :) Could you please advise me if I should for my folks too ?

---

### Post by John.Michael.Kane on 2007-10-23
> **Inxsible said:**
> Seems like things shouldn't be too difficult. 
No things shouldn't be too difficult,however. be prepared for issues anyway. This would include backing up valuable files etc.

> **Inxsible said:**
> SD-Plissken, I intend to keep Feisty 32 only because I do not want to be without Ubuntu, in case Gutsy-64 does give me problems. After a couple of weeks, once I have the G-64 to be the way I like it, I would probably remove F-32.
That is perfectly understandable. Most 64bit user in this section advise keeping a separate install while getting use to 64bit, and making sure it does what you need, and also just in case the install goes south. 

> **Inxsible said:**
> 1 last thing. My parents run F-32 too. They use the computer for basic things like surfing, email, messengers, printing etc. The machine is pretty decent too with Intel Core 2 Duo, since I bought them a new one recently. Should I upgrade them to G-64 too?
The old saying if it is not broke don't fix it comes to mind. This said.

As long as the hardware is not known to be problematic under Linux you should be fine installing it for them.

> **Inxsible said:**
> Remember that they would NOT want any "additional" hassles to install things and such and they would also probably want everything to work ( meaning whatever should and would work on Windows ).

They should be fine using 64bit even for only surfing, email, Instant messaging, printing,. They would also be covered for multimedia codecs, and flash if they need those.

The only odd program I can see that might be an issue would be skype as that uses a guide, and they may not want to go that route even if it's simple.

> **Inxsible said:**
> I am probably gonna go with G-64 on my machine. I think, I would love the challenge of getting everything working on a 64bit OS. :) Could you please advise me if I should for my folks too ?
IMHO you should only switch them if they wanted too. 

Also you would have to make sure all the programs they use can be had through synaptic, and without any hassle to them, Which might preclude the use of any external repos or guides etc. As what would not be a hassle to you or any of us eg using third party repos, and guides might very well be a pain in the rear to them.

Hope this helps.

---

