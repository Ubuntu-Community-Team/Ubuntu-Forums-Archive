---
title: "Data corruption, I'm going mad !"
date: 2008-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by parazythum on 2008-03-16
Hello,

This is my first post here.

I have searched the web, I didn't find anything of value, and my problem drives me crazy. Let me explain :

- I have two disks, and data loss occur sometimes when I copy very large files from one disk to the other, no matter from which one the file comes - sometimes the MD5 sum differs, sometimes not. 'large files' are about 1GB.
- this problem occurs under Ubuntu 7.10 (my preferred OS) or Windows XP SP2 (I use it for things that can't be run under Linux) - no matter what the system is !
- my specs :
    * mobo : ASROCK 4COREDUAL-VSTA. Northbridge: VIA PT880 Ultra. Southbridge: VIA VT8237A. Latest BIOS from official site - all parameters in the BIOS carefully set
    * CPU : Core2Duo 2.40GHz
    * RAM : 2*1GB 667MHz set to dual channel, used their specs to set values in BIOS -> 4/5 ratio between FSB and RAM (memory faster than the system)
    * GPU : nVidia 6800 AGP 8x
    * 1 SATA1 300Gb Maxtor
    * 1 SATA2 320GB Western Digital (set to SATA1 with the jumper at the back of the HD)
    * SATA is regognized under Ubuntu (dmesg tells me so) and XP
    * several partitions, all ext3 or NTFS + 1 linux swap
    * latest via drivers under XP
- my tests so far :
    * mem tests from Grub : all OK
    * HD tests with the official tools from Maxtor and WD : SMART tests OK, no bad sectors found
    * searched for bad sectors with each system tools :
        - e2fsck -C for ext3
        - chkdsk for NTFS tested at reboot (before the OS is fully launched)
    * looked at the logs in each system, I'm a Windows expert, and a 1+ year old Ubuntu user (not an expert but I'm loosing slowly but surely my bad Windows habits :) )
    * not heat problems, I have several extra temperature probes in my box
    * not OC'd anything ! I have a fairly decent system !
    * usually, posts from several guys on forums always end up with something like 'bah, it's a virus problem' or similar
    * I have even looked for rootkits on my system (yeah, I know, Linux is supposed to be virus-free, but I tried that anyway)
    * I didn't see anything of value on the Asrock or Via sites

The problem still occurs after zillion tests, updates, etc. Sometimes the files get corrupted, sometimes not. The occurrences increase with the size of the file copied. I tested with several file types (tgz, VMWare image, etc)

I don't know what to do next... Any idea ? I can post logs, etc. Thanks if you read this till the end.

---

### Post by nonewmsgs on 2008-03-16
hmmmm...are you transfering files from different partition types?  i know the windows utility that allows writing to ext3  (ifoedit i think?) treats it like a FAT partition including the file size limitations.  do you have an ext3 to ext3 under linux to test it?

---

### Post by John Jason Jordan on 2008-03-16
> **parazythum said:**
> I don't know what to do next... Any idea ? I can post logs, etc. Thanks if you read this till the end.
I had similar problems when I built a new system a year ago. Turned out the problem was a flaky SATA controller on the motherboard. A BIOS upgrade helped, but still did not completely resolve the problem. Finally, after nearly a month of tearing my hair out I returned the motherboard and bought an ASUS motherboard. No problems since. I'm not saying that this is your problem because I have no knowledge of your motherboard at all. I'm just suggesting another place where the source of the problem could be lurking.

Another thing you might try is the Ultimate Boot CD. I've lost the URL for it, but it is a free download. The UBCD runs a command line operating system and includes tons of hardware testing utilities, including disk-thrashing tests. If there are any marginal sectors or blocks the tests will turn them up. These tests are far more thorough than fsck.

---

### Post by parazythum on 2008-03-16
Thanks for the fast answers.

nonewmsgs : what's bugging me is that the md5 sum of the copied files aren't always the same ! Yes, I have this utility to read ext3 partitions in Windows, I will search about limitations, I didn't even think about that ! Strange enough, this client doesn't complain when I try to read big files. The problem only occurs when *writing* files, never when reading them. I already got rid of the microsoft unix utilities because a copy over the network of big files didn't go right either (I came back to Samba).

JJJ : I read about this kind of things for several mobos, but I didn't read anything about mine (Asrock 4CoreDual-VSTA). It's the first time I bought something other than Asus, I think I will in the future stick to it. This time it was just a question of "no I won't drop my AGP card, let's try this strange dual pcie / agp strange mobo with dual core support"

---

