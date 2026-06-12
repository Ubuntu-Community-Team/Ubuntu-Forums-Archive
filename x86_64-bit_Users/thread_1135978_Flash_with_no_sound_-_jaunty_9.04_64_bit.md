---
title: "Flash with no sound - jaunty 9.04 64 bit"
date: 2009-04-24
forum: x86 64-bit Users
---

### Post by kingaaronj on 2009-04-24
I upgraded my Dell Vostro 200 to Jaunty 9.04 64 bit this morning.  Any flash video I try playing plays with no sound.  I dug through my sound options for a while and everything looks good.  I can play videos in totem or vlc just fine with sound, but any flash video in firefox plays with no sound.  I'm using the flashplugin-nonfree package in the jaunty repositories.

Any ideas?  By the way, I have no problems with my Dell XPS 1530 laptop.  Jaunty is running great on there! :)

---

### Post by dacorr on 2009-04-24
i had a similar issue earlier, i found it was not happy about more than one app running that is using the sound device, i was running flash with sound and amorak.

i have found it does this every time regardless of the app though, never used to

Dac

---

### Post by kingaaronj on 2009-04-24
I think my issue is a little different.  I don't think any other programs were using the sound device when I launched Youtube in Firefox.

---

### Post by jespdj on 2009-04-24
I also have an XPS M1530, just did a fresh install of Jaunty 64-bit, installed flashplugin-nonfree and the sound works normally on for example YouTube. So probably there is some configuration problem on your system.

Sorry that I don't have a solution for you, but at least you now know that it's not impossible to have it working...

---

### Post by Bram77 on 2009-04-24
I'm having the exact same problem. I have a Creative X-Fi and I'm using Alsa with the Creative drivers. All was fine in 8.10.
I'm using the 32bit version b.t.w.

---

### Post by wcorey on 2009-04-25
I, too, am having sound problems with 9.04 and a Dell XPS-720. It worked much better with 8.10. I also experience the problem with totem playing avl files, except there the volume is extremely low but way more audible than flash. If I crank up the ext volume full up I can just about hear audio in flash, i.e. web guy vs. sales dude. With the sound applet it is much louder but even there at full volume it is just a pleasant volume, not loud.

---

### Post by Tilex on 2009-04-25
After upgrading, no sound in FLASH movies in Firefox using "libflashplayer.so" plugin.

I have Jaunty 9.04 AMD64 ... would be great if someone could give us a hint as to why this is happening !

---

### Post by mickcalcara on 2009-04-25
I am having the same problem except I have Jaunty 32 bit.

---

### Post by kingaaronj on 2009-04-26
I just checked launchpad and nobody had filed a bug report about this yet.  So I went ahead.  If you want to follow it, I filed it here: [https://bugs.launchpad.net/ubuntu/+bug/367173]("https://bugs.launchpad.net/ubuntu/+bug/367173")

---

### Post by dtsat on 2009-04-26
Sorry I'm no help, but Dell Studio 1537 w/Ati here, and Ubuntu is one of the few releases that works on this lappy with proprietary drivers, so don't give up hope! Keep searching, it'll work!

---

### Post by jespdj on 2009-04-26
Do all the people who have this problem do an upgrade, instead of a fresh install?

Because I did a fresh install (not an upgrade from a previous version of Ubuntu) and I do not have this problem.

So it might have to do with the fact that you did an upgrade.

---

### Post by ferrarix on 2009-04-26
I have this same problem on my Acer Extensa 5620G Laptop (Core2Duo).

I did a fresh install of Kubuntu 9.04 x64 using Wubi. I tried various versions of Flash Player but only the video comes and no sound.

---

### Post by dBuster on 2009-04-26
I am running Jaunty and have been since alpha3 and I have no issues with flash or sound.  I do know that photo sharing site, flikr, videos do not play but that is not a show stopper and could be something with my user_chrome.css file blocking them.  

I do know during the testing phase that there was something about the alsa mixer I believe and some issues with flash and the sound involved there.  Check out the development threads for Jaunty and look for the sticky.  Browse through that and see if anything is related.  

Good luck to all and I am happy with the Jaunty release!  Especially since this laptop would only take the Jaunty install and no other versions...

---

### Post by clansman77 on 2009-04-26
i have also noticed that using the 64 bit plugin the videos get stuck after the 3-4 seconds and the upload speed dramatically increases in conky..

---

### Post by clansman77 on 2009-04-26
the upload speed increases and chokes the network traffic.i can confirm this occurs with 64 bit flash, and swfdec plugin also.i can get sound and video playback in gnash with youtube.i did a fresh install of jaunty 64 bit with / as ext4 and retained my ext3 home partition from the previous install, i am also using nvidia proprietary drivers from the repo.

---

### Post by nunquamsecutus on 2009-04-26
I was having this issue as well. I did a fresh install of kubuntu 9.04 and installed flash through the package manager. What fixed the issue for me was that the PCM audio channel was turned down completely. I turned that up and now I have audio in flash.

---

### Post by TheBuzzSaw on 2009-04-26
During YouTube video playback, my speakers make a weird crackling sound. The video also plays through at roughly 10x normal speed.

---

### Post by falconac on 2009-04-26
I installed adobe-flashplugin from Adobe's website and finally fixed the problem.  I had to remove the (newer) adobe-flashplugin I already had installed, which Deb warned me against doing, but at least now I can hear youtube.

---

### Post by TheBuzzSaw on 2009-04-26
I went ahead and installed the 64-bit alpha. Works fine.

---

### Post by kingaaronj on 2009-04-27
I just gave the 64 bit alpha a try, copying the .so file into the .mozilla/plugins directory, and that didn't work either.

---

### Post by huntzire on 2009-04-27
> **TheBuzzSaw said:**
> During YouTube video playback, my speakers make a weird crackling sound. The video also plays through at roughly 10x normal speed.

Mine does that randomy or right after playing a mp4 or a mkv file and randomly when I launch games.

I think it might have something to do with pulseaudio, though such was working perfectly prev distro.

hmmm

note i always do a fresh install

---

### Post by SergeantOreo on 2009-04-27
I just installed Ubuntu 9.04 last week also and encountered the same issue.
I read the [Launchpad.net thread]("https://bugs.launchpad.net/ubuntu/+bug/367173") and re-installing the Flash plugin worked for me. :)

