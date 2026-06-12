---
title: "WoW randomly freezing up"
date: 2008-07-20
forum: Wine
---

### Post by maulik001 on 2008-07-20
:confused:

So I just started using Ubuntu bout 3 weeks ago and just installed WoW on it. I can play the game fine, get pretty good fps and barely any latency, but it keeps randomly freezing on me. I cant even get to the kill process menu and try to stop WoW.exe

I have a toshiba p100 with nvidia geforce go 7600, and am using the latest wine. I have also done all the optimization tweaks to the registry and the config.wtf file in my WTF folder.

I hate using windows vista so dont want to do a dual boot, so if anyone can show me how to solve this problem it would be sweet.

If you need any more info let me know, oh and if they are logs or something like that please also tell me how to get them, still learning how to use the terminal and stuff.

thanks
maulik

---

### Post by llama320 on 2008-07-20
I haven't tried this with WoW specifically, but sometimes compiz and wine don't get along terribly well. So if you're using compiz, try
```
metacity --replace
```
This will activate metacity, thus stopping compiz
If you want to reactivate compiz:
```
compiz --replace
```

I can't say this will definitely work, but it's worth a shot

Good Luck

---

### Post by flytripper on 2008-07-20
I use WoW and found the compiz-fusion-icon to be a great help in quick swithching between window decorators

---

### Post by maulik001 on 2008-07-21
> **llama320 said:**
> I haven't tried this with WoW specifically, but sometimes compiz and wine don't get along terribly well. So if you're using compiz, try
```
metacity --replace
```
This will activate metacity, thus stopping compiz
If you want to reactivate compiz:
```
compiz --replace
```

I can't say this will definitely work, but it's worth a shot

Good Luck

i hadnt installed compiz, but heard that ubuntu comes with it preinstalled so did the replace, hope it works will let you know.

---

