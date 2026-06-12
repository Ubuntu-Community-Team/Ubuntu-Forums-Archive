---
title: "Guild Wars + Lubuntu - not working?"
date: 2011-09-17
forum: Wine
---

### Post by eversilentone on 2011-09-17
My main desktop is in the middle of a refit so I'm trying to get GW to run on my laptop. It's running the latest version of lubuntu with WINE 1.3.28 and I've successfully downloaded and installed GW. When I run the exe the launcher turns the screen black, the cursor changes to the ingame cursor, but then it freezes; when I go back to the desktop it says that there's an error and to contact WINE. 

I couldn't fine anything specific about WINE and lubuntu, so I wondered if that might be the problem? I should add that although my laptop is old and feeble (Dell Inspirion 1300) it did use to run GW natively on Windows XP, so I know the hardware is capable. 

I've downloaded and can play SuperTuxKart, the game they suggest you play to ensure your 3d graphics are working, and that's all fine.  Help would be appreciated as I'm likely to be without my main desktop for another 3 weeks!

---

### Post by Sworddragon on 2011-09-17
I'm having problems with Wine 1.3.28 and Guild Wars [here](http://ubuntuforums.org/showthread.php?t=1845489) too. Are you running on 32 bit or 64 bit?

---

### Post by eversilentone on 2011-09-17
32 bit I think?  Not sure how to check, but doubt Lubuntu has a 64 bit version?

EDIT: I just installed POL and now I get this error, if that's any help?