---

### Post by kingaaronj on 2009-04-27
Well I finally found a solution thanks to this thread: [http://ubuntuforums.org/showthread.php?t=1130384]("http://ubuntuforums.org/showthread.php?t=1130384") dug up by gynoid on launchpad.  I set up the pulse audio managing software and was able to see that flash was simply sending audio to the wrong device!  Two clicks and I had it transfered over to the proper device.  Hopefully that link will help some of you if it's a simple problem.

---

### Post by JPBodner on 2009-04-27
I can confirm another case of no audio, which I fixed by uninstalling and reinstalling flash plugins.  Now if I could only get Amarok to work....

---

### Post by TheBuzzSaw on 2009-04-27
> **kingaaronj said:**
> I just gave the 64 bit alpha a try, copying the .so file into the .mozilla/plugins directory, and that didn't work either.
It worked for me. Make sure you disable/uninstall the old Flash plugin.

---

### Post by Storm Rider on 2009-04-27
I had no sound after a 64 bit install of Jaunty.  Check your volume control on the top taskbar.  My problem was that the Master slider was at 0.  Problem solved for me.  Hope your as lucky :)

---

### Post by Bram77 on 2009-04-28
I've fixed it in 9.04 32bit by resetting the default ALSA soundcard.

```
~$ asoundconf list
Names of available sound cards:
HDMI
Headset
XFi
~$ asoundconf set-default-card XFi
```

I use a Creative XFi card, so you should replace XFi to whatever card has your preference in the output of "asoundconf list".

---

### Post by clansman77 on 2009-04-29
i also fixed the sound problem by using the volume control options and changing the stream in pulse audio manager.i also modified a script to reinstall the flash plugin suggested elsewhere.if somebody needs it i can upload the same..

---

### Post by WildeBeest on 2009-04-29
I did a fresh install of Jaunty 32 bit and have the same problem. Video but no audio.

---

### Post by MariLoc on 2009-05-01
I was able to fix this by disabling the on board audio. Hope this helps!

---

### Post by miegiel on 2009-05-01
> **Bram77 said:**
> I've fixed it in 9.04 32bit by resetting the default ALSA soundcard.

```
~$ asoundconf list
Names of available sound cards:
HDMI
Headset
XFi
~$ asoundconf set-default-card XFi
```

I use a Creative XFi card, so you should replace XFi to whatever card has your preference in the output of "asoundconf list".

Thx Bram, you made my day :D

---

### Post by Bram77 on 2009-05-01
My pleasure :)

---

### Post by TwistedTripper on 2009-05-03
I fixed my flash sound problem by installing Gnome Alsa Mixer and unmuting Digital under AV200 (I use a Xonar D2/PM souncard with digital coax to my amp) and ticking the IEC958 check box.

