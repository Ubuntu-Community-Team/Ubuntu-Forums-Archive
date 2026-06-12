---
title: "Need some serious help..."
date: 2004-12-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by tranceConscious on 2004-12-15
Hello all.
I'm new in the Ubuntu community and I need some help.

I'm not new to linux. On the contrary I've been playing with it since the first versions of slackware back in the late 80's early 90's. And I say playing cause I never used it seriously. I just liked the adventure of installing and configuring everything until I got the system working with X.
Lately I've tried out many distros [debian, knoppix, knoppel, gnoppix, gentoo] and finally I decided to keep ubuntu as my secondary OS cause it's just plain and simply great. I primarily use windows xp only because I produce music with cubase, so i cannot make a full move to linux until I find something similar with cubase to work. Anyway...

Recently I bought an ASUS A8V Deluxe mobo, and an Amd64 3500+ [939].
I also have and adaptec ultra 160 scsi card with a hp/compaq dlt vs80 and
for my sounds I have disabled the onboard sound card to use my ESI [ego systems] Waveterminal 192l.

I installed ubuntu 64 with all the defaults.

Now for the questions...

1) When I boot i get  this error message:

modprobe: FATAL: Error inserting aic79xx (/lib/modules/...../aic79xx.ko) No such device.

How do I get rid of that?

2) How do I enable my sound card? I've heard there is support for it in alsa. How do I configure alsa?

3) How do I enable my onboard Promise Raid controller???

4) I think all of the above answers have to do with kernel configuration, right? So, I'm using the default kernel (amd64-generic). I've seen some kernel named amd64-k8. Is that kernel better for my CPU? And If yes how do I install that kernel instead?

5) I need to connect to my RAS server at work with callback. Is there a dial-up tool that can work for such a connection?

6) I've found a music production program called wired. I have downloaded the sources for it. What is the procedure for compiling it. (It says nothing at the readme file)

Sorry if I 'm being tireing ....

But please support me... I want to get rid of microsoft from my system.... :grin:

---

### Post by Newbie on 2004-12-21
I am in the same boat except that I am just looking into linux as I am sick of windows. I have an Athlon, so I'm not sure which version would be best. I would prefer one that is as user-friendly as possible (I am used to MS products which do everything for you) If someone could help me out with a few suggestions, and perhaps warnings on what I am getting myself into I would really appreciate it.

Thanks in advance

---

### Post by ahyden on 2004-12-27
[QUOTE=tranceConscious]Hello all.
I'm new in the Ubuntu community and I need some help.
[/QUOTE]

Hey, I'm also new here but I've been playing around with Linux for some time so I will try to answer some of the questions :)

[QUOTE=tranceConscious]
1) When I boot i get  this error message:

modprobe: FATAL: Error inserting aic79xx (/lib/modules/...../aic79xx.ko) No such device.

How do I get rid of that?
[/QUOTE]

If it's a module you don't need, and don't want the system to load it, you should be able to find it in /etc/modules (without the .ko). Remove that line and ubuntu will not try to load it again.

[QUOTE=tranceConscious]
2) How do I enable my sound card? I've heard there is support for it in alsa. How do I configure alsa?

3) How do I enable my onboard Promise Raid controller???

4) I think all of the above answers have to do with kernel configuration, right? So, I'm using the default kernel (amd64-generic). I've seen some kernel named amd64-k8. Is that kernel better for my CPU? And If yes how do I install that kernel instead?

5) I need to connect to my RAS server at work with callback. Is there a dial-up tool that can work for such a connection?
[/QUOTE]

If your sound card isn't enabled by default it probably wasn't found. If you know the name of the right module for your card you can load it manually with:
sudo modprobe module

I don't know about amd64-k8, but you can try it by install it:
sudo apt-get install linux-amd64-k8
it will be added to your startup boot menu

sorry I don't know much about this

[QUOTE=tranceConscious]
6) I've found a music production program called wired. I have downloaded the sources for it. What is the procedure for compiling it. (It says nothing at the readme file)
[/QUOTE]
This is the usual procedure for compiling something:
./configure
make
sudo make install

You will probably get errors when running ./configure, because you need development libraries. You have to install these with apt-get install. It may be hard to tell which ones you need if you're not experienced with this.

[QUOTE=tranceConscious]
Sorry if I 'm being tireing ....

But please support me... I want to get rid of microsoft from my system.... :grin:[/QUOTE]

I know it wasn't much help but I hope it's better than nothing :)
Maybe someone more experienced here on the board can help?

---

### Post by Dylanby on 2004-12-27
Well I'm also a newbie. But my new computer is an AMD64 3200 (939) & I'm running the *-k8 kernel.

