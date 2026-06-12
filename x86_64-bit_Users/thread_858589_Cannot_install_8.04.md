---
title: "Cannot install 8.04"
date: 2008-07-13
forum: x86 64-bit Users
---

### Post by Roaster on 2008-07-13
Hello, it's been a while since I have been here so bear with me if this has been asked before. I recently decided to give Vista a try. I know, I know. WRONG! Any way I'm now trying to reinstall 8.04.1 x64 and I cannot get it to install AT ALL! Tried Wubi, tried clean install on a new hard drive. I formated the drive with Win XP Pro and want to dual boot with XP again. I have never had this problem installing Ubuntu. It will get to the OS menu and when I choose Ubuntu it acts normal until it get to a certain point and it just sits there. "Loading, please wait" and then just a blinking cursor. I recently put in a new video card (9600GT). Maybe that is the problem. I'm downloading the alternative cd as I write but I've never used this before so I probably will be back with more questions. Could Vista have caused this? I put the new video card in  when I tried Vista. Many thanks in advance for any help you can give me.

---

### Post by Kilz on 2008-07-13
> **Roaster said:**
> Hello, it's been a while since I have been here so bear with me if this has been asked before. I recently decided to give Vista a try. I know, I know. WRONG! Any way I'm now trying to reinstall 8.04.1 x64 and I cannot get it to install AT ALL! Tried Wubi, tried clean install on a new hard drive. I formated the drive with Win XP Pro and want to dual boot with XP again. I have never had this problem installing Ubuntu. It will get to the OS menu and when I choose Ubuntu it acts normal until it get to a certain point and it just sits there. "Loading, please wait" and then just a blinking cursor. I recently put in a new video card (9600GT). Maybe that is the problem. I'm downloading the alternative cd as I write but I've never used this before so I probably will be back with more questions. Could Vista have caused this? I put the new video card in  when I tried Vista. Many thanks in advance for any help you can give me.

Sounds like it is having problems detecting some piece of hardware. Since you added a new video card that is a good possibility. The alternate install cd is text based and is rather simple. Use the arrow keys and enter to select things.

---

### Post by tuxxy on 2008-07-13
Did you install windows first to dualboot?

---

### Post by Roaster on 2008-07-13
> **tuxxy said:**
> Did you install windows first to dualboot?

Hi, I did have Vista installed and then tried to dual boot with 8.04. Couldn't get it installed and definately did not like Vista so reformatted hard drive, installed XP Pro SP3 and am still trying to get Ubuntu installed. Can't even get the alternate cd to work. Long live Windows XP, I guess. Sure liked 8.04 while I had it. Hope some one can help me out. Bout ready to reinstall the old video card and see if that solves the problem. Maybe Ubuntu doesn't like DirectX 10. Appreciate any help I can get. Been running Ubuntu before why can't I now?:confused:

---

### Post by Kilz on 2008-07-14
> **Roaster said:**
> Hi, I did have Vista installed and then tried to dual boot with 8.04. Couldn't get it installed and definately did not like Vista so reformatted hard drive, installed XP Pro SP3 and am still trying to get Ubuntu installed. Can't even get the alternate cd to work. Long live Windows XP, I guess. Sure liked 8.04 while I had it. Hope some one can help me out. Bout ready to reinstall the old video card and see if that solves the problem. Maybe Ubuntu doesn't like DirectX 10. Appreciate any help I can get. Been running Ubuntu before why can't I now?:confused:

Does the Alternate CD come to this screen or one that is similar.
[http://news.softpedia.com/images/reviews/large/installfeistyfawn-large_001.png](http://news.softpedia.com/images/reviews/large/installfeistyfawn-large_001.png)

If not, what happens?

---

### Post by Roaster on 2008-07-14
> **Kilz said:**
> Does the Alternate CD come to this screen or one that is similar.
[http://news.softpedia.com/images/reviews/large/installfeistyfawn-large_001.png](http://news.softpedia.com/images/reviews/large/installfeistyfawn-large_001.png)

If not, what happens?

Yes, thanks, it does get to that screen. When I click "Install" it shows 'loading Linux kernel', goes to a screen with a blinking cursor and at the bottom it says 'kernel alive' and mapping something, I can't remember exactly. I definately think it has to do with the video card and drivers because I can use the same cd to install it on my wife's machine. Sorry it's taken so long to respond. Work gets in the way:)

---

### Post by bford16 on 2008-07-14
> **Roaster said:**
> Yes, thanks, it does get to that screen. When I click "Install" it shows 'loading Linux kernel', goes to a screen with a blinking cursor and at the bottom it says 'kernel alive' and mapping something, I can't remember exactly. I definately think it has to do with the video card and drivers because I can use the same cd to install it on my wife's machine. Sorry it's taken so long to respond. Work gets in the way:)
Did you actually have 8.04 before, or some other (earlier) version of Ubuntu?  Do you have any SATA drives?  Does your machine by any chance have a VIA chipset?

---

### Post by Roaster on 2008-07-14
> **bford16 said:**
> Did you actually have 8.04 before, or some other (earlier) version of Ubuntu?  Do you have any SATA drives?  Does your machine by any chance have a VIA chipset?

Yes, yes and no. I have had 8.04 running on this computer before. I got the bright idea to run Vista and upgraded my video card to an Nvidia 9600GT. When I tried to reinstall 8.04 with Vista it would not install and as I said earlier I did not like Vista(anyone interested, I'll sell it)so I reformatted the hard drive and reinstalled XP Pro with the 9600GT driver and still it won't install. I had been running an Nvidia 7600GS, XP Pro and dual booting 8.04. All the drives are SATA, optical and hard drives, thanks

---

### Post by Artemis3 on 2008-07-15
Yes, the 9600 is not well supported with the included driver, so you either do the text "alternate" install; then install nvidia driver from nvidia's page, or place your old card, install as usual and then install the nvidia driver and have it well working before swapping cards.

---

### Post by Roaster on 2008-07-16
> **Artemis3 said:**
> Yes, the 9600 is not well supported with the included driver, so you either do the text "alternate" install; then install nvidia driver from nvidia's page, or place your old card, install as usual and then install the nvidia driver and have it well working before swapping cards.

Hello, I did get the alternate cd to work, up tp a point. The alt cd got all the way to "configuring linux generic kernel" at 83% of the install and just sat there for hours. I'm mean at least 2 hours I waited for it to "configure" the damn thing and finally gave up. I do not know what else to do. I sure as hell ain't gonna go 'backwards' just to run Ubuntu, so I guess it's goodbye 'til they figure something out about the drivers. So long, see ya! Thanks to all that helped!

---

