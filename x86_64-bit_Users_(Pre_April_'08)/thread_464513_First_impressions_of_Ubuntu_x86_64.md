---
title: "First impressions of Ubuntu x86_64"
date: 2007-06-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by scourge on 2007-06-04
I've been an Ubuntu user for a couple of years now, and got used to fixing problems, using the command line etc. I knew I'd be ready to try the 64-bit version on my new hardware.


1. Installation

On the first try the live cd didn't boot, apparently because of a bug in the 64-bit VESA graphics driver. Disabling the splash screen (using the "nosplash" boot option) solved the problem. After the boot the livecd and installation worked as expected.

2. First boot into the new Ubuntu install

Not surprisingly the VESA driver bug was still there and Ubuntu wouldn't start unless I disabled the splash screen. I changed /boot/grub/menu.lst to disable the splash for good, or until the next kernel upgrade.

My hardware was detected just like in the 32-bit version. Both cores of my Core 2 Duo were correctly utilized. I'd just have to configure xorg.conf so that I could use widescreen modes and install the restricted NVIDIA driver. My new graphics card is a GeForce 8800GTS, so I figured I'd need the nvidia-glx-new package instead of nvidia-glx which is suggested by the Restricted Drivers Manager. I installed it successfully, but X wouldn't start because of a missing NVIDIA module (wfb). I then searched these forums and found out that I'd have to install that module manually. Now it's finally working.

3. Installing apps/codecs

Just like the 32-bit version, Totem sent me to install the correct codecs when it couldn't play a media file. Installing w64codecs (as opposed to w32codecs in Ubuntu X86) took care of the rest (Mplayer and Kaffeine). Kaffeine's digital tv and Mplayer plugin worked without problems.

I thought I'd have a problem with the Flash plugin, but Kilz's nspluginwrapper script too care of everything painlessly. No reason to use the 32-bit Firefox. Skype was easy to install, thanks to a helpful Sticky post in this forum. Installing RealPlayer was identical to my previous experience on Ubuntu x86. Even Quake4 was almost as easy to install as before and worked perfectly.

4. Performance

The desktop doesn't really feel any more responsive than before, but some things seem to be faster. Compiling programs is definitely faster, and I think Gimp and Blender are as well. And then there's my own little chess program, Sloppy, which was part of the reason why I wanted to try Ubuntu x86_64. Sloppy uses 64-bit integers for board representation and keys in the hash table, so I expected it to run significantly faster. And it did, about 38% faster than the 32-bit version. I'd call that a pretty nice speedup.

5. Conclusion

I'm not going back to 32-bit. Getting everything to work took a bit more effort than before, but it was totally worth it. All the 32-bit binaries seem to run just fine, so I didn't lose anything, just gained some performance.

---

### Post by dmfield on 2007-06-08
here here, its just a little harder than the 32bit, but hey, thats why i love Linux.. However 64bit, could be the goose that lays the golden Egg for Linux, as 64bit vista is a complete waste of time... Ubuntu 64 is so much more usable

---

### Post by capecove on 2007-06-08
Excellent news. I'm a newbie but love working in Ubuntu and eliminating all that paid for software that doesn't really work so great afterall. I'm a convert. Thankfully my installation went off without a hitch. I can't wait for the newxt few years of my learning.

---

### Post by JAPrufrock on 2007-06-08
Feisty is my 3rd 64 bit Ubuntu OS.  It was the easiest install _by far_.  Who knows, maybe Ubuntu will win the battle of the 64 bit.

---

### Post by Cappy on 2007-06-09
> **JAPrufrock said:**
> Feisty is my 3rd 64 bit Ubuntu OS.  It was the easiest install _by far_.  Who knows, maybe Ubuntu will win the battle of the 64 bit.

Really, how so? I've never really used anything besides Ubuntu so I'm clueless!

---

### Post by scourge on 2007-06-09
I've now used this thing for a week, and I'm still happy. I should add to my first post that the NVIDIA problem apparently isn't specific to 64-bit Ubuntu, so 32-bit users will have to go through the same trouble if they have a GeForce 8800. The VESA driver bug however doesn't exists in the 32-bit version.

I also optimized my chess program a bit more for 64-bit (only changed two simple bit-fiddling functions), and am now getting a speedup of about 60% when compared to the 32-bit binary on a 32-bit OS. I'm pretty pleased with that result.

---

### Post by crjackson on 2007-06-09
> **scourge said:**
> I've now used this thing for a week, and I'm still happy. I should add to my first post that the NVIDIA problem apparently isn't specific to 64-bit Ubuntu, so 32-bit users will have to go through the same trouble if they have a GeForce 8800. The VESA driver bug however doesn't exists in the 32-bit version.

I also optimized my chess program a bit more for 64-bit (only changed two simple bit-fiddling functions), and am now getting a speedup of about 60% when compared to the 32-bit binary on a 32-bit OS. I'm pretty pleased with that result.

This is the post I've been waiting for to help me.  I too got bit (as well as many others) bit the VESA driver bug you referf to.  I managed to install by hitting the F4 key and chaging the resolution to 640x480 and it was smooth and quick.

Rebooting after install, I still had the black screen, so I boot into recovery mode and then exit to my desktop.  I KNOW NOTHING ABOUT LINUX OR GRUB...

Can you give me a quick post on how to permanentaly disable the splash to help me and MANY others.

I'll be sure to pass this information along to anyone else who needs it as well.  Heck, it may work out so well that it becomes a sticky...

Thank you so very much...:D

---

### Post by Cappy on 2007-06-09
Here is the fix:
```
sudo gedit /boot/grub/menu.lst
```

Scroll down past all the lines beginning with "#" and "##".

You'll see something like this:
```

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=Longnumber ro quiet splash
initrd		/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=Longnumber ro single
initrd		/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=Longnumber ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=Longnumber ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

```

Take out the words that say "splash". If you added a "VGA=whatever" line take it out too.
It should look like this:
```

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=Longnumber ro quiet
initrd		/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=Longnumber ro single
initrd		/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=Longnumber ro quiet
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=Longnumber ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

```

Now save the file.
DO NOT COPY AND PASTE ANY LINE FROM THIS POST; ONLY REMOVE THE WORD "splash".
Good luck

---

### Post by crjackson on 2007-06-09
Great!  I'll be doing this tonight after I get home from work.  I'm 99.9% confident this will solve the issue for me.

If it does, I'll be looking for 'KILZ' plugin wrapper script for flash, and installing wine.

I anticipate total success, and elimination of x86 Feisty in favor of A64.

Thanks a billion...:D

---

### Post by scourge on 2007-06-09
> **Cappy said:**
> Here is the fix:
```
sudo gedit /boot/grub/menu.lst
```

Can't use gedit in recovery mode. "sudo nano /boot/grub/menu.lst" works outside of X too.


> Take out the words that say "splash".

Yeah, or replace every instance of "splash" with "nosplash".

It's also possible to edit the boot options while in Grub by pressing the 'e' key. That won't be a permanent change though... Well, actually editing menu.lst isn't permanent either: as soon as you install/update a kernel the changes are gone.

---

### Post by Cappy on 2007-06-09
Oops, I thought he was able to get to X!

On the GRUB menu pick the option with "(recovery mode)".
Like scourge said,
```
nano /boot/grub/menu.lst
```
You don't need to use "sudo" while in recovery mode.

Once you are done making the changes use Control + O to save it. Then use Control + X to exit nano.
Then you can just do
```
reboot
```
and it should work!

---

### Post by crjackson on 2007-06-09
It worked.  Now it just boots up and shows me all the text while loading.

This is a minor thing, is there anyway to hide the loading text also?

BTW...  BIG THANKS...  I'll get my flash / wine issues squared away and back up my image...

Man this is great...

Thanks again...:D

---

### Post by JAPrufrock on 2007-06-09
> **Cappy said:**
> Really, how so? I've never really used anything besides Ubuntu so I'm clueless!

I meant that I've used Dapper, Edgy and Feisty 64 bit OSs (all 64 bit).  Feisty was super easy to install and configure compared to Dapper or Edgy.  Regarding the battle of the 64 bit OS, look at  [this]("http://www.catb.org/~esr/writings/world-domination/world-domination-201.html").

---

### Post by scourge on 2007-06-10
> **crjackson said:**
> It worked.  Now it just boots up and shows me all the text while loading.

Great to hear that.

> This is a minor thing, is there anyway to hide the loading text also?

I thought the "quiet" option would do that, but doesn't seem so. Anyway, the vesa bug is a known one, it's critical, and it's not in a restricted driver, so I expect it to be fixed soon.


> BTW...  BIG THANKS...  I'll get my flash / wine issues squared away and back up my image...

Man this is great...

Thanks again...:D

I can recommend Kilz's script for installing Flash for the 64-bit Firefox. Couldn't be easier. And there are 64-bit packages of wine [here]("http://wine.budgetdedicated.com/archive/index.html").

---

### Post by crjackson on 2007-06-10
Installed the flash, works like a charm.  It shoud be in a sticky.  So many people having trouble and it's just a click away to fix it.

I'll be having some wine later today, righ now I stuck in windows again for video processing.  Once that's done, I be having another cup of ubuntu and chasing it with wine...

---

### Post by Magneto on 2007-06-12
If only your post had links to the nvidia solution :) 
I spent all day back and forth with 64bit and 32 bit installs and they all failed or came up buggy. So I was going to go to debian etch but that ended when text field usage in gnome caused x to crash :(. But installing Deb today refreshed my memory since I hadnt used linux in months and I came up with the same grub resolution fix as someone else posted.  That made my ubuntu installs nicer but the gui install stil is slow as hell on my dual core intel box with 2gb of ram. 
Then I just used automatix and a bunch of xorg backups to be able to post this while looking for the wfb module fix for nvidia :lol: 
Anyway its good to be back and this seems alot more functional a 64bit os than vista, xp or deb amd64 etch. 

Do folks have something against automatix2? see alot of info on installing codecs but rarely involving it

---

### Post by crjackson on 2007-06-12
> **Magneto said:**
> Do folks have something against automatix2? see alot of info on installing codecs but rarely involving it

Some folks seem to swear by it, other think it's El Diablo.  I can only suggest you try it and see.  I personally haven't but probably will.  Just so I can see for myself.  If it jacks anythijng up, all I have to do is restore my drive image.

---

### Post by Magneto on 2007-06-13
> **crjackson said:**
> Some folks seem to swear by it, other think it's El Diablo.  I can only suggest you try it and see.  I personally haven't but probably will.  Just so I can see for myself.  If it jacks anythijng up, all I have to do is restore my drive image.
I have used it in the past and again today. Im just not up on the latest ubuntu trends :lol: 
IMO it was kinda worth it - swiftfox works and so does mplayer but nvidia drivers didnt and the install process died on me a few times while setting up fonts. 

My only problem now are firefox and gnome lockups. Gnome locks up and I have to alt+tab to get back the ability to interact with windows and toolbars. And firefox will freeze if I try to use the customize feature too much and this will also lock up Gnome. I have to go to a terminal to kill firefox and then all is fine again. Weird. Weird keyboard repeating too. But nothing too broken 
Is that an angry ferret?

---

### Post by Cappy on 2007-06-13
Here is your Alt+Tab problem:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/41301](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/41301)

