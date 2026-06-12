---
title: "Nvidia 8800GT Sli will not boot to gui on driver install"
date: 2008-10-31
forum: x86 64-bit Users
---

### Post by Spinalcracker on 2008-10-31
After installing Intrepid 8.10 and doing all available updates through synaptic, I went to install the Nvidia driver (177.80).  I have tried doing this four separate ways, all with the same result.

1. Hardware manager and choosing enable.
2. Synapic, selecting the driver and modules
3. EnvyNG
4. ctl-alt-F2, login, stopping gdm, sudo sh NVIDIA-177.80.run etc etc

In each and every case the driver installs without error.  Upon reboot, the screen blinks a couple times after the ubuntu progression splash is done and then drops to a text command prompt to login.

What's worse is at the command line if I manually edit xorg.conf (which is still supposed to override HAL to my understanding), to use the "nv" driver, or the "vesa" driver it still only boots to the command prompt.  If I try to purge the nvidia driver at that point, same thing.  Only boots to command prompt.  Only way for me to get a graphical interface back is to do a full re-install.  I had zero issues in Hardy and manually updated the driver on every new version put out, ran games through wine etc.  I am baffled on this one.

I am realllllly hoping someone can help.  I would like to continue using Ubuntu.

Motherboard:  EVGA 780i
Processor:    Intel 8400duo
Video Card:   8800GT x 2 SLI

Thanks guys :)

---

### Post by sirchmeister on 2008-10-31
I have the EXACT same setup as you minus the motherboard. I have the 680i.

I also have the EXACT same problem and have not found any help yet. Have you tried 32bit yet? (I haven't)

---

### Post by Spinalcracker on 2008-10-31
> **sirchmeister said:**
> I have the EXACT same setup as you minus the motherboard. I have the 680i.

I also have the EXACT same problem and have not found any help yet. Have you tried 32bit yet? (I haven't)

I have not tried the 32bit version.  I am really hoping to not have to go there because I have 4gigs of ram and really need the 64bits to get the most of that.

---

### Post by sirchmeister on 2008-10-31
> **Spinalcracker said:**
> I have not tried the 32bit version.  I am really hoping to not have to go there because I have 4gigs of ram and really need the 64bits to get the most of that.

4GB here as well..

I thought that 4GB could be utilized under Linux?

---

### Post by Spinalcracker on 2008-10-31
> **sirchmeister said:**
> 4GB here as well..

I thought that 4GB could be utilized under Linux?

It can on a 64bit install.  The 32bit is what limits max ram.

---

### Post by Rott3n on 2008-10-31
Same exact problem different hardware though.
7600gt's
dfi expert mobo
2 gigs of ram
Everything goes fine after update but as soon as I activate nvidia drivers I can't login after reboot.

---

### Post by dagrump on 2008-10-31
Bet if you sniffed around in the intrepid archive you might scare something up. Them bones aren't even dry yet.
* I found scribbles, you need to identify your primary video card in your xorg.conf file, it appears to be BusId 1:0:0   Of course lspci to to get busid. I'm lookin at junk I tried. Search the intrepid archives, I know this was discussed there.

---

### Post by iSTRONG on 2008-11-01
*deleted*

---

### Post by iSTRONG on 2008-11-01
i have the same problem but with different hardware.

P5K deluxe + 8800 GTS + 8400 GS

Anyone found a fix yet?

---

### Post by iSTRONG on 2008-11-02
i fixed my problem like this: [http://ubuntuforums.org/showthread.php?t=966315](http://ubuntuforums.org/showthread.php?t=966315)

maybe that's your problem as well.

---

### Post by dagrump on 2008-11-02
Thats what I said yesterday, look at post 7 above. 
I also decided to give it another shot & got it working. I'm still not understanding why it didn't work the times before, but WTH it worked this time.
Of course don't forget the Option  "SLI" "SFR", line.

---

### Post by RaveJunkie on 2008-12-24
I have the same problem and hardware, except i have 8 gigs DDR3 and SLI 9800gt's   <<< just braggin rights really.....


I cant get my ubuntu to see both cards...... it all looks great but i think one card would do the same..... i guess im not really complaining, more confused.


ps.    LOVING ubuntu x64   >   stomps my vista ultimate in everything but playing games, and runs lower resources.

---