I *think* I read somewhere that to compile packages you should install the "build-essential" package & to track those packages you could install "check-install".

But I'm not sure that this is the "Debian" (Ubuntu) way, if that's important to you.
I'm also interested in this too (haven't had time to look into it to deep). Perhaps some guru can chime in? I know there's a way to build a quick .deb from source & install it with dpkg so that it integrates better with your system.

---

### Post by leech on 2004-12-27
> **tranceConscious]Hello all.
I'm new in the Ubuntu community and I need some help.

I installed ubuntu 64 with all the defaults.

Now for the questions...

1) When I boot i get  this error message:

modprobe: FATAL: Error inserting aic79xx (/lib/modules/...../aic79xx.ko) No such device.

How do I get rid of that?

[/QUOTE]
Actually, it won't be in the /etc/modules.  What you need to do is modify /etc/hotplug/blacklist.  Simply add 'aic79xx' to one of the lines there.  The reason it doesn't load that, is becaues the initial ramdisk loads it up (otherwise your linux kernel wouldn't be able to know your scsi devices are there.)

> 2) How do I enable my sound card? I've heard there is support for it in alsa. How do I configure alsa?


Try running 'sndconfig'  according to this page said:**
> http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Ego_Sys#matrix[/url] there isn't a driver written for your card yet.  Though I seem to recall there being a generic Envy24HT driver...  sndconfig would find it if it can...

> 3) How do I enable my onboard Promise Raid controller???


I would think that the Promise Controller (if enabled in the bios) would be detected by the hotplug scripts.  Not sure though.  Since I'm using SCSI (as it you are as well) I haven't bothered installing anything on the Promise Raid Controller that comes with the motherboard.

[QUOTE]
Sorry if I 'm being tireing ....

But please support me... I want to get rid of microsoft from my system.... :grin:

Hey, that's what the community is for.  I help someone, someone helps me, someone helps someone else.  It all works out in the end.  Some of us have been using linux for years (I've been using it since about '97).  And others are just starting to go to it due to being sick of Microsoft.  But we all started somewhere.  Welcome to the 'club'.

Leech

---

### Post by leech on 2004-12-27
Update, just found that if you do a 'sudo modprobe snd-ice1724' you should have sound.  If that works, then I'd put 'snd-ice1724' into your /etc/modules so that it'll load up on start.  I'm not sure why Alsa isn't detecting it right away.  

Looks like it's supported from at least 1.03 and up of ALSA.  Not sure what comes with Warty.

Leech

---

### Post by tranceConscious on 2005-03-03
Thanx for the help...

I'll check out all the feedback I got from you guys and post what I managed to do or not.

---

### Post by gratefulfrog on 2005-03-06
sorry to step in so late in the conversation, but I have the same hardware and can tell you its a long battle to get the sound to work.  In may opinion, all those things mentioned above are off target; Wary sound should work fine with your hardware, but your BIOS options may need looking at. I would start there if you have strange errors like the ones you mention. 

Also, be sure that everything is up to date.

Finally, you could give up like me and move on to a Hoary distribution with the hope that something will work better! It did in my case, with a lot of struggling and lots of help from the Ubuntu team (if you file a bug report on Bugzilla, they reply fast and are very helpful!)

Last thing you could do to see if Wary has a chance of working with sound is to try to run the live CD, just as an experiment; This worked perfectly on my ASUS A8V devlus AMD64 3000+ 939 pin, even the front panel mic+headhones worked, although I've never been able to get it to work on any other distribution!

---

### Post by tranceConscious on 2005-03-07
Well I don't want to make the onboard sound to work. I want to make my waveterminal 192l soundcard to work.

And by the way. 

What is Hoary and where do I get it???

---

### Post by kubla on 2005-03-07
[QUOTE=tranceConscious]
And by the way. 

What is Hoary and where do I get it???[/QUOTE]

Hoary is the "unstable" branch of ubuntu, roughly equivelant to Debian's Sid.

To get it, edit your /etc/apt/sources file and change all instances of "warty" to "hoary".

Then, from the command-line:

sudo apt-get update

then:

sudo apt-get dist-upgrade

Ian

ps. I really suggest you read a bit more of the forums though. This is a subject that has been covered many, many times.

---

### Post by GingerMegs on 2005-03-15
Hello,

you might try the following link to start with:
[http://channels.lockergnome.com/linux/archives/20020213_configuring_multimedia_apps.phtml](http://channels.lockergnome.com/linux/archives/20020213_configuring_multimedia_apps.phtml)

---

