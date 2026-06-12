---
title: "Microsoft Office 2007 (Wine) error - Ubuntu 12.04"
date: 2013-02-10
forum: Wine
---

### Post by LifeEnemy on 2013-02-10
Hi all,

I'm having some trouble with my office programs. I installed M$ office with WINE about a month ago (the open-source alternatives don't work well enough for me). It worked fine for a while, but recently started crashing. First, it was powerpoint (which I rarely use), but not Excel crashes too. The program just darkens after it opens, then crashes. The error report is below. Any suggestions? Thanks in advance! :D

```
Unhandled exception: 0xe0000002 in 32-bit code (0x7b83bb85).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b83bb85 ESP:0032de24 EBP:0032de98 EFLAGS:00000246(   - --  I  Z- -P- )
 EAX:7b8267ad EBX:7b8b3ff4 ECX:0032deac EDX:00000000
 ESI:00000000 EDI:e0000002
Stack dump:
0x0032de24:  00000000 00000004 23047b0e e0000002
0x0032de34:  00000000 00000000 7b83bb85 00000000
0x0032de44:  7bc95f16 0032e01c 00000040 0032de98
0x0032de54:  681739e4 00000040 7bc770b1 00000005
0x0032de64:  0032e01c 00000040 6827d9f9 00000000
0x0032de74:  0000006a 0032df88 7ffd8000 00000000
Backtrace:
=>0 0x7b83bb85 in kernel32 (+0x2bb85) (0x0032de98)
  1 0x33231034 in mso (+0xc31033) (0x0032e038)
  2 0x7bc413a6 in ntdll (+0x313a5) (0x0032e138)
  3 0x7bc42950 NtDeviceIoControlFile+0x6f() in ntdll (0x0032e1a8)
  4 0x7b841e70 DeviceIoControl+0x25f() in kernel32 (0x0032e228)
  5 0x7b87e079 in kernel32 (+0x6e078) (0x0032e4b8)
  6 0x7b881d0b GetDriveTypeW+0x12a() in kernel32 (0x0032e518)
  7 0x32ee3234 in mso (+0x8e3233) (0x0032e748)
  8 0x32ee3dd7 in mso (+0x8e3dd6) (0x0032e760)
  9 0x32ee3ee8 in mso (+0x8e3ee7) (0x0032e784)
  10 0x32ee4141 in mso (+0x8e4140) (0x0032e7a4)
  11 0x02bc0426 (0x0032ede0)
  12 0x3263308e in mso (+0x3308d) (0x0032fab0)
  13 0x3267ae1b in mso (+0x7ae1a) (0x0032fac4)
  14 0x326c26ce in mso (+0xc26cd) (0x0032fb20)
  15 0x326bf4e5 in mso (+0xbf4e4) (0x0032fb34)
  16 0x326be064 in mso (+0xbe063) (0x0032fba0)
  17 0x326be36a in mso (+0xbe369) (0x0032fbc8)
  18 0x326bd7b2 in mso (+0xbd7b1) (0x0032fbd4)
  19 0x3002ad99 in excel (+0x2ad98) (0x0032fc78)
  20 0x30026ca6 in excel (+0x26ca5) (0x0032fd60)
  21 0x30003ad8 in excel (+0x3ad7) (0x0032fdd0)
  22 0x300037ec in excel (+0x37eb) (0x0032fe60)
  23 0x7b85efac call_process_entry+0xb() in kernel32 (0x0032fe78)
  24 0x7b86022b in kernel32 (+0x5022a) (0x0032feb8)
  25 0x7bc78970 call_thread_func_wrapper+0xb() in ntdll (0x0032fed8)
  26 0x7bc7b81d call_thread_func+0x7c() in ntdll (0x0032ffa8)
  27 0x7bc7894e RtlRaiseException+0x21() in ntdll (0x0032ffc8)
  28 0x7bc4dcae call_dll_entry_point+0x33d() in ntdll (0x0032ffe8)
  29 0x6802b4ed wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
  30 0x6802b5ab wine_switch_to_stack+0x2a() in libwine.so.1 (0xbfe6fdf8)
  31 0x7bc53b25 LdrInitializeThunk+0x3c4() in ntdll (0xbfe6fe68)
  32 0x7b8667ca __wine_kernel_init+0xa49() in kernel32 (0xbfe71018)
  33 0x7bc542db __wine_process_init+0x25a() in ntdll (0xbfe710a8)
  34 0x68028a4c wine_init+0x2db() in libwine.so.1 (0xbfe71118)
  35 0x7bf00d0b main+0x8a() in <wine-loader> (0xbfe71568)
  36 0x6819a4d3 __libc_start_main+0xf2() in libc.so.6 (0x00000000)
0x7b83bb85: movl	0xfffffff0(%ebp),%ecx
Modules:
Module	Address			Debug info	Name (135 modules)
PE	  8f0000-  f44000	Deferred        msores
PE	 11a0000- 1b7d000	Deferred        msointl
ELF	20000000-200fc000	Deferred        msi<elf>
  \-PE	20010000-200fc000	\               msi
ELF	200fc000-2019d000	Deferred        urlmon<elf>
  \-PE	20110000-2019d000	\               urlmon
ELF	2019d000-202a4000	Deferred        comctl32<elf>
  \-PE	201a0000-202a4000	\               comctl32
ELF	202a4000-2031f000	Deferred        wininet<elf>
  \-PE	202b0000-2031f000	\               wininet
ELF	2031f000-2033d000	Deferred        msimtf<elf>
  \-PE	20320000-2033d000	\               msimtf
ELF	2033d000-20373000	Deferred        mscoree<elf>
  \-PE	20340000-20373000	\               mscoree
ELF	20373000-203e2000	Deferred        setupapi<elf>
  \-PE	20380000-203e2000	\               setupapi
ELF	203e2000-20400000	Deferred        libgcc_s.so.1
ELF	20497000-204b9000	Deferred        mmdevapi<elf>
  \-PE	204a0000-204b9000	\               mmdevapi
ELF	204b9000-204c0000	Deferred        libasyncns.so.0
ELF	204c0000-20638000	Deferred        libvorbisenc.so.2
ELF	2097f000-209cd000	Deferred        libpulse.so.0
ELF	24033000-24262000	Deferred        shell32<elf>
  \-PE	24040000-24262000	\               shell32
ELF	28243000-282aa000	Deferred        dbghelp<elf>
  \-PE	28250000-282aa000	\               dbghelp
ELF	2e9f3000-2ea1b000	Deferred        winepulse<elf>
  \-PE	2ea00000-2ea1b000	\               winepulse
PE	30000000-31118000	Export          excel
PE	32600000-33618000	Export          mso
ELF	33e67000-33e7b000	Deferred        psapi<elf>
  \-PE	33e70000-33e7b000	\               psapi
ELF	392b2000-392bc000	Deferred        libwrap.so.0
ELF	39ff0000-3a03e000	Deferred        libflac.so.8
PE	3a780000-3a889000	Deferred        riched20
PE	3a9d0000-3b750000	Deferred        oart
PE	3bd10000-3bea5000	Deferred        ogl
ELF	445fa000-44672000	Deferred        shlwapi<elf>
  \-PE	44610000-44672000	\               shlwapi
ELF	46e19000-46e4f000	Deferred        uxtheme<elf>
  \-PE	46e20000-46e4f000	\               uxtheme
ELF	4a01e000-4a043000	Deferred        imm32<elf>
  \-PE	4a020000-4a043000	\               imm32
ELF	57fa6000-57fbe000	Deferred        wtsapi32<elf>
  \-PE	57fb0000-57fbe000	\               wtsapi32
ELF	5c333000-5c33b000	Deferred        libogg.so.0
ELF	61ce1000-61d46000	Deferred        libpulsecommon-1.1.so
ELF	652c5000-652e6000	Deferred        cabinet<elf>
  \-PE	652d0000-652e6000	\               cabinet
ELF	658e6000-65911000	Deferred        libvorbis.so.0
ELF	68000000-68022000	Deferred        ld-linux.so.2
ELF	68022000-68166000	Dwarf           libwine.so.1
ELF	68166000-68181000	Deferred        libpthread.so.0
ELF	68181000-6832b000	Dwarf           libc.so.6
ELF	6832b000-68330000	Deferred        libdl.so.2
ELF	68330000-68339000	Deferred        libnss_compat.so.2
ELF	68339000-68346000	Deferred        libnss_files.so.2
ELF	68346000-683b4000	Deferred        advapi32<elf>
  \-PE	68350000-683b4000	\               advapi32
ELF	683b4000-684cf000	Deferred        gdi32<elf>
  \-PE	683c0000-684cf000	\               gdi32
ELF	684cf000-6860a000	Deferred        ole32<elf>
  \-PE	684f0000-6860a000	\               ole32
ELF	6860a000-68764000	Deferred        user32<elf>
  \-PE	68620000-68764000	\               user32
ELF	68764000-6877e000	Deferred        version<elf>
  \-PE	68770000-6877e000	\               version
ELF	6877e000-687ff000	Deferred        rpcrt4<elf>
  \-PE	68790000-687ff000	\               rpcrt4
ELF	687ff000-6882c000	Deferred        msvcr80<elf>
  \-PE	68810000-6882c000	\               msvcr80
ELF	6882c000-688d1000	Deferred        msvcrt<elf>
  \-PE	68840000-688d1000	\               msvcrt
ELF	688d1000-68911000	Deferred        winspool<elf>
  \-PE	688e0000-68911000	\               winspool
ELF	68911000-6894a000	Deferred        msvcr100<elf>
  \-PE	68920000-6894a000	\               msvcr100
ELF	6894a000-6896c000	Deferred        libncurses.so.5
ELF	6896c000-6898b000	Deferred        libtinfo.so.5
ELF	6898b000-68ac4000	Deferred        oleaut32<elf>
  \-PE	689a0000-68ac4000	\               oleaut32
ELF	68ac4000-68b5e000	Deferred        libfreetype.so.6
ELF	68b5e000-68b74000	Deferred        libz.so.1
ELF	68b74000-68b9e000	Deferred        libexpat.so.1
ELF	68b9e000-68c31000	Deferred        winex11<elf>
  \-PE	68bb0000-68c31000	\               winex11
ELF	68c31000-68c3a000	Deferred        libsm.so.6
ELF	68c3a000-68c4c000	Deferred        libxext.so.6
ELF	68c4c000-68d80000	Deferred        libx11.so.6
ELF	68d80000-68d9a000	Deferred        libice.so.6
ELF	68d9a000-68da0000	Deferred        libuuid.so.1
ELF	68da0000-68da4000	Deferred        libxau.so.6
ELF	68da4000-68dab000	Deferred        libxdmcp.so.6
ELF	68dab000-68daf000	Deferred        libxinerama.so.1
ELF	68daf000-68db9000	Deferred        libxrender.so.1
ELF	68db9000-68dc2000	Deferred        libxrandr.so.2
ELF	68dc2000-68dc6000	Deferred        libxcomposite.so.1
ELF	68dc6000-68dd6000	Deferred        libxi.so.6
ELF	68dd6000-68de1000	Deferred        libxcursor.so.1
ELF	68de1000-68e34000	Deferred        libcups.so.2
ELF	68e34000-68e72000	Deferred        libgssapi_krb5.so.2
ELF	68e72000-68f36000	Deferred        libgnutls.so.26
ELF	68f36000-68f44000	Deferred        libavahi-common.so.3
ELF	68f44000-69013000	Deferred        libkrb5.so.3
ELF	69013000-6903b000	Deferred        libk5crypto.so.3
ELF	6903b000-69044000	Deferred        libkrb5support.so.0
ELF	69044000-69056000	Deferred        libtasn1.so.3
ELF	69056000-690db000	Deferred        libgcrypt.so.11
ELF	690db000-690e0000	Deferred        libcom_err.so.2
ELF	690e0000-690f2000	Deferred        libp11-kit.so.0
ELF	690f2000-6913b000	Deferred        libdbus-1.so.3
ELF	6913b000-6913f000	Deferred        libkeyutils.so.1
ELF	6913f000-69157000	Deferred        libresolv.so.2
ELF	69157000-69160000	Deferred        librt.so.1
ELF	69160000-69173000	Deferred        gnome-keyring-pkcs11.so
ELF	6bf72000-6bfe4000	Deferred        libsndfile.so.1
ELF	6c10f000-6c136000	Deferred        mpr<elf>
  \-PE	6c120000-6c136000	\               mpr
ELF	6c423000-6c457000	Deferred        libfontconfig.so.1
ELF	6f02c000-6f058000	Deferred        libm.so.6
ELF	6f609000-6f61b000	Deferred        libavahi-client.so.3
ELF	70141000-7015b000	Deferred        libnsl.so.1
ELF	70890000-708b1000	Deferred        libxcb.so.1
ELF	720b8000-720be000	Deferred        libxfixes.so.3
ELF	7546f000-754b0000	Deferred        usp10<elf>
  \-PE	75480000-754b0000	\               usp10
ELF	75675000-7567b000	Deferred        libxxf86vm.so.1
ELF	779cd000-779d2000	Deferred        libgpg-error.so.0
ELF	77d2a000-77d32000	Deferred        libjson.so.0
ELF	79db5000-79dc1000	Deferred        libnss_nis.so.2
ELF	7b800000-7ba44000	Dwarf           kernel32<elf>
  \-PE	7b810000-7ba44000	\               kernel32
ELF	7bc00000-7bcd9000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bcd9000	\               ntdll
ELF	7bf00000-7bf04000	Dwarf           <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Microsoft Office\Office12\EXCEL.EXE
	0000003d    0
	0000003c    0
	0000003b    0
	0000003a    0
	00000039   15
	00000037    0
	00000036    0
	00000035    0
	00000034    0
	00000033    0
	00000032    0
	00000031    0
	00000030    0
	00000025    0
	00000024    0
	00000023    0
	00000009    0 <==
0000000e services.exe
	0000001f    0
	0000001e    0
	00000015    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001a    0
	00000019    0
	00000014    0
	00000013    0
0000001b plugplay.exe
	00000020    0
	0000001d    0
	0000001c    0
00000021 explorer.exe
	00000022    0
00000026 rpcss.exe
	0000002f    0
	0000002e    0
	0000002d    0
	0000002c    0
	0000002b    0
	0000002a    0
	00000028    0
	00000027    0
System information:
    Wine build: wine-1.5.22
    Platform: i386
    Host system: Linux
    Host version: 3.2.0-37-generic
```


