---
title: "Running archangle freenix server for WoW in wine?"
date: 2015-08-07
forum: Wine
---

### Post by hansooloo2 on 2015-08-07
Has anyone got this to work I've tried a handful of times and I'm not the kind of guy to pay to play WoW in a server with none of my friends in it?

---

### Post by hansooloo2 on 2015-08-08
**1.)** Go to the link below in a new tab and follow the download instructions. Instead of using bitTorrent Ubuntu has a built in application called **Transmission bitTorrent Client** you can use to download the torrent file be for opening it with archive manager and extracting it to the desired location.
[URL="http://www.wow-one.com/forum/topic/139-243-tbc-client-download-and-install/"]
http://www.wow-one.com/forum/topic/139-243-tbc-client-download-and-install/[/URL]

> 
[FONT=tahoma][COLOR=#2f4f4f]**2. Downloading the wow 2.4.3 client:**[/COLOR][/FONT]

[FONT=tahoma]2.4.3 WoW No-Install (full client):[/FONT] [FONT=tahoma][http://goo.gl/F96JS1](http://goo.gl/F96JS1)[/FONT] *[FONT=tahoma](Not currently working)[/FONT]*
[FONT=tahoma]Mirror1: [http://goo.gl/cXOLyy](http://goo.gl/cXOLyy)[/FONT]


[COLOR=#2f4f4f][FONT=tahoma]**3. Installing the wow **[/FONT][FONT=tahoma]**2.4.3**[/FONT][/COLOR][FONT=tahoma][COLOR=#2f4f4f]** client:**[/COLOR][/FONT]

[FONT=tahoma]Simply download & extract tbc, with Winrar.[/FONT]


[COLOR=#2F4F4F][FONT=tahoma]**4. Set your realmlist**[/FONT][/COLOR]

[FONT=tahoma]Realmlist.wtf is a text File that tells your WoW game client which server (realm) to connect to. [/FONT]

[FONT=tahoma]Realmlist.wtf[/FONT][FONT=tahoma] is located in your world of Warcraft directory. To change the server (realm) you want to connect to open the [/FONT][FONT=tahoma]realmlist.wtf file, and replace its content with:[/FONT]

[FONT=tahoma]For [COLOR=#2f4f4f]**Archangel**[/COLOR]:[/FONT]

[QUOTE][INDENT][COLOR=#2F4F4F]**[FONT=tahoma]set realmlist vanillafeenix.servegame.org[/FONT]**[/COLOR]

[/INDENT]



[FONT=tahoma][COLOR=#2f4f4f]**[B]5. Create your Feenix game account**[/B][/COLOR]

Create your 2.4.3 game account on our [vanilla wow website]("http://www.wow-one.com/")[/FONT]
[FONT=tahoma]Click to sign up for your feenix gameaccount on the [/FONT][FONT=tahoma][Vanilla wow realm website]("http://www.wow-one.com/account/creation")[/FONT]


[/QUOTE]

**6.)** After the **Realmlist.wtf** file is configured and you have a freenix account. You'll need to **install wine to run Burning Crusade**.

**7.)** After wine is installed open up Configure Wine in your applications list. Under the **Application tab** select **Add application** and go to the directory with the **Freenix 2.4.3 client** folder. Inside the folder directory select **Wow.exe** and add it to the Applications list for wine. Then select your desired windows version and then **Apply** and **Okay**.

**8.)** In Ubuntu go to the directory you have the **Freenix 2.4.3 client** folder in and right click and select open with **Wine Windows Program Loader**. Then open the **Wow.exe** program to run the game.

**9.)** After signing in to the WoW login it will prompt you to select a server if it did not find the Archangle server by default. You will need to select **Development** and then **PvP** be for selecting **Search Realmlist**. This should connect you dirrectly to the Archangle game server or offer you a selection of the freenix servers to pick from that you configured your **Realmlist.wtf** file for. After selecting your realm you may create your character and start playing WoW.

---

