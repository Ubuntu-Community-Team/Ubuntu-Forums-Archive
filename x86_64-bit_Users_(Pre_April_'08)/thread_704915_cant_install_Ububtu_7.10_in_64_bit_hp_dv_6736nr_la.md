---
title: "cant install Ububtu 7.10 in 64 bit hp dv 6736nr laptop"
date: 2008-02-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by rocky909 on 2008-02-22
[SIZE="4"]:KSI am a new comer in the gutsy Ubuntu world.Pls help me to install this os.I want to dual boot with VISTA ( I hate it but it came wt my laptop from bestbuy nd I need to use it untill I am familiar wt Linux world)

:guitar:**_My system_**- ***hp laptop dv 6736nr***
AMD Turion 64 x2 TL 60
2 GB RAM
Nvidia GeForce Go 7150M (shared)
15.4" WXGA High Def. Bright View Wide Screen Display (In the system I tried to find which model,it says only "PnP")
With webcam,Light Scribe 8X DVD drive

:confused:**_My problem while installing Ubuntu 7.10 (Plan to dual boot with VISTA)_**
I tried Ubuntu-7.10 thrice for last 4 days to make sure it works from 3 different cd nd source.(I had a genuine disk from Ubuntu which they sent me over mail-didnt work after a while,2nd & 3rd one one-downloaded from this site)
At first I configured the graphics to wide screen nd hp wide aspect. but later wen it was not installing then I did just as it said me (I just continued to have her) ..evertime when it comes to loading window after tht it kept me on nd on for almost 5 hrs..It said like this(Icant recall full)
Loading..Please wait..(at the top of the black nd white window,I waited each time like 2 hrs nd one time 5 hrs)Just below this it says with few line like this--
Ubuntu is a free operating sytem.It does not gurantee .....
then in the same window, it said me like this
If u want to get in as root pls enter command sudo nd lab la..( I didnt do nothing as I dont know any command.)
from this window I cant go anywhere as it kept me waiting nd waiting..I waited for 5 hrs at one point..

So frnds u hav any solution for this new comer to join in ur Ubuntu world..
I heartly thank your help and spending ur valuable time.

Rocky
NY,U.S.A[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

---

### Post by major_rocks on 2008-02-22
i had a few troubles as well when i was trying to install Gusty on my hp laptop: (amd 64 x2 athlon 1.9Ghz)....eventually i got it. I installed the 32 bit version of Gutsy.

Try this...boot from the live disk in "safe graphics mode" once you are running the live disk, click to install......then you wont be able to see the buttons on the bottom of the window for "forward", "back" or "cancel", so what i did was to remove the top and bottom panels, that gave me just enough to be able to see which buttons i wanted...("forward") was all i was interested in.....see if that helps, it worked for me.

---

### Post by rocky909 on 2008-02-22
I am still trying to install 64 bit Ubuntu as it will give my 64 bit pc peak performance..but if i cant then I have no other way without following man. Anyway i hav a ques in my mind..is hp  a trouble maker for Ubuntu?
thank u very much 4 ur support

---

### Post by rocky909 on 2008-02-22
I am still trying to install 64 bit Ubuntu as it will give my 64 bit pc peak performance..but if i cant then I have no other way without following you  man. Anyway i hav a ques in my mind..is hp a trouble maker for Ubuntu?
thank u very much 4 ur support

---

### Post by major_rocks on 2008-02-22
> Anyway i hav a ques in my mind..is hp a trouble maker for Ubuntu?

Well...most major hardware vendors have one OS in mind, and unfortunatly thats windows.....but there are plenty of people here to help you get Ubuntu installed on your HP.

Here's a closed thread with a few links to help ya out:

[http://ubuntuforums.org/showthread.php?t=528618]("http://ubuntuforums.org/showthread.php?t=528618")

BTW, im not sure how much of a performance gain you will get with 64 bit Ubuntu......if your HP is anything like mine, there is a mix of 64 and 32 bit hardware:shock:........seems to me, i got robbed....lol

---

### Post by TimThorpe on 2008-02-23
This thread is what I followed it worked great.

[http://ubuntuforums.org/showthread.php?t=575750](http://ubuntuforums.org/showthread.php?t=575750)

---

### Post by rocky909 on 2008-02-23
My laptop is Amd-TL-60,(64bit)(thts why tring 64 bit ubuntu),nvidia 7150m
I also tried by pressing F6 & giving the command in boot like this--
noacpi nolacpi
then pressed enter
but again ubuntu hangs the photos i provided here(pls click to see larger view)[ATTACH]60485[/ATTACH]

[ATTACH]60486[/ATTACH]

[ATTACH]60487[/ATTACH]..
[ATTACH]60486[/ATTACH]
All the photos are from the same window where I was hanged for starting the ubuntu..i added top and bottom view for your better understanding.
Advance thank you for your comments and suggession.

Rocky
NY

---

### Post by rocky909 on 2008-02-23
I downloaded it from here
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
and I got the original cd of 64 bit from ubuntu..
is the above link not reliable? I downloaded from here 2wice.
Thank you for your comments and hoping to see more.
cheers
Rocky
N.Y.

---

### Post by rocky909 on 2008-02-23
> **major_rocks said:**
> Well...most major hardware vendors have one OS in mind, and unfortunatly thats windows.....but there are plenty of people here to help you get Ubuntu installed on your HP.

Here's a closed thread with a few links to help ya out:

[http://ubuntuforums.org/showthread.php?t=528618]("http://ubuntuforums.org/showthread.php?t=528618")

BTW, im not sure how much of a performance gain you will get with 64 bit Ubuntu......if your HP is anything like mine, there is a mix of 64 and 32 bit hardware:shock:........seems to me, i got robbed....lol

I went there ..but it said that for dv 6736nr series that will not work..
But thank you very much dude for sending me thread.
cheers
Rocky

---

### Post by Yellow Pasque on 2008-02-23
rocky909, I recommend that you try the "alternate install CD" to get around any issues with graphics. The alternate install CD is text-based, so you can deal with the video driver after you get your system installed. And since you have an nvidia chipset, I recommend the Envy program.

---

### Post by major_rocks on 2008-02-23
rocky....

here's a link where you can get the "alternate" install iso

[http://mirror.anl.gov/pub/ubuntu-iso/CDs/7.10/]("http://mirror.anl.gov/pub/ubuntu-iso/CDs/7.10/")

you want the: "	ubuntu-7.10-alternate-amd64.iso" , just download the iso and burn to a cd. btw...did you try booting into "safe graphics mode" ? to see if that works.

---

### Post by rocky909 on 2008-02-23
> **Temüjin said:**
> rocky909, I recommend that you try the "alternate install CD" to get around any issues with graphics. The alternate install CD is text-based, so you can deal with the video driver after you get your system installed. And since you have an nvidia chipset, I recommend the Envy program.

hi Temujin
I followed this link to download twice.. u think I can get the alternate cd from here?

---

### Post by Yellow Pasque on 2008-02-23
It's easy to get Ubuntu. Just go to the top of this page and put your mouse over the "Products Menu". Get Ubuntu is one of the options. Then you can select what you want.

Here's a direct link too: (Ubuntu64 7.10 Alternate) [http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=amd64&mirror=http%3A%2F%2Fftp.wayne.edu%2Flinux_distributions%2Fubuntu%2F&debug=&download-button=&alternatecd=alternate](http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=amd64&mirror=http%3A%2F%2Fftp.wayne.edu%2Flinux_distributions%2Fubuntu%2F&debug=&download-button=&alternatecd=alternate)

---

### Post by rocky909 on 2008-02-23
> **Temüjin said:**
> It's easy to get Ubuntu. Just go to the top of this page and put your mouse over the "Products Menu". Get Ubuntu is one of the options. Then you can select what you want.

Here's a direct link too: (Ubuntu64 7.10 Alternate) [http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=amd64&mirror=http%3A%2F%2Fftp.wayne.edu%2Flinux_distributions%2Fubuntu%2F&debug=&download-button=&alternatecd=alternate](http://www.ubuntu.com/getubuntu/downloading?release=desktop-newest&arch=amd64&mirror=http%3A%2F%2Fftp.wayne.edu%2Flinux_distributions%2Fubuntu%2F&debug=&download-button=&alternatecd=alternate)

ok..let me go ahead and do tht...I will inform u about the updates Temujin..
Rocky

---

### Post by sergiom99 on 2008-02-23
I too used the "Alternate install CD" in text-mode and followed dark stang's instructions posted here> [http://ubuntuforums.org/showthread.php?t=575750](http://ubuntuforums.org/showthread.php?t=575750)

As you can see I have your same videocard, and similar setup. You can follow that whole thread's instruction and i think you will finally got your stuff working.
I would go for 32bit though.
good luck dude!

---

### Post by rocky909 on 2008-02-23
> **sergiom99 said:**
> I too used the "Alternate install CD" in text-mode and followed dark stang's instructions posted here> [http://ubuntuforums.org/showthread.php?t=575750](http://ubuntuforums.org/showthread.php?t=575750)

As you can see I have your same videocard, and similar setup. You can follow that whole thread's instruction and i think you will finally got your stuff working.
I would go for 32bit though.
good luck dude!

I am thinking to go for 32 bit now dude..64 bit will give me a headache, I think..
I will let knw was going on here dude.

---

### Post by Yellow Pasque on 2008-02-23
Go for 64-bit. The speed increase is worth any minor hassles in setting it up.

---

### Post by rocky909 on 2008-02-23
you prefer 32 bit or 64 bit? And can u expalin why you like that one?
I am not too knowledgeable abt tht..But I think 64 bit will give me speeder processor but again I am thinking for availablity of softwares like the way you said about web browseing..

---

### Post by rocky909 on 2008-02-23
> **major_rocks said:**
> rocky....

here's a link where you can get the "alternate" install iso

[http://mirror.anl.gov/pub/ubuntu-iso/CDs/7.10/]("http://mirror.anl.gov/pub/ubuntu-iso/CDs/7.10/")

you want the: "	ubuntu-7.10-alternate-amd64.iso" , just download the iso and burn to a cd. btw...did you try booting into "safe graphics mode" ? to see if that works.

thanks man for the link..and I didnt tried to do it from safe graphics mode.....You think thats better???

---

### Post by Kilz on 2008-02-23
> **rocky909 said:**
> you prefer 32 bit or 64 bit? And can u expalin why you like that one?
I am not too knowledgeable abt tht..But I think 64 bit will give me speeder processor but again I am thinking for availablity of softwares like the way you said about web browseing..

There is no such thing as a version of linux that does not require you to do some setup. Both 32 and 64bit may require you do do additional things to get them running 100%. Dont think that by installing the 32bit version that you will just have to click a few times and it will be all done with no work. The entire rest of this forum (thousands of posts daily) contains almost all 32bit issues. It is recommended that you install the version that is designed for your hardware.

---

### Post by rocky909 on 2008-02-23
> **Kilz said:**
> There is no such thing as a version of linux that does not require you to do some setup. Both 32 and 64bit may require you do do additional things to get them running 100%. Dont think that by installing the 32bit version that you will just have to click a few times and it will be all done with no work. The entire rest of this forum (thousands of posts daily) contains almost all 32bit issues. It is recommended that you install the version that is designed for your hardware.

let me go ahead and try with the safe mode..(64 bit)
thanks for ur advices

---

### Post by Kilz on 2008-02-23
> **rocky909 said:**
> let me go ahead and try with the safe mode..(64 bit)
thanks for ur advices

No problem, I just want you to know that there may be work regardless of what version you install. New users sometimes fear that they will have to do something beound their abilities and are willing to settle for less if they can avoid it. Im just saying there is no way to avoid some setup so you might as well go for the best outcome.
No matter what, we will do our best to help you get it all setup, you are not alone.

---

### Post by rocky909 on 2008-02-24
> **TimThorpe said:**
> This thread is what I followed it worked great.

[http://ubuntuforums.org/showthread.php?t=575750](http://ubuntuforums.org/showthread.php?t=575750)

it's a good link Tim..thanks man

---

### Post by ghost_ryder35 on 2008-02-24
try booting into your bios setup and setting your drive as **ata **or **sata** instead of the option that is selected.  I had the same problem and that was what my problem was.  (I had previously had the 32bit version running with no problems)

---

