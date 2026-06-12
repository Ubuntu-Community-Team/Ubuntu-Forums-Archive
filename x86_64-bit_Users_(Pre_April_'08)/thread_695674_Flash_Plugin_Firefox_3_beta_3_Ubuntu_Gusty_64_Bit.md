---
title: "Flash Plugin Firefox 3 beta 3 Ubuntu Gusty 64 Bit"
date: 2008-02-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by ronb94 on 2008-02-13
Hello
I am using Ubuntu gusty 64 bit.
I installed the Firefox 3 beta 3 from synaptic.But I dont have flash.I tried install flash with Nspluginwrapper, its installed but I stil dont have flash on the new firefox.On the old Firefox flash is working.
How can I install flash on the new firefox?
Thanks

---

### Post by Kilz on 2008-02-13
This should make all installed plugins for ff 2 available to ff3.

```
sudo mv /usr/lib/firefox-3.0/plugins /usr/lib/firefox-3.0/pluginsold
sudo ln -s  /usr/lib/mozilla/plugins /usr/lib/firefox-3.0/
```

---

### Post by ronb94 on 2008-02-13
I dont have this directory in the /usr/lib.
Here what I have with the name firefox in the /usr/lib :
```
mozilla-firefox
firefox
firefox-3.0-3.0b3pre
firefox-addons
```

---

### Post by Kilz on 2008-02-13
> **ronb94 said:**
> I dont have this directory in the /usr/lib.
Here what I have with the name firefox in the /usr/lib :
```
mozilla-firefox
firefox
firefox-3.0-3.0b3pre
firefox-addons
```


It looks like your firefox folder is named different. A little editing of the commands should do it.

```
sudo mv /usr/lib/firefox-3.0-3.0b3pre/plugins /usr/lib/firefox-3.0-3.0b3pre/pluginsold
sudo ln -s  /usr/lib/mozilla/plugins /usr/lib/firefox-3.0-3.0b3pre/
```
Then restart the browser.

---

### Post by MiataMuc on 2008-02-13
Hi,

I just copied "libflashplayer.so" and "npwrapper.libflashplayer.so" from */usr/lib/mozilla/plugins* to */usr/lib/firefox-3.0-3.0b3pre/plugins* which did the trick.

Hope, this helps,

Flo

---

### Post by ronb94 on 2008-02-13
> **Kilz said:**
> It looks like your firefox folder is named different. A little editing of the commands should do it.

```
sudo mv /usr/lib/firefox-3.0-3.0b3pre/plugins /usr/lib/firefox-3.0-3.0b3pre/pluginsold
sudo ln -s  /usr/lib/mozilla/plugins /usr/lib/firefox-3.0-3.0b3pre/
```
Then restart the browser.

Thanks worked:)

---

### Post by Bad_Byte on 2008-02-16
[QUOTE=Kilz;4324262]It looks like your firefox folder is named different. A little editing of the commands should do it.

Thanks, that did the trick =)

---

### Post by edantes on 2008-02-17
Firefox 3 is the answer!!!  Finally a browser that won't freeze under minor stress. 

10  simultaneous YouTube instances without blinking.

Too bad the add-ons I need to survive are not available yet.

---

