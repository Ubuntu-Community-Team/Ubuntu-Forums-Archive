---
title: "I need to know how to downgrade Wine"
date: 2008-07-15
forum: Wine
---

### Post by AlexisMclovin on 2008-07-15
The way I installed Wine 1.0 was add the repositories and stuff to terminal so it will automatically update and install Wine. I really didnt think it would download development packages...but it did. Now my windows apps that worked with 1.0 doesnt work with 1.1. I need to know how to downgrade from Wine 1.1 to Wine 1.0. I havent successfully built anything from source yet, so any other way would be much appreciated.

---

### Post by ibuclaw on 2008-07-15
Hmm... which game would that be?

Anyhow, the way I'd go about it would be to do the following
[LIST]
[*]Open up synaptic and search for "wine"
[*]Select the package, right-click and go into it's properties.
[*]Click on the "Versions" tab and check that 1.0.0 is there (or a previous version to the one you have installed)
[*]If there is, click "Close" and Press "**Ctrl+E**"
[*]Then select the previous version of wine and click "Force Version".
[*]If it gives you the option. When you click "Apply", the WINE package will be downgraded.
[/LIST]

[EDIT]
This goes the same for all packages in Ubuntu. So long as the versions are in different repos. (One reason why I never run "**apt-get clean**", because I'd like to be able to fall back if something goes wrong).

If you are exceptionally paranoid, you can also "**Lock**" packages at their current version too (So it never gets upgraded until you unlock it again).
To do this, select the package, then click "Package" in the toolbar and select "Lock Version".

Regards
Iain

---

### Post by AlexisMclovin on 2008-07-15
Thank you so much , much appreciated

well the game was a M.U.G.E.N game and wine doesnt openly say they support the MUGEN program on their compatibility section, but their 1.0 release supports it.

---

### Post by bodhi.zazen on 2008-07-15
Wine is finicky that way. I find if it is working, well no reason to update wine :)

You can also go to synaptic an lock the version of wine so it will not up updated.

Package -> lock version

Or in the command line:

```
echo "wine hold" | sudo dpkg --set-selections
```

---

### Post by greyfox1 on 2008-07-15
This is very good to know!  I noticed that Steam games, which ran very well under 1.0, are a slideshow for me under 1.1.  Thanks for the solutions posted here!

---

### Post by YokoZar on 2008-07-15
Wine 1.0 is now available in hardy-updates; if you want to use it, you can stop using the budgetdedicated repository entirely.

To clean out the later packages so they don't automatically reinstall, you can uninstall wine and clean the package cache (eg with sudo apt-get clean)

---

### Post by ibuclaw on 2008-07-15
Thanks for letting us know! I will notify my team :)

Regards
Iain

---

### Post by AlexisMclovin on 2008-07-15
Well downgrading wine didnt fix my problem like i thought it would , and i dont know what to do next >.> but that was good to know anyway

---

### Post by ibuclaw on 2008-07-15
```
sudo aptitude purge wine && sudo apt-get install wine
```

Perhaps?

Regards
Iain

---

### Post by AlexisMclovin on 2008-07-16
Jeez still nothing...Ill just wait for the new wine to come out and see how it does, thanks for the help though

---