```
=*--> Crash <--*
Exception: 80000101 
App: Gw.exe
ProgramId: 1
Build: 34355
When: 9/17/2011 18:51:25
Flags: 0

*--> System <--*
Name: jk-ME051
IpAddr: 192.168.0.103
Processors: 1 [GenuineIntel:6:13:8]
OSVersion: 5.1

*--> Thread 0xfffffffe <--*
eax=00000000 ebx=000037dc ecx=000037ed edx=00000006 esi=6a85815f edi=6a87eff4
eip=72f76832 esp=014ddac4 ebp=014ddad0
cs=200202 ss=0073 ds=007b es=007b fs=007b gs=0033 efl=0000003b

esi-32 6A85813C  252f6d25 79252f64 3a482500 253a4d25 
esi-16 6A85814C  49250053 3a4d253a 25205325 00070070 
esi +0 6A85815C  00010004 61250002 20622520 25206525 
esi+16 6A85816C  4d253a48 2053253a 25205a25 696c0059 
esi+32 6A85817C  50006362 5849534f 534e4100 33585f49 
esi+48 6A85818C  312d342e 00383639 59795b5e 5b5e005d 
esi-32 6A87EFD4  6a87f0f4 6a882740 6a87f184 00000000 
esi-16 6A87EFE4  00000000 00000000 00000000 00000000 
esi +0 6A87EFF4  0015cd7c b76f5020 72f89c30 6a792e70 
esi+16 6A87F004  6a792490 6a738bae 6a791ef0 72f877f0 
esi+32 6A87F014  6a738bde 6a7923b0 6a738bfe 00000000 
esi+48 6A87F024  0000037f 00000022 00000040 00000000 

*--> Code <--*
72F76812  ffffffa3 20000000 68280000 00e990ff .... ...h(......
72F76822  ffff0000 00000000 00000000 0000cd80 ................
72F76832  c38db600 0000008d bc270000 00008b1c .........'......
72F76842  24c38db6 00000000 8dbf0000 000089e0 $...............
72F76852  e8193f00 0089c7e8 e2ffffff 81c396c7 ..?.............
72F76862  01008b83 78feffff 5a8d2484 29c2528b ....x...Z.$.).R.

*--> Trace <--*

*--> Stack <--*
014DDAC4  6a74ce71 6a87eff4 014ddbf0 014ddbf8 q.tj...j..M...M.
014DDAD4  6a75034e 00000006 014ddb70 00000000 N.uj....p.M.....
014DDAE4  6a792579 00000130 000000c8 6a78ccf2 y%yj0.........xj
014DDAF4  014ddb34 00000130 000000c8 000000c4 4.M.0...........
014DDB04  6a8803c0 6a87eff4 000000c4 000000c3 ...j...j........
014DDB14  014ddbe0 6a782212 7e159df8 000000c4 ..M.."xj...~....
014DDB24  014ddc08 7e144930 00000000 4d5f434c ..M.0I.~....LC_M
014DDB34  fbad8000 7e159df8 7e159e5d 7e159df8 .......~]..~...~
014DDB44  7e159df8 7e159ebb 7e159f24 7e159df8 ...~...~$..~...~
014DDB54  7e159f24 00000000 00000000 00000000 $..~............
014DDB64  00000000 00000000 014ddb88 00000020 ..........M. ...
014DDB74  00000000 00000000 00000000 00000000 ................
014DDB84  00000000 00000000 00000000 00000000 ................
014DDB94  00000000 00000000 00000000 00000000 ................
014DDBA4  00000000 00000000 00000000 00000000 ................
014DDBB4  00000000 00000000 00000000 00000000 ................
014DDBC4  00000000 00000000 00000000 00000000 ................
014DDBD4  00000000 00000000 00000000 00000000 ................
014DDBE4  00000000 00000000 00000000 6a87eff4 ...............j
014DDBF4  68eee5df 014ddc40 6a74588*--> Crash <--*
Exception: 80000101 
App: Gw.exe
ProgramId: 1
Build: 34355
When: 9/17/2011 18:51:25
Flags: 0

*--> System <--*
Name: jk-ME051
IpAddr: 192.168.0.103
Processors: 1 [GenuineIntel:6:13:8]
OSVersion: 5.1

*--> Thread 0xfffffffe <--*
eax=00000000 ebx=000037dc ecx=000037ed edx=00000006 esi=6a85815f edi=6a87eff4
eip=72f76832 esp=014ddac4 ebp=014ddad0
cs=200202 ss=0073 ds=007b es=007b fs=007b gs=0033 efl=0000003b

esi-32 6A85813C  252f6d25 79252f64 3a482500 253a4d25 
esi-16 6A85814C  49250053 3a4d253a 25205325 00070070 
esi +0 6A85815C  00010004 61250002 20622520 25206525 
esi+16 6A85816C  4d253a48 2053253a 25205a25 696c0059 
esi+32 6A85817C  50006362 5849534f 534e4100 33585f49 
esi+48 6A85818C  312d342e 00383639 59795b5e 5b5e005d 
esi-32 6A87EFD4  6a87f0f4 6a882740 6a87f184 00000000 
esi-16 6A87EFE4  00000000 00000000 00000000 00000000 
esi +0 6A87EFF4  0015cd7c b76f5020 72f89c30 6a792e70 
esi+16 6A87F004  6a792490 6a738bae 6a791ef0 72f877f0 
esi+32 6A87F014  6a738bde 6a7923b0 6a738bfe 00000000 
esi+48 6A87F024  0000037f 00000022 00000040 00000000 

*--> Code <--*
72F76812  ffffffa3 20000000 68280000 00e990ff .... ...h(......
72F76822  ffff0000 00000000 00000000 0000cd80 ................
72F76832  c38db600 0000008d bc270000 00008b1c .........'......
72F76842  24c38db6 00000000 8dbf0000 000089e0 $...............
72F76852  e8193f00 0089c7e8 e2ffffff 81c396c7 ..?.............
72F76862  01008b83 78feffff 5a8d2484 29c2528b ....x...Z.$.).R.

*--> Trace <--*

*--> Stack <--*
014DDAC4  6a74ce71 6a87eff4 014ddbf0 014ddbf8 q.tj...j..M...M.
014DDAD4  6a75034e 00000006 014ddb70 00000000 N.uj....p.M.....
014DDAE4  6a792579 00000130 000000c8 6a78ccf2 y%yj0.........xj
014DDAF4  014ddb34 00000130 000000c8 000000c4 4.M.0...........
014DDB04  6a8803c0 6a87eff4 000000c4 000000c3 ...j...j........
014DDB14  014ddbe0 6a782212 7e159df8 000000c4 ..M.."xj...~....
014DDB24  014ddc08 7e144930 00000000 4d5f434c ..M.0I.~....LC_M
014DDB34  fbad8000 7e159df8 7e159e5d 7e159df8 .......~]..~...~
014DDB44  7e159df8 7e159ebb 7e159f24 7e159df8 ...~...~$..~...~
014DDB54  7e159f24 00000000 00000000 00000000 $..~............
014DDB64  00000000 00000000 014ddb88 00000000 ...h@.M..Xtj....
014DDC04  6a85a4b6 7e159df8 6a85815f 68eee32c ...j...~_..j,..h
014DDC14  000000f8 68eee5df 6a85833e 68eee444 .......h>..jD..h
014DDC24  6a85833e 0000ffff bfa9569e 7e159df8 >..j.....V.....~
014DDC34  68ef5ff4 7e15eaf8 00012345 014ddca0 ._.h...~E#....M.
014DDC44  68eba2ea 68eee444 68eee32c 000000f8 ...hD..h,..h....
014DDC54  68eee5df 00000000 20011145 00000000 ...h....E.. ....
014DDC64  00000000 6a87f580 00000001 68eed6f1 .......j.......h
014DDC74  014ddc90 00012345 00012345 00000000 ..M.E#..E#......
014DDC84  00000000 7e15eaf8 68eedf4e 00000003 .......~N..h....
014DDC94  68ef5ff4 7e15eaf8 7e151b00 014ddd60 ._.h...~...~`.M.
014DDCA4  68eb8233 7e15eaf8 ffff0000 00000000 3..h...~........
014DDCB4  00003c00 60012345 20011145 15000000 .<..E#.`E.. ....
014DDCC4  68f9734f 7e115868 7d8c3888 014ddd30 Os.hhX.~.8.}0.M.
014DDCD4  68fc79ce 00000001 690d7ff4 014ddd50 .y.h.......iP.M.
014DDCE4  68fb5c31 20011145 68eee2c0 7d8c3888 1\.hE.. ...h.8.}
014DDCF4  00183ca0 68cff886 00000001 000037ed .<.....h.....7..
014DDD04  7e151b00 7e15eaf8 7e15eaf8 7e15eaf8 ...~...~...~...~
014DDD14  ffffffc8 ffffffff ffff0000 00003c00 .............<..
014DDD24  60012345 00000009 68ef5ff4 014ddd90 E#.`....._.h..M.
014DDD34  00000000 00000000 00000000 00000000 ................
014DDD44  48fa4100 00001e00 00001e00 68eb674b .A.H........Kg.h
014DDD54  68ef5ff4 7d8c3888 7e15eaf8 014ddd90 ._.h.8.}...~..M.
014DDD64  68eb8dab 00001e00 00000000 00000000 ...h............
014DDD74  00000000 7d8c3888 7e15eaf8 7e15a860 .....8.}...~`..~
014DDD84  68ef5ff4 28000000 7d8c3888 014dddc0 ._.h...(.8.}..M.
014DDD94  68eb18ae 7d8c3888 28644040 7d8c66a8 ...h.8.}@@d(.f.}
014DDDA4  68eb628f 68cff8ae 00193d20 0012d534 .b.h...h =..4...
014DDDB4  690d7ff4 7d8c3888 20000000 014dde20 ...i.8.}...  .M.
014DDDC4  68f991f0 7d8c3888 28644040 7e15a860 ...h.8.}@@d(`..~
014DDDD4  68d1dea0 68008337 0016a044 014dde80 ...h7..hD.....M.
014DDDE4  68c749f5 00000020 00172f90 00000000 .I.h ..../......
014DDDF4  00000000 7d8c3888 08000000 00000000 .....8.}........
014DDE04  7d92b900 7d9b8da4 72f87806 014dde80 ...}...}.x.r..M.
014DDE14  690d7ff4 7d8c3888 69090672 014dde40 ...i.8.}r..i@.M.
014DDE24  68f9a2da 7d8c3888 00000000 68cfb83c ...h.8.}....<..h
014DDE34  68cff886 690d7ff4 7d8c3888 014dde70 ...h...i.8.}p.M.
014DDE44  68f347e0 7d8c3888 00183ca0 014ddeb0 .G.h.8.}.<....M.
014DDE54  68c8fc8d 00000000 00002379 00000300 ...h....y#......
014DDE64  690d7ff4 7d8c3888 00001403 014dde90 ...i.8.}......M.
014DDE74  68f20a15 7d8c3888 69090672 014ddeb0 ...h.8.}r..i..M.
014DDE84  68c82a80 690d7ff4 7d8c3888 014dded0 .*.h...i.8.}..M.
014DDE94  68f20d25 764590c0 07244c28 00000ad8 %..h..Ev(L$.....
014DDEA4  68c74750 7642a619 68d1dea0 014ddf10 PG.h..Bv...h..M.
014DDEB4  00000024 0000037b 72f87806 00180468 $...{....x.rh...

*--> LogQueue <--*

*--> DirectX Device Info <--*
VendorId    = 0x8086
DeviceId    = 0x2582
Version     = 6.15.0008.0006
Description = Direct3D HAL
Compat      = 0x140000c1
VidMem      = 64 MB

*--> DirectSound Device Info <--*
3D channels  = 32
2D channels  = 32
EAX support  = None
Device count = 1
```

---

### Post by uKEN on 2011-09-17
I'm having a problem with GW proph+Lubuntu+wine..(the only camp I own).

may be a older vers of wine will work ?

I realy want to talk like a pirate :D

EDIT: I have tryed 1.3 ,1.2 ,and 1.0..nither work :(

EDIT: chek that I got the 1.0 to work but looks realy bad

---

