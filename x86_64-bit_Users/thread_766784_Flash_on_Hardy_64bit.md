---
title: "Flash on Hardy 64bit"
date: 2008-04-25
forum: x86 64-bit Users
---

### Post by ronb94 on 2008-04-25
Hello
I don't have flash on firefox 3b5 in ubuntu 8.04 64bit.
"flashnon-free" already installed" I tried with nspluginwrapper but its not working too.(nspluginwrapper was installed before and warked with firefox but after upgrade to ubuntu 8.04 flash is not working).

---

### Post by fogcat on 2008-04-25
Did you look into the sticky about flash on 64Bit?  I have flash just fine.  Hope you find what you are looking for.

fogcat

---

### Post by MrGyswer on 2008-04-25
I am also having this problem

---

### Post by slowcoach on 2008-04-25
Give swfdec a try, works well for me with Lenny 64bit.

---

### Post by old_geekster on 2008-04-25
I am using "ia32-sun-java6-bin".  I also installed "ia32-libs".  This is the ia32 shared libraries for AMD64 and ia64 systems.  You can find them in "Synaptic".  I can't get flash to work with any of the 64-bit versions.

---

### Post by tjwoosta on 2008-04-25
i have just installed swfdec on hardy 64bit and it works fine for most flash like watching youtube and stuff but for some reason flash objects dont autoplay (i need to click on stuff to make it show up)

also i cant access any chatrooms that require flash!

has anyone had any luck with flash-nonfree or gnash in 64bit?
(i havn't tried yet)

i had some problems making flash work in gutsy and was told to install the 32bit firefox within 64bit ubuntu but i decided to keep searching and eventually i found a working (patched) flash, so im hoping the same will be true in hardy.

also how would i uninstall swfdec ?
(i installed it from the popup bar that shows up in firefox at the top)

---

### Post by cmdrtebok on 2008-04-27
I was wondering how one would uninstall swfdec as well. I'm still having problems running flash. It sounds just like what the previous poster was describing At first it wouldn't work at all but then i installed swfdec with the banner popup and now it works maybe 3/4 of the time.

Youtube works but collegehumor videos don't (I mean maybe its better that I can't view that anymore...) 

 I want to try exactly what they have on the sticky but I should probably start with a clean slate right?

---

### Post by vishalrao on 2008-04-28
To get Flash on Hardy amd64, I just visited a Flash-enabled page in Firefox where it asked to install the plugin and I clicked that (might have also clicked allow popup/install), I believe Ubuntu's FF plugin takes care of installing your choice of Adobe Flash or one of the other Free versions via the apt machinery... works fine for me.

---

### Post by jespdj on 2008-04-28
> **old_geekster said:**
> I am using "ia32-sun-java6-bin".  I also installed "ia32-libs".  This is the ia32 shared libraries for AMD64 and ia64 systems.  You can find them in "Synaptic".  I can't get flash to work with any of the 64-bit versions.
ia32-sun-java6-bin is the 32-bit version of Sun Java 6, which does not have anything to do with Flash. Installing 32-bit Java or other 32-bit libraries will not make Flash work in your 64-bit browser.

Just install the package **flashplugin-nonfree**. On 64-bit Ubuntu, this will automatically install nspluginwrapper and other necessary 32-bit stuff to make Flash work in 64-bit Firefox.

---

### Post by tjwoosta on 2008-04-29
if you see grey boxes that you have to click on to make them play, it is because you have the swfdec player instead of the prefered flashplugin-nonfree

to remove the swfdec player do this
```
sudo apt-get purge swfdec-mozilla
```
then install the working flashplayer like this
```
sudo apt-get install flashplugin-nonfree
```

this works on hardy 64 bit fine, no need to install any 32 bit java or librarys or anything

---

### Post by cmdrtebok on 2008-04-29
I have the flash nonfree, not the swfdec. Most of the time flash works however 3 times already today it just decides to stop. Twice was plain grey boxes with no arrow in it and once all sound just didn't feel like initializing. Is anyone else having this problem? Could this be a conflict from my previous failed attempts at installing flash?

---

