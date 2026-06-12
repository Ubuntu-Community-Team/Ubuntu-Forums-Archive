---
title: "Feisty - ready for AMD 64 X 2 ?"
date: 2007-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by mhenriday on 2007-04-27
When I first downloaded the 64-bit version of **Feisty** to my new **AMD 64 X 2 5000**+, I found it an unmitigated disaster - I was informed that my **nVidia** (**Geforce 7900 GTX**) card was unsupported, and was unable to get a readable screen. By writing
[INDENT]sudo apt-get install nvidia-glx
sudo nvidia-x config[/INDENT]
in the console, however, I was able to resolve this difficulty, but even after gaining access to a screen I found the distro very buggy ; among other things I couldn't get **SCIM** to work. Strangely enough, however, most of the problems seemed to iron themselves out, possibly with the help of the various updates that were sent out after I installed **Feisty** from a live CD on 22 April ; thus a couple of days later, **SCIM**, for example, began to work satisfactorily without any additional effort on my part. Naturally enough, this made me very happy, but, alas, several problems yet remain : for example, the volume control in the panel at the top of the screen is turned off, and I can't get any sound out of my machine. As I am running a dual boot with **Windows XP** and have no audio difficulties with the latter, I know that this is not a hardware problem. Another difficulty relates to video clips ; thus, for example, I find myself unable to download and open the two video clips found on this [web page]("http://www.esa.int/esaEO/SEMRLH12Z0F_index_1.html") from **ESA**. Again, the videos perform perfectly on **Windows XP** on the same machine, so this cannot be a hardware problem....

Does anyone have any suggestions as to how these difficulties can be ameliorated ? Otherwise I am very pleased with **Feisty** - I'm also running the 32-bit version on an old **Pentium III** from 1999 - and would like to be able to recommend it to others as an alternative to the legacy OS, but hesitate to do so until I've resolved the problems mentioned above....

Henri

---

