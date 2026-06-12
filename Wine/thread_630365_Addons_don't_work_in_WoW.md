---
title: "Addons don't work in WoW"
date: 2007-12-03
forum: Wine
---

### Post by solaris_wiz on 2007-12-03
I've searched for a solution to no avail, so I apologize if this has already been covered somewhere.

After completely making the switch from M$ to ubuntu, I was eager to get back to my WoW addiction.  Yes...I said addiction.  Anyhow, like many WoW players, I use MULTIPLE addons to assist me in game play.

Before I had ever researched it, I assumed the addons were the same with wine as they were with WinXP, so I put the addons in the respective folder under $HOME/.wine/

My issue is this, after my addons not working, I researched to find that I did put them in the right spot.  I also check owner/group/file permissions and ownership against existing WoW addons...installed with WoW.

When I was playing on the M$ side, I had a button to "configure addons" or something of that nature...and I don't have that option with WoW/wine.  Has anyone else experienced this?  Any ideas?  Suggestions? should I just kick the habit?

Thanks in advance, and if you need more info from me...I'm only the internet away. el oh el.

---

### Post by poet_will on 2007-12-03
I think I'm getting the same thing.  Are you getting a hard-lock on the computer and have to push the power button to shut it off?  That is what I have to do.  I'm not sure what the cause is.  I have updated all of my addons and removed all out of date addons and I still get the issue.  Any help would be appreciated on my part as well.

Thanks

---

### Post by Sammi on 2007-12-03
Addons work exactly the same way in Linux/Wine as in Windows. At least I haven't been able to spot any difference. Just put the addons in the right directory: [I]gamedir/Interface/AddOns

[/I]They should then show up in the "Addons" page, which you find by logging on and looking in the bottom left corner of the character selection screen in WoW.

---

### Post by poet_will on 2007-12-03
Ok, I did a bit more troubleshooting to no avail.  I even deleted both the Interface folder and the WTF folder (after backing them up) and still as soon as I enter the world my computer hard-locks.  This was not the case before patch 2.3.  I'm going to ask for help on this issue in the Wine forums, so look there if you are interested.

---

### Post by poet_will on 2007-12-03
OK! My WoW is working now.  I remembered that when I was using Compiz that I had to set Composite to "0" in my xorg.conf.  I changed it back to "1" and now i am running again fine.  This is the section in the xorg.conf that I changed:
```

Section "Extensions"
	Option		"Composite"	"1"
EndSection

```

Hope this helps someone else!

---

### Post by solaris_wiz on 2007-12-03
> **poet_will said:**
> I think I'm getting the same thing.  Are you getting a hard-lock on the computer and have to push the power button to shut it off?  That is what I have to do.  I'm not sure what the cause is.  I have updated all of my addons and removed all out of date addons and I still get the issue.  Any help would be appreciated on my part as well.

Thanks

No, I'm not getting the same thing, I'm just not getting addons.

> **Sammi said:**
> Addons work exactly the same way in Linux/Wine as in Windows. At least I haven't been able to spot any difference. Just put the addons in the right directory: [I]gamedir/Interface/AddOns

[/I]They should then show up in the "Addons" page, which you find by logging on and looking in the bottom left corner of the character selection screen in WoW.

> **solaris_wiz said:**
> When I was playing on the M$ side, I had a button to "configure addons" or something of that nature...and I don't have that option with WoW/wine.
I'm not getting that button at all.  But I appreciate the response.

---

### Post by FiatLux on 2007-12-04
Are you able to run WoW without any addons installed except for Blizzards own?
Are you using the latest versions of the addons?

---

### Post by Ferrat on 2007-12-04
> **solaris_wiz said:**
> 
I'm not getting that button at all.  But I appreciate the response.

If your not getting an AddOn button at the bottom left corner of the Character select screen that means your AddOn's are not in the right place

---

### Post by pedro_orange on 2007-12-04
./home/<usr>/.wine/drive_c/Program\ Files/World\ of\ Warcraft/Interface/Add\ Ons

Is the default location for installing add ons.

So. Say you want to install Omen (Threat Meter)
You download the file from your chosen website, you unzip it. 
You copy this folder, move to the above folder (if you just spammed Next during the WoW install) and drop the folder in that directory.

NB - Might be an idea to check whats in the unpacked folder. Sometimes you get Add-Ons that have an extra folder of wrapping around them. 

(eg. Folder > Folder > Add On Files)

When you log in, and you are at the character select screen, you should see in the bottom left hand corner an "Add Ons" button which will tell you that WoW has detected Add Ons in that folder.

Hope this helps :)

---

### Post by solaris_wiz on 2007-12-06
I appreciate the reponses, but I've put the addons in the correct folder.  I stated that in the OP.  Any other suggestions?  folders are correct and so are file/folder permissions.

---

### Post by Ferrat on 2007-12-06
> **solaris_wiz said:**
> I appreciate the reponses, but I've put the addons in the correct folder.  I stated that in the OP.  Any other suggestions?  folders are correct and so are file/folder permissions.

If you can start wow and play it then wow works and then it's a problem with wow not finding the addons and that means they can't be in the right place, simple reduction logic. 
but if wow doesn't work at all that's another issue. 

what it could be for ex. if you got two wow folders from copying or reinstalling and the addons are in the wrong one (done that fault myself ^^ )

---

### Post by Faud on 2007-12-07
What addons are you trying to use? Just wondering..
I have 
Bongos 2, Omen, AtlasLootEnhanced, Lightheaded, Cart(map mod) FuBar(with a nice selection of addons for that).

All of those are working perfectly for me. Maybe you got a bugged addon if you are putting them in the right place.

---

### Post by solaris_wiz on 2007-12-11
I removed the addons and WoW.  I reinstalled them all and now they're working.

Pretty weird considering I did everything the same...in that I put the addons in the exact same place.

---

