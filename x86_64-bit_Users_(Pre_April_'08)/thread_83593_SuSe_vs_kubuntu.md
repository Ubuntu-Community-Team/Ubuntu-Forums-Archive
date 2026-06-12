---
title: "SuSe vs kubuntu"
date: 2005-10-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by peanut butter on 2005-10-29
i not sorecentaly came from SuSe and have a few questions.

1.is there a configuration like YAST (you canfind it in wikkipedia) or install yast on kubuntu?:smile: 

2. how do you upgrade when anothe version comesout(had to format and do a clean install last time)?

3.can i install 32 bit packages such as ndiswrapper (they dont seem to have 64 bit debs) on kubuntu (i could do this on SuSe but cant figure out on kubuntu)?

4. why is kubuntu better than SuSe?


ps.i am getting tiered of not having yast. Yast was soo easy.:confused:

---

### Post by adwait on 2005-10-29
1)Well there is no EXACT equivalent of yast in Kubuntu. For installing and removing packages you can use adept/kynaptic/synaptic. For all other administration activities, start Konqueror and then click settings on the default home page.
2)When a new version comes out, you can edit the file /etc/apt/sources.list and change the name from old version to new version and then run
```
sudo apt-get update
sudo apt-get dist-upgrade
```
3)I think so.........not very sure though
4)You're the one who's used both..........you tell me.......

---

### Post by manicka on 2005-10-29
Interestingly Yast is the reason I moved away from SuSE. I like the way the different control panels are set out in ubuntu/kubuntu.

Upgrade can be done with Synaptic or with apt in a terminal

sudo apt-get update
sudo apt-get dist-upgrade

after changing the sources in /etc/apt/sources.list to match the new version. e.g to upgrade recently from hoary to breezy you would have changed all the references of hoary in the sources list to breezy, then run the above commands..... nice and simple :)

Not sure about the ndiswrapper question

Why is it better. In all I find Ubuntu a bit slicker and less bloated than SuSE, but SuSE is a fine distro to. I particularly like the SUPER releases.

---

### Post by peanut butter on 2005-10-29
the reason i liked yast was it was easy to use and everything was there in oneplace. inubuntu icouldent find a lot of config tools for GRUB etc (i checked out Grime but it wont let you change the stuff around.

---

### Post by manicka on 2005-10-29
Ubuntu is a bit more hands on than SuSE when configuring some things like Grub. I like it that way, others don't and choose flavours of Linux to suit their needs. If you were happy with SuSE then why not use it. The main thing is that you're using Linux :)

---

### Post by peanut butter on 2005-10-30
the reason i dont use suse is because i have 9.0 and it is too old. and i am too lazy to download 6 cds for 10.0
and i likehow big ubuntu is on my harddrive giving it a10 gb partion and Windows a 30 gb because its soo big

---

### Post by manicka on 2005-10-30
You could try SuSE SUPER which is a 1 cd version of SuSE that uses apt/synaptic to add extra packages. Quite similar to Ubuntu  in concept.

---

### Post by LittleReinhart on 2005-11-01
Hey,

When I switched over to linux half a year ago, I started with Suse 9.2 (or 9.3, not shure). The reson why I looked for an other distro is cus suse is to "windows-like" (in my opinion). You have to click everywhere, and you don't know what the computer realy does.

I don't now if (k)ubuntu is better than suse, it's just different.
I remember me having dependencie problems with Yast (but it was my first linux-experience, probable my own fault). Now with apt-get you don't have to think about dependencies.

My most used apt-get commands:

apt-get update
apt-get upgrade
apt-cache search "part of programname"
apt-get install programname

This might help in getting what you want: [http://packages.ubuntu.com/breezy/](http://packages.ubuntu.com/breezy/)
I have used synaptic for a while, but I prefer the command line.

peanut butter, to change the grub config, I just use "vi /boot/grub/menu.lst" I don't know if that is what you are looking for.
You now have a dualboot. You might want to concider using a virtual windows (if your computer is fast enough). I use VMware (this is not freeware) everytime I nead to use Autocad, Simens Step7, or any other program that doesn't have a good linux-variant. You can disable the networkcard in VMware so you wont get virusses. And the best thing is... you never nead to reboot if you nead to use a windows-based program.

Greetings,
Reinhart

---

### Post by peanut butter on 2005-11-01
yes i agree it is a little like windows.
and SuSe 10 uses APT so its just as easy
to run a windows program i use [wine]("http://www.winehq.org")
because i cant run theese programs with 512 mb ram because it would betoo slow. also i have never gotten a virus using windows maby norton A/V is fixing that.

---

### Post by peanut butter on 2005-11-02
Also the only reasoni haven't completely dumped windows is because mymom wont use linux and she uses the computer regularley.
if you have any ideas on how to convince her please PM me!

---

### Post by nikodell on 2005-11-18
Well SuSE for me now I will check out the next release of the 64 bit version.
 As of today i have a fully working SuSE 10 x86_64 system stable and i can get the system up and running in a short time. 

I did get most everything working in KUBUNTU but the fact that i could not get one fully working browser is enoughe to make me wait for a better release."I want all my pluggins real quicktime java flash so till then its SuSE foe ME.

ALOHA and nice system so far and i do like some things better in KUBUNTU

---

### Post by nikodell on 2005-11-19
[QUOTE=nikodell]Well SuSE for me now I will check out the next release of the 64 bit version.
 As of today i have a fully working SuSE 10 x86_64 system stable and i can get the system up and running in a short time. 

I did get most everything working in KUBUNTU but the fact that i could not get one fully working browser is enough to make me wait for a better release."I want all my pluggins real quicktime java flash so till then its SuSE foe ME.

ALOHA and nice system so far and i do like some things better in KUBUNTU[/QUOTE] So I tested Mandravia 2006/X86_64 and the basic setup went well the basics up and running browser with flash and java and all. But on other basic software I had found it almost impossible to find dependent packages to install and now i understand the gripe most people have with rpms . SuSE is much better with this but I can say i do prefer apt-get as the management software. Cannot wait for the next version to try out I hope it comes together so that i can pull the permanent switch.

Wheres my spellcheck

---

