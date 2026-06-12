---
title: "HOW to tell if my computer is 64bit capable?"
date: 2009-04-04
forum: x86 64-bit Users
---

### Post by uberbuntufan64y on 2009-04-04
Hi I am running Ubuntu and I was wondering if I could install the 64 bit version instead. I need to check if my pc is capable but I dont know how. Someone suggested for me to check the sticker on the case, but it is peeled off.

Any ideaz?:KS

---

### Post by Butthead on 2009-04-04
Um type "uname -m" in terminal, perhas? :confused:

---

### Post by uberbuntufan64y on 2009-04-04
> **Butthead said:**
> Um type "uname -m" in terminal, perhas? :confused:

Whats that?

---

### Post by fballem on 2009-04-04
I think this will do the job:

1) Open a Terminal

2) enter the following code in the terminal:
```

sudo lshw >lshw.txt

```

3) Use Nautilus and locate the file lshw.txt (it will be in your home folder). Double-click and choose to Display the contents.

4) Near the top should be an entry for your motherboard that will identify the width (mine is 64-bits). As you scroll down, you will see entries for CPUs. If you have a 64-bit motherboard and at least 2 CPUs, then you can run 64-bit ubuntu.

Hope this helps,

---

### Post by Butthead on 2009-04-04
Open up your Konsole (or whatever it's called if you're running Gnome) and type "uname -m" (without the quotes) in it.

If you see x86_64 displayed, yes you can.

---

### Post by punkybouy on 2009-04-04
type cat /proc/cpuinfo and give us the output.

---

### Post by uberbuntufan64y on 2009-04-04
A few questions: What is a konsole. What is a terminal. I tried typing the things suggested but random windows just pop up. I guess they are shortcut keys or something?

I don't see a Gnome or KDE, I think what it is is XFCE

---

### Post by Didius Falco on 2009-04-04
> **uberbuntufan64y said:**
> A few questions: What is a konsole. What is a terminal. I tried typing the things suggested but random windows just pop up. I guess they are shortcut keys or something?

I don't see a Gnome or KDE, I think what it is is XFCE

Konsole and Terminal are different names for the same thing: a window for command lines, like those above.

The reason for the differing names is that terminal is the name used in Ubuntu, which uses the Gnome desktop GUI. Kubuntu, which is Ubuntu with a different desktop GUI on top, uses KDE.KDE tends to put a K in the front of application names to distinguis them from Gnome based applications.

To find terminal, go to your menu>applications>Terminal. Once you open that up, you can type (or cut and paste) commands into it. Be careful, though - there are commands that can destroy your install, or even wipe your whole PC.

Read this: [http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326) and then go find some good tutorials on commands. Look in the Absolute Beginners forum and you'll find a link to a free download of the Ubuntu Pocket Guide, which is a great reference. Terminal is like a hammer - used properly it can help build and maintain a strong home. Used improperly and you may find yourself looking the smoldering ruins of your house.

On Edit: I haven't used the XFCE desktop, so it the location and name may differ.

---

### Post by SketchyClown on 2009-04-05
> **uberbuntufan64y said:**
> Hi I am running Ubuntu and I was wondering if I could install the 64 bit version instead. I need to check if my pc is capable but I dont know how. Someone suggested for me to check the sticker on the case, but it is peeled off.

Any ideaz?:KS

Easy. Download and burn the 64bit live-cd or alternate cd and if your computer will boot the cd, it is 64bit capable. If you get an error on boot, then it is not.

---

### Post by TopEnder on 2009-04-05
Hi,
I don't believe the Code: sudo lshw >lshw.txt gives the correct read out for the Motherboard. My output of the above code is:
[COLOR="Blue"]hardy-64bit
    description: Desktop Computer
    product: ASI VA20
    vendor: AnabelleB
    serial: 9909245
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp[/COLOR] (the rest truncated).  I am running a triple boot system Windows XP 32bit, Ubuntu 8.04 64bit & Ubuntu 8.10 32bit and the code shows width: 32bit.

---

### Post by fballem on 2009-04-05
> **TopEnder said:**
> Hi,
I don't believe the Code: sudo lshw >lshw.txt gives the correct read out for the Motherboard. My output of the above code is:
[COLOR="Blue"]hardy-64bit
    description: Desktop Computer
    product: ASI VA20
    vendor: AnabelleB
    serial: 9909245
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp[/COLOR] (the rest truncated).  I am running a triple boot system Windows XP 32bit, Ubuntu 8.04 64bit & Ubuntu 8.10 32bit and the code shows width: 32bit.