I have it too.

---

### Post by Kilz on 2007-06-13
> **crjackson said:**
> Some folks seem to swear by it, other think it's El Diablo.  I can only suggest you try it and see.  I personally haven't but probably will.  Just so I can see for myself.  If it jacks anythijng up, all I have to do is restore my drive image.

The thing some people dont like about automatix is that it installs a lot of proprietary applications on your system. Things like Swiftfox and codecs that you may not want on your system.
A lot of new Ubuntu users come from Windows and dont seem to realize why this is a bad thing, hence Automatix's popularity. But if you think about it, one of the best things about Linux is that its free (as in freedom). A lot of people have worked hard so that you have a free operating system. I personally dont think installing proprietary applications is a good thing, it sends the wrong message that its ok.
Granted there are some bits of software that are proprietary and cant be replaced by free software. An example of this is the video drivers for a lot of cards. But IMHO linux users should choose free software where they can over proprietary applications.
Again Swiftfox is a good example. Its a non free application that is built from free code because of a loophole in the MPL. There are plenty of other choices that are free (Swiftweasel, Firefox, Iceweasel, Flock). IMHO we should use and support them over the non free.
Automatix gives limited info about the freedom of the applications it installs, dose it fast, and throws in everything but the kitchen sink. It also cheats new users out of knowledge. None of the things it installs are impossible to install. A new user fires it up, and it does all the work for them. But they dont learn anything. Sadly if something goes wrong (and dont think it never does) the new user is left without the knowledge that might help solve the problem.