### Post by DREMA on 2008-02-17
Buaaaa :( its doesn't work for my, I linked the plugins directory of my default firefox to the beta 3 directory, but it doesn't detect any plugin.
What could be wrong?
Thanks

---

### Post by DREMA on 2008-02-18
Anyone?

---

### Post by Kilz on 2008-02-18
> **DREMA said:**
> Buaaaa :( its doesn't work for my, I linked the plugins directory of my default firefox to the beta 3 directory, but it doesn't detect any plugin.
What could be wrong?
Thanks

You might want to look at the symlinks I suggested above. They are not a link from firefox to firefox. Also check that the link in fact works by opening it.

---

### Post by DREMA on 2008-02-18
Yep, they're correct, this is what I have on the directory.
```

drema@sagitta:~/Escritorio/firefox3.0b3$ ls plugins
flashplugin-alternative.so  libtotem-mully-plugin.so
libtotem-basic-plugin.so    libtotem-mully-plugin.xpt
libtotem-basic-plugin.xpt   libtotem-narrowspace-plugin.so
libtotem-gmp-plugin.so      libtotem-narrowspace-plugin.xpt
libtotem-gmp-plugin.xpt

```

But it doesn't detect any plugin.
What should I do?

---

### Post by DREMA on 2008-02-19
Buuump .p

---

### Post by Kilz on 2008-02-19
Open the browser, click Help, then About Firefox. A small window will open. Near the bottom of that is a string starting with Mozilla/5.0 . Please copy that string and paste it to a reply here.

---

### Post by DREMA on 2008-02-21
Yea, I saw my error, I downloaded the beta from the mozill apage, thats a 32-bits compilation, so my plugins of my 64bits firefox doesn't work.
I installed the synaptic one and now everything works fine.
Thanks man for your help :)

A little offtopic, why the same beta version looks different? the synaptic version, the mozilla page version, the win version, all of them are beta 3.

---

### Post by Plasma_NZ on 2008-03-03
Awesome post, fixed my problem..

I used the flashplayer script install [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)
Selected gusty, then follows the fix's in this post, had to change the comands slightly due to folder name being different, but it works now.....

---

### Post by tbzep on 2008-04-17
> **MiataMuc said:**
> Hi,

I just copied "libflashplayer.so" and "npwrapper.libflashplayer.so" from */usr/lib/mozilla/plugins* to */usr/lib/firefox-3.0-3.0b3pre/plugins* which did the trick.

Hope, this helps,

Flo

This worked for me also....copied to  /usr/lib/firefox--3.05b/plugins.

---

### Post by jobsonandrew on 2008-04-19
yeah it seems that depending on what version of firefox 3 you have.. the folders are named differently.

on my 64 bit Hardy machine, i copied like this:
```
andy@UbuntuLaptop:/usr/lib/mozilla/plugins$ ls
libflashplayer.so  npwrapper.libflashplayer.so
andy@UbuntuLaptop:/usr/lib/mozilla/plugins$ sudo cp * /usr/lib/firefox-3.0b5/plugins
andy@UbuntuLaptop:/usr/lib/mozilla/plugins$ cd ../../firefox-3.0b5
andy@UbuntuLaptop:/usr/lib/firefox-3.0b5$ cd plugins
andy@UbuntuLaptop:/usr/lib/firefox-3.0b5/plugins$ ls
libflashplayer.so  npwrapper.libflashplayer.so

```

sorry but i cant be bothered to explain further.. i will if you like though

edit: forgot to mention that after restarting firefox, this all worked cool

---

### Post by SunEyed on 2008-04-19
I upgraded from gutsy to hardy and flash is working but still the same and isn't perfect.
With this firefox Firefox/3.0b5

---

### Post by fragility14 on 2008-04-23
my firefox flash stopped working after the most recent upgrade two days ago (on hardy beta)...I had done the fix here multiple times and it always made it work...it doesn't work now...did anything change with the recent upgrade?

strangely flash still works on konqueror...

---

### Post by cmdrtebok on 2008-04-29
Well I got flash to work however after a while it stops working and just shows grey boxes where the flash needs to be. Restarting the system fixes it but then it happens again after a while. Any ideas?

---

### Post by ripleyscat on 2008-04-29
> **MiataMuc said:**
> Hi,

I just copied "libflashplayer.so" and "npwrapper.libflashplayer.so" from */usr/lib/mozilla/plugins* to */usr/lib/firefox-3.0-3.0b3pre/plugins* which did the trick.

Hope, this helps,

Flo

Im using Ubuntu 8.04 Hardy Heron 64bit and can confirm that this works, but I don't really understand why it works, the only plugins in the /usr/lib/firefox-3.0b5/plugins folder now are libflashplayer.so and npwrapper.libflashplayer.so, and I have put them there manually. Prevously the /usr/lib/firefox-3.0b5/plugins cupboard was bare so to speak, there were no plugins shown at all. The rest of the  Firefox plugins appear in /usr/lib/firefox/plugins, however Firefox-3.0b5 works perfectly. Apart from these small configuration niggles I have to say, this is my first 64bit Linux install and, all in all, it rocks!

---

### Post by NipitMaster on 2008-05-01
> **MiataMuc said:**
> 
I just copied "libflashplayer.so" and "npwrapper.libflashplayer.so" from */usr/lib/mozilla/plugins* to */usr/lib/firefox-3.0-3.0b3pre/plugins* which did the trick.


I went to do the same, but */usr/lib/firefox-3.0b5/plugins* was a some kind of link to */usr/lib/firefox-addons/plugins* so I put it in the later instead and it worked.

---

### Post by SunEyed on 2008-05-01
There is the adobe installer in the sypnatic manager so it's much more easier to install and use. Still, if i have many embbed videos on a page or in the browser, they will go grey and won't show till the limits is below of the supported.

---

### Post by Zer0Nin3r on 2008-05-01
> **edantes said:**
> Too bad the add-ons I need to survive are not available yet.

Don't know if it's the answer just yet, but I will try what is posted in here as I am experiencing problems with Flash on the laptop.  Desktop works fine for some reason.

But I agree.  The add-ons I truly like aren't available yet.

**Update**
Boo-yah!  It works now.  Here's what I did:

Copy *libflashplayer.so* from '/usr/lib/flash-plugin' --> '/usr/lib/firefox-3.0b5/plugins'

note--
I am running 32-bit.

And when I restarted Firefox I have flash!

Thanks all!  Quick and simple, yet slightly annoying.

---

### Post by Timokl on 2008-05-10
This worked for me! Thanks a lot!

---

### Post by rikhard.fsoss on 2008-05-23
hi all me too have a problem with FF3b5 using amd64 hardy, i installed flashplugin-nonfree and nspluginwraper, it works fine, but if after a while flash stop working with a grey box.

but with konqueror everything is ok?!!!

does anyone have a clue?

thanks

rj

---

### Post by coldstatue on 2008-06-18
edit: wrong thread

---

