---
title: "Bye to Windows...maybe?"
date: 2007-10-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by steeviee on 2007-10-08
Hi all,
I am not new to computers, but I am a complete newb to linux so please bear with me. First of all, I was just wondering if I should even try to use Ubuntu, as it seems that my hardware is not supported. Maybe you guys might have some advice on that matter. I currently have a MSI P6N diamond MB, and an Intel q6600 processor with two 8800gts video cards. I would like to do a dual boot system with XP 64 and Ubuntu, also I would like to run Vista 64 on Ubuntu using vmware. That is my ultimate goal, if it is not feesable Just let me know. I have tried to install Ubuntu on my current system but for some reason it will not load. I get the startup screen, then menu options and once I choose my option everything just goes black. The cd stays running for some time after but eventually stops. 

Please please help. I want to get away from the Microsoft stronghold but it seems that I may not have a choice in the matter.
I am not going to purchase new hardware just to use ubuntu, I would like to work with what I have. Any and all suggestions regarding this matter are greatly appreciated and would like to thank you in advance for your help.
Regards
Steven

---

### Post by steveneddy on 2007-10-08
Why don't you try a few live cd's of different version of linux and see which one runs better on your hardware?

---

### Post by incubus on 2007-10-09
That's a very good suggestion.  If it still fails, consider trying the "alternative" installation CD, since it has very minimalistic requirements.  Once you have Ubuntu installed it's easier to debug.  I also suggest that you search the forums for people with similar problems (with your graphic cards and motherboard, for example).

Regarding virtualization, also consider VirtualBox.  It's also very easy to set up.

Most importantly, don't be afraid of asking around if you search and can't find an answer.  That's the spirit here.

incubus

---

### Post by polygone on 2007-10-09
Using the x86 alternate cd did the job for me, as the other one just kept hanging up.  I think my DVD drive wouldn't give the data fast enough and it would freeze.  I am a noob, though, so I could be way off.  Either way, try the alternate.  I like it better.

---

### Post by tech9 on 2007-10-09
> **steeviee said:**
> Hi all,
I am not new to computers, but I am a complete newb to linux so please bear with me. First of all, I was just wondering if I should even try to use Ubuntu, as it seems that my hardware is not supported. Maybe you guys might have some advice on that matter. I currently have a MSI P6N diamond MB, and an Intel q6600 processor with two 8800gts video cards. I would like to do a dual boot system with XP 64 and Ubuntu, also I would like to run Vista 64 on Ubuntu using vmware. That is my ultimate goal, if it is not feesable Just let me know. I have tried to install Ubuntu on my current system but for some reason it will not load. I get the startup screen, then menu options and once I choose my option everything just goes black. The cd stays running for some time after but eventually stops. 

Please please help. I want to get away from the Microsoft stronghold but it seems that I may not have a choice in the matter.
I am not going to purchase new hardware just to use ubuntu, I would like to work with what I have. Any and all suggestions regarding this matter are greatly appreciated and would like to thank you in advance for your help.
Regards
Steven

once your typing skills are up to par, you will have no problem using ubuntu instead of windows
Even though ubuntu has an excellent GUI, it is still Linux, thus - command line driven

---

### Post by steeviee on 2007-10-09
Thanks for all of the suggestions. I have tried to use the live CD and nothing happens. No matter which menu option I choose it always starts to load and nothing. I guess I know what that means, although I have not tried any other flavor I could check out red hat or something of the sort.
As far as using command lines I have used dos a long time ago. It has been some time but I am sure that the whole command line will come back to me. I know the commands are not the same, but I think that I can manage once I learn the commands....That is if I could ever get it loaded on my computer.
Regardless I appreciate all of the suggestions and am not about to give up I just wish there was an easier way just not the Windows way. I have to get it loaded before I can learn. Thanks again for all of your suggestions, I do appreciate them.
Regards
Steven

---

### Post by steveneddy on 2007-10-09
I think you need to go to distrowatch.com and see what they have to offer in the way of linux distros. You may be surprised at the many choices one could make regarding a different feel or style.

:popcorn:

---

### Post by nzadLithium on 2007-10-10
If you havent already got ubuntu installed you will need to do a text based install. Using the alternate cd as polygone said.

Once you've got that going you will have to log in to ubuntu using the command line. 

So once you've booted ubuntu (after its installed) and the screen has gone black you need to hit ctrl + alt + f1

this will give you your command line.

login using the account and password you used in the installer.

type sudo passwd

then setup the root password.

when you run all the commands prefixed by sudo that i'm about to tell you you will need to have this password.

now you need to run 

sudo apt-get install nvidia-glx-new

this will setup the latest version of the Nvidia drivers.

the package manager says you then need to run 

sudo nvidia-glx-config enable

I dont remember having to do this but it wont cause any harm

then do 

sudo nvidia-xconfig

this should setup your gui to use nvidia drivers.

Now when you restart it should go hopefully.

I don't know what nvidia support is like for the 8800 cards but they work as good if not better than the windows ones for my 7600

Post back whether you get it to work or not.

If not post where you got up to or what your confused by.

---

### Post by nzadLithium on 2007-10-10
oh btw to restart from command line use

sudo shutdown -r now

---

### Post by PurposeOfReason on 2007-10-10
You could always pop in the Gutsy **beta** CD to check it out. If it works, wait a few days for the real deal and you'll be set. From what I hear, it is a lot better with newer hardware.

---

### Post by nzadLithium on 2007-10-11
It seems that your processor and motherboard will work fine in gutsy. But people seem to have had problems with the processor detection in fiesty. Could probably be fixed by a kernel upgrade though??? Otherwise just wait for gutsy release. I think gutsy is released 6 days from now??

---

### Post by wheredidrealitygo on 2007-10-11
As long as it's a recent release of Ubuntu it should be fine, I've used both Feisty (7.04) and Gutsy (7.10) with the same processor no problem, Gutsy in both 32 and 64-bit.

---

### Post by steeviee on 2007-10-12
Oh geez,
I am astonshed at the amount of support I have received. I knew there was more than one reason I wanted to switch. You linux users are extremly supportive and knowledgable. I can't thank you enough for your time and suggestions. I am going to try and install feisty by using the command line. I have alway felt that you learn better that way, so here goes. I pretty much gave up and was resigned to leaving the machine that I wanted to use for linux to a windows machine, until I came back and read this thread again. I have everything backed up, and am going to try and install this tonight. Before I do that I might try and download the beta version. If I get it feisty installed then I will install the beta version tomorrow. If you don't hear from me in a while....than I am sure you can figure out what happened to me. I hope that by the next time I post this thread I will be in firefox on a fresh install on Ubuntu

---