Here's a list of my libraries in wine. I remember having difficulty with one during setup. Not sure if it's relevant:

*msxml 6 (native
riched20 (native)

That's all, just those two. Is that sufficient? How do I get more if needed?

Thanks again for reading.

---

### Post by mike acker on 2013-02-10
what problems did you find in LibreOffice that caused you to want to run Ofc ?

the major problems i'm aware of are compatibility of LibreOffice -> MSFT/Ofc

the other way seems OK

---

### Post by LifeEnemy on 2013-02-10
I tried it for a while and it didn't meet my needs (I left OpenOffice for the same reason when that was the default).

-files looks different going to/from LO/MSOffice (example: I need powerpoints to work in the labs I teach)
-equation editor is terrible in Libre
-other general frustrations (where things are, etc.)

I appreciate the input, but I've tried and decided against other office suites. I just need to get MS working.


Edit: whoa! my tag changed! :P

---

### Post by LifeEnemy on 2013-02-12
I might be able to install MS Office 2013 if anyone thinks that would help? Although I imagine the older version would have had more time to have the kinks worked out between it and WINE

---

### Post by Mark Phelps on 2013-02-13
Office 2013 does not work in Wine.  It takes CodeWeavers YEARS to figure out how to get each new Office version working.  By the time they got SOME of Office 2010 working, 2013 was already out.  MS doesn't make internal info on their Office changes available, so it takes a long time to figure them out.

If you really need MS Office components, MS Windows is really the only way to go.

Sorry.

---

### Post by LifeEnemy on 2013-02-13
I think you misunderstand. I'm using office 2007, not 2013. WineHQ gives office 2007 a silver rating, so it should at least be able to run. I've used it before without significant problems. Right now, word and excel seem to be working fine, it's just PowerPoint that stopped working, and that's what I'm trying to fix.

Can someone please just look at the error report and suggest *something* I can try?

Edit: I think I need more libraries but I'm not sure which ones Orr how to add them. I have a Windows partition If that helps.

---

### Post by Mark Phelps on 2013-02-13
> **LifeEnemy said:**
> I think you misunderstand. I'm using office 2007, not 2013. 
OK ... but my comment was based on your comment
> I might be able to install MS Office 2013 if anyone thinks that would help? 

> WineHQ gives office 2007 a silver rating, so it should at least be able to run. I've used it before without significant problems. Right now, word and excel seem to be working fine, it's just PowerPoint that stopped working, and that's what I'm trying to fix.
If you look through the Test Results on the linked page, you may find something that helps:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=13]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=13")
> 
Edit: I think I need more libraries but I'm not sure which ones Orr how to add them. I have a Windows partition If that helps.Sorry, don't actually use MS Office in Wine (anymore, that is, too much trouble trying to get stuff like PowerPoint and Outlook working), so I can't help you with the details.