I now get sound from you tube with sound preferences set to Digital (ALSA).

On a clean Ubuntu 9.04 64bit install and installed flash using synaptic flashplugin-installer.

---

### Post by SukiSuki on 2009-05-03
I was having a similar problem (no sound in flash, but direct links to media files still work), [this guide]("http://ubuntuforums.org/showthread.php?t=789578") fixed everything for me.

for me the problem was that I had been configured for alsa, and not pulse-audio, and the configuration broke when I upgraded, the above link got my pulse audio setup properly.

---

### Post by wolf_99 on 2009-05-05
So I went over the guide, did every thing in it. Went to every flash problem mentioned in Googles first 3 pages. Even updated pulse.

Still no sound in flash. Any ideas?

---

### Post by Tilex on 2009-05-05
> **wolf_99 said:**
> So I went over the guide, did every thing in it. Went to every flash problem mentioned in Googles first 3 pages. Even updated pulse.

Still no sound in flash. Any ideas?

It may sound silly, but in Jaunty, my PCM volume was muted by default.  So Flash videos didn't have sound until I realized that.

---

### Post by mike.thenes on 2009-05-13
Hi,

Re no sound with flashplayer. I had this problem too, and Pulse Audio was the fix in my case.  I believe Pulse is the default now in Jaunty, but when I checked Synaptic I found that it wasn't installed in my verson. So (making sure that you also have the 64-bit alpha plugin of Flash player installed in your Mozilla plugins directory), install Pulse Audio from Synaptic.  Worked for me, so I hope it's helpful for others.

Regards,

Mike

---

### Post by simplified on 2009-06-18
Hi All

I found that if you are using "Tab Mix Plus" or the "Session Manager" for firefox that it's best to do the following:

- Clear all private data (you can keep your Passwords, Authenticated Sessions and Cookies!)
- Run the following:

```
sudo apt-get update
sudo apt-get remove flashplugin-installer flashplugin-nonfree
sudo apt-get install flashplugin-installer flashplugin-nonfree

```

...then restart Firefox. This worked for me, I can only assume that Firefox was caching something - I tried everything else without any luck. Good luck! :D

---

### Post by tinygreen on 2009-09-16
Here is what worked for me:

I had the same problem on a fresh install, using the adobe flash plugin from apt (flashplugin-installer). All other sound applications were working, but not flash.

I noticed that pulseaudio did not start, because the pulse user was not in the pulse-rt group, so I just fixed that in /etc/group and now it works. You can also do that by typing ```
sudo usermod -aG pulse-rt pulse
``` in a terminal.

---

### Post by pyroclastic on 2009-09-16
try to configure ur audio. i had the same problem,

---

### Post by cerulean on 2009-10-08
Solved for me - (Jaunty 64bit)

Sound has been working on my system for months, including Flash videos. Today I was messing with commands to suspend from a cron job and after I resumed from that suspend no sound in flash videos. Worked in every other conceivable player, but no flash. 
I uninstalled and reinstalled, rebooted, restarted firefox etc - nothing.

Using this thread I tried "Appendix A - General Troubleshooting" from here [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

The trick was to install the PulseAudio applet/Device Chooser - I think it's padevchooser in Synaptic.

From the applet (should show up on the top bar on the right side in gnome) select the Volume Control after you launch the app (Applications >Sound and Video >Pulseaudio Device Chooser). Then the Playback tab, then under "Show" dropdown select "Applications". At this point in real time any audio playing app will show up in a list with controls.  When I started playing a video it showed up and the VU meter showed it was playing audio - I had to select the drop down on the far right (expand the window to read it) and sure enough Flash was going to my motherboard's built in audio instead of my USB soundcard. Why on earth only Flash decided to switch soundcards I have no idea.

Hope that helps someone =)
Press **ENTER** to look up in Wiktionary or **CTRL+ENTER** to look up in Wikipedia

---

### Post by shnurui on 2009-10-08
Final Solution!

Fresh install to get audio on firefox -Failed
Fresh Pluggin install to get audio on firefox - Failed
Reinstall all audio drivers - Failed
Installed Pulse Audio control - Failed
Installed Pulse Jack Control - Failed....

REMOVED OSS-Driver compatibility issue obviously - success.

This is NOT ideal, I use OSS to transfer to my 5.1 digital surround.

Someone build an OSS plugin?

---

### Post by Nattydread69 on 2009-10-17
agreed I need OSS for my particular sound card, but no sound with flash now :(

---