### Post by Cappy on 2007-04-27
You need to install firefox with Flash 9:
[http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)
Alternatively (or additionally), you can install Opera with Flash 9:
[http://ubuntuforums.org/showthread.php?t=413040](http://ubuntuforums.org/showthread.php?t=413040)

You havn't provided any information about your sound, however. Make sure your ALSA sound card is selected in System-->Preferences-->Sound and in the field "Device".
Make sure your sound tracks are all enabled in the Volume Control And Edit-->Preferences....

---

### Post by mhenriday on 2007-04-27
> **Cappy said:**
> You need to install firefox with Flash 9:
[http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)
Thanks for the reference, **Cappy** ! I went straight to the Manual Howto and saved and installed the [http://home.comcast.net/~ubuntu64user/ia32-lib-firefox-amd64.deb](http://home.comcast.net/~ubuntu64user/ia32-lib-firefox-amd64.deb) and [http://home.comcast.net/~deletebox/firefox32-1.5.0.7-2-ubuntu-amd64.deb](http://home.comcast.net/~deletebox/firefox32-1.5.0.7-2-ubuntu-amd64.deb) packages without any difficulty. I then proceeded to download and install the **Flash 9** plugin as per **Kilz**'s instructions. But when I attempted to follow these his last instructions - «Finally to make sure sound works with flash use this command, make sure to change <username> to your username.
```
chown -R <username>:users /home/<username>/.macromedia
```I received the notice below : ```
mhenriday@mhenriday-desktop:~$ chown -R mhenriday:users /home/mhenriday/.macromedia
chown: cannot access "/home/mhenriday/.macromedia": The file or the catalogue does not exist
``` (My translation from the Swedish))
> Alternatively (or additionally), you can install Opera with Flash 9:
[http://ubuntuforums.org/showthread.php?t=413040](http://ubuntuforums.org/showthread.php?t=413040)I do have **Opera** installed, but I think I'll wait until I've succeeded in resolving the problems in **Firefox** before attempting to deal with them in yet another browser !...

> You havn't provided any information about your sound, however. Make sure your ALSA sound card is selected in System-->Preferences-->Sound and in the field "Device".
When I open the «**Devices**» tab under **Sound**, I see four fields which provide for testing ; the fourth of which is entitled «Sound Capture» with «ALSA - Advanced Linux Sound Architecture» selected by default. When I attempt to perform a test, I get the following message, which I find difficult to interpret in detail, but the general purport of which seems quite clear :
[INDENT]«gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect: Connection refused»[/INDENT]
An attempt to perform the other three tests merely leads to closure of the audio settings window....
> Make sure your sound tracks are all enabled in the Volume Control And Edit-->Preferences....When I right-click on the volume-control icon in the panel (which, by the way, has a white circle with a line running through it against a red background to show that it has been disabled), I get the following encouraging message : «The volume control did not find any elements or units to control. Either you do not have the correct GStreamer plugins installed, or you have not configured any sound card.» (My translation from the Swedish.) I should be happy to configure my sound card, if only I knew how ! As I mentioned above, none of these problems have arisen in the upgrade I performed from 32-bit **Edgy** to 32-bit **Feisty** on my old **Pentium III**....

Where do I go from here ?

Henri

---

### Post by Kilz on 2007-04-27
> **mhenriday said:**
> Thanks for the reference, **Cappy** ! I went straight to the Manual Howto and saved and installed the [http://home.comcast.net/~ubuntu64user/ia32-lib-firefox-amd64.deb](http://home.comcast.net/~ubuntu64user/ia32-lib-firefox-amd64.deb) and [http://home.comcast.net/~deletebox/firefox32-1.5.0.7-2-ubuntu-amd64.deb](http://home.comcast.net/~deletebox/firefox32-1.5.0.7-2-ubuntu-amd64.deb) packages without any difficulty. I then proceeded to download and install the **Flash 9** plugin as per **Kilz**'s instructions. But when I attempted to follow these his last instructions - «Finally to make sure sound works with flash use this command, make sure to change <username> to your username.
```
chown -R <username>:users /home/<username>/.macromedia
```I received the notice below : ```
mhenriday@mhenriday-desktop:~$ chown -R mhenriday:users /home/mhenriday/.macromedia
chown: cannot access "/home/mhenriday/.macromedia": The file or the catalogue does not exist
``` (My translation from the Swedish))
.



That folder, .macromedia is made after you use flash in the browser. If you had not tried flash yet , its possible it wasnt there.

---

### Post by mhenriday on 2007-04-28
> **Kilz said:**
> That folder, .macromedia is made after you use flash in the browser. If you had not tried flash yet , its possible it wasnt there.

Thanks for you're speedy reply, **Kilz** ! I've tried clicking on various videos in both the 32-bit and the 64-bit versions of **Firefox** I now have on my computer, but they universally fail to load, and when I repeat the command```
chown -R mhenriday:users /home/mhenriday/.macromedia
``` in a terminal, I get the response I mentioned above. Do you have any suggestions as to what I could do to «try» flash in such a way that would lead to the installation of the .macromedia folder ? Interestingly - and frustratingly - enough, in the 32-bit version of **Firefox**, the volume-control icon on my panel remains disabled, and when I try to open it, I still get a message to the effect that  «The volume control did not find any elements or units to control. Either you do not have the correct GStreamer plugins installed, or you have not configured any sound card.», just as I do in the 64-bit version that came bundled with 64-bit **Feisty**....

I had hoped that after succeeding in setting up a dual-boot system, I should be able to use the 64-bit **Feisty** almost exclusively, but these difficulties with audio and video constrain me to continue using **XP** as my main OS. I should be very grateful for any suggestion that can help me resolve these problems. One solution, of course, might be to replace the 64-bit version of **Feisty** with the 32-bit counterpart, but that would be giving up too easily....

Henri

---

### Post by mhenriday on 2007-04-29
After going back to **Kliz**'s [*HowTo*]("http://ubuntuforums.org/showthread.php?p=1174435"), I did manage to get the flash player installed in such a way that I can run, e g, **Mark Fiore**'s latest video release, [*Gun Crazy*]("http://www.markfiore.com/animation/guncrazy.html") (well worth watching, by the way), on both my 64-bit and my 32-bit **Firefox** installation. Alas, sound is still unavailable, and despite the fact that I went to the [*Gstreamer plugins page*]("http://packages.ubuntulinux.org/warty/libs/gstreamer-plugins") in the **Ubuntu** libraries section and installed everything in sight, I still get that tiresome message to the effect that no Gstreamer plugins or units which control volume can be found (this being the result I get when I either double-click on the icon or right-click and choose «open volume control» ; if I right-click  and try to choose «settings» («options»), the menu simply disappears !). Admittedly, ***Gun Crazy*** is kind of fun to watch with the sound turned off, but when I attempt to catch the latest version of ***ZDNet***'s [DL.TV]("http://dl.tv/"), I'm left with neither sound nor picture ; when I click to start the video I get a black screen showing a narrow grey row with a small hint of orange to the extreme left. Nothing loads and nothing happens. Worse still is what happens when I go to **NASA**'s page and try to watch that organisation's TV programmes : first comes a black screen saying «no video», then Firefox gets wiped and I have to restart the browser. Fun and games !...

Equally strange is that I now find my desktop folder locked ; upon trying to download a programme like the latest Swedish version of **Adobe Reader** - *AdobeReader_sve-7.0.9-1.i386.tar.gz* - to it, the download fails, but I have no difficulty downloading the same programme to my home directory ! If I then attempt to draw the new programme from my home directory to my desktop folder, I am informed that I don't have the necessary permissions to write to this folder ! I had had no difficulty downloading the *Gstreamer plugins* to my desktop, so this change came as quite a surprise to me. I've checked under «permissions» in the help section to see how I could regain access to my desktop, but failed to find anything of help. Any suggestions ?....

My conclusion is that the 64-bit version of **Feisty** still requires a great deal of work. Given the enthusiasm **Ubuntu** programmers seem to bring to their work, I am sure that these - and other problems - will be resolved in rapid order, once they are apprised of them. In the meantime, I'd very much appreciate hearing of any work-arounds for those mentioned above....

Henri

---

### Post by nss0000 on 2007-04-29
mh:

It's always possible that inone-or-both x32/x64 .....

1) your onboard soundchip is not supported ( ex. my ASUS-m2n )

2) Your soundcard is not supported ( ex.  Turtle-Beach )

