---
title: "wine cfg wont run and any wine apps"
date: 2008-03-19
forum: Wine
---

### Post by Onyxblack on 2008-03-19
I have had wine working before - just started up my comp now none of the apps run and winecfg wont even run...

I have tried a removal of wine
i have tried a reinstall of wine
i have tried a complete removal and re installation 

this is what i get when typing winecfg

onyx@gamer:~$ winecfg
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:advapi:RegisterEventSourceW ((null),L"Print"): stub
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:winsock:WSASocketW Unsupported socket family -1!
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:winsock:WSASocketW Unsupported socket family -1!
fixme:winsock:convert_af_w2u unhandled Windows address family 26
fixme:winsock:WSASocketW Unsupported socket family -1!
fixme:ds:DsRoleGetPrimaryDomainInformation ((nil), 1, 0x34ee20) stub
fixme:advapi:LsaOpenPolicy ((null),0x34edbc,0x00000001,0x34edb8) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:profile:CloseProfileUserMapping (), stub!
fixme:advapi:ObjectOpenAuditAlarmW stub (L"Spooler",0x4c0148,L"Server",L"\\\\gamer",0x2139d8,0xb4,0x00000001,0x00000001,(nil),0,1,0x75bfb4fc)
fixme:advapi:ObjectCloseAuditAlarmW stub (L"Spooler",0x4c0148,0)
err:winspool:add_printer_driver Failed adding driver "wineps.drv" ("Windows NT x86"): 1805
fixme:winspool:AddPrinterW Can't create printer L"photosmart_7700_series"
err:winspool:CUPS_LoadPrinters printer 'photosmart_7700_series' not added by AddPrinterA (error 1801)
onyx@gamer:~$

---

### Post by Onyxblack on 2008-03-19
Nevermind - i figured out my own problem

I was installing some software the night before and it required some dll files from my windows machine - so what i did was just copy the entire system dirrectory to my wine c drive and skiped everything.... apperently it didn't like that...

at least... in the process of doing so - i was able to figure out how to run photoshop 7 :)

Image to prove :) [http://rsbb.servebeer.com/ubuntu/ps.png](http://rsbb.servebeer.com/ubuntu/ps.png) 
(note that it is a large file i do run 3840x1024 and it is a full screenshot of my desktop

---

### Post by happyhamster on 2008-03-19
:shock: How do you run 3840x1024? Is that a triple monitor setup? It looks amazing.

---

### Post by Onyxblack on 2008-03-19
I use matrox triplehead2go

analog
[http://cgi.ebay.com/Matrox-TripleHead2Go-T2G-A3A-AJF-Analog-NEW_W0QQitemZ310032759407QQihZ021QQcategoryZ3697QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/Matrox-TripleHead2Go-T2G-A3A-AJF-Analog-NEW_W0QQitemZ310032759407QQihZ021QQcategoryZ3697QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

digital
[http://cgi.ebay.com/MATROX-TRIPLEHEAD2GO-DIGITAL-EDITION-T2G-D3D-IF-NEW_W0QQitemZ290214101178QQihZ019QQcategoryZ3762QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/MATROX-TRIPLEHEAD2GO-DIGITAL-EDITION-T2G-D3D-IF-NEW_W0QQitemZ290214101178QQihZ019QQcategoryZ3762QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

The only video card manufacturer that supports it is nvidia, and i would recommend nothing else. In ubuntu I have had to tinker with the driver a bit to get it to display correctly, and there are breaks in the screen but you get used to it and dont even realize their there. (its also verry hard to find backgrounds for this resolution.

I have 3 19" LG flatron moniters that run 5000:1 contrast and 2 ms responce

It makes for awsome gaming seeing that the TH2G makes the computer read it as 1 display and break it in to 3 you get the same FPS rate as if you where running 1 moniter. (if you ever tried to move anything graphic between a 2 moniter setup you know what im talking about) and with 3 moniters your cross hairs are in the middle moniter and not split between 2 moniters (if your running dual)

screen shot
[http://rsbb.servebeer.com/desktop2.JPG](http://rsbb.servebeer.com/desktop2.JPG) (thats a windows screen shot with 'desktopspace')
[http://rsbb.servebeer.com/SS/WoWScrnShot_012108_200310.jpg](http://rsbb.servebeer.com/SS/WoWScrnShot_012108_200310.jpg) (screen of world of warcraft - no menu)

---

### Post by happyhamster on 2008-03-19
Awesome. Funny thing is I sort of have it the other way around: I have 1 monitor for 2 pc's :)

BTW, just noticed that you mentioned the 3 monitors in your sig already. Completely missed that. I have a blind spot for sigs I guess.

---

### Post by Onyxblack on 2008-03-19
I think i got ya beat there too ;)

When i first got it
[http://rsbb.servebeer.com/server/Img0040.jpg](http://rsbb.servebeer.com/server/Img0040.jpg)

Now - 4 months later - 

[http://rsbb.servebeer.com:8080/server/2.jpg](http://rsbb.servebeer.com:8080/server/2.jpg)

7 computers :) 1 moniter

---