I stand corrected on the width for the motherboard, with my thanks. Could you please provide the entries for the CPU? (they're a little farther down in the file).

Actually, I quite liked the suggestion from SketchyClown - download and burn the 64-bit version to a CD, then boot from it as a live CD. It seems a much simpler solution than anything the rest of us have come up with, and does not require the use of a terminal.

Thanks for the correction,

---

### Post by TopEnder on 2009-04-05
> **fballem said:**
> I stand corrected on the width for the motherboard, with my thanks. Could you please provide the entries for the CPU? (they're a little farther down in the file).

Actually, I quite liked the suggestion from SketchyClown - download and burn the 64-bit version to a CD, then boot from it as a live CD. It seems a much simpler solution than anything the rest of us have come up with, and does not require the use of a terminal.

Thanks for the correction,
I hope this is what you wanted? 
[COLOR="Blue"]*-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU
          slot: Socket 775
          size: 2GHz
          capacity: 4GHz
          width: 64 bits
          clock: 333MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq[/COLOR]
TopEnder

---

### Post by mgranet on 2009-04-05
Yep. You have a 64bit capable processor.

---

### Post by jespdj on 2009-04-05
> **SketchyClown said:**
> Easy. Download and burn the 64bit live-cd or alternate cd and if your computer will boot the cd, it is 64bit capable. If you get an error on boot, then it is not.
Hmmm... Why go through all this trouble (download a big 700 MB file and spend a CD-R on it) if there is a much faster and cheaper way to find out?

All Intel **Core 2 Duo** processors are 64-bit capable.

---

### Post by EnglishSparrow on 2009-04-05
Do you know what processor your system has?

---

### Post by Chemical Imbalance on 2009-04-05
> **Butthead said:**
> Open up your Konsole (or whatever it's called if you're running Gnome) and type "uname -m" (without the quotes) in it.

If you see x86_64 displayed, yes you can.

This is incorrect.  This will only list the current kernel version you have.  This tells you nothing of what your cpu is capable of.

Oh and yes, your Core Duo is definitely 64bit capable.

---

### Post by Butthead on 2009-04-05
> **Chemical Imbalance said:**
> This is incorrect.  This will only list the current kernel version you have.  This tells you nothing of what your cpu is capable of.

Oh and yes, your Core Duo is definitely 64bit capable.

I stand corrected then. ;)

---

### Post by Chemical Imbalance on 2009-04-05
> **Butthead said:**
> I stand corrected then. ;)

I hope I didn't sound snide or anything, I just didn't want the thread-poster to run that command and think his/her cpu isn't 64bit.

---

### Post by jespdj on 2009-04-06
> **Chemical Imbalance said:**
> Oh and yes, your Core Duo is definitely 64bit capable.
No! The Intel **Core Duo** is 32-bit only.

But the OP has an Intel Core **2** Duo, and those are 64-bit.

Core Duo and Core 2 Duo are two totally different CPUs.

---

### Post by stchman on 2009-04-06
> **uberbuntufan64y said:**
> Hi I am running Ubuntu and I was wondering if I could install the 64 bit version instead. I need to check if my pc is capable but I dont know how. Someone suggested for me to check the sticker on the case, but it is peeled off.

Any ideaz?:KS

If it has a 64 bit processor then it is 64 bit capable.  What processor do you have?

---

### Post by Chemical Imbalance on 2009-04-06
> **jespdj said:**
> No! The Intel **Core Duo** is 32-bit only.

But the OP has an Intel Core **2** Duo, and those are 64-bit.

Core Duo and Core 2 Duo are two totally different CPUs.

I said *his* core duo is.  Sorry, I was too lazy to put the 2 there.  I have one myself, I should know.

---

### Post by Butthead on 2009-04-06
> **Chemical Imbalance said:**
> I hope I didn't sound snide or anything, I just didn't want the thread-poster to run that command and think his/her cpu isn't 64bit.

No offense taken.  That's how we all learn the intricacies of the Linux OS. :guitar:

I guess I could have researched it better instead of just arbitrarily throwing my idea out too.  I figured that "uname -m" did query the processor though, and since he did say he had Linux running...:-k

---

### Post by jespdj on 2009-04-07
> **Chemical Imbalance said:**
> I said *his* core duo is.  Sorry, I was too lazy to put the 2 there.  I have one myself, I should know.
But he does not have a Core Duo - he has a Core 2 Duo. Please don't create confusion...

---

### Post by Chemical Imbalance on 2009-04-07
> **jespdj said:**
> But he does not have a Core Duo - he has a Core 2 Duo. Please don't create confusion...

Again, I am sorry.  I just said in my post I was too lazy to put the 2 there.  Sorry, I try to proofread my posts, but I guess that  slipped.  Seriously "my bad" :)

Core Duo=32bit
Core 2 Duo =64bit

---

### Post by Chemical Imbalance on 2009-04-07
> **Butthead said:**
> No offense taken.  That's how we all learn the intricacies of the Linux OS. :guitar:

I guess I could have researched it better instead of just arbitrarily throwing my idea out too.  I figured that "uname -m" did query the processor though, and since he did say he had Linux running...:-k

No problem man :)

We all make mistakes --just look at my post above

---

### Post by uberbuntufan64y on 2009-04-10
Does it have anything to do if it is amd or intel chip? i think it is one of these...

my internet has been slow recently so i dont want to have to download a nother disk before i can find out if it is 64 or 32...

---

### Post by 3Miro on 2009-04-10
> **uberbuntufan64y said:**
> Does it have anything to do if it is amd or intel chip? i think it is one of these...

my internet has been slow recently so i dont want to have to download a nother disk before i can find out if it is 64 or 32...

AMD Athlon 64 and Athlon 64 X2 are both 64-bit compatible. The new Phenom and Phenom II chips also. Intel Core 2 Duo/Quad chips are 64-bit compatible as well as some of the old Pentium D (look for EMT64).

The 64-bit version of Ubuntu is called AMD64, which is just the name of the standard. It works the same way on Intel and AMD chips. I have both Intel and AMD CPUs on different computers, works just fine.

---

### Post by uberbuntufan64y on 2009-04-12
i think its about two years old, if that helps

---

### Post by movieman on 2009-04-13
> **uberbuntufan64y said:**
> i think its about two years old, if that helps

Most desktop CPUs from the last two years will run 64-bit, but a lot of laptop CPUs won't.

---

