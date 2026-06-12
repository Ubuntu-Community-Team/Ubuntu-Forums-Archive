---
title: "ubuntu amd 64 bit can`t boot"
date: 2007-01-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by ilanesh on 2007-01-08
I just have downloadet ubuntu 64 bit amd, I could not find i386 64 bit, now it will not boot up on my acer laptop, it tells me that my machine is not amd 64 bit, how can this be? My acer is 64 bit and also dual core, what to do now? Please help, I want to try 64 bit on my 64 bit dual core machine.
Thanks for help.

---

### Post by teaker1s on 2007-01-08
386i is 32bit
amd 64 bit for amd only

the generic kernel has smp support for duel core intel, though i have seen some complaints in forums with intel duo core

if you have amd64 bit then try downloading other install options
alternative amd 64bit iso

---

### Post by 3rdalbum on 2007-01-09
Trust me, unless your laptop has over 4 gigabytes of RAM and you really need to use all of it, you'll be much happier with the 32-bit version. The normal i386 32-bit version works on 64-bit machines as well, and it's less frigging around when you want to install proprietry software.

---

### Post by Sammi on 2007-01-09
Intel dual core 64 bit does have a bit of problems, as I have come to understand. Cutting edge dekstop hardware is a weak point in Linux in general. 

But as teaker1s mentions, you should try the regular 32 bit version, as it has the almost stable support for Intel dual core.

---

### Post by ilanesh on 2007-01-09
thank you to all of you for your response.
I have a Acer Aspire and he is the best I could get and also linux friendlier then all the others.
Now that I have a 64 bit I even can not try it out, sadly. Why there are not intel 64 bit linux operating systems?
My dual core works very good and fast with Pclinuxos smp kernel, 
but I wanted Ubuntu or Kubuntu 64 for intel, not amd, here in my country is all intel, and intel laptops and pc`s are lots better and faster and less problems then with amd.
I talked first about it with my technician and he warned me about amd .
so now the question is, why no i386 64 bit? cause most people use intel computers but not amd. Is there any hope that there will be a i386 64 bit on Ubuntu distro`s?

---

### Post by MikeBuffer on 2007-01-10
> amd 64 bit for amd only

This is not accurate. The confusion comes from the terminology used in the Ubuntu distributions: the 64-bit Ubuntu 6.10 distribution is called ubuntu-6.10-desktop-amd64.iso but works on both AMD and Intel 64-bit processors. It's historical; AMD developed 64 bit extensions before Intel did, but now Intel have them.

