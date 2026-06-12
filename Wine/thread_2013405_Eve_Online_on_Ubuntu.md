---
title: "Eve Online on Ubuntu?"
date: 2012-06-30
forum: Wine
---

### Post by psychoclips on 2012-06-30
What is the best and most stable way for a beginner to run Eve Online in ubuntu?

---

### Post by Dlambert on 2012-06-30
[http://support.eveonline.com/Pages/KB/Article.aspx?id=499](http://support.eveonline.com/Pages/KB/Article.aspx?id=499) 

> **How to run EVE Online under Linux**

                                   Installing EVE Online on Linux

As of  March 10th, CCP will no longer offer Linux support for EVE Online; however, we want to be sure our Linux players don’t get left behind so we’ve put together a guide that explains some work-around solutions that utilize third-party programs. Please note that CCP cannot offer technical assistance with problems that might arise during installation or use of one of the third-party programs mentioned below but you can usually get any help you might need from their respective web sites


There are a few options.

Free:
[Wine]("http://www.winehq.org/")
[Wine-Doors]("http://www.wine-doors.org/wordpress/")

Paying:
[URL="http://www.cedega.com/"]Cedega
[/URL][CodeWeaver Games]("http://www.codeweavers.com/products/cxgames/")

*Do note that after installing EVE under Linux it can happen that you see a black screen for a while, be patient.  The log on window will appear eventually.*

[Wine]("http://www.winehq.org/")_:_

To install Wine either use your distributions package management software or download the source and compile/install it manually.  Information on how to download and  install Wine for a few distributions can be found [here]("http://www.winehq.org/download/")

To install EVE using Wine follow these steps.
1. Download the Windows client from our [homepage ]("http://www.eve-online.com/download/windows.asp")
2. Right click on the EVE client installer and select "open with Wine Windows Program Loader"
3. This starts the EVE client installation process.
4. Follow the instructions [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18563") to get EVE to run fully.
5. When completed simply run the EVE online Client using the Shortcut created on your desktop.


[Wine-Doors]("http://www.wine-doors.org/wordpress/")_:_

Wine-Doors is a frontend application for Wine and includes easy installation for a number of additional programs and games with easy installation procedures.  Wine-Doors binaries and sources can be found [here]("http://www.wine-doors.org/wordpress/?page_id=3")

To install EVE using Wine-Doors follow these steps:
1. Download the Windows client from our [homepage ]("http://www.eve-online.com/download/windows.asp")
2. Start Wine-Doors
3. Find EVE Online in the list of available applications and press the install option behind it, then press Apply.
4. Navigate to where you saved the EVE installer and press Open.
5. This starts the EVE client installation process.
6. Install all Windows Fonts available 
6. When completed simply go to Applications --> Wine --> Programs --> EVE and select EVE Online to start.


---

### Post by psychoclips on 2012-07-01
I've read that article already. However everything I've looked up has shown that: 
A. Eve running  via wine is  glitchy and annoying to patch.
B. Definitely isn't the way for a beginner to try.
C. There are many articles that tell of using wine but on OLDER versions of ubuntu and eve.

I did consider wine. But I want an easier and less annoying way. Surely a better way exists.

---

### Post by ubudog on 2012-07-01
Have you tried running Eve Online in a virtual machine?

---

### Post by bud986 on 2012-07-02
The best way to run it on Linux is probably wine.

---

### Post by Dlambert on 2012-07-02
> **psychoclips said:**
> I've read that article already. However everything I've looked up has shown that: 
A. Eve running  via wine is  glitchy and annoying to patch.
B. Definitely isn't the way for a beginner to try.
C. There are many articles that tell of using wine but on OLDER versions of ubuntu and eve.

I did consider wine. But I want an easier and less annoying way. Surely a better way exists.

Eve is no longer supported on Linux though. SO WINE is the only way. I recommend PlayOnLinux. It will make patching easier.

---

