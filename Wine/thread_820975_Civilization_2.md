---
title: "Civilization 2"
date: 2008-06-06
forum: Wine
---

### Post by Raistlin82 on 2008-06-06
Hi all, not sure if this has been posted before, if it has I apologize!  Is there any way to play Civ 2 in Ubuntu hardy.  When i try to run the exe with wine nothing happens :confused:

---

### Post by conscious on 2008-06-07
Do you know about freeciv? It's pretty similar and can be installed from the repositiries.

Civilization II seems to work pretty bad on Wine:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=444](http://appdb.winehq.org/objectManager.php?sClass=application&iId=444)

---

### Post by Raistlin82 on 2008-06-07
Hi there, yeah I tried freeciv, and it is decent, but there is just something about good ol civ 2 that I love! Yep I'm a bit of a sado :) cheers for the reply though!

---

### Post by randomsusers on 2008-08-03
> **Raistlin82 said:**
> Hi all, not sure if this has been posted before, if it has I apologize!  Is there any way to play Civ 2 in Ubuntu hardy.  When i try to run the exe with wine nothing happens :confused:

Like you, I'm a big CIV 2 fan. Civ 2 does not require registry entries to run, so I just copied my entire install directory to ~/.wine/drive_c/Civ2 and tried to run it there. 

(wine CIV2.EXE)

Startup screen comes up ok, but the game hangs from there. No sound. Looking in the terminal window I see:

wine: Unhandled page fault on read access to 0xffffffff at address 0x13c7:0x00001dfc (thread 0018 ) starting debugger
fixme:dbghelp:addr_to_linear Failed to linearize address 0013:0000f76e (mode 0)
...

I'm running Ubuntu 8.04.1, wine 1.0.0.

BOTTOM LINE: Broken and beyond my ability to fix. If anyone hears different, I'd sure like to know.

Regards,
Toad

---

### Post by crhylove on 2008-08-03
I too, am a HUGE fan of the original Civ 2.  Civ 3 was a huge disappointment, and one of the worst games I ever spent money on.  In fact, I try most games from a torrent before purchase now as a direct result of how horrible Civ 3 was.  Civ 4 is better, and certainly LOOKS good, but is about 10% as fun as Civ 2.

So, like you, I have tried in vain and often to get Civ 2 running in Wine.  It will not.  There is actually a bug actively being worked on in Wine that is preventing game play, and apparently a user recently even had success loading a saved game, which is a step in the right direction, as that was previously impossible.

The Good News is though, that with Virtualbox, you can install a TinyXP VM very easily, and run Civ 2 very comfortably in a VM, as it does not take a lot of resources given it's age (and I turn off the heralds because they are annoying).  You can even run in "Seamless Mode" which makes it look and act like a native app.

I play Civ 2 in exactly this way at least once a month.

______________________________


Now anybody who wants to be a cry baby should stop reading.  I understand that the devs making freeciv have labored long and hard on a work that they do primarily for passion.  I also understand that it has incrementally improved over the years due to their tireless efforts.  I also understand the inherent value of FOSS, and that I could "fix it myself" if I wanted to or (more to the point) if I knew how.

All that being said, seriously this will start a flame war, Freeciv sucks.  It's about 5% of the Civ 2 experience.  The gameplay is less fun.  The keyboard shortcuts are worse, less intuitive, harder to remember, use, and not easy enough to modify.  The graphics are on par with Civ 2, but that's actually a catastrophe as Civ 2 came out over a decade ago, and this is 2008, people.  Freeciv is really, really, not even remotely good enough, especially for Civ 2 fans of which there are millions.

For instance, I grew up with my brother.  We are close.  We play music together still, talk on the phone, share computer tips and often Skype and are just basically pretty close and know what we are both into and doing.  I found out just recently that he has been a Civ 2 fan pretty much as long as I have.  He's much younger than me, too (I got into it a little late, I suppose).  Civ 2 was the monumental success it was because it is just really, really, unabashedly a great game, with great gameplay and ease of use.

There is another FOSS project that attempts to duplicate Civ 2, and does a much better job, but it is Windows only.  It did at one point run well under Wine, too, and it's called "C-evo".  Let me just state clearly taht C-Evo isn't even 25% as fun as Civ 2.  Which still makes it about 3 times more fun than freeciv.

I've often mused on hiring a developer to fork freeciv and make it a better civ 2 clone.  As a starving artist though (sometimes literally), I don't feel that finding funds to allocate for that project would really be worth my while at this time.

Try the VM though, Civ 2 works GREAT in virtualbox on tinyxp sp3.  I don't miss native Windows at all!

---

### Post by randomsusers on 2008-08-03
> **crhylove said:**
> I too, am a HUGE fan of the original Civ 2.  Civ 3 was a huge disappointment, and one of the worst games I ever spent money on.  In fact, I try most games from a torrent before purchase now as a direct result of how horrible Civ 3 was.  Civ 4 is better, and certainly LOOKS good, but is about 10% as fun as Civ 2.

I agree with you on CIV 3. It was SOOOOO bad, I never even considered buying Civ 4. Not the worst game I ever bought, but certainly one I never expect to play again. 

I've been hammering away at this all afternoon. I think I might have finally had a breakthrough. First, the stats:

I'm running ubuntu 8.04.1, 64-bit version, wine 1.0.0
I copied the entire CIV2 directory from my PeeCee to a thumbdrive and copied it straight into drive_c under .wine. I also copied the WING.DLL file into the CIV2 directory, not that I'm sure if this made a difference or not.

I went into the Applications -> Wine -> Configure Wine and set the Windows version to Win95, selected Emulate Virtual Desktop, and set the desktop to 1024 x 768. Then I double-clicked on CIV2.EXE. Hot DAMN, it started working!

I was able to start a game, I saved the game, I ran a few turns, I saved again, and I loaded up a saved game that I had played on the PeeCee. NO PROBLEMS, except that the sound doesn't work.

Continuing to fiddle, the Zoom functions execute very slowly, but I haven't seen any other problems.

> **crhylove said:**
> The Good News is though, that with Virtualbox, you can install a TinyXP VM very easily, and run Civ 2 very comfortably in a VM, as it does not take a lot of resources given it's age (and I turn off the heralds because they are annoying).

I've never heard of Virtualbox or TinyXP. If they are free, please drop some info. (I'm so cheap, I squeeze every quarter until the eagle craps in my hand.) I've only been using ubuntu for a few days and civ2 is the first Windoze game I got running, so I'm still a newbie.