---

### Post by LifeEnemy on 2013-03-08
Hi Mark/all,

Apologies for disappearing. Things got really busy (they still are :P  gotta pretty much rewrite my thesis proposal). I realized that what I wanted most was consistent formatting between my computer & the universities, but for whatever reason M$ office under WINE still had similar problems as libre office. SO, I just went back to Libre for now. Being able to actually use the plugin for my citation software is nice too :)  Thanks for all the help, and patience with my snark. I'm at a very stressful point in my life, for multiple reasons =/

Should I mark this thread as solved? Not sure since the issue wasn't really taken care of. Also, I can't find the where to do that in this new layout :P

---

### Post by Mark Phelps on 2013-03-08
> **LifeEnemy said:**
> Hi Mark/all,
Should I mark this thread as solved? Not sure since the issue wasn't really taken care of. Also, I can't find the where to do that in this new layout :P

If it was me, I would not mark it as solved.

I think Office is NEVER going to run well in Wine, or any of its companions.

Don't get me wrong -- I think CodeWeavers has done a AMAZING job getting anything in MS Office working!

But, every few years, MS comes out with a new version of MS Office, and CodeWeavers has to start all over again.

---

### Post by LifeEnemy on 2013-03-08
grrr @ microsoft

There are some things I wish Libre/Openoffice did better, but they are free products, and do a pretty good job for that.