A solution would be to install the cheapest SB16 work-a-like you can buy. They work.

nss
******

---

### Post by mhenriday on 2007-04-29
> **nss0000 said:**
> mh:

It's always possible that inone-or-both x32/x64 .....

1) your onboard soundchip is not supported ( ex. my ASUS-m2n )

2) Your soundcard is not supported ( ex.  Turtle-Beach )

A solution would be to install the cheapest SB16 work-a-like you can buy. They work.

nss
******

Thanks **nss** ! From what I can see, my computer is running a **Creative Sound Blaster X-Fi** card on an **MSI Nash 1.0** mainboard. Do you know of any directory available which would allow me to check whether this configuration is supported in **Feisty** ?...

Henri

---

### Post by kuja on 2007-04-29
> **mhenriday said:**
> When I first downloaded the 64-bit version of **Feisty** to my new **AMD 64 X 2 5000**+, I found it an unmitigated disaster - I was informed that my **nVidia** (**Geforce 7900 GTX**) card was unsupported, and was unable to get a readable screen.
I have an MSI GeForce 7900GTX and it works fine for me in Feisty  ... then again, I carried over from Edgy, I'll try the live cd in a bit and give the final word on that.

> **mhenriday said:**
> Thanks **nss** ! From what I can see, my computer is running a **Creative Sound Blaster X-Fi** card on an **MSI Nash 1.0** mainboard. Do you know of any directory available which would allow me to check whether this configuration is supported in **Feisty** ?... Henri

For checking soundcards you can go to alsa-project.org, but you'd be wasting your time. That card is famously unsupported in Linux has so far not released a driver or specs for it, though I heard they actually will be releasing a driver for it, but I can't remember where I read that or when it would be released.

---

### Post by Cappy on 2007-04-29
Creative said closed source X-Fi drivers will be available in second quarter 2007. I would pick up a $10 Creative sound card on ebay. Most of the good sound cards (like the Audigy 2/4, live, etc.) are being phased out by creative for lower priced X-Fi cards. You can buy the current no-number Audigy cards but I've read they have problems such as static. Like kuja said, look on alsa-project before buying a card to see if it is perfectly supported. Almost all of them are except X-Fi.

---

### Post by mhenriday on 2007-04-29
As I mentioned, **kuja**, my **nVidia  GeForce 7900 GTX** problem was resolved by installing nvidia-glx and then configuring nvidia. But I wonder if this difficulty has not now been resolved in the **Feist**y ISO. Let me know what happens when you try the live CD !...