Regards,
Toad

---

### Post by Raistlin82 on 2008-08-03
TinyXP VM sounds like something i will have to look into, anyone got a link?  Civ 2 was and still is awesome, Civ 4 is great but 2 still wins it for me!:)

---

### Post by Stargazer989 on 2008-08-22
> **Toadbrooks said:**
> I agree with you on CIV 3. It was SOOOOO bad, I never even considered buying Civ 4. Not the worst game I ever bought, but certainly one I never expect to play again. 

I've been hammering away at this all afternoon. I think I might have finally had a breakthrough. First, the stats:

I'm running ubuntu 8.04.1, 64-bit version, wine 1.0.0
I copied the entire CIV2 directory from my PeeCee to a thumbdrive and copied it straight into drive_c under .wine. I also copied the WING.DLL file into the CIV2 directory, not that I'm sure if this made a difference or not.

I went into the Applications -> Wine -> Configure Wine and set the Windows version to Win95, selected Emulate Virtual Desktop, and set the desktop to 1024 x 768. Then I double-clicked on CIV2.EXE. Hot DAMN, it started working!

I was able to start a game, I saved the game, I ran a few turns, I saved again, and I loaded up a saved game that I had played on the PeeCee. NO PROBLEMS, except that the sound doesn't work.

Continuing to fiddle, the Zoom functions execute very slowly, but I haven't seen any other problems.



I've never heard of Virtualbox or TinyXP. If they are free, please drop some info. (I'm so cheap, I squeeze every quarter until the eagle craps in my hand.) I've only been using ubuntu for a few days and civ2 is the first Windoze game I got running, so I'm still a newbie.

Regards,
Toad

if you could hand me a few instructions on how to do this, i'd appreciate it. i don't care about sound, i sometimes prefer it WITHOUT (Starcraft was good without sound. "your warriors have engagded the enemy" was suicidally annoying.)

---

### Post by randomsusers on 2008-08-22
> **Stargazer989 said:**
> if you could hand me a few instructions on how to do this, i'd appreciate it. i don't care about sound, i sometimes prefer it WITHOUT (Starcraft was good without sound. "your warriors have engagded the enemy" was suicidally annoying.)

What I wrote above is all there is to it. I LITERALLY copied my entire CIV2 installation directory and all subdirectories from my PeeCee to a flashdrive. Then I created the directory ~/.wine/drive_c/CIV2 and put the whole mess in there along with the WING.DLL file. Then I used the Wine console to execute the program, as in: 

Applications -> Accessories -> Terminal
cd .wine/drive_c/CIV2
wine CIV2.EXE

Other than slow zoom and lack of sound, I've had no troubles.

Good luck,
Toad

---

