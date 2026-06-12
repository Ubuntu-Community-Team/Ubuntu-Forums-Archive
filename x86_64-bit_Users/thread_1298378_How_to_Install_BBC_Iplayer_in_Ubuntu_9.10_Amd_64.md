---
title: "How to Install BBC Iplayer in Ubuntu 9.10 Amd 64"
date: 2009-10-22
forum: x86 64-bit Users
---

### Post by gdbutcher on 2009-10-22
This method worked on my Desktop running 9.04 AMD 64 (Jaunty) and Laptop running 9.10 (karmic koala Beta).

**Step 1:** Install flash and other plugins using the excellent script from here:**[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html#comment-150888]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html#comment-150888")** A copy is attached to this post, chmod +x it and run in terminal

**Step 2:** Download and install getlibs from here: **[http://taurinocerveza.com/scripts/getlibs-all.deb]("http://taurinocerveza.com/scripts/getlibs-all.deb")**

**Step 3:** Download and install Adobe Air from here: **[http://get.adobe.com/air/]("http://get.adobe.com/air/") **

**Step 4:** Install Adobe Air ```
sudo ./AdobeAIRInstaller.bin
```

**Step 5:** Copy and paste the following lines into the terminal, one at a time:```
sudo apt-get install ia32-libs
sudo getlibs -l libgnome-keyring.so
sudo getlibs -l libgnome-keyring.so.0
sudo getlibs -l libgnome-keyring.so.0.1.1 
```

**Step 6:** Copy and paste this final line into the terminal: ```
sudo cp /usr/lib/libadobecertstore.so /usr/lib32 
```

**Final Step:** Install the BBC Iplayer from here: [B][http://www.bbc.co.uk/iplayer/install/]("http://www.bbc.co.uk/iplayer/install/")
[/B]

I can't claim any credit for this, many thanks to the everyone on these websites for there work:

[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html")
[http://www.bauer-power.net/2009/05/getting-adobe-air-to-work-in-ubuntu-904.html ]("http://www.bauer-power.net/2009/05/getting-adobe-air-to-work-in-ubuntu-904.html")

Any comments corrections etc are more than welcome, hope it works for you too!

---

### Post by typos1 on 2009-10-24
Yeah I tried this from another site. It doesnt work.

Air froze part way through install from bbc site.

Tried to install manually, says "package not found" even though its sat on my desktop. Tried putting somewhere else, still no luck.

Already got latest ia32 libs. The other lines go on for ever saying "package not found". Says ubuntu not in repositories, treid putting it in, wont accept it.

Nothing happens when I put "sudo cp /usr/li/libadobestore.so /usr/lib32" in a terminal and hit return

---

### Post by Jean-Danjou on 2009-10-24
I know it's a stupid question, but why do you need to install Iplayer for? 
So far, I never installed any thing for it, and I use BBC iPlayer without a problem, including full screen..
... I think I missed something in this post ! Don't get it ! Doh!

Merci :)

AMD 64.
ATI 4670
Ubuntu 9.10

---

### Post by gdbutcher on 2009-10-25
> > **typos1 said:**
> Yeah I tried this from another site. It doesnt work.

Sorry to here that Typos1, like you I've never got Adobe Air to install directly from the BBC website, but I didn't have any problems installing it manually using this method on either machine. Dont knpw why it would work on both of mine and not yours, very strange.

[QUOTE]why do you need to install Iplayer for? 

Jean-Danjou, if you install the Iplayer Desktop, you can download the programs to watch later, you can even watch them offline (if you turn off the "BBC IPLAYER REPORTING PARTICIPATION" in settings screen). Which is pretty handy if your traveling and/or staying somewhere without internet access.

In general the programs are stored on your hard drive for about 30 days, once you start watching 1 however you have only 7 days to watch it in.

---

### Post by Jose Catre-Vandis on 2009-10-25
I'm with Jean-Danjou. Iplayer works fine for watching online.

If you need to download programmes to watch later, use the excellent [get_iplayer]("http://linuxcentre.net/getiplayer") (or there are many other alteratives out there)

---

### Post by typos1 on 2009-10-25
I needed to instal iplayer cos it wouldnt play anything on the iplayer site. I tried to download a programme (so i could watch it with sound) and to download you need AIR. It appeared to install from the BBC site. Bu then went all funny and just has one long moving bar whenever I go to it.

Stillno sound with Flash movies

---

### Post by gdbutcher on 2009-10-25
Typos1, can I just confirm for my benefit and for the benefit of anyone else who may read this guide, since I posted this thread, have you tried  installing Iplayer using this guide? taking all of these steps? and it does not work for you?

I put together these steps from various web pages for people who wanted to Install the Iplayer Desktop. The other solutions I found were a) out of date (containing bad links, etc.) or b) didn't work.

I just wanted to put a working solution in one place so that other people don't have to spend ages trawling through the same pages I did.

I have now followed these steps 3 times and successfully installed it each time. The last thing I want to do is mis-advise people.

Has anyone else tried this and got it working or is it just me?

---

### Post by typos1 on 2009-10-26
Yes, I tried using this guide. I gave up trying to get it to work (been trying since end of June), for about 3 weeks then tried again and noticed this thread. It only upgraded to version 9 something, so I used "find plugins" that didnt work so I went directly onto the site and downloaded it. And it worked, well it plays videos (it always said "there appears to be a problem" before), but still no sound. I tried installing iplayer desktop, but nothing happpens when you click on the icon and theres just an install bar that hangs when you go into desktop on the iplayer site.

---

### Post by gdbutcher on 2009-10-26
Sounds like a flash problem like this one here: [http://ubuntuforums.org/showthread.php?t=1182762]("http://ubuntuforums.org/showthread.php?t=1182762")

in your firefox address bar write: 

```
about:plugins
```

right at the bottom of the page what does it say under Shockwave Flash?

mine says:

```
File name: npwrapper.libflashplayer.so
Shockwave Flash 10.0 r32
```

because Flash 10 is installed, does yours say 9.something?

---

### Post by typos1 on 2009-10-26
No, not now-as I said after I saw it was only 9 and plugin finder didnt work, I got the update to 10 manually and it worked, finally, just not sound. 

Sound works with everything else but not flash movies, some one suggested its wher Firfox is sending the sound, but what they suggested didnt work

I ve had a few nasty comments from some people when I ve asked for help-I ve spent so long on it with no sucess, then just as I thought I d cracked it, theres still no sound

---

### Post by mrfotheringham on 2009-10-29
> **gdbutcher said:**
> This method worked on my Desktop running 9.04 AMD 64 (Jaunty) and Laptop running 9.10 (karmic koala Beta).

**Step 1:** Install flash and other plugins using the excellent script from here:**[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html#comment-150888]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html#comment-150888")** A copy is attached to this post, chmod +x it and run in terminal

**Step 2:** Download and install getlibs from here: **[http://taurinocerveza.com/scripts/getlibs-all.deb]("http://taurinocerveza.com/scripts/getlibs-all.deb")**

**Step 3:** Download and install Adobe Air from here: **[http://get.adobe.com/air/]("http://get.adobe.com/air/") **

**Step 4:** Install Adobe Air ```
sudo ./AdobeAIRInstaller.bin
```

**Step 5:** Copy and paste the following lines into the terminal, one at a time:```
sudo apt-get install ia32-libs
sudo getlibs -l libgnome-keyring.so
sudo getlibs -l libgnome-keyring.so.0
sudo getlibs -l libgnome-keyring.so.0.1.1 
```

**Step 6:** Copy and paste this final line into the terminal: ```
sudo cp /usr/lib/libadobecertstore.so /usr/lib32 
```

**Final Step:** Install the BBC Iplayer from here: [B][http://www.bbc.co.uk/iplayer/install/]("http://www.bbc.co.uk/iplayer/install/")
[/B]

I can't claim any credit for this, many thanks to the everyone on these websites for there work:

[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html")
[http://www.bauer-power.net/2009/05/getting-adobe-air-to-work-in-ubuntu-904.html ]("http://www.bauer-power.net/2009/05/getting-adobe-air-to-work-in-ubuntu-904.html")

Any comments corrections etc are more than welcome, hope it works for you too!
Cheers worked for me

---

### Post by timgood on 2009-10-31
Running an AMD Quad Core Processor under Karmic, the installation of iPlayer Desktop fails with segfault linked to gio libraries. Some people have highlighted this as an AMD processor problem. I've never managed to get any Air applications to work under Ubuntu. YMMV - but there are many of us with AMD who can't get Air to work.

---

### Post by 00edd on 2009-11-02
what really annoys me is that in this little demonstration of 9.10 on the BBC [http://news.bbc.co.uk/1/hi/technology/8326264.stm](http://news.bbc.co.uk/1/hi/technology/8326264.stm), the impression is clearly given that the iplayer now works easily on ubuntu ("and here we have the iplayer"). great, I thought, finally. so I upgraded yesterday from 9.04 to 9.10, believing I can just install that now from the software centre, or at least easily, only to find that the same problems I had before on my 64bit machine are still exactly the same as before. what a piss-take!

anyone who asks why not watch online in a browser, I tell you why. because the ubuntu wireless driver for my card is utter rubbish. I have vista parallel installed, and get a stable 12-13Mbps there. but in ubuntu I get a very unstable, maximum 3Mbps connection, the vast majority of time no faster than 800kbps. if I have my laptop right beside the router, I also get the 12-13Mbps, but a mere 5 meters away in my room the picture is as above. I was hoping that'd get a bit better as well with the upgrade, but no, nothing. I'm really disappointed!

---

### Post by keithy on 2009-11-03
Brilliant,

Thank you. worked first time. & I'm a noob!!!

cheers

---

