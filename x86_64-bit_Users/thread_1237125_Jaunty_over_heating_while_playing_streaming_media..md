---
title: "Jaunty over heating while playing streaming media.."
date: 2009-08-11
forum: x86 64-bit Users
---

### Post by peoplenamed on 2009-08-11
Ok.. so after a couple months of my computer randomly shutting off while im streaming media i have finaly come to the realization that the problem is over heating. I did not have this problem in Hardy 64 bit. It also happens when i watch a dvd.. My temporary work around is a little widget i found right clicking and add to panel.. called cpu freq scaling monitor.. it was default set to on demand giving me dual 500mhz-2ghz as needed. i changed it to conservative 500mhz dual all the time.. everything still works great.. Still gets HOT.. but stays below 70 celcius.. i know this cant be right.. and i want all the performance i can get..also it looks like my cpu is in the red on that little meter associated with freq scaling monitor.. but when i type top into the console im using nothing.. any help?
specs
duAl boot vista 64(runs cool) up 2 date jaunty 64 bit
amd turion x2 64 bit
ati radeon hd 3200
4g ram ddr?
hp pavillion dv7...
EVERY thing else works. compiz is always running... if i turn that off i save like 2 degrees..

---

### Post by shane2peru on 2009-08-11
> **peoplenamed said:**
> Ok.. so after a couple months of my computer randomly shutting off while im streaming media i have finaly come to the realization that the problem is over heating. I did not have this problem in Hardy 64 bit. It also happens when i watch a dvd.. My temporary work around is a little widget i found right clicking and add to panel.. called cpu freq scaling monitor.. it was default set to on demand giving me dual 500mhz-2ghz as needed. i changed it to conservative 500mhz dual all the time.. everything still works great.. Still gets HOT.. but stays below 70 celcius.. i know this cant be right.. and i want all the performance i can get..also it looks like my cpu is in the red on that little meter associated with freq scaling monitor.. but when i type top into the console im using nothing.. any help?
specs
duAl boot vista 64(runs cool) up 2 date jaunty 64 bit
[COLOR="Red"]amd turion x2 64 bit
ati radeon hd 3200[/COLOR]
4g ram ddr?
hp pavillion dv7...
EVERY thing else works. compiz is always running... if i turn that off i save like 2 degrees..

I highlighted the problem that you have in the above quote.  I too have the same thing in a Toshiba Laptop, except I have the Radeon HD 3100.  It is indeed overheating.  The only way I have found to solve this is to install the ATI proprietary drivers.  I recently had this problem again, when some update, messed it up, and I had to re-install them.  I tell you that, so that if you ever run into this problem again, more than likely you just need to re-install you ATI proprietary drivers.  It is an annoyance, but cools the machine off a lot.  I do some video processing on mine and it will run up to just over 100 degrees C, but it doesn't overheat or shutdown.  You can get the drivers here:

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Use them at your own risk though, because 'officially' they are not supported.  I'm by no means an expert, but I can help walk you through this if you would like.  

Shane

---

### Post by peoplenamed on 2009-08-11
i should be able to get them to install.. i also read another thread that said my heat sync was made of aluminum over another metal.. not sure what.. im not replacing the heat sync. f^^^ that. what is a good temp for this cpu?

---

### Post by shane2peru on 2009-08-11
Mine idles at around 65 degrees C.  Before I installed the proprietary drivers it was around 75 or 80, I don't remember now.  Any kind of processor work made it shoot through the roof and shutoff because of over heating.  

Shane

---

### Post by peoplenamed on 2009-08-11
ya... those were the same drivers that i had installed in the first place.. i reinstalled everything.. went really quick! no errors.. still hot... u said that u get upto 100C ?? that seems like its super super hot. i dont think that is a good thing to do. Mine shuts off when that happens. ive seen old cpu's melt out of machines before.. and im poor. so im tryin not to take ne chances.. i know ther are governors that wont let that happen.. but.. not takin chances. anything too strenuous i will just run on windows for now.. too bad.

---

### Post by shane2peru on 2009-08-11
> **peoplenamed said:**
> ya... those were the same drivers that i had installed in the first place.. i reinstalled everything.. went really quick! no errors.. still hot... u said that u get upto 100C ?? that seems like its super super hot. i dont think that is a good thing to do. Mine shuts off when that happens. ive seen old cpu's melt out of machines before.. and im poor. so im tryin not to take ne chances.. i know ther are governors that wont let that happen.. but.. not takin chances. anything too strenuous i will just run on windows for now.. too bad.

Give it a try.  I hit 100C when I'm doing some serious video processing, it is not normal to hit that hot.  You can continue monitoring the temps and go from there.  It is my understanding too that AMD usually runs hotter than Intel's do, however that may be old info.  I don't know how hot it runs in Vista I don't ever spend time in Vista.  I tried checking temp limits on this processor too, but wasn't able to find anything that was very useful.  Hope that helps.

Shane

---

### Post by novafluxx on 2009-08-11
> **peoplenamed said:**
> i should be able to get them to install.. i also read another thread that said my heat sync was made of aluminum over another metal.. not sure what.. im not replacing the heat sync. f^^^ that. what is a good temp for this cpu?

Unfortunately a lot of manufacturers are using aluminum now instead of copper (or gold!) to cut costs. Aluminum is not as good at conducting thermal energy as the other the materials.

You'll notice "COPPER PIPES" being touted about in advertising now too. This is because that while the heatsink is aluminum, there are copper pipes going though the heatsink, making it more efficient.

A completely copper heatsink, with pipes, would be the best (and cheapest compared to gold) solution.

---

### Post by fumduck on 2009-08-11
I have a after market heat sink.. and mine ahs been crashing for a bit.. I thought I was gonna have to redo my thermal paste... but if it's happening to everyone.. I have an amd opteron 1.6 ..
and gigabyte radeon hd 4650.. with some large venting in my case.. also I'm only watching like ten minutes of video and restart.. My normal temps would be around 40 to 44 C tops (its summer)(winter like  25 to 30 c). My bios is set to restart when it hits  65c ... I guesss I will try the ati drivers

---

