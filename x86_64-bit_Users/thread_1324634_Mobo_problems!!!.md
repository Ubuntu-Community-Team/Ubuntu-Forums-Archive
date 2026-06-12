---
title: "Mobo problems!!!"
date: 2009-11-12
forum: x86 64-bit Users
---

### Post by Chame_Wizard on 2009-11-12
Bought a month ago an another mobo(939N68PV-GLAN) for my JMW5,this week I have to downgrade my CPU from a AMD Athlon 64 3700+(2.2 GHZ,1 MiB L2[pin was broken))to a 3200+(2 GHZ,512 KB L2).
Have to use the on-board Graphic card(Gforce 7 series),since the 7300 GT isn't recognize yet.
2048 MiB 3200,DDR 400 MHz 
Use of on-board Souncard
Sony Optiarc AD-7201A DVD±R/RW Dual Layer
1st HDD: 250 GiB WD 2500 AAAJS SATA1(which has 7.10 on it+XP Pro won't be booting any more)
2nd HD:500 GiB WD 5000 AAAKS SATA2(2 partitions of 250 GiB EXT3,Intrebex 8.10 is on the first one)


So this what I did.


1st and 2nd boot:Routine check

3rd boot:is fine,but have to restart X-server due to graphic problems,but it freezes anyway.

4th boot: Works fine this time,while hardware devices(sound) and Adept Manager are trying to be up to date/make corrections ,it's freezing....again.

5th boot:Adept Manager is busy and was installing the updates(462 MiB big include de kernel),but the the screen becomes snowy and eventually all blank.

So after this ,I checked the BIOS and changed the graphic card settings,restart it,only to found it to get this message:
```

Reboot and select proper boot device
Or Insert Boot Media in selected Boot device and press a key
```

Restart my PC again and checking the BIOS result:both my 2 SATA HDDs are gone/missing and my DVD±R/RW Dual Layer drive isn't recognize well.

So I decided to clear the CMOS(by first noting every BIOS configuration) and then remove the CMOS battery.

But still both my 2 SATA disk are gone/missing in the BIOS(even after changing the SATA data ports).

The only things what I did was changing the SATA Operation mode to AHCI,the graphic card issue and my boot settings(USB will be the 3rd device to boot).After that Save the BIOS configuration still getting the above message.

Tried 2 different Kubuntu Intrebex live CDs(both X86_64),but it gives errors on boot(initframs/busybox and no booting the CD at all).


:confused:

---

### Post by HappyFeet on 2009-11-12
If your sata drives are not showing up in the BIOS, your mobo is most likely hosed. You could try reflashing your BIOS to see if that helps.

---

### Post by sanderj on 2009-11-13
Can you play with the BIOS SATA settings to if that helps?
And: your SATA and power cables are well connected between mobo and drives?

If even your IDE DVD drive is not well recognized, can you connect an old IDE (PATA) drive to see if that works?

---

### Post by JBAlaska on 2009-11-13
Boot to the LiveCD and start gparted, does it see your sata drives? if so save your /home partition data and reinstall Ubuntu. I've never been able to pull off a Mobo swap without re-installing.

---

### Post by sanderj on 2009-11-13
> **JBAlaska said:**
> Boot to the LiveCD and start gparted, does it see your sata drives? 

If the BIOS does not see the SATA drives (like the OP says), I don't think an OS nor an application will see the drives either.

---

### Post by Chame_Wizard on 2009-11-13
> **HappyFeet said:**
> If your sata drives are not showing up in the BIOS, your mobo is most likely hosed. You could try reflashing your BIOS to see if that helps.


I already done that. :P

[this is the mobo]("http://www.asrock.com/MB/overview.asp?Model=939N68PV-GLAN") in question.

---