### Post by Lessss on 2009-11-13
This worked for me. I think it's the dll

---

### Post by emailadress on 2009-12-02
@ crhylove: I couldn't agree more. I have really been giving freeciv an honest try these last weeks because I know that games with bad graphics need time to get used to and appreciate the gameplay in itself. It has failed miserably. It is incredible how much this game sucks. Units which are almost dead defend even with healthy ones who could win the battle present in the city, the interface is ridiculously uncomfortable, the "improvements" (eg techtree) incomplete (can't click on symbols to set research focus eg), the AI much to agressive, the whole game seems to revolve around one standard concept (monarchy-trade-republic), and all in all it completely misses this "easy to do-you automatically get the hang of it"-civII experience. I have no idea about software development but if the community is able to create a whole (awesome) OS, how hard can it be to copy a game which is 13 years old? Because thats what most people want as far as I can read in forums. A copy that runs well, not some freaky hybrid trying to "improve" on the best game ever produced, completely ******* it up the process... What a pity!

---

### Post by Noob64 on 2010-02-24
I don't care what any  of you say. Civ3 was the best civilization  game I ever played. Don't get me wrong, I like civ2,but it had way less strategic value  then civ3 Period.

civ3 had real artillery units compared to civ4,civ2. To a degree civ3 better then civ4. with enough support 

units you could defeat  more high tech nations. In civ4, I had to us my  artillery like regular units. Often times loosing them. Thats  bad design if you ask me. In civ4 managing you 

economy was way harder then in civ3.

civ2 is just plane to easy because, if I out numbered you for the most part, I will win period. But I do miss using spies like terrorist in that game,  and thats all i miss from civ2.

  plus governments in civ3 are  way better implemented in civ3 then civ2. and way more realistic then civ4 to a degree.

The only thing I really like about civ4 is the fact  that I can choose a religion.

---

### Post by Wockerman on 2010-09-26
I have managed to get Civ2 working with miminal effort under Ubuntu 10.04 LTS.

Steps:

1)  Create an ISO image of the CDROM.
2)  Create a directory  /home/username/wine/dosdevices/W:
3)  Mounted the CD image using gmount-iso to /home/username/.wine/dosdevices/W:
4)  Install game from here
5)  Run using wine from /home/username/.wine/c_drive/MPS/Civ2.exe

I presume the later changes to Wine have fixed the bugs but this works well.  Funnily enough the bug with Windows versions when running multiple displays affects ubuntu too - with two screens you can have the interface on one screen and dialogue boxes pop up on both screens - some on the correct screen, some on the wrong screen.

---

### Post by skoberlink on 2010-11-15
Hey sorry to bring this out of the grave but I just recently started playing Civ 2 again. On 10.10 and the latest wine, I'm actually having no problems except for 1.

My problem is I can't listen to the music or view the videos when using an ISO. It just says there is no disk which is required for these parts. Any suggestions or am I just left without those? I mean obviously it's very playable without the music or vids I just like the whole experience.

---

### Post by Dead Angel on 2011-08-19
Okay, so my mum purchased a Win 7 64 bit machine recently. I fubared it, but had it running for six months (enough to get a decent Steam libary of my own).

I downloaded Civ II as soon as I got the PC because I knew of few games I'd like and the Civ V demo failed hard on my machine.

So here is where I got the link to a patcher to get around the text box problem that is known in Wine: [http://forums.civfanatics.com/showthread.php?t=193215](http://forums.civfanatics.com/showthread.php?t=193215)

Here is where I got CivII: [http://www.bestoldgames.net/eng/download.php](http://www.bestoldgames.net/eng/download.php)

It works in wine, give it a run and force it close before you complain, yes the first time (when you patch it) it hangs, that's 'normal' afact. After this, it will run normally.




I'm running 10.04 LTS. That's all I know.

At any rate, have fun trying to get this to work. I'm too busy playing.

(There is a torrent for the windows version of SMAX I'll try next. I'll report back if I can get it to work.)

---

### Post by Dead Angel on 2011-08-19
Spoke too soon. Granted GNOME became a buggy piece of **** every version released until 10.10 when it was kille.. but the animations for units are SO SLOW....

Here's sto hoping it's a GNOME problem and those who no longer use GNOME do not suffer the same problem.

---

### Post by _____ on 2011-10-12
I get an winevdm.exe error when I try to get this running on 11.04....anyone have any info?

---

### Post by ergo-proxy on 2011-10-12
> **_____ said:**
> I get an winevdm.exe error when I try to get this running on 11.04....anyone have any info?
 
Try with the lastest (beta) wine version and if doesn't work try with the stable version.

---

