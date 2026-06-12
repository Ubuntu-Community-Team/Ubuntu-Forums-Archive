---
title: "disappointed with Pulse Audio . Is this fixed  or contiues to bug  people. PL Help ."
date: 2009-07-17
forum: x86 64-bit Users
---

### Post by sieger007 on 2009-07-17
I am considering getting rid of my Ubuntu partition. No one has ever seriously addressed this issue 
I am running 64 Bit Jaunty (latest version ) and need Skype working Acceptably , and Desperately. 
On my Vista partition that has Realtek Hi Definition codecs it flies like a  Viper. 
I tried the sound guide step by step ( see below)
I have ALSA Drivers installed.
and also tried starting skype via  command 
([http://ubuntuforums.org/showthread.php?t=1091320&highlight=skype+sound](http://ubuntuforums.org/showthread.php?t=1091320&highlight=skype+sound)) 
[http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+guide)

All the precautions were taken and directions observed.
My sounds appeared cracked . Initially fine. Later on crackled. and then there is NO SOUND.
What is the solution...Pl someone help .
I did find Realtek Linux Drivers on their website.Downloaded relevant libraries, ./conf --> ./make  and ./make-install all that but I DONT know how I can make it use that driver ..is that better than the ALSA  driver. I thought ALSA is better.
Also In Skype 2.0 there is ONLY a Pulse Audio Option that works. Anything other than that DOES NOT work.
Whats happening...someone please save me. That was totally unproductive and unlike Ubuntu when my skypecast LOST VOICE both ways , and the other fellow got annoyed.

---

### Post by jocko on 2009-07-18
> **sieger007 said:**
> I did find Realtek Linux Drivers on their website.Downloaded relevant libraries, ./conf --> ./make  and ./make-install all that but I DONT know how I can make it use that driver ..is that better than the ALSA  driver. I thought ALSA is better.
Also In Skype 2.0 there is ONLY a Pulse Audio Option that works. Anything other than that DOES NOT work.
Whats happening...someone please save me. That was totally unproductive and unlike Ubuntu when my skypecast LOST VOICE both ways , and the other fellow got annoyed.
The driver you find on the realtek website is the alsa driver. It may be newer than the one in the ubuntu kernel, but it will probably not help you with your problem. Your problem is with skype, not your sound driver. I don't use skype, but from what I can see on these forums, skype is well known for having poor audio support for linux.
And you should not use anything else than pulseaudio if you want to have sound from more than one source.

---

### Post by cfbmoo1 on 2009-07-18
I've had to remove Pulse Audio with Synaptic in order to get things like Flash and other sound using programs to work properly on my 9.04 64 bit install. I'm running on an Intel STAC92xx Analog ALSA driver now and can get sound but not from everything at the same time, but at least I'm getting sounds now.

Has the recent update I saw yesterday on my netbook to Pulse Audio resolved the sound issues where things like Flash and whatnot are not working properly? I really would like to see Pulse Audio run on my desktop system but if it's not going to work it gets yanked and I'll make due with ALSA.

Guess I'll try reinstalling Pulse Audio and see what happens since they updated it. ](*,)

Update: I just tried reinstalling pulseaudio and then the package updates. My sound still wouldn't work properly so I switched back to the ALSA drivers after uninstalling pulseaudio. ](*,)](*,)](*,)

---

### Post by Arup on 2009-07-18
I have absolutely no issues with Pulse, in Skype I select the HDA and my CPU usage is less than 2% on all eight cores. Overall I am quite pleased with Pulse in Jaunty over Hardy and Intrepid. There was a recent upgrade related to Pulse actually.

---

### Post by sieger007 on 2009-07-19
[COLOR="Blue"]My Linux partition is damned. So I can t do any more poking around.
One problem not solved and 3 more came up.
I guess I have to backup my files and do a fresh install. 
Initially I could not Sudo . It says I am not in the subdoers file. When I tried it fix that ....I cant login, it gives a bunch of crappy messages chown klog:klog not  found etc. I went the recover way and dropped to root and tried some stuff - no avail
I got all this wonderful presents , when I updated packages. It all started with my terminal fonts not showing up properly - they'd look 'L  ike Th is or pro bab ly  Wo rse' . So I started yet another operation trying to figure that out .....and then on..no more sudo....no more login....and Damned.......
This is like those windows update experiences or worse still cos there is no system restore point concept.


So rather than spend time, not knowing what the hecks happening, I will do a fresh re-install.
Basically here is what I want  as Bottomline :
<> AMD64 Distro 
<> light distro . Easy to use and configure or at least with good doc so I can figure something out . < 2g total HDD Space. 
 I have a Qosmio wigth C2D 4G ram. So speed and ram are not a problem
<> I can install the latest version of the ***atheros AR9281 WLAN Driver with 802.11N support ***.So far I am frustrated there also , I can only get some 1-2 mbps on Ubuntu c.f.  Draft N speeds on Windows
<> Best Skye sound support . I have r***ealtek Hi Def Codecs*** in windows 
<> Support for NFTS partition in RW mode ( that is good Jaunty has it built in ) 
<> Support for Chicony USB 2.0 Built in Web Camera
<> Torrent and P2P's installable easily 

Thats all and I have been  just running around and catching my own tail trying to figure this out.
When Jaunty was up and running , my Skype  worked for Just  first 2 mins. Then on there was NO SOUND. I cant hear and I am not heard. Whenever at all I heard something, I could easily be mistake for a fisherman howling  in  some sailors language and beleive me that has broken many a potential good relationships. 
So  just put that all in Plain English.Folks am open to something that is AMD64 Linux and not Ubuntu ( or non Buntu/ Debian ) also . Any insight there would help me.
Thanks
Sam

[/COLOR]

---

### Post by sieger007 on 2009-07-19
[COLOR="Gray"][B]Oh BTW - whenever skype worked......if I select  Default , HDA etc - No Sound
I have to keep all options i/p, o/p and ring as pulse.
Only then there is any sound [/B]
[/COLOR]

---