---

### Post by Magneto on 2007-06-13
> **Kilz said:**
> The thing some people dont like about automatix is that it installs a lot of proprietary applications on your system. Things like Swiftfox and codecs that you may not want on your system.
A lot of new Ubuntu users come from Windows and dont seem to realize why this is a bad thing, hence Automatix's popularity. But if you think about it, one of the best things about Linux is that its free (as in freedom). A lot of people have worked hard so that you have a free operating system. I personally dont think installing proprietary applications is a good thing, it sends the wrong message that its ok.
Granted there are some bits of software that are proprietary and cant be replaced by free software. An example of this is the video drivers for a lot of cards. But IMHO linux users should choose free software where they can over proprietary applications.
Again Swiftfox is a good example. Its a non free application that is built from free code because of a loophole in the MPL. There are plenty of other choices that are free (Swiftweasel, Firefox, Iceweasel, Flock). IMHO we should use and support them over the non free.
Automatix gives limited info about the freedom of the applications it installs, dose it fast, and throws in everything but the kitchen sink. It also cheats new users out of knowledge. None of the things it installs are impossible to install. A new user fires it up, and it does all the work for them. But they dont learn anything. Sadly if something goes wrong (and dont think it never does) the new user is left without the knowledge that might help solve the problem.
As a 9yr user of Linux and someone who values their time I'd rather use non-free apps and codecs that work now than spend hours searching for politically correct solutions. For me firefox is buggy and with my debian experiences with iceweasel I wont touch it but swiftfox works, so I use it. I hated it before and hadn't used it in a long while but things change.
The entire reason I stopped using Ubuntu as my primary system was because of the time and effort involved versus other operating systems(non-linux). I couldn't justify it to myself. 
Although its nice that we may want other people to learn about linux and its inner workings that is not what most people want. Most people want to press power and have everything work. Those people are the reason why there is an IT Support industry. 


