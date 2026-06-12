---
title: "Flash Updated Today"
date: 2008-02-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by JJNova on 2008-02-06
Ok, so Ubuntu informed me that there were updates for my computer. I click the icon, up pops the synaptic screen informing me that it's a Flash update. "Awesome", I thought, "A more stable version of flash. I'm growing kind of tired of having to 'ps aux' everytime I view YouTube." The install goes successfully, and I restart firefox.

And now YouTube won't work. When visiting the site, the information bar pops-up at the top of Firefox informing me that I need to install missing plugins. I click on the button to do so, and it tells me that Flash-Plugin is already installed. "No ****", I said aloud, as I recall watching a video earlier in the day. 

has anyone else updated their flash and had problems? Anyone know of a solution? Does anyone know if this is strictly a 64-bit problem ?

Thanks.

---

### Post by sfdev on 2008-02-06
I've got 64, and yes mine got broken too today... I'll check what can be done to fix this....

---

### Post by michaelp on 2008-02-06
Same problem on 32-bit.

---

### Post by sfdev on 2008-02-06
Well I've found a lazy mans solution for myself.

1. In the synaptic,search for flash and then mark the plugin for complete removal
2.  delete your firefox profile /home/YOU/.mozilla/firefox (I didnt care)
3. reinstall Flash plugin (visit youtube or whatever, and in the bar select install plugin)
4. Enjoy...

I take no responsibility for your damages...

---

### Post by JJNova on 2008-02-06
Thanks sfdev, that's the same techinque I used. The same solution is available here,

[http://ubuntuforums.org/showthread.php?t=689548](http://ubuntuforums.org/showthread.php?t=689548)

---

### Post by impact on 2008-02-06
Easier way: [http://ubuntuforums.org/showthread.php?t=689548](http://ubuntuforums.org/showthread.php?t=689548) without deleting profile... just uninstall flashplugin-nonfree via synaptic, then open firefox, go to youtube video and when it asks you to install flah, let the installer do its magic.

edit: I am a slow typer... :)

---

### Post by sfdev on 2008-02-06
so then it seems profile removal was unnecessary...

---

### Post by Kilz on 2008-02-06
Another easy fix would be to[ Just rerun the setup script.]("http://ubuntuforums.org/showthread.php?t=476924")

---

### Post by andradelipe on 2008-02-06
Guys!

New version means to me, more slow! why flash videos became so slower after every new version of this player?
I set up back my" Shockwave Flash 9.0 r31", it works so fast! :)

---

### Post by Kilz on 2008-02-06
> **andradelipe said:**
> Guys!

New version means to me, more slow! why flash videos became so slower after every new version of this player?
I set up back my" Shockwave Flash 9.0 r31", it works so fast! :)

The new version is r115. r31 would be good, and one of my scripts installs r48. Sometimes the newest isnt the best.

---

### Post by impact on 2008-02-07
What do you mean, slower? Mine seem to play at the same speed as before the update.

---

### Post by bwtranch on 2008-02-07
Uh, guys this was a 64 bit question. Remember?

---

### Post by Kilz on 2008-02-07
> **bwtranch said:**
> Uh, guys this was a 64 bit question. Remember?

Do you have some information ( a link would be nice) that says there is a problem specific to the r115 plugin in amd64?

---

### Post by jmuggins on 2008-02-07
Kilz, Another "Me, too", but i fixed mine by finding your Sticky. Thanks very much!
I didn't think I was such a n00b! ;)

---

### Post by crjackson on 2008-02-07
> **Kilz said:**
> Do you have some information ( a link would be nice) that says there is a problem specific to the r115 plugin in amd64?

It was not specific to 64-bit.  My 32-bit machines had the same issues.

---

### Post by ubuntu-freak on 2008-02-07
Profile removal isn't needed as such, but 
 
**rm $HOME/.mozilla/firefox/pluginreg.dat**
 
is a good idea when you change or edit plugins. Firefox recreates it with updated plugin information.
 
Nathan

---

### Post by Kilz on 2008-02-07
> **crjackson said:**
> It was not specific to 64-bit.  My 32-bit machines had the same issues.

Yes, but bwtranch made the comment that this is 64bit, meaning specific to 64bit. I have to take that to mean that either they know of some issue and should provide a link, or they know nothing and are spreading FUD.

---

### Post by utUtu on 2008-02-07
It's not that the flash was updated.  It was updated last Oct 2007, but it took Ubuntu that long to fix the meta package of the md5sum mismatch error.  They hardcoded the check again, so if Adobe releases a new version today or tomorrow, it will fail again for new install.  They even forgot to properly  change the version to 115 - still 48.

---

