---
title: "World of Warcraft, Laptop, Nvidia, Low FPS possible solution but i need help."
date: 2008-11-26
forum: Wine
---

### Post by gimp0r on 2008-11-26
Hi.

I have been plagues by the low FPS problems in wow.

I have a HP laptop running Ibex with a nvidia graphics card, which seems to work perfectly for everything else including compiz. When i load WoW it is sometimes okay for the first few minutes but then the FPS drops to around 5FPS wherever i am. This becomes almost unplayable.

I have tried all of the tweaks and additions to the config.wtf and they really have made no difference.

Then i started to look at the Nivdia driver. Both that are available through the restricted drivers interface. there is also a package called nvidia-settings which i think is installed by default but may need to be installed separately.

Their is a feature in the newer nvidia drivers called PowerMizer which basically underclocks your GPU when it is not needed. This seems to be enabled by default since around october 2007

If i load nvidia-setings after a fresh boot my card will be running at maximum speed ~425 clock speed.. however when i then load WOW and check back the nvidia-settings the "PowerMizer" Feature had underclocked my card down to 100Mhz.

I managed to force the card to stay at maximum speed temporarily using some of the tweaks mentioned in other threads and wow ran perfectly.. infact betyter than it has in a long time ~25FPS at medium settings in northrend. Which i was happy with :)

There does not seem to be a way of disabling this feature permanently though as it always seems to revert to lowest settings when i quit wow and doesnt even come back after a reboot.

hopefully somebody here more knowlegable than myself will be having the same problem be able to post a workable solution. 

Thx

Ps.. Gimp0rs wall of text hits reader for 5000 word damage (Critical)

---

### Post by binbash on 2008-11-26
removing(or disabling) pulse audio gave me 5 more fps at wow

---

### Post by OMJD on 2008-11-26
I'm having this exact issue and my system should be more than up to the job of running WoW. Infact, I get over 70FPS on Vista, but when using Ubuntu + Wine, I get about 15FPS.

System:

Ubuntu 8:10
CPU: Intel Quad Core Q6600
RAM: 3GB
GPU: Nvidia 8800GT 512mb (Driver version: 177)
Wine: 1.1.9

How did you disable "PowerMizer"? 

Cheers.

- Rich

---

### Post by gimp0r on 2008-11-26
There is a few threads on this forum about it, i am unsure exatly which one made it stay on the fastest speed though. I am work at the moment so i can't really write too much.

Could you load nvidia-settings and see if it is downclocking your GPU in the PowerMizer section. I would be intersested to see if it suddenly downlocks when you load WOW like it does with mine.

I think the best solution at the moment is either permanently disabling the powermizer program or running an older version of the nvidia driver from before it was introduced.

---

### Post by gimp0r on 2008-11-27
okay the easiest way just as a test (think it lasts about 30 seconds) is to open console and type 

nvidia-settings -q all

you should notice it straight away.. if you want to see it working load nvidia-settings and click the powermizer tab just when you are typing the above.

---

### Post by OMJD on 2008-11-27
Ty for your input, but I don't really understand.

> **gimp0r said:**
> okay the easiest way just as a test (think it lasts about 30 seconds) is to open console and type 

nvidia-settings -q all

- What am I testing?

> you should notice it straight away..

- Notice what?

> if you want to see it working load nvidia-settings and click the powermizer tab just when you are typing the above.

- See what working? I followed your instructions and viewed the powermizer tab when I inputted the command given, I saw nothing..

---

### Post by gimp0r on 2008-11-27
Okay. this only seems to work sometimes and only on certain nvidia drivers

Does your powermizer tab show the card underclocked? It looks something like this

Performance level - NV clock - Memory Clock
0                    100          100
1                    250          200
2                    450          666

Only one of these will be highlighted. If yours is on 0 when wow is running badly then the card is underclocked.

Running that command should force it to go to level 2 at maximum speed

I will post some screenshots later if i can or maybe a youtube video depending on how drunk i get :/

---

### Post by m0rbidpercepti0ns on 2009-10-16
I am having the same problem and am sturggling HARD to figure it out. Youve defenitly given me some new idea of what to try...i cant Alt TAB out of WoW though,it freezes.ive tried all tweaks and everything,and i went from a non functioning WoW,to 5-10FPS at best. Im going to test a few of the ideas here and let you all know how it works. In the NVidia X Settings..my card is under clocked for sure. If you click below to..n-vidia settings configuration it has a checked enable box for Powermizer..im going to try and run WoW without it,along with a few other ideas..ill post back what i find out.

---

### Post by beastrace91 on 2009-10-16
You really should try not to bump dead threads (this one has been down for almost a year)

Anywho - what video card do you have, what driver version, and what Wine version? Alot of the time you can see a performance increase by updating any (or all) of the above listed things to newer versions :)

~Jeff

---