Personally I like the M$ ribbon/menu thing though. I'm very visual and prefer that to digging through menus.

---

### Post by cbanakis on 2013-03-08
Office 2010 seems to work fine in wine for me.

2007 worked fine too, but it has been a while since I used it.
(There could be new problems that werent there when I used it)

Honestly, I do not think there is anything wrong with Libre, or Open Office.

The only flaw, is that not everyone uses them.

So formatting, margins, etc are always messed up when a libre document is opened with MS Office.

However, I have the exact same problem when creating something in the Mac version of MS Office, and opening in Windows.
Also different releases (Opening an office 2007 file in Office 2010) and so on, and so forth.

I think that we should erase all traces of Microsoft Office, since Libre and Open are the only Office programs that are available on all 3 major platforms.

If everyone picked 1, the world would be a better place.
And we can't all pick MS, since they do not make a Linux version.

---

### Post by Mark Phelps on 2013-03-09
> **cbanakis said:**
> 
If everyone picked 1, the world would be a better place.
And we can't all pick MS, since they do not make a Linux version.

You're presuming that everyone trying to run Office in Wine actually has a choice regarding what to pick -- which is not necessarily true.

Some folks are just trying to use Office in Linux because they're used to it and don't want to learn new tools.  THEY have a choice.

Others have been send Office documents by other people and HAVE to use Office on those documents.

