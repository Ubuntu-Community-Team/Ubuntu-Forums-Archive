---
title: "firefox crashes after installing flash 10 (64-bit)"
date: 2009-01-06
forum: x86 64-bit Users
---

### Post by afeasfaerw23231233 on 2009-01-06
I've followed this tutorial:  [http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)
and install flash 10. But now firefox crashes and disappears everytime when visiting flash-content webpage. 
Here's is my about:plugins
```
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 d21

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r15

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 d20

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```

I don't know why there are three version installed. 

If I run firefox in terminal, here is what it says when firefox crashes and disappears: 
```
Illegal instruction
```

I followed this howto and installed 32-bit flash with npwrapper. But firefox freeze randomly on flash webpages. So this evening I googled again and found out 64-bit flash for firefox 3 was released. But now firefox crashes and closes all the time and becomes unusable. Can anyone help? Many Thanks!

p.s. my os is ubuntu 8.04 64-bit

---

### Post by stchman on 2009-01-06
Did you completely remove the old Flash 10?

```
sudo apt-get autoremove flashplugin-nonfree
```

The instructions look fine as it tells you to install the plugin in your ~/.mozilla/plugins folder.

I did that on my three 64 bit Hardy boxes and all is well.

---

### Post by afeasfaerw23231233 on 2009-01-06
Thanks for quick reply!
I think it didn't have a clean remove
```
sudo apt-get autoremove flashplugin-nonfree
[sudo] password for wong: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
wong@wong-desktop:~$ sudo apt-get autoremove flashplugin-nonfree
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
wong@wong-desktop:~$ sudo apt-get autoremove flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
The following packages were automatically installed and are no longer required:
  lib32ncurses5 libc6-i386 lib32gcc1 lib32asound2 lib32z1 lib32stdc++6
The following packages will be REMOVED:
  lib32asound2 lib32gcc1 lib32ncurses5 lib32stdc++6 lib32z1 libc6-i386
0 upgraded, 0 newly installed, 6 to remove and 19 not upgraded.
After this operation, 12.2MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 122212 files and directories currently installed.)
Removing lib32asound2 ...
Removing lib32stdc++6 ...
Removing lib32gcc1 ...
Removing lib32ncurses5 ...
Removing lib32z1 ...
Removing libc6-i386 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

I run firefox and it crash again.
Would you tell me what to do next?

---

### Post by stchman on 2009-01-06
Is it now working?

Problem when you remove something without autoremove the dependencies stay.  The autoremove removes all unused unneeded dependencies.

---

### Post by afeasfaerw23231233 on 2009-01-06
no, it crashes.
I run it in terminal and 
```
wong@wong-desktop:~$ firefox
Illegal instruction
```
and firefox disappears

---

### Post by CJ56 on 2009-01-06
Presumably you've checked out Kilz' instructions in the sticky at the top of the forum?

Well worth doing, one line at a time, is

```
sudo apt-get -y purge nspluginwrapper
sudo apt-get -y purge mozilla-plugin-gnash
sudo apt-get -y purge swfdec-mozilla
sudo apt-get -y purge flashplugin-nonfree
sudo rm -rfd /usr/lib/nspluginwrapper
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/flashplugin-alternative.so
```

As Kilz tells us to... This clears out all the gunge from previous installations and sets you up to -

Download the Flash 10 for 64-bit tar.gz from the Adobe website and close Firefox

Then extract the .so file and copy it into .mozilla/plugins in your Home Folder. 

Restart FF and it should work a charm...

---

### Post by stchman on 2009-01-06
> **afeasfaerw23231233 said:**
> no, it crashes.
I run it in terminal and 
```
wong@wong-desktop:~$ firefox
Illegal instruction
```

This is a big step, but I think you need to delete your ~/.mozilla folder.  Before deleting the ~/.mozilla folder make sure you have your bookmarks backed up.  You can get the plugins from addons.mozilla.org website.

I cannot guarantee this is going to work but it has worked for me in the past when Firefox misbehaves.

Remember when you delete your ~/.mozilla folder it is gone forever so I want to let you know.  To delete the folder do the following in a terminal.

```
rm -rf ~/.mozilla
```

After that you can reinstall the Flash 10 plugin and all your Add-ons.

---

### Post by afeasfaerw23231233 on 2009-01-06
to: cj56 
thanks for your reply. I run all your command and download 64-bit tar.gz from the Adobe but firefox still crashes again.

---

### Post by afeasfaerw23231233 on 2009-01-06
> **stchman said:**
> This is a big step, but I think you need to delete your ~/.mozilla folder.  Before deleting the ~/.mozilla folder make sure you have your bookmarks backed up.  You can get the plugins from addons.mozilla.org website.

I cannot guarantee this is going to work but it has worked for me in the past when Firefox misbehaves.

Remember when you delete your ~/.mozilla folder it is gone forever so I want to let you know.  To delete the folder do the following in a terminal.

```
rm -rf ~/.mozilla
```

After that you can reinstall the Flash 10 plugin and all your Add-ons.

I delete .mozilla and extract libflashplayer.so to .mozilla/plugins . but it still crashes again

---

### Post by CJ56 on 2009-01-06
Does the same thing happen if you use Epiphany instead of Firefox? It uses the same Flash plugin in the .mozilla/plugins folder -

---

### Post by afeasfaerw23231233 on 2009-01-06
Yes, epiphany also crashes and all windows disappear immediately when i visit new york times or any other flash webpage.

---

### Post by afeasfaerw23231233 on 2009-01-06
I just discover that it crashe on some websites with flash. It crash on newyorktimes.com cbsnews.com abc.com , etc but NOT on youtube. Why is that?

---

### Post by afeasfaerw23231233 on 2009-01-07
bump

---

### Post by Avoozl on 2009-01-07
Try doing:

```
sudo updatedb && locate libflashplayer.so
```

and see if there are any other versions of flash lying around that may be interfering with the new version.  I know you already tried purging them with apt but if they were installed manually or by a script somehow there may still be other (older) versions lying around messing things up, especially since it seems to tell you that you have three different versions which is very strange.

---

### Post by afeasfaerw23231233 on 2009-01-08
Thanks for reply. 
Here's the result. 
```
 sudo updatedb && locate libflashplayer.so