Thanks, by the way, for the tips on [alsa-project.org]("http://alsa-project.org/") ; unfortunately, my visit there was, as you suggested, something of a waste of time - the [Soundcard Matrix]("http://www.alsa-project.org/alsa-doc/") was last updated more than two years ago ! In any event, it is discouraging to hear that my **SB X-fi**, which there is described as having «completely new architecture», still remains unsupported. This, at any rate, is what I was able to find after visiting the ***Creative Open Source*** [Soundcard Support page]("http://opensource.creative.com/soundcard.html") :
> X-Fi series
The X-Fi series of products are not supported under Linux. (Yet)
Closed-source drivers will be available for the X-Fi series of sound cards.
It looks like the first public Beta will be available end calendar Q3 or early calendar Q4. It has taken more resources than expect[ed] to redesign our software and drivers for Vista.
It is planned that the drivers will have full support for ALSA (playback, recording, mixer, MIDI, synthesis) and OpenAL 1.1 (with EAX effects).

Only six months to go ! But at least I can stop desperately searching for something to download to get the sound working in **Feisty** ! But I still can't understand why I can't watch a video from, say, **NASA**, even if the sound doesn't work....

Henri

---

### Post by nss0000 on 2007-04-29
If your using FesteringFaunx64 then fageddaboudit using x64 FLASH or MPLAYER -- there ain't none. Even Automatix2 won't save_your_hide. 
What you can do is some clever fudge installing FireFox-x32 and the media_support_files for it. This n.g. has a bunch of howtos for that.

nss
******

---

### Post by mhenriday on 2007-04-30
> **nss0000 said:**
> If your using FesteringFaunx64 then fageddaboudit using x64 FLASH or MPLAYER -- there ain't none. Even Automatix2 won't save_your_hide. 
What you can do is some clever fudge installing FireFox-x32 and the media_support_files for it. This n.g. has a bunch of howtos for that.

nss
******

Something strange is going on - as I mentioned above, I have no difficulty playing **Mark Fiore**'s videos - albeit without sound - from both 32-bit and 64-bit **Firefox**. But when I try to play **NASA**'s videos on either system, I get that irritating «no video» message smack in the middle of the a black screen. Turning to the **NASA** video player help section, I read the following :
> Videos may play in Windows MediaPlayer, RealPlayer or QuickTime. 

Now it just so happens that I have in fact downloaded and installed the 32-bit **Real Player 10** available on **Automatix 2**. With this I should have expected that I could play **NASA**'s video's from 32-bit **Firefox**. But no dice ! What other media support files do I need to download, and where can I gain access to them ? I already have **Flash**, which I managed to install from **Kliz**'s very useful *HowTo*....

Henri

---

### Post by kuja on 2007-04-30
> **mhenriday said:**
> As I mentioned, **kuja**, my **nVidia  GeForce 7900 GTX** problem was resolved by installing nvidia-glx and then configuring nvidia. But I wonder if this difficulty has not now been resolved in the **Feist**y ISO. Let me know what happens when you try the live CD !...

Thanks, by the way, for the tips on [alsa-project.org]("http://alsa-project.org/") ; unfortunately, my visit there was, as you suggested, something of a waste of time - the [Soundcard Matrix]("http://www.alsa-project.org/alsa-doc/") was last updated more than two years ago ! In any event, it is discouraging to hear that my **SB X-fi**, which there is described as having «completely new architecture», still remains unsupported. This, at any rate, is what I was able to find after visiting the ***Creative Open Source*** [Soundcard Support page]("http://opensource.creative.com/soundcard.html") :


Only six months to go ! But at least I can stop desperately searching for something to download to get the sound working in **Feisty** ! But I still can't understand why I can't watch a video from, say, **NASA**, even if the sound doesn't work....

Henri

Worked like a charm. Anyhow, I picked up a SB Audigy 7 for about $30 on newegg and it works well.

---

### Post by mhenriday on 2007-05-01
Hullo, **kuja** ! Glad to hear that the **Feisty** live CD «worked like a charm», but was that with or without installing nvidia-glx and configuring nvidia in console ?