---

### Post by cbanakis on 2013-03-21
> **Mark Phelps said:**
> You're presuming that everyone trying to run Office in Wine actually has a choice regarding what to pick -- which is not necessarily true.

Some folks are just trying to use Office in Linux because they're used to it and don't want to learn new tools.  THEY have a choice.

Others have been send Office documents by other people and HAVE to use Office on those documents.

I think you missed my point.

If everyone used Libre, how would someone send you an office document?

And how would you not be use to the tools, if thats all you ever used?

My point was that the only flaw with libre or open, is that sometimes you get an office file, and maybe your used to office.

I think you agreed with me without knowing it.

If MS Office was removed from existance, after a couple years, no one would miss it, and the world would be a better place. :)
Nothing about it is noticably better.  You just want it, so you can open the file made by someone else you uses it.
Or maybe your used to it.

None of that makes it better.

Its sorta like those people who buy an inferrior gaming console, and you ask them why they bought it, and they say "So I can play such and such proprietary exclusive game".
(If that game was available on all consoles, you probably would not have bought that one)

---

### Post by Claus7 on 2013-03-23
Hello,

> **LifeEnemy said:**
> Hi all,

I'm having some trouble with my office programs. I installed M$ office with WINE about a month ago (the open-source alternatives don't work well enough for me). It worked fine for a while, but recently started crashing. First, it was powerpoint (which I rarely use), but not Excel crashes too. The program just darkens after it opens, then crashes. The error report is below. Any suggestions? Thanks in advance! :D

[...]


Here's a list of my libraries in wine. I remember having difficulty with one during setup. Not sure if it's relevant:

*msxml 6 (native
riched20 (native)

That's all, just those two. Is that sufficient? How do I get more if needed?

Thanks again for reading.

maybe you have figured out the trouble up to now yourself, yet I will add some hints to your problem:
1) some times installing power point (which causes most of the trouble in whine) does not work out of the box and you should be patient and redo the installation.
2) even if it is working nicely, for some reason might stop working. Some times you have to wipe the entire wine installation to make it working again, so using different bottles and crossover for that reason might be a better solution, not that it happens all the time though.
3) using winetricks you might have to override some libraries from winecfg (riched20 is one of them-take a look [here]("http://ubuntuforums.org/showthread.php?t=1714345")) in order to make power point work well. So, your installation might be ok, yet you might need to do this configuration in order to make it work fine.
4) updates might have caused your trouble. I think that from time to time you have to update your hidden wine folder (erase it completely and then wait to be created again next time you pick up a wine executable). Link: [here]("http://forum.winehq.org/viewtopic.php?t=103").

Hope it helped,
Regards!

---