[sudo] password for wong: 
/home/wong/.mozilla/plugins/libflashplayer.so
/usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
```

Is this ```
/usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so 
```causing the problem? What should I do? 

Here's the about:plugins now. But only one flash version is shown this time. ```

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 d20

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```

---

### Post by SnakeHips on 2009-01-08
> **afeasfaerw23231233 said:**
> I just discover that it crashe on some websites with flash. It crash on newyorktimes.com cbsnews.com abc.com , etc but NOT on youtube. Why is that?

Yeah its a funny one because it bombs on [www.adobe.com](www.adobe.com) !! but works fine on [www.nba.com](www.nba.com) for example ...

[http://bugs.adobe.com/jira/browse/FP-1026](http://bugs.adobe.com/jira/browse/FP-1026)

---

### Post by afeasfaerw23231233 on 2009-01-09
Yeah. Then what should I do to fix it? I can't use firefox or epiphany to visit many sites....

---

### Post by afeasfaerw23231233 on 2009-01-09
> **SnakeHips said:**
> Yeah its a funny one because it bombs on [www.adobe.com](www.adobe.com) !! but works fine on [www.nba.com](www.nba.com) for example ...

[http://bugs.adobe.com/jira/browse/FP-1026](http://bugs.adobe.com/jira/browse/FP-1026)

According to your link, it seems that because of lacking "lahf" instruction in the cpu flag the crash occurs. Mine CPU is a Pentium 4 506 and doesn't have lahf in the cpu flag also. No more way to get flash works unless upgrading to a Core 2 Duo?

---

### Post by Yellow Pasque on 2009-01-09
If you've purged the nspluginwrapper package and still have an npwrapper.<whatever> file, then you need to manually remove the npwrapper file.
```
sudo rm /usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
```

---

### Post by afeasfaerw23231233 on 2009-01-09
I just remove /usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so but it still crashes.

---

### Post by SnakeHips on 2009-01-10
> **afeasfaerw23231233 said:**
> According to your link, it seems that because of lacking "lahf" instruction in the cpu flag the crash occurs. Mine CPU is a Pentium 4 506 and doesn't have lahf in the cpu flag also. No more way to get flash works unless upgrading to a Core 2 Duo?

...well it's early days for 64bit Flash.....not sure that "lahf" is the prob. Adobe *may* be using linux users as a test bed but I have no worries with that ,afterall its still in development. Strange it works on some sites and not others though...

---

### Post by afeasfaerw23231233 on 2009-01-15
> **SnakeHips said:**
> ...well it's early days for 64bit Flash.....not sure that "lahf" is the prob. Adobe *may* be using linux users as a test bed but I have no worries with that ,afterall its still in development. Strange it works on some sites and not others though...

Well... Then my flash won't work probably until it releases a newer version...

---

### Post by f.pier on 2009-01-15
I have a slightly different problem: I installed on my PC 8.10-64 and then, at the end of installation I typed this command

sudo apt-get install ubuntu-restricted-extras

So everything worked properly, included Flash. Everything was OK until.... last automatic update (2 days ago).
I sincerely don't know what it did, but since that update Flash doesn't work at all.
Instead of flash pictures there is a black spot.

---

### Post by phatcartoon on 2009-03-14
I really wish there was a solution to this problem.  The exact same thing has been happening to me.  Every time I went to websites like Pandora or Hulu my firefox browser would crash.  Searched the web for hours and could not find a solution.  I finally install macromedia under the add/remove and everything works.....Though this pretty much just reinstalled the old flash system.  Might not be 64bit, but hey, at least it works.

Some one please,  find an solution to this problem.

---

### Post by freackout on 2009-03-15
> **afeasfaerw23231233 said:**
> I've followed this tutorial:  [http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)
and install flash 10. But now firefox crashes and disappears everytime when visiting flash-content webpage. 
Here's is my about:plugins
```
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 d21

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r15

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 d20

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```

I don't know why there are three version installed. 

If I run firefox in terminal, here is what it says when firefox crashes and disappears: 
```
Illegal instruction
```

I followed this howto and installed 32-bit flash with npwrapper. But firefox freeze randomly on flash webpages. So this evening I googled again and found out 64-bit flash for firefox 3 was released. But now firefox crashes and closes all the time and becomes unusable. Can anyone help? Many Thanks!

p.s. my os is ubuntu 8.04 64-bit

in 32 bit i find it easier to simply remove all flash stuff in synaptic then go to youtube get the tar.gz, extract and run the  sh ./flash(tab) it works every time no prob however remember the youtube site is only 32 bit so get the tar.gz for 64 bit and bobs yo uncle.

---

### Post by ethoxyethaan on 2009-03-15
check these directories:

/usr/lib/firefox-addons/plugins/
/usr/lib/mozilla/plugins/

then check 

~/.mozilla/plugins/

if you see anything related to adobe flash kill it.

try deleting ~/.adobe aswell.

---

### Post by ju2wheels on 2009-03-18
The d20 version is old. I would recommend deleting it and replacing it with d21: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz)

There is a newer one than d21 (they correct the name and its r22) but I wouldnt recommend this release as its less stable than d21.

---

### Post by Kareeser on 2009-03-18
You have conflicting versions of flash on your computer. That's all.

1. Open firefox.
2. In the address bar, type "about:config", and accept the warning
3. In the search box, type "plugin"
4. Doubleclick "plugin.expose_full_path"
5. In the address bar, type "about:plugins", and look at the output. There should only be ONE section for flash. If you have more than 1, you must delete the duplicates through Nautilus or the Terminal. With full paths exposed, you can do the dirty work yourself and remove the npwrapper or libflashplayer.so file.

---

### Post by LaneLester on 2009-03-28
At least this thread shows me I'm not alone. I'm running Intrepid 64-bit and this is the only entry for plugins:
[INDENT]Shockwave Flash

    File name: /root/.mozilla/plugins/libflashplayer.so
    Shockwave Flash 10.0 d21

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes[/INDENT]
I have confirmed that the only instance is:
/root/.mozilla/plugins/libflashplayer.so
(I run as root)

And I still get firefox crashing the same as others do: on some flash sites, but not others.

Lane

---

### Post by VastOne on 2009-04-19
> **LaneLester said:**
> At least this thread shows me I'm not alone. I'm running Intrepid 64-bit and this is the only entry for plugins:
[INDENT]Shockwave Flash

    File name: /root/.mozilla/plugins/libflashplayer.so
    Shockwave Flash 10.0 d21

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes[/INDENT]
I have confirmed that the only instance is:
/root/.mozilla/plugins/libflashplayer.so
(I run as root)

And I still get firefox crashing the same as others do: on some flash sites, but not others.

Lane

Ditto for me here...

Brand new install (completely clean) and with only File name: libflashplayer.so Shockwave Flash 10.0 r22 (Adobe Alpha 64) running, I crash no matter what even when running firefox -profilemanager -no-remote to start a new profile.

This has been going on for months now and only on this machine (AMD 64 2 gig 2year old machine) but on a brand new HP quad core, I have no issues.  If it is hardware related, wouldn't we be seeing issues elsewhere?

Frustrating to no end....

Edit Upon further review it appears to be a hardware issue after all. I have a AMD 64 3400+ Family 15 that apparently has LAHF issues and it's all over the web about these known issues and I have as yet found a solution

VastOne

---

### Post by LaneLester on 2009-04-19
> **VastOne said:**
> Ditto for me here...

...
Frustrating to no end....

I just ran into another 64-bit dead end on a different issue. I've decided that 64-bits is more trouble than it's worth. I want an OS that works and with which all the apps work. I'm going back to 32 bits, and I hope I have sense enough to stay there.

Lane

---

### Post by stanca on 2009-04-26
Since when I added flashblock to firefox the crashes disappeared,but as an alternative I have opera browser too.
I added fasterfox addon too.:popcorn:

---

### Post by rukna on 2009-05-27
I ran into the same issue of Firefox crashing after upgrading my flash to 64 bit. I'm using Intrepid, BTW. 

After noticing so many users having issues with no solution in sight, I bit the bullet and manually removed the libflashplayer.so and re-installed the non-free flash plugin. Things are back to normal. The whole point of me upgrading to Adobe's Flash was to install Adobe Air (and then use some of the infamous Air apps), but I guess I'll wait until the Flash fix is out.

---

### Post by rhaces on 2009-06-17
I've been having this same issue for some weeks, it happened when I downloaded the 64 bit libflashplayer from the adobe labs. I had tried to install flash with apt-get install flashplugin-installer or with apt-get install flashplugin-nonfree but afther apt finished downloading the .tar.gz it sent an error of shsum and stuff. I just tried again today to download it with apt-get install flashplugin-nonfree and everything worked great. Have been browsing arround and no crash, think this is the solution

Cheers

---

### Post by rukna on 2009-06-17
I forgot to update this thread, but I got the flash 64 work on my browser, as well.

I think I removed the nswrapper and all instances of the flash plugin, including physically removing of it's directories and then simply copied the libflashplayer.so to my ~/.mozilla/plugins directory. YMMV

Out of curiousity, what does your about:plugin show for Flash?

Mine shows File name: /home/<myusername>/.mozilla/plugins/libflashplayer.so

---

### Post by rhaces on 2009-06-17
> **rukna said:**
> I forgot to update this thread, but I got the flash 64 work on my browser, as well.

I think I removed the nswrapper and all instances of the flash plugin, including physically removing of it's directories and then simply copied the libflashplayer.so to my ~/.mozilla/plugins directory. YMMV

Out of curiousity, what does your about:plugin show for Flash?

Mine shows File name: /home/<myusername>/.mozilla/plugins/libflashplayer.so

I did that, I erased everything, and still got the prob. the about:plugins also sayed just like your's. Now with the flashplugin-nonfree installed, my about:plugins is:

```
Shockwave Flash

    File name: /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r22

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```

---

### Post by Tails9 on 2009-09-10
I have the same problem. I'm on AMD64 2800+, running Flash 10.0 d20.

---

### Post by rukna on 2009-09-10
I know it works because I configured it again today. I was subscribing to Firefox's nightly releases which started giving me issues, and so I went back to the 3.5 stable release.

And to get Flash working, I downloaded the tar.gz for Flash 64 from Adobe, copied the .so to ${HOME}/.mozilla/plugins directory and fired it up with no problem.

Like before, "about:plugins" shows that it's loading the right .so

---

### Post by Anusiya on 2009-09-11
The fix was posted in Gentoo buglists. See [HTML]http://ubuntuforums.org/showthread.php?t=1263905[/HTML] Flash is working perfectly now. 

Thanks,
Anusiya

---

### Post by asaturn on 2009-10-06
my firefox still crashes.

I have the instruction set...

```
saturn@n500:~$ cat /proc/cpuinfo | grep lahf_lm
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm

```


and I tried the .C fix ... still didn't work. still crashes.

---

### Post by afeasfaerw23231233 on 2009-10-08
Wow! I've just found out this thread: [http://ubuntuforums.org/showthread.php?t=1263905](http://ubuntuforums.org/showthread.php?t=1263905)
It works perfectly after downloading flashplugin-lahf-fix.tar.gz and run the C. Problem solved.

to asaturn:
Why don't you post a question in that [thread]("http://ubuntuforums.org/showthread.php?t=1263905") ?

> **Anusiya said:**
> The fix was posted in Gentoo buglists. See [HTML]http://ubuntuforums.org/showthread.php?t=1263905[/HTML] Flash is working perfectly now. 

Thanks,
Anusiya

I was late :)

---

### Post by fabiomanzoni on 2009-10-08
> **afeasfaerw23231233 said:**
> Wow! I've just found out this thread: [http://ubuntuforums.org/showthread.php?t=1263905](http://ubuntuforums.org/showthread.php?t=1263905)
It works perfectly after downloading flashplugin-lahf-fix.tar.gz and run the C. Problem solved.

to asaturn:
Why don't you post a question in that [thread]("http://ubuntuforums.org/showthread.php?t=1263905") ?



I was late :)

I had the same problem. Installing the fix above fixed my firefox on gmail, newyorktimes, etc.
Thanks

---

### Post by afeasfaerw23231233 on 2009-10-08
[This sticky thread]("http://ubuntuforums.org/showthread.php?t=1259102") was 4 weeks ago. I forgot to check the main page of x64 for help.

---