### Post by parazythum on 2008-03-16
I read carefully the ext2ifs page : there are problems under some windows OS only if the 48bit lba mode is not enabled (I launched an utility to verify that) OR the "large files" option isn't set (and it is). So it's not an ext2 driver problem.

I've just tried once more to copy big files from different partition types under Ubuntu and XP, even from and to ext3 ones (nonewmsgs's post made me doubt). The corruption doesn't occur when Im copying within the same disk !

I also copied several times a big file from my other ubuntu pc (network) to ext3, fat32 and ntfs, all went well.

Ah, yes, I forgot this information about my ubuntu system : I compiled myself and installed the latest ntfs-3g (and tested it) before posting.

Conclusion : 
- the random file corruptions only occur when I'm reading **from one disk to the other (both ways)** on my system under Ubuntu AND Windows
- once a file is correctly written (I verify with a md5sum), it will always be correct. The corruption problem occurs **only when writing** files, NOT reading

I got another idea now : I will try to disable the use of the internal cache on my disks with a SMART utility.

---

### Post by rumblered on 2008-03-17
> **parazythum said:**
> 
- the random file corruptions only occur when I'm reading **from one disk to the other (both ways)** on my system under Ubuntu AND Windows


This has to be a hardware problem, and I'll bet it's your RAM. If you boot into memtest for around 24 hours, it might be able to detect an error and confirm that. Also, you can test for the problem with only one of the RAM chips installed, then test again with the other one. Possibilities are that one of them is bad, or that it's just not handling the load of two RAM chips given the combination of hardware you're using (I once had a motherboard that wasn't stable with 3 RAM chips, however any two of them would work correctly)

What is the exact RAM you're using, and what is the voltage setting? Turning up the voltage slightly might help.

---

### Post by Jouke74 on 2008-03-17
Hmmm, I agree that it must likely a hardware problem. I think there are three major possibilities:

1. Bad memory. If you are in the Grub menu, use option 3 to test the memory as previous poster said. However, bad memory often leads to computer crashes, and as far as I read this is not the case.

2. Bad Sata controller. To test this you could ask the shop where you bought the computer to put in a new PCI Sata controller card and connect your non-booting harddrive to this card. Then, after driver installation, run a few tests which always tend to fail. 

(Or indeed buy a new mobo).

3. A cheaper option to test first is replace both of your Sata cables and make sure they are well connected to your ports (harddisk side as well as computer side). This also leads to strange things if there is a small fracture in one of the cable connections.

---

### Post by parazythum on 2008-03-17
Yesterday evening, I flashed the firmwares of my two HDs, I have read many things about Maxtor and Seagate drives having problems in early versions. It didn't solve my case, but it resulted in a speed boost under the two OS (e.g. : synaptic loads in 3 seconds instead of 6 before !!!)

I also tried a copy of big files from my DVD drive : corrupted files also ! My two HDs are SATA, my DVD burner is IDE (different interfaces, same problem !!!)

Jouke74 : I have already done a mem test under Grub for 6 hours, nothing. I'll try 24 hours for each chip if nothing else works. The SATA cables are short ones, I already replaced them as well as extracted and reinserted my RAM chips in their sockets in case of bad contacts.

Rumblered and Jouke74 : I'll try first to raise the voltage, I have read about it on another forum, but I am a little doubtful about that kind of trick. What do you think also, if the latter don't work, that I come back to 533 MHz instead of 667 for the RAM ? (the bus speed would match better the FSB).

---

### Post by Jouke74 on 2008-03-17
Good to see that the memory is ok. I suspected that already.

I don't know about upping the voltages, I have never tried it myself. But what voltages you want to up? If the memory is working fine then it should not matter for the memory and memtest would have seen that. Are you by the way sure you have locked your PCI bus, so your harddrives are not "overclocked"? 

What is the power supply unit you use?

Also did you test copying large files from USB stick? The point here is that I want to make sure the problem is only, from and to IDE, related (Sata and IDE use the same interfaces). 

It is very interesting, cause in my opinion this already should have lead to Ubuntu and windows installing badly (why wouldn't you have corruption there?) If it is really only big files this might explain the good installs, but this is very weird. I am afraid that the end conclusion of this is that you will have to buy a new motherboard...

---

### Post by parazythum on 2008-03-17
I have read on another forum that the memtest+ from grub doesn't detect all the problems. I didn't keep track of this post, but it was very interesting.

The voltage tip makes sense too, because I have a big-power-hungry GPU that could interfere with the rest (but I also have a good power supply ~600W) --- I will increase it a little, can't hurt if done right (max 10%)

What's this PCI bus frequency locking ? I thought it was set to a certain value and didn't move... I'll search that way too, seems interesting and could cause out-of-sync data transfers. If it looks promising it will be my #1 test, but not this evening it's St Patrick's day \\:D/

I have a USB hard drive that could be used to test big files transfers, but I think it will work, as do the network transfers.

Jouke74 : you're right, I had problems installing Ubuntu from the alternate CD, but NOT with the desktop version. I didn't think about bad transfers at this time...

I will add comments after all the tests in the pipe are done :)
- more voltage in the RAM chips
- PCI bus locking (I'll have to check other forums)
- lower the RAM frequency (but it's Corsair, that should not be a solution !)
- last on the list if everything else failed : change the mobo and resell the older one on e-bay :lolflag:

---

### Post by parazythum on 2008-03-20
Hi there,

I finally had the time to test and... nothing. Nothing. Triple-nothing.

I forced the PCI bus to 33.33MHz. I increased the voltage in the RAM chips. I lowered the RAM chips frequency (667->533). Nada.

One interesting thing : I have a device that permits to connect a HD in SATA or IDE mode through USB. I copied two big files on it : they were also corrupted.

So I think I'll have to test the RAM chips further... and that's all I can think about now. I think the whole PC will soon get through my window !!!

Any more ideas, apart writing to ASROCK ?

---

### Post by Jouke74 on 2008-03-20
Write ASROCK and make sure you throw the motherboard through their window :lolflag:

I am sorry, it sounds like a defect SATA controller which also usually regulates IDE connections on motherboards (southbridge). Buy a new Mobo, preferably MSI or Asus.

---

### Post by rsk02 on 2008-03-21
Did you try changing cables as suggested earlier in the thread? I had a similar problem sometime ago and after much needless swapping of more expensive components I found that the cable ws bad. In my case, it was a PATA cable connected to a PATA disk. Transfers from the SATA drives were also getting corrupted.

---

### Post by rumblered on 2008-03-21
> **parazythum said:**
> 
One interesting thing : I have a device that permits to connect a HD in SATA or IDE mode through USB. I copied two big files on it : they were also corrupted.


Yes, that is interesting. To absolutely eliminate the possibility that it's a HD controller problem, you can put a file on a ramdisk (you should have one in /dev/shm by default), then md5 it, then copy it to a drive over your USB device.

> **parazythum said:**
> 
So I think I'll have to test the RAM chips further... and that's all I can think about now. I think the whole PC will soon get through my window !!!

Any more ideas, apart writing to ASROCK ?

Did you try it with just one RAM chip installed yet?

---

### Post by parazythum on 2008-03-22
Hello,

I tried wit one RAM chip only, both of them, and it did the same, the files were corrupted.

I did this several times : I transfered a file to the ram disk : MD5 OK. I copied from there to my sata HD : there was sometimes a difference.

So the transfers to USB, which don't use the HD controller, are corrupt too. Now the #1 suspects are my two RAM chips. I'll try to do a looong RAM test, but not with MemTest+.

---

### Post by rumblered on 2008-03-22
Well, you can make your RAM test very similar to the problem scenario by doing a ramdisk-to-ramdisk copy as your test.

---

### Post by parazythum on 2008-03-23
I tried more tests :
- downgraded the BIOS to v1.80 instead of v2.30 : nothing
- I have DDR2 chips, tried two DDR chips in their place, same problem
- used another RAM tester from Microsoft (it's called "Microsoft Windows Memory Diagnostic", nice dos program with many good tests, m$ can provide good things sometimes) - no errors found after 12h.

I noticed that the USB and the SATA controllers share the same IRQ, but I don't know how to change that. I tried to disable the USB controller in the BIOS, no improvement.

Didn't try the ramdisk to ramdisk copy yet, but I think I'm gonna buy me a new system soon ! I'm tired of this problem. Maybe Asrock will answer me before I throw their mobo, I wrote them too.

---

### Post by parazythum on 2008-05-01
OK, I have solved this issue : I bought yesterday a nice new motherboard, an ASUS P5K Pro. I installed on it Hardy Heron, 64 bits version. I used the AHCI option in the BIOS for my two SATA disks, it worked under Ubuntu and WinXP.

I then tried again my file copy tests. I even copied multiple files from and to multiple partitions at the same time to stress the system. Result : nice and right MD5 sums :)

So : I'll dump the Asrock motherboard. Shame on them, they never replied to my messages, I shouldn't have bothered to contact them. DON'T BUY ASROCK !

---

