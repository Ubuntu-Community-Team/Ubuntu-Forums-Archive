---
title: "Wine 1.3 won't work!"
date: 2012-02-22
forum: Wine
---

### Post by GenoDesigns on 2012-02-22
Hey everyone,

I recently installed Ubuntu 11.10 on my laptop. I'm loving it.

But there is 1 problem. I use Photoshop a lot. And I know there's an option that I can use GIMP. But it doesn't satisfy me.

I did some research on how to open Photoshop.exe with Wine. But it doesn't work for some reason. 

It gives me an error. Here is a screenshot of the error.

[IMG]http://i.imgur.com/NuWNK.png[/IMG]

I open Photoshop.exe with *Wine Windows Program Loader* And it gives me that error.

If anyone is there. Please help me. 
Contact me here or at [email]dnovosard@gmail.com[/email]

Thanks!






@bodhi.zazen

---

### Post by roelforg on 2012-02-22
This error message would sooooooo fit in with these links:
[http://thedailywtf.com/Articles/Successed!.aspx](http://thedailywtf.com/Articles/Successed!.aspx)
and
[http://thedailywtf.com/Articles/Pop-up_Potpourri_0x3a__Arcade_Edition.aspx](http://thedailywtf.com/Articles/Pop-up_Potpourri_0x3a__Arcade_Edition.aspx)

---

### Post by roelforg on 2012-02-22
But seriously,
what were you doing that caused the error... erm... i mean success.

---

### Post by dagroves on 2012-02-22
Wine 1.3 is a beta version and will not work with Photoshop. If you want Photoshop to work use Wine 1.2.

---

### Post by forrestcupp on 2012-02-22
You also need to actually install Photoshop again using Wine, and not just try to run photoshop.exe off of a previous Windows install.

Plus, which version of Photoshop are you using. I may be wrong, but I don't think the latest version works with Wine.

---

### Post by GenoDesigns on 2012-02-22
> **roelforg said:**
> But seriously,
what were you doing that caused the error... erm... i mean success.
Nope. Just tried to use PS.


> **dagroves said:**
> Wine 1.3 is a beta version and will not work with Photoshop. If you want Photoshop to work use Wine 1.2.

I just removed Wine 1.3 and installed Wine 1.2. And when I try to open Photoshop with Wine 1.2..nothing comes up.

---

### Post by GenoDesigns on 2012-02-22
> **forrestcupp said:**
> You also need to actually install Photoshop again using Wine, and not just try to run photoshop.exe off of a previous Windows install.

Plus, which version of Photoshop are you using. I may be wrong, but I don't think the latest version works with Wine.

I installed Photoshop from Ubuntu itself. 

I'm using Photoshop Portable.

---

### Post by dagroves on 2012-02-22
You will have to use an older version such as CS3 or CS2, both of those work under Wine 1.2.
**Remember, Pirating is illegal and not endorsed on these forums.** (Only put that because "Photoshop Portable" is not a real product from Adobe, that is a version made by a user.)

---

### Post by GenoDesigns on 2012-02-22
> **dagroves said:**
> You will have to use an older version such as CS3 or CS2, both of those work under Wine 1.2.
**Remember, Pirating is illegal and not endorsed on these forums.** (Only put that because "Photoshop Portable" is not a real product from Adobe, that is a version made by a user.)

So Photoshop Portable will not work with Wine 1.2 correct? 

Will PS CS4 work with Wine 1.2?

---

### Post by grahammechanical on 2012-02-22
May I go over the way we use wine to run Windows programs just to make sure that this problem is not caused by a misunderstanding of how wine does things?

When wine is installed it installs a utility called Uninstall Wine Software. It should be called Add/Remove Wine Software because that is what it does. Find that utility in the Dash by typing wine and run it. when the dialog opens click the button marked Install and then browse to the location of the program's exe file and install the program just as you would do in Microsoft Windows.

This should put an icon of the program on the desktop or in the Dash which will run the program when you click on it.

Wine creates an imitation of the Windows file system to fool the program into thinking it is installed in a Windows file system. This is why the program needs to be installed through wine so that all its files are put in the correct places for a Windows program.

Regards.

---

### Post by dagroves on 2012-02-22
> **GenoDesigns said:**
> So Photoshop Portable will not work with Wine 1.2 correct? 

Will PS CS4 work with Wine 1.2?

It might, I have not tried CS4 with 1.2. You best bet would be use CS2 or CS3, both of those work, I know because I was using them about 2 months ago on Ubuntu 11.10 and on 11.04.

---

### Post by Bromden on 2012-02-22
I've tried both CS5 and CS4 on Wine 1.3 and they both works. I've always used the portable versions, the only limitations with Wine are that you can't use the GPU and with CS5 there are some graphic glitch on the interface, but nothing very bothersome.

Unfortunately Illustrator and InDesign they doesn't work, I dunno why but only Photoshop goes on Wine. Anyway that's not a problem, as a designer I can say that Scribus and Inkscape are perfect substitute.

However if you really need to use PS on Linux, work with the CS4.

Oh some version of photoshop need the file "Amtlib.dll", into the "system" folder of Wine, to work. ;)

---

### Post by GenoDesigns on 2012-02-22
> **grahammechanical said:**
> May I go over the way we use wine to run Windows programs just to make sure that this problem is not caused by a misunderstanding of how wine does things?

When wine is installed it installs a utility called Uninstall Wine Software. It should be called Add/Remove Wine Software because that is what it does. Find that utility in the Dash by typing wine and run it. when the dialog opens click the button marked Install and then browse to the location of the program's exe file and install the program just as you would do in Microsoft Windows.

This should put an icon of the program on the desktop or in the Dash which will run the program when you click on it.

Wine creates an imitation of the Windows file system to fool the program into thinking it is installed in a Windows file system. This is why the program needs to be installed through wine so that all its files are put in the correct places for a Windows program.

Regards.

I appreciate your effort to help me. Thanks.

But the problem is still not fixed. When I browse for the .exe to install. It doesn't load up. It does nothing.

---

### Post by oldos2er on 2012-02-22
Thread moved to Wine.

---

### Post by cwwilson721 on 2012-02-22
Also, try starting ANY wine-related program that is giving you issues in a terminal. You will get alot of info in that window.

---

### Post by GenoDesigns on 2012-02-23
Not helping guys :(

---

### Post by Bachstelze on 2012-02-23
> **dagroves said:**
> Wine 1.3 is a beta version and will not work with Photoshop. If you want Photoshop to work use Wine 1.2.

[Wrong.](http://appdb.winehq.org/appview.php?iAppId=17)

---

### Post by cwwilson721 on 2012-02-23
> **GenoDesigns said:**
> Not helping guys :(START THE PROGRAM IN A TERMINAL.

We ARE trying to help. Just "doesn't work" says NOTHING.
The terminal "reveals all".

Read the sticky [Sticky: ** Before asking for help with Wine << PLEASE READ BEFORE POSTING **]("http://ubuntuforums.org/showthread.php?t=885111")

---

### Post by forrestcupp on 2012-02-23
And to add to what cwwilson721 said, when you run it in a terminal and it doesn't work, come back here and post what the output in the terminal says. We can't help you if you don't help us.

---