Just for the fun of it, I went to your [Simple 64 homepage]("http://www.xnowherex.net/simple64/") and installed the script ; I'm hoping that it will prove useful in the future. A couple of comments and queries :
[LIST=1]
[*]Blue text against that blue-black background can be hard to read - if you don't feel it would mess up the spooky atmosphere too much, you might try yellow instead.

[*]Why do you _start _with a removal command ```
[sudo] dpkg --remove simple64 simple64-data
```instead of placing it _last _with a note to the effect that it can be used by persons wishing to remove the script ?

[*]Shouldn't ```
http://www.xnowherex.net/simple64/simple64-data_15_amd64.deb
```be prefaced by a «wget» ?

[*]Will the installer work for **Sun Java 6** as well as for **Sun Java 5** ?
[/LIST]

I am sure that I speak for all those **Ubuntu** users who lack programming or script-writing skills when I express my gratitude for the work that people like yourself and **Kilz** do in your spare time to make life easier for us all. Here's a link to an [*article*]("http://www.theinquirer.net/default.aspx?article=39291") by **Fernando Cassia** on a French colleague of mine, **Michel Xhaard**, who over the last few years has written **Linux** drivers for 352 webcams in his spare time (if he's like most doctors, he doesn't have too much of the latter in the first place) ! Think how wonderful it would be if someone with the proper training would suddenly be struck by the idea of writing **Linux** (64) drivers for all the unsupported soundcards out there !...

Henri

---

### Post by kuja on 2007-05-01
> **mhenriday said:**
> Hullo, **kuja** ! Glad to hear that the **Feisty** live CD «worked like a charm», but was that with or without installing nvidia-glx and configuring nvidia in console ?

Just for the fun of it, I went to your [Simple 64 homepage]("http://www.xnowherex.net/simple64/") and installed the script ; I'm hoping that it will prove useful in the future. A couple of comments and queries :
[LIST=1]
[*]Blue text against that blue-black background can be hard to read - if you don't feel it would mess up the spooky atmosphere too much, you might try yellow instead.

[*]Why do you _start _with a removal command ```
[sudo] dpkg --remove simple64 simple64-data
```instead of placing it _last _with a note to the effect that it can be used by persons wishing to remove the script ?

[*]Shouldn't ```
http://www.xnowherex.net/simple64/simple64-data_15_amd64.deb
```be prefaced by a «wget» ?

[*]Will the installer work for **Sun Java 6** as well as for **Sun Java 5** ?
[/LIST]

I am sure that I speak for all those **Ubuntu** users who lack programming or script-writing skills when I express my gratitude for the work that people like yourself and **Kilz** do in your spare time to make life easier for us all. Here's a link to an [*article*]("http://www.theinquirer.net/default.aspx?article=39291") by **Fernando Cassia** on a French colleague of mine, **Michel Xhaard**, who over the last few years has written **Linux** drivers for 352 webcams in his spare time (if he's like most doctors, he doesn't have too much of the latter in the first place) ! Think how wonderful it would be if someone with the proper training would suddenly be struck by the idea of writing **Linux** (64) drivers for all the unsupported soundcards out there !...

Henri

It worked like a charm, without having to install any drivers.

It starts with a remove command to hopefully remove the possibility of my packages conflicting wit themselves. I have the two urls being wgetted at the same time by the same wget, so it shouldn't need a second wget in there. I'll think about changing the font, that or I may give that page a stylesheet all by itself (at the time this was the "fast" way of doing it though). About Java 6, not yet, but I'm working on that now actually.

---

### Post by mhenriday on 2007-05-04
Aside from the fact that **SB X-fi** remains unsupported in **Ubuntu**, a couple of years after it was introduced - for which **Creative Labs** must bear the responsibility as the code hasn't been released, I still get the feeling that **Feisty** isn't really ready for 64-bit computing. But in this it is hardly alone, 64-bit seems to be regarded as an unwelcome Cinderella by all operative systems - and applications ! - who seem to welcome the role of wicked stepmother. I do hope the prince turns up in the near future, but I confess to worries about that glass slipper, not to mention the pumpkin coach !...

Every time I boot to **Feisty**, a notice to the effect that «MP-BIOS bug: 8254 timer not connected to 10-APIC» flashes on briefly on my screen. Booting proceeds, and the consequences, if any, of this lack of connection are not evident to me. Is this a problem that needs to be fixed, and in that event, how can this be done ?...

Henri

---

