---
title: "i8kutils available on x86-64?"
date: 2006-10-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by siersmak on 2006-10-09
Hello,

I have a new Inspiron 6400 with an Intel Core 2 Duo processor, running 64-bit Dapper.  I've read much about laptops overheating (esp. here:  [http://ubuntuforums.org/showthread.php?t=186003)](http://ubuntuforums.org/showthread.php?t=186003)), and would very like some control over my fans with the i8kutils package.  I have the multiverse and universe repositories enabled in synaptic, but it appears that i8kutils and the i8k.o kernel module is not available on x86-64 because the only item that appears when I search for i8k is 'sensors-applet'.  Am I understanding this correctly, or am I possibly overlooking something?

-Ken

---

### Post by mattyj on 2006-10-10
I would really like to do this as well.  Given almost all new Dell laptops will be 64 bit capable, it would be really nice to move those over.

---

### Post by mattyj on 2006-10-10
What would it entail to create the 64 bit version?  Could it be in the final version of Edgy?

[http://packages.ubuntu.com/dapper/utils/i8kutils](http://packages.ubuntu.com/dapper/utils/i8kutils)

---

### Post by mattyj on 2006-10-11
Have you tried this?  I have yet to purchase one, waiting for this to get sorted out...

Things you might try first
When switching to a 64-bit operating system, there are still programs that are not natively compiled for the AMD64 architecture. The first thing you can try, if there is a i386 version available, is to force the program to install using the i386 architecture. For other architectures this does not work (when you for instance try to force to install a SPARC compiled application) but luckily the AMD64 architecture is backwards compatible with i386, so these 32bit applications should run fine. The downside of this is that some calls to libraries might not work and need their 32-bit version as well. If you omit the 'force architecture' option dpkg will tell you:

dpkg: error processing packagename_i386.deb (--install):
package architecture (i386) does not match system (amd64)

You can do a forced i386 installation like this:

Code:
sudo dpkg -i --force-architecture packagename_i386.deb

---

### Post by siersmak on 2006-10-11
I haven't because i8kutils requires the i8k kernel module, which from what I can tell has not been ported to x86_64 yet - it is not included as an option in the vanilla 2.6.18 kernel when configured for 64-bit.

-Ken

---

### Post by mattyj on 2006-10-11
Missed that.  Bummer.

---

### Post by siersmak on 2006-10-13
I just heard back from the i8kutils developer, and he said that he doesn't have an x86_64 Dell laptop to test his app on.  He indicated that if anybody has one that would be willing to test his dangerous smm program he'd be happy to help with driver development.  My boss would not approve my use of this machine for that purpose, but if anyone can offer up their machine for testing PM me and I'll get you two in contact (I don't feel comfortable posting his email address on the forum, but if you look at the source of i8kutils you'll easily find his email address).

-Ken

---

### Post by kansei on 2007-09-07
*bump* to almost 1-year later and still no 64-bit i8k.

It's the single thing pushing me to dump 64-bit ubuntu, I'm sick of this laptop burning me all the time haha.

If there is anything that they need a 64-bit dell laptop to test with, let me know.. I'm here, willing and able :)

---

### Post by mattyj on 2007-09-08
I have been running stock Feisty on my Latitude D820 an d monitored the temps.  It does fine, same as in Windows, max temps ~  70, processors rated 110C.  Fans turn on and off at reasonable points.  I think Dell and Ubuntu talked a lot about this now that Dell is selling laptops with ubuntu on them.

MJ

---

### Post by kansei on 2007-09-08
Well the Dell I run is a D620 Core2duo and .. it shouldn't be hitting 70C, there's no reason for it. That's *why* there is a fan there, and in 64-bit linux there is 0 fan control. The fan sits at a silly low speed. I have read of someone frying their board when taxing the graphics card in 64-bit linux. I hesitate to do much with the laptop since not even a minute shoots the CPU temps over 70 (with GDM not even running so no gpu stress). I think it's dumb that something so small can be reason enough to just stick with a 32-bit OS on the computer.

Unless the D820 is equivalent to the D6*3*0 (santa rosa chipset and such) and maybe the D630 fixed the whole fan speed control issue, it's still an issue.

---

### Post by inphektion on 2007-09-08
No D620 is equiv to the D820 chipset and all. the DX30 were the first with santa rosa for all dell latitudes.

---

### Post by kansei on 2007-09-09
> **inphektion said:**
> No D620 is equiv to the D820 chipset and all. the DX30 were the first with santa rosa for all dell latitudes.

And you say that your fan speed does in fact change? My fan sits at an rpm where is is completely inaudible, even with the processor thrashing about. On my thinkpad as soon as I see the CPU or GPU temp hit 53C I hear the fan start to spin more to keep it down.

It would be awesome just to even see those sensor values on the D620.. all I get is the ACPI CPU value. Right now with the ibm-acpi sensors I see CPU, minipci, hard drive, gpu, and battery temps.

---

### Post by inphektion on 2007-09-09
Well on my d820 I'm running windows.  I've never heard the fan on this computer.  I have an XPS laptop with windows too and I hear the fan all the time.  So maybe it isn't the lack of i8k mods causing you not to hear your fan but I would like to know for sure as I'm getting a precision 6300 in a month and want to run ubuntu 64 on it.

---

### Post by kansei on 2007-09-09
> **inphektion said:**
> Well on my d820 I'm running windows.  I've never heard the fan on this computer.  I have an XPS laptop with windows too and I hear the fan all the time.  So maybe it isn't the lack of i8k mods causing you not to hear your fan but I would like to know for sure as I'm getting a precision 6300 in a month and want to run ubuntu 64 on it.

I'll have to restart that computer into windows and run prime95 or something to hear it spin up.. I sit there and put my ear on the fan when I run 'stress' in linux and the fan stays constant the whole time.

---

### Post by gorn on 2007-09-22
I am not a ubuntu user, but you guys seem the most vocal about this.

I converted the i386 assembly to x86_64 (really just a s/l /q / and a s/%e/%r/). The module compiles and loads into the kernel and I can get some data.
[quote=/proc/i8k]1.0 A02 CVBxxxx 43 -22 1 27660 75270 -1 -22[/quote]

My current issue is that when I set a fan speed, the BIOS seems to override it after a little bit. (Actually I also had this happen with dellfand [[http://dellfand.dinglisch.net/]](http://dellfand.dinglisch.net/]) so I figured I'd try i8k and then realized that required patching). I think that it's my BIOS D630 Bios A02 according to i8k. I'd be really interested to hear of this working properly for anyone, or perhaps all the core2duo BIOSes are this way.

I'm betting that there is some flag we can set to allow OS fan control.

Kernel module for x86_64
[http://gorn.wmn.cc/kernel/i8k_64/](http://gorn.wmn.cc/kernel/i8k_64/)

If anyone dual boots 32 bit and 64 bit testing for differences would be useful.

-KB

---

### Post by kansei on 2007-09-23
Thanks a ton for your work! I'll start testing in the AM and let you know if anything weird happens.

---

### Post by Mr_bleu on 2007-09-23
[http://ubuntuforums.org/showthread.php?t=463590](http://ubuntuforums.org/showthread.php?t=463590)
Try that.  It's working for me. It's run from the terminal, no fancy gui, but it works like a champ.

---

### Post by gorn on 2007-09-23
> **kansei said:**
> Thanks a ton for your work! I'll start testing in the AM and let you know if anything weird happens.


Cool. What kind of hardware are you on?
I upgraded to the D630 A03 BIOS, with no change.

I've tried i8k, dellfand and i8kfangui under Vista and all have the same problem. Sometimes manual control works for a while, but eventually the hardware will change the fan speed on it's own (This can happen in either direction, of I have the fan high and it turns it low, or I have the fan low and it turns it high).

---

### Post by Mr_bleu on 2007-09-23
My hardware's listed in the signature.  Dell E1505 Notebook w/ T7200 processor 2 gb Ram 667 Mhz, 
Intel integrated gma950.

---

### Post by kansei on 2007-09-23
> **gorn said:**
> Cool. What kind of hardware are you on?
I upgraded to the D630 A03 BIOS, with no change.

I've tried i8k, dellfand and i8kfangui under Vista and all have the same problem. Sometimes manual control works for a while, but eventually the hardware will change the fan speed on it's own (This can happen in either direction, of I have the fan high and it turns it low, or I have the fan low and it turns it high).

I'm on a D620 (Core2duo T7200) with nvidia quadro graphics, 2gb ram, intel 3945

---

### Post by inphektion on 2007-09-24
Maybe you can start a thread over on [http://www.lesswatts.org](http://www.lesswatts.org)
effectively controllers the fan speed and temp of cpu has to consume less power.  Maybe some intel expert over there could help with this.

---

### Post by Ptero-4 on 2007-09-24
Does i8k work in MacBooks?

---

### Post by bimbo on 2007-09-25
I have a Latidude D830 on Gutsy 32bit.  I can load i8k just fine and when I try to turn the fan off, it will do so, but only for a very short period until something turns it on again. (I guess it's the BIOS)

i8kfangui under Windows successfully keeps the fan off. Has anybody found anyway to do that on Linux?

---

### Post by kansei on 2007-09-25
> **bimbo said:**
> I have a Latidude D830 on Gutsy 32bit.  I can load i8k just fine and when I try to turn the fan off, it will do so, but only for a very short period until something turns it on again. (I guess it's the BIOS)

i8kfangui under Windows successfully keeps the fan off. Has anybody found anyway to do that on Linux?

The same is happening to 64-bit D630 people. I believed someone mentioned it only happened after a recent BIOS update. I'd revert back to an older BIOS if you don't need any new features or bugfixes in the latest and see if it helps.

--Though if it all works fine in windows.. HMMM I was under the impression that the i8k utils for Windows were ports from the *nix stuff. Maybe the Windows version you have is actually newer than the Ubuntu package? That could easily be the case if you are on Feisty Fawn.

i8kutils on Ubuntu Gutsy Gibbon (32-bit) is version 1.27 btw

Maybe start a thread in the Dell hardware support forum discussing i8k on the Dx30 models?

---

### Post by bimbo on 2007-09-25
Hmm does anybody know where /if you can get old BIOS on the Dell site? I can only see the most recent version...


But still, it's weird that it works with i8kfangui under Windows but not under Linux. Maybe i8kfangui keeps turning off the fan so often that it sticks?

I don't think Dell likes you asking in the Dell forums, as after all, it probably DOES void the warranty ;). Then again, if the hardware is sanely built, it will turn off if it gets too hot no matter what.

I'm running Gutsy, but i8k was not updates since 2005. I mailed the author of the module but didn't get an answer so far.

---

### Post by bimbo on 2007-09-25
Ok so I did flash it back to A02, didn't change anything. I'm wary about trying A01 because thats older than the one mine shipped with and it might not work on my revision.

---

### Post by kansei on 2007-09-25
> **bimbo said:**
> Hmm does anybody know where /if you can get old BIOS on the Dell site? I can only see the most recent version...


But still, it's weird that it works with i8kfangui under Windows but not under Linux. [B]Maybe i8kfangui keeps turning off the fan so often that it sticks?
[/B]
I don't think Dell likes you asking in the Dell forums, as after all, it probably DOES void the warranty ;). Then again, if the hardware is sanely built, it will turn off if it gets too hot no matter what.

I'm running Gutsy, but i8k was not updates since 2005. I mailed the author of the module but didn't get an answer so far.

You might be on to something. If the linux and windows i8k driver stuff is virtually the same, could just be the util frontend polling to make sure the fan stays off. I haven't looked at the windows code.

I keep trying to remind myself to try the x64 stuff posted here.. I shall go home and do that right now :)

---

### Post by bimbo on 2007-09-25
Unfortunately, I haven't found sources for the latest version of i8kfangui so far. And the sources I saw where partly assembler which I can't read at all... 

As for the polling: I tried dellfand with 1s intervals, that didn't help, either. Maybe if you have a really tight look on the order of 100ms but then you burn a lot of power by waking up the CPU that often? Is there a possibility to simply override that BIOS code in RAM?

There however IS a i8kfangui version for 64bit, IIRC. So in any case, it should be possibly to port it from there.

---

### Post by kansei on 2007-09-25
Ok I'm testing the dellfand stuff on 64 bit right now (version 0.8)
reference: [http://ubuntuforums.org/showthread.php?t=463590](http://ubuntuforums.org/showthread.php?t=463590)

and I too have the issue where it won't stay at the set speed for more than a second. If I issue the command "sudo dellfand 1 1 25 26 27" to force high speed, it basically alternates half a second on high, half a second on low, etc.

Changing that to "sudo dellfand 1 0.1 25 26 27" (a 0.1 second sleep time) makes it stay on high more often, but still not enough. Even setting it to a 0 second sleep time (i.e. it makes the computer barely usable, pegs the CPU at 2ghz, etc) it still goes to the low speed momentarily (no better than the 0.1 second sleep actually.

Again, this is on a D620, not a D630. Latest BIOS revision, 2GHZ Core2duo (most 620s are a CoreDuo)

edit: just realized that the dellfand process is resident, and I had 8 of them going. Time to try again with 0.1 second sleep. Still goes to low speed. Same for 0 second sleep time. This is great, at least I can in some way control the fan! Thanks for the research and work guys!

Time for some more testing.

---

### Post by Mr_bleu on 2007-09-25
I have no issues running dellfand.  Right now my cpu temp's at 115.  You have it running at high speed at a VERY low temp <27 celcius>  "If I issue the command "sudo dellfand 1 1 25 26 27" .  1 is the output mode  <0 is verbose> 1<2nd listed> is the time interval between speeds. 25 is the minimum speed, 26 low turn on speed and 27 high turn on speed.  I might be misunderstanding, but you're trying to keep it too close together.  I'm currently running "sudo dellfand 1 10 25 30 34".  It's working swell.  It reverts to bios controlled when you reboot the pc/notebook.  My apologies if I've misunderstood.:popcorn:

---

### Post by gorn on 2007-09-25
Okay I'm surprised and happy that bimbo has i8kfangui working on Windows.

Do you use it regularly? Could you test it a bit more extensively with both turning the fan low/off when the bios wants it high and with turning the fan high when the bios wants it low or off?

Also what version are you using and did you have to do any special settings?

It shouldn't matter, but Vista or XP?

I think that the assembly code will not need to be changed, but a register it passes to SMBIOS should have a different value. If i8kfangui is doing that properly on the 830 I'll need to find out why that same value isn't working on the 630, also I'll need to add that to dellfand and i8k.

For those interested,

The assembly code is the same (basically) between the i8k kernel module and the dellfand program. I do NOT know x86 (much less -64) assembly, but I know assembly for the HCS12 so I can somewhat read this.

Here's a basic idea of what it does

**Load Data from memory into registers**
```

        asm("pushq %%rax\n\t"
          "movl 0(%%rax),%%edx\n\t"
          "pushq %%rdx\n\t"
          "movl 4(%%rax),%%ebx\n\t"
          "movl 8(%%rax),%%ecx\n\t"
          "movl 12(%%rax),%%edx\n\t"
          "movl 16(%%rax),%%esi\n\t"
          "movl 20(%%rax),%%edi\n\t"
          "popq %%rax\n\t"

```
%rax is a register that contains an address. The address is saved to the stack and then the memory from that address is copied into the registers. IE edx = rax[0], ebc = rax[1], ecx = rax[2]....


**Call APM/SMBIOS**
```

          "out %%al,$0xb2\n\t"
          "out %%al,$0x84\n\t"

```

This is the real work. Out is used to send a command to a port. 0xB2 is the APM port, I haven't yet found out what 0x84 is. I feel like %al should be uninitialized, but perhaps it overlaps with one of the other registers (again I don't know x86 assembly)

**Copy values from SMBIOS to memory**
```

          "xchgq %%rax,(%%rsp)\n\t"
          "movl %%ebx,4(%%rax)\n\t"
          "movl %%ecx,8(%%rax)\n\t"
          "movl %%edx,12(%%rax)\n\t"
          "movl %%esi,16(%%rax)\n\t"
          "movl %%edi,20(%%rax)\n\t"

```
xchgq swaps the first item on the stack into %rax, and the old value form %rax goes onto the stack. The moves are like before but the opposite (rax[1] = ebx, rax[2] = ecx)

**I really don't know**
```

          "popq %%rdx\n\t"
          "movl %%edx,0(%%rax)\n\t"
          "lahf\n\t"
          "shrl $8,%%eax\n\t"
          "andl $1,%%eax\n"
          :"=a"(rc)
          :    "a"(regs)
          :    "%ebx", "%ecx", "%edx", "%esi", "%edi", "memory");

```

I need to do a bit of reading for that last line. I'm thinking this is related to copying registers into variables from inline assembly into C.

---

### Post by kansei on 2007-09-25
> **Mr_bleu said:**
> I have no issues running dellfand.  Right now my cpu temp's at 115.  You have it running at high speed at a VERY low temp <27 celcius>  "If I issue the command "sudo dellfand 1 1 25 26 27" .  1 is the output mode  <0 is verbose> 1<2nd listed> is the time interval between speeds. 25 is the minimum speed, 26 low turn on speed and 27 high turn on speed.  I might be misunderstanding, but you're trying to keep it too close together.  I'm currently running "sudo dellfand 1 10 25 30 34".  It's working swell.  It reverts to bios controlled when you reboot the pc/notebook.  My apologies if I've misunderstood.:popcorn:

I'm just trying to get it working first. I realize the numbers are crazy low. But even on high fan speed the processor sits ar 45C so nothing is triggering it to go to the lower fan speed.

Edit: I just played around with it some more and have settled on these numbers for now:
dellfand 0 5 38 53 60 (using it with verbose output for now so I can monitor it as I stress test it)

Now I need to either write a quick init script or see if it came with one to use :) then I can put my numbers in once and keep them across restarts :D

---

### Post by gorn on 2007-09-25
So dellfand is or isn't working on the D620 C2D? Or it's working okay, just sometimes the BIOS takes control?

Just curious.

> **kansei said:**
> I'm just trying to get it working first. I realize the numbers are crazy low. But even on high fan speed the processor sits ar 45C so nothing is triggering it to go to the lower fan speed.

Edit: I just played around with it some more and have settled on these numbers for now:
dellfand 0 5 38 53 60 (using it with verbose output for now so I can monitor it as I stress test it)

Now I need to either write a quick init script or see if it came with one to use :) then I can put my numbers in once and keep them across restarts :D

---

### Post by bimbo on 2007-09-26
Even using 
dellfand 0 0.1 45 55 65
sorta works, but eats a whole core on its own and thus make CPU temp skyrocket, so not really useful either.

BTW, it might be that dellfand can't deal with fractions of a second (might very well use INT instead of FLOAT!), as 0.9 does just the same. I will look at the code later and try to modify the sleep approach.

---

### Post by bimbo on 2007-09-26
Here's a patch that allow for fraction of a second sleep times. So far that didn't seem to stop the BIOS from occasionally interfering. You won't hear it if you run it at say 0.1s but it definitely isn't good for the fan. 

So use it for testing, but DON'T use it for production. I'm not responsible if you fry your machine or anything like that.

I won't put a howto use the patch here, if you can't figure that out, you shouldn't be using it.

As for gorn: as soon as I get the inclination to deal with the mess that XP is, I will run some more tests on i8kfangui 3.1. Unfortunately, I haven't yet found sources for that, only for earlier version, so maybe I'll try the earlier version first to see if it works there.

---

### Post by bimbo on 2007-09-26
Ok what I found
[LIST]
[*]It does work under Windows, uses 200ms fan setting intervals, let it do it any less frequent, you will see the BIOS occasionally taking comamnd (I suspect with 200ms it's simply faster than i8kfangui updates RPM reading.
[*] More interesting: BIOS in command, slow mode is ~2900rpm, with i8kfangui, the slow mode is 2250RPM (!) which makes for barely audible fan!
[/LIST]

So apparently, there is a fancontroller somewhere (probably PWM) that seems to be able to do more than the Dell BIOS uses it for (in fact, i8kfangui has code for some fancontrollers where you can use very fine grained speed settings, that however does not work on D830). 

Two things I'm wondering about:
1) How can we define RPM settings? I think I'd very much like to have the fan be able to spin a 1500rpm, that should be no louder than the HD but still cool quite enough for idle tasks (then again if you're willing to have the CPU at about 55-60° it can run fanless most time it seems.
2) Is there a way to get the BIOS to stop interfering altogether? If the BIOS is simply sitting in RAM (which it generally does, IIRC), one might be able to patch it on the fly? Or have the kernel intercept all calls originating from the BIOS?

---

### Post by kansei on 2007-09-26
> **gorn said:**
> So dellfand is or isn't working on the D620 C2D? Or it's working okay, just sometimes the BIOS takes control?

Just curious.

Is working ok. the BIOS takes control (or at least that is what it seems like) but not very often. I can get it going for half an hour on the max fan speed, but then sometimes once every couple seconds the fan speed changes for a split second.


right now I'm running it as 'sudo dellfand 0 4 40 53 60'

and just leaving the terminal window open to monitor stuff.

---

### Post by gorn on 2007-09-26
Okay I have to rip things apart to know how they work. I have a stand alone assembly program that sets the fan to mode 2, here it is with comments.

Notice I only write to 0xB2, not 0x84 like dellfand and i8k do.

All it does is set the fan to speed 2, but if you are curious compile with:
```
gcc fan2.S -o fan2
```


fan2.S
```

.text

.globl main
        .type main,@function

main:

        # First we need to get io permission on
        # Port 0xB2 (APM)

        movl $1, %edx  # Turn on
        movl $1, %esi  # Length of 1 port
        movl $0xB2, %edi # Port number 0xB2
        call ioperm  # Do it

        movl $0x01a3, %eax # Command 0x01a3 (D_SET_FAN)
        movl $0x0200, %ebx # Speed:Fan (Speed 2, Fan 0)

        # ecx, edx, esi, edi maybe should be set to zero
        # But it seems fine without doing so

        out %al,$0xb2
        # Make the call to the APM port
        # APM will then read eax and ebx for the command

        # that's it

```

---

### Post by gorn on 2007-09-27
New toys!

BE CAREFUL
I do NOT understand this stuff. I did NOT program in safe guards. I am NOT responsible for what you do. You are interacting with the BIOS of your machine, anything could happen.

That said. I have a few tools here that you might enjoy playing with:

[http://gorn.wmn.cc/dell/dellfantools-20070926.tar.bz2](http://gorn.wmn.cc/dell/dellfantools-20070926.tar.bz2)

**getemps** - My dell has 5 temperature sensors it seems so to view them all easily I wrote this program. Then I added the fan RPMs to it since I wanted to try running without the i8k kernel module. Then I added fan mode.
Usage:
gettemps <numberOfFans> <pollTime in milliseconds>
Example:
gettemps 5 500
Default (no arguments) is gettemps 5 0 (0 means no loop, run once)

**setfan** - Sets the fan to a mode (NO TEMPERATURE CHECKING)
setfan <repeatTime in milliseconds> <mode>
Example:
setfan 100 2
**NOTE** - I don't know if setting your fan that rapidly is okay or not.
Again 0 time means run once


**getsmm** - This is the new and dangerous stuff SM like SMBios, dell has an SMBIOS lib and I read something else calling i8k smbios. SMM was a typo.
Getsmm can be used to interact with the SMBIOS the same way the current fan control does, but you can pick your own commands. Only two registers every seem to be used EAX and EBX. EAX contains the command code and EBX contains any arguments. I've included my list of commands, originally based off of the fan.cc headers, but including my findings.
Output is in the following format:
[status] : hex : decimal
status is either 0 or -1. -1 means there was an error.
hex and decimal are the output value i display in both formats for ease of use.


Interesting notes are that setfan accepts not just 0-2 but also 0x80-82, those these seem to just be equivalents (perhaps it only checks 7 bits).
**And 31a3 which seems to step down the fan one mode, but not always, perhaps depending on temperature or perhaps time since the change and the reason for change (user versus bios).**

If you want to test a bunch of values with getsmm you could write a bash loop, or add a C loop to the program. I did this for the setfan command and that's how i found the 0x80s, but I have avoided it for the other commands as it could crash the system and I wouldn't know which command crashed it (i suppose syncing after every call).
I noticed that fan control/status seems to be XXa3 so i played with XX and that's how i got to 31.

-Kevin

---

### Post by bimbo on 2007-09-27
BTW, the SMBIOS spec is available at [http://www.dmtf.org/standards/smbios](http://www.dmtf.org/standards/smbios)

I still wonder if one could program the fan controller directly, for more finely grained speed setting...

---

### Post by bimbo on 2007-09-27
There is also an smm debug thingy in i8kutils, including a test script.

And on the i8kfangui forum someone says
"Another thing is that the BIOS is still in control when I8KFanGUI is running. If the BIOS thinks that the fan shoud run at a certain speed, it will set that speed and the fan will obey. I8KFanGUI will override this setting at regular intervals. If the interval is one second, then the BIOS will have control over the fan for that interval. Try to decrease this interval in I8KFanGUI. AFAIR, this setting is hidden somewhere in "display options"."

So unless we can somehow intercept the BIOS and stop it from taking over control there won't be any better solution than to push fan control command every 100 or 200ms.

---

### Post by mehturt on 2007-11-25
I just installed all the i8k stuff on my D630 amd64 running Gutsy..
the gkrellm i8k plugin however increases the load of the machine quite dramatically

---

### Post by dyssident on 2008-01-04
I got the fan on my Vostro 1500 working perfectly using dellfand. See [this thread]("http://ubuntuforums.org/showthread.php?p=4069092").

---

