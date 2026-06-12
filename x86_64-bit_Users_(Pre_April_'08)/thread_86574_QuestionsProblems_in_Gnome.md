---
title: "Questions/Problems in Gnome"
date: 2005-11-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by seatea on 2005-11-05
I have an older Mac, a PM G4 400mHz-576 MB RAM, I  installed Ubuntu  on looking  for an alternative to Mac OS X. I am still using Mac OS 9. I have been pleased with the  appearance of Gnome and what  it has  to offer. I have experienced a couple of problems though that I am not sure are due to my slower processor or something  intrinsic to Breezy Badger. Most programs  don't load  as quickly as my OS 9 versions. Firefox is not terrible in loading, but does  take a few seconds longer  than Internet  Explorer in the  Mac OS. Also, Firefox seems to be harder to get the cursor to move to the far left in search fields when trying to place it with the mouse. At first I thought I was not placing it correctly, a problem I have not had in OS 9 with IE, but after paying closer attention, I noticed  that there  is  less space on the far left to try to place the cursor compared to IE. This isn't realy a problem, but more  of an  annoyance. Evolution, compared to Outlook Express in the OS 9 environment, takes longer to load  although it is not anything extreme. It may be that it is just a larger program. The one program that  is really  bothersome is the  built in Help guide. It takes almost two minutes to load the  guide  and fully load the Gnome User Guide component. Has anyone  else experienced long  delays for that program to fully load? 

One problem or quirk I  have found  in  Ubuntu is  in the  GUI Find program. I was trying to get it to search  for a file that was hidden and even after selecting for it to search for hidden files, it  wouldn't show them. Has  anyone else tried to use this  option to find hidden files? I can show hidden files in Nautilus. Is this  a bug with the Find program or is there a problem with my installation of the Gnome environment? 

One of the  reasons I  have  not  tried  out  Mac OS X is because I  had thought  it would  run too slowly  on my  system. I  am wondering now  if  it  would  be just  as fast as Ubuntu. Has anyone used both and can offer a comparison?

---

### Post by jessecurry on 2005-11-06
Having used both OS X and Ubuntu on a beige G3(much slower than your system) I've found OS X to be faster. I would assume that OS X would also run better on your G4, but Ubuntu gives you access to some interesting software.
You actually should be able to install OS X, and then X11 for OS X if you wanted an X environment.

---

### Post by Rxke on 2005-11-06
that glacial help thingy is a known issue. To get better load times, you can consider prelinking. I did this, and while taking some time initially to get things prelinked, it works a treat. OSX does prelinking as standard, BTW.
There's a howto about prelinking in the howto section (grin, where else?)

---

### Post by farruinn on 2005-11-06
With your amount of RAM I think OS X would run quite well on your computer (in my experience RAM seems to be the biggest factor for OS X). I also think Ubuntu/Gnome would be faster though. It might be worthwhile to give OS X a try to see if it performs any better than Gnome, but I find Tiger to be more sluggish on my iBook (900 MHz, 256 MB RAM).

Rxke: I also installed the prelink package recently, but I haven't seen a considerable boost in performance. Is there any way to measure this?

---

### Post by seatea on 2005-11-07
Thanks for the comments.

I feel better, at least about my computer, that it is a known problem. Maybe there  wil be  a fix soon. I did look at the prelinking  thread, but decided against it. The potential for a "broken" computer was too disconcerting for me to try the prelinking. I am so new  at Linux that  I already wonder if I have broken something  on my setup from my use of the command line in troubleshooting some of the programs on my computer. My attempts to get RealPlayer, which I never got to function, and my Microtek scanner, which I also never got functioning, to work on my computer still trouble me with the idea that I might have inadvertently gotten rid of something that I shouldn't have. I keep thinking back to a /dev/dsp/ file I think I removed, based on a forum recommendation, in my RealPlayer efforts. I have debated about re-installing  Breezy just to start over in case I made any problematic changes, but on the other hand, I find myself thinking that it would be  better to keep using my current installation  and  learn how to fix things  as they come up. I think I at least have a better handle on things now, though. I keep getting hung up every time I think about  upgrading to Mac OS X. I had gotten to the  point  that  I  felt comfortable troubleshooting Mac OS  9 and had my system running the way I wanted it to when X began its first release. All that time spent on those  OS 9 books seemed to just go out  the  window. Then there is the  issue of all the money I spent on software to use in  OS 9. I have not been in  the mood to upgrade all those applications  to OS X. I suppose that is just the nature of the business, but, for now, I am still on the fence  about sticking  with Apple. Their comments about switching to Intel processors have also contributed to my reluctance to get in  deeper with the  ppc architecture. I am impressed with Ubuntu ppc even with my difficulties with it, but worry about how dedicated  they will be to supporting it over the  long haul.

---

### Post by farruinn on 2005-11-07
In response to the linux community continuting to support ppc: I don't think it will really be a problem since Apple isn't the only company to make computers using this architecture. Last I knew IBM still makes PPC based machines, so I don't think support for this arch will fall off the radar once the switch begins.  I do, however, wonder how well x86 macs will be supported.  Will it be better? Worse? No different?

---

### Post by Rxke on 2005-11-07
@farruinn: the prelinking isn't a performance-booster, only makes some apps load faster (You probably know that already, because this is explained in the how-to, but there might be other people reading this thread)
Now, I have a pretty old machine: first gen iBook, and as an example, on my machine, launching OpenOffice stuff took aaaages. Now it only takes decades ;) 
Seriously: the load time was so bad that I considered OpenOffice almost unuseable, I just didn't want to wait that long to start typing. 