On **[http://releases.ubuntu.com/edgy/](http://releases.ubuntu.com/edgy/)** they say that the AMD64 distro is for computers based on the AMD64 or EM64T architecture; [EM64T ]("http://en.wikipedia.org/wiki/EM64T")is one name for the Intel 54-bit implementation. However, I think it is a pity that the distro text does not make it clearer that it works on Intel64 as well as AMD64 CPUs.

I have installed 64-bit Ubuntu using the standard "64-bit PC (AMD64)" desktop CD on a laptop with an Intel Core 2 Duo: details [here]("http://ubuntuforums.org/showthread.php?t=334962"). It's not perfect, but it definitely supports this CPU.

Back to your question:
> it tells me that my machine is not amd 64 bit, how can this be?

Are you certain your CPU is 64-bit? Intel's branding is quite confusing, for some reason they don't make it very obvious that some CPUs are 64-bit. If you can find out the processor number (eg under System Properties in Windows if you can't boot linux), you can look it up on the [intel website here]("http://www.intel.com/products/processor_number/"). Mine for example is a [T7400]("http://www.intel.com/products/processor_number/chart/core2duo.htm"), which is shown to support Intel64.

Hope this helps,
Mike.

---

### Post by ilanesh on 2007-01-12
Hi MikeBuffer,
thank you for your response, I have 
"Intel Core Duo Processor T2250
1.73 GHz
Intel Graphics Media Accelerator 950
120B HDD
1GB DDR

Windows Vista Capable

this is what i see on my laptop.

oh
Processor 1
vendor id genuineintel
cpu family 6
model 14
model name genuine intel (r) cpu T2250
siblings 2
CPU Cores 2

hope this is enough info.
thanks for your help.

---

### Post by MikeBuffer on 2007-01-13
Hi Elanish,

All "Core Duo" processors are 32-bit, whereas "Core 2 Duo" are 64-bit. This is why the 64-bit version of Ubuntu will not run on your machine. However, it's still a good processor and the 32-bit version of Ubuntu should work well on it. 

As many people have said, Intel's naming scheme is crazy -- they appear to be almost deliberately  hiding the major  transition from 32-bit to 64-bit, which is very confusing for end users like ourselves!

Mike.

---

### Post by ilanesh on 2007-01-13
Hi Mike,
wow, this is not good, cause I told to my technician that I want a duo core 64 laptop and he said it is a 64 bit, now can this be that there are is a misunderstanding? He should know this as  a technician. also I wanted one where I can still use also 32 bit and also 64 bit, i must call him tomorrow and tell him this  that this is now not a 64 bit machine, am disapointed.
when you go to buy a laptop and tell them you want a 64 bit duo core and then you don`t get it this is very confusing.
thanks for telling me, cause I was a 100% sure I  got what I wanted.
Ilana.

---

### Post by MikeBuffer on 2007-01-13
Well then you should definitely take this up with the technician. See this other post of mine for a link to a PDF doc from Intel that specifies exactly the capabilities of each chip type:
[http://ubuntuforums.org/showpost.php?p=2006387&postcount=1]("http://ubuntuforums.org/showpost.php?p=2006387&postcount=1"). 
It clearly identifies your T2250 as NOT Intel-64.

MIke.

---

### Post by ilanesh on 2007-01-14
Hi Mike,
I called today my technician where I bought my laptop, and he even checked it out for me and it is really a Intel Pentium 64 bit, there are no 32 bit laptops and 32 bit pc`s anymre to sell.
it is windows vistA capable and works on windows vista 64 bit, so then it is just that ubuntu is made only for AMD 64 bit but no for intel pentium,
my technician will not lie to me.
Thank you for your patience with me and trying to hekp me, I have to ait till there will be come out also only for INTEl laptops and computers a linux 64 bit.
Sadly they make only for AMD, and most people use only INTEL. Is there any change that there will be also for intel a 64 bit?
thanks again for your understanding.
Ilana.

---

### Post by touristguy87 on 2008-03-27
Hi, 
your technician may not be lying to you, just not knowing what he is talking about. 

The question is, can he install Ubuntu for AMD64 on it. 

I just read through all this and my "new" e1705 with core duo definitely will not run Ubuntu-64.

all you need to do is check your system find out the cpu model, I have two T2400s and a T2080 and you can see clearly that neither are core2 and core2 is what you need to run U64, and sure enough, U64 won't run on any of the 3. How may ways do you want to see this sliced?

Now as far as getting 64-bit Vista to run on it, or even XP64, that's another story. They may run on it but only in 32-bit mode. I really don't know. But the simple thing with U64 is that all you have to do is boot the CD and it'll take you a minute to find out the real deal. With Vista and XP you pretty-much have to reinstall it on every new system you want to try it on.Otherwise you could just install it to an external drive beind usb and then boot off that drive and it would work. 

That will work with Ubuntu, with very few failures.

you certainly should have no problem booting U64 off the U64 cd.

---

### Post by touristguy87 on 2008-03-27
...of course the problem is exactly *why* you need to run U64...I am not eager to get "stuck behind the curve" either, but still it's going to be a long time before the 64-bit market can really shake itself free from the 32-bit codebase. And by that time I will just have to make the decision to shuck these old laptops. If that day ever comes.

For now I would just put the i386 version on it and keep getting up...unless you really need to build or run 64 bit code. And if that is the case, just go down to your local Circuit City and buy one of their Core2 Toshiba laptops, they have them for about $750. But you'll have to pay for a Vista license in the process, and probably Office too.

The problem is how to get a core2 laptop without supporting Microsoft which I think is one reason that we all are even messing about with Ubuntu ;) If MS can enforce a "PC tax" on every new core2 sold, then it's hard to see how to get one without paying the tax. Though i think that Dell will sell a bare one to you.

---

### Post by Sammi on 2008-03-27
Check that your women and children are safe, for tonight the dead walk again :twisted:

Hello necromancy.:rolleyes:

But seriously, this tread is well over a year old, and the point of it is moot now i believe.

---