[quote=Cappy]
Here is your Alt+Tab problem:
[https://bugs.launchpad.net/ubuntu/+s....20/+bug/41301](https://bugs.launchpad.net/ubuntu/+s....20/+bug/41301)

I have it too.[/quote]

Thanks! there seem to be some workarounds/fixes I can try out.

---

### Post by Kilz on 2007-06-13
> **Magneto said:**
> As a 9yr user of Linux and someone who values their time I'd rather use non-free apps and codecs that work now than spend hours searching for politically correct solutions. For me firefox is buggy and with my debian experiences with iceweasel I wont touch it but swiftfox works, so I use it. I hated it before and hadn't used it in a long while but things change.
The entire reason I stopped using Ubuntu as my primary system was because of the time and effort involved versus other operating systems(non-linux). I couldn't justify it to myself. 
Although its nice that we may want other people to learn about linux and its inner workings that is not what most people want. Most people want to press power and have everything work. Those people are the reason why there is an IT Support industry. 


Thats strange, since Swiftfox is just a build of the Firefox code , with a few about:config settings turned on. The patches on the Swiftfox site prove this to be true. I addressed that some things may have to be proprietary. Swiftfox isnt one of them. It is so unfree that it cant be added to a distro's repositories. You cant give it to someone. Something you can do with the application its based on and the code its built from.
Part of getting something free in cost is spending time looking and doing things. Free isnt just about cost, but about the freedoms the application or code has. That you want to have everything "just work" says loads. Why not just use Windows? You wont have to look for a thing, it will be full of proprietary applications. You should be happy with that right?
Sadly we have more "users" with the an eye towards "using" with no care of what was given to them or care that its free. They are willing to trade freedom for convenience. I wonder if it was convenient for those who gave of their time so that you could have the free operating system?

---

### Post by Cappy on 2007-06-13
I personally use Skype because it's cross-platform. I tried open source SIP apps and it sounded utterly horrible on both ends (Windows to Linux). Oddly, I've seen posts on the Skype forums saying "how inferior skype sound quality is to SIP".

Eurodance di.fm time?
```

totem http://64.236.98.50:80/stream/1024

```

---

### Post by FloSynergy on 2007-06-17
hi folks,

i've just bought a new box since my old asus laptop just doen't cut the mustard any more - gotta run some hectic graphics now.

so i reckoned i may as well get something that's close to top of the range:
NF61S Micro AM2 Biostar Mainboard
AMD Athlon 64 x2
2Gb Ram
80Gb Samsung IDE HDD

tried to install from 2 boot cd's : 6.06 for AMD 64.

Since that (two days ago) I have been battling.
If I allow the cd to move to default installation, it gets stuck right at the beginning of the splash page. (it displays, but there is no movement at all).
If i specify acpi=off or noacpi, it pauses briefly, trying to check out the hdd, then starts loading up from disc. It does all this fine, but then bombs out fairly close to the end, chucking me into a garish blue screen which tells me that x-server has failed to start.

on reading the relevant log, i am told that there is no screen - no device.

this leaves me in text-mode, and the installation does not progress at all.

how shall i continue?

thanks,

looking forward to your help,

flo

---

### Post by Cappy on 2007-06-17
Try boot parameter "nosplash" instead.

eurodance di.fm time?

---

### Post by w3bu53r on 2007-06-18
> **scourge said:**
> I've been an Ubuntu user for a couple of years now, and got used to fixing problems, using the command line etc. I knew I'd be ready to try the 64-bit version on my new hardware.


1. Installation

On the first try the live cd didn't boot, apparently because of a bug in the 64-bit VESA graphics driver. Disabling the splash screen (using the "nosplash" boot option) solved the problem. After the boot the livecd and installation worked as expected.
.
No wonder what I had was blank screen, I thought Ubuntu gypped me again because my Gentoo & Sabayon Live boot fine with splash screen.

---

### Post by FloSynergy on 2007-06-19
ok,

i chopped out the boot option section referring to the splash page, and added apci=off - this sorted the issue out - i managed to get ubuntu to install - kinda.:(

now i have a different issue - ubuntu does not seem to recognise the mainboard properly.

i've posted more detail [here,]("http://ubuntuforums.org/showthread.php?p=2872181#post2872181") but if anyone here has any useful ideas, please lemme know.

thanks, be well,

Flo

---