@seatea
 re: the prelinking warning: I think it is a bit overblown. The reason the warning is there, is because someone tried to do this on an unplugged laptop with an almost empty battery. Of course, mid-prelinking, his machine shut down. And he had messed up his system.... again: OS X does prelinking too (called optimising, I think, not sure, I'm Dutch-speaking...) so if it was this dangerous, it surely wouldn't be done as a default.
 re: re-installing or not: when starting out in Linux, it is fairly 'normal' to mess up your system, when you're taking your "first steps"... tweaking, fiddling, fooling around... and sometimes breaking stuff. If you think stuff is totally going weird, consider re-installing. It might be time-consuming, but it's all part of the learning-curve. And after awhile you know what to do and where not to go; you learn to make (temporary) backups or copies of important files you are 'messing' with etc... 
I share your feelings re: another investment of software. Mac being in a transition and all that. 
I personally am wearing out my (already ancient) hardware and will very probably build my own Intel or AMD box when the time has come I really have to upgrade... While impressively complete, Linux-PPC will never be as complete re: drivers etc as the X86 arch... Some stuff just doesnt get written because there are not enough coders with a ppc... I love my Apples, they gave me back my faith in computers, mid 90's when everything had become boring faceless business machines, with samey boring faceless apps, but... 
Linux has become so good... It does virtually everything i need, for free. As a favour in return, I try to help out other people with Linux problems (despite being a n00b,) submitting some bugreports, doing a little bit of translating, or even typo-correcting... getting involved in brainstorming for stuff you think is cool (for me that is the Oolite space-trader game [http://oolite.aegidian.org/](http://oolite.aegidian.org/) ) etc... That's what makes Linux rock: no matter how computer-illiterate you are, you can always add a bit to the puzzle somewhere, which makes you feel part of a bigger picture.

---

### Post by farruinn on 2005-11-07
[quote=Rxke]Now, I have a pretty old machine: first gen iBook, and as an example, on my machine, launching OpenOffice stuff took aaaages. Now it only takes decades ;) [/quote]

I should have timed OpenOffice before I set up prelinking, but I timed it last night and it was 45 seconds - this program definitely takes the longest to start out of all the ones I use :???:

---