### Post by Mr.Clark on 2008-04-29
> **jespdj said:**
> Just install the package **flashplugin-nonfree**. On 64-bit Ubuntu, this will automatically install nspluginwrapper and other necessary 32-bit stuff to make Flash work in 64-bit Firefox.I've done this, and it all worked fine, except that the BBC iPlayer quality is dire... I've watched it on the same machine in Windows just fine, so it's obviously a setting here somewhere... are there any options for flashplugin-nonfree that I can look at?

---

### Post by gigabz666 on 2008-04-29
> **tjwoosta said:**
> i have just installed swfdec on hardy 64bit and it works fine for most flash like watching youtube and stuff but for some reason flash objects dont autoplay (i need to click on stuff to make it show up)

also i cant access any chatrooms that require flash!

has anyone had any luck with flash-nonfree or gnash in 64bit?
(i havn't tried yet)

i had some problems making flash work in gutsy and was told to install the 32bit firefox within 64bit ubuntu but i decided to keep searching and eventually i found a working (patched) flash, so im hoping the same will be true in hardy.

also how would i uninstall swfdec ?
(i installed it from the popup bar that shows up in firefox at the top)

This is frustrating, I have had the exact same problem as you with not being able to access chatrooms. Those chatrooms I know work because I've accessed them with the same distribution but in 32 bit on my laptop. My upgrades were slightly different so I wondered if there was a mix up with some personal settings in my home partition.

With my 64 bit set up I used the CD to format the root partition and install kubuntu 8.04 64 bit. On my laptop I just did the version upgrade from the adept manager. So I wondered if maybe someone wasn't updated in my /home with the fresh install. How did you upgrade to Hardy? Might be able to at least rule out that.

---

### Post by tjwoosta on 2008-04-29
> How did you upgrade to Hardy? Might be able to at least rule out that. 
i upgraded to hardy the safe way (i partitioned my harddrive and put hardy beside gutsy)

that way if something went wrong with hardy i could fall back to gutsy

but like i said in my last post i fixed the problems i was having with flash by simply removing swfdec player and installing the traditional flashplugin-nonfree
(my flash now works perfectly for every site ive been to)

---

### Post by gigabz666 on 2008-04-30
> **tjwoosta said:**
> 
but like i said in my last post i fixed the problems i was having with flash by simply removing swfdec player and installing the traditional flashplugin-nonfree
(my flash now works perfectly for every site ive been to)

I didn't have swfdec player installed. I used the flashplugin-nonfree package straight away, youtube and videos at gamespot which use flash work perfectly, but any chat room at userplane I can't get into. The new window opens and it says connecting constantly. If I didn't have flash at all, it would ask me to install the flash player, but it doesn't do that. However I still can't get into a room cause it just states connecting. On my laptop I get into the room perfectly, and I was able to before in Gutsy. It's weird. Do you use userplane? If not, do you mind trying? 

[http://http://www.userplane.com/directory/index.cfm?action=domain.home]("http://http://www.userplane.com/directory/index.cfm?action=domain.home")
You can try any of those, they all give the same result, just constantly says connecting.

---

### Post by beast-usa on 2008-04-30
> **tjwoosta said:**
> i have just installed swfdec on hardy 64bit and it works fine for most flash like watching youtube and stuff but for some reason flash objects dont autoplay (i need to click on stuff to make it show up)

also i cant access any chatrooms that require flash!

has anyone had any luck with flash-nonfree or gnash in 64bit?
(i havn't tried yet)

i had some problems making flash work in gutsy and was told to install the 32bit firefox within 64bit ubuntu but i decided to keep searching and eventually i found a working (patched) flash, so im hoping the same will be true in hardy.

also how would i uninstall swfdec ?
(i installed it from the popup bar that shows up in firefox at the top)

Add & remove (first thing on the list under applications)
Add & remove has tons of toys LOL
will un-install your flash ......but it won't get rid of that flash block, I installed that playing on one of my laptops. I have installed & un-installed that thing a dozen times
and it still locks the flash files until you click on it.

---

### Post by Abdujaparov on 2008-04-30
Hi everyone,
I've installed correctly the plug-in flash non free and it works correctly but if I restart or if I launch another session the plug-in doesn't work anymore but I reinstall the plug-in it restart to work correctly?
Why this behaviour?
How can I solve?
Thanks, bye bye.

---

### Post by tjwoosta on 2008-04-30
> 
Add & remove (first thing on the list under applications)
Add & remove has tons of toys LOL
will un-install your flash ......but it won't get rid of that flash block, I installed that playing on one of my laptops. I have installed & un-installed that thing a dozen times
and it still locks the flash files until you click on it.


i also tried using the add/remove feature to remove the swfdec player but it did not work correctly

the more reliable way to do it would be to go to the menu System-Administration-Synaptic Package Manager  (just click search and put whatever your looking for)

this method does the same thing as the commands i said earlier  except with a GUI (not as fancy as add/remove but there are more options, like complete-removal)

also usually there are things that dont even show up in the add/remove list but you can find them in synaptic no-prob

---

### Post by jamesford on 2008-04-30
it keeps dying on me too, works fine for a while then i just get grey where theres supposed to be flash

---

### Post by pingpongboss on 2008-04-30
> **cmdrtebok said:**
> I have the flash nonfree, not the swfdec. Most of the time flash works however 3 times already today it just decides to stop. Twice was plain grey boxes with no arrow in it and once all sound just didn't feel like initializing. Is anyone else having this problem? Could this be a conflict from my previous failed attempts at installing flash?

exactly the issues i'm also seeing. Flash video sites like youtube also tend to crash firefox very very often.

---

### Post by greglaun on 2008-05-29
gigabz666, I had the same problem with userplane.  It seems to have gone away after I blacklisted the ipv6 module in /etc/modprobe.d/blacklist

---

### Post by doorknob60 on 2008-05-29
I recommend everyone that's having problems to go get Flash Player 10 Beta and install it using the instructions from the sticky, Flash 9 has problems on both 64 bit and 32 bit machines of mine, but I don't seem to have any problems with Flash 10.

---

### Post by PorcelainMouse on 2008-06-12
tjwoosta is right.  That was my problem, too, almost.

I didn't notice that swfdec-mozilla was an alternate SFW player, but I had Gnash installed (another free SFW player) and it was preventing the Adobe SFW plug-in from working. Gnash was an active plug-in in Firefox, but Adobe's would show up after successful installation.

Some details: This configuration mistake involves the "Debian alternatives system."  It is an abstraction layer that allows mutiple software packages to be installed simultaneously that provide the same features and let's front-end programs call them without having to know which ones are installed.  [See update-alternatives manual page]  A post on launchpad.net really helped explain everything.

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/195422/comments/29](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/195422/comments/29)

It pointed me to the 'update-alternatives' command, which you can use to see which command or utility is being used by the alternatives system.

Before, when the adobe player wasint' working (only gnash was availible in firefox), here's what I saw:
$ update-alternatives --list xulrunner-addons-flashplugin
/usr/lib/gnash/libgnashplugin.so
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so
$ update-alternatives --display xulrunner-addons-flashplugin
xulrunner-addons-flashplugin - status is auto.
 link currently points to /usr/lib/gnash/libgnashplugin.so
/usr/lib/gnash/libgnashplugin.so - priority 50
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so - priority 50
Current `best' version is /usr/lib/gnash/libgnashplugin.so.

Which completely explains what was happening.  After uninstalling (purge) Gnash, I see this:
$ update-alternatives --list xulrunner-addons-flashplugin
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so
$ [pdestefa@sml-116-6634 firefox 10:11]$ update-alternatives --display xulrunner-addons-flashplugin
xulrunner-addons-flashplugin - status is auto.
 link currently points to /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so - priority 50
Current `best' version is /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so.

Now, the Adobe player is active.  I assumed that since Firefox 3 let me disable Gnash, it would handle multiple plug-ins for the same MIME type, but the Debian alternates system hides "conflicting" back-ends for some software capabilities.

---

### Post by Yellow Pasque on 2008-06-12
I wouldn't suggest that most users run the beta. In fact, the most stable version seems to be 9.0r48. Again, please see Kilz's Flash guide at the sticky section of this forum.

---

