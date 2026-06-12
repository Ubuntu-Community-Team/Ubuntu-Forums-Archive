---
title: "Errors while installing Oblivion under Wine."
date: 2013-07-04
forum: Wine
---

### Post by Zenithex on 2013-07-04
I have been trying to install Oblivion (5th anniversary just in case it matters...) using Wine 1.4 and Ubuntu 12.0.4,
When I first tried it I received this screen and error;

[http://tinypic.com/view.php?pic=2v3seh2&s=5](http://tinypic.com/view.php?pic=2v3seh2&s=5)

Here is a copy of terminal when installing it;

```
cathal@Zenithex:~$ cd /media/Oblivion
cathal@Zenithex:/media/Oblivion$ wine setup.exe
cathal@Zenithex:/media/Oblivion$ fixme:heap:HeapSetInformation 0x2d4000 0 0x23fcb0 4
fixme:atl:AtlModuleInit SEMI-STUB (0x40f900 0x40f010 0x400000)
err:ole:marshal_object couldn't get IPSFactory buffer for interface {7871bfad-dad5-402f-9007-2593e9a07532}
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:StdMarshalImpl_ReleaseMarshalData could not map object ID to stub manager, oxid=2600000027, oid=2
err:ole:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
fixme:heap:HeapSetInformation 0x2d4000 0 0x23fcb0 4
fixme:atl:AtlModuleInit SEMI-STUB (0x40f900 0x40f010 0x400000)
err:ole:marshal_object couldn't get IPSFactory buffer for interface {7871bfad-dad5-402f-9007-2593e9a07532}
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:StdMarshalImpl_ReleaseMarshalData could not map object ID to stub manager, oxid=3d0000003e, oid=2
err:ole:CoReleaseMarshalData IMarshal::ReleaseMarshalData failed with error 0x8001011d
fixme:heap:HeapSetInformation 0x2d4000 0 0x23fcb0 4

```

I have restarted my PC twice going straight to installing before opening anything else, but still the same error

Thanks for any help, I am completely new to Ubuntu and Wine!
-Zenithex

---

### Post by mastablasta on 2013-07-04
check UESP website (unnoficial elder scrolls page). unfortunatelly i can not give you the exactl link to the installation page right now as that site is blocked where i work. However i do know they have good instructions on how to install and run Oblivion in linux.

---

### Post by mastablasta on 2013-07-04
check UESP website (unnoficial elder scrolls page). unfortunatelly i can not give you the exactl link to the installation page right now as that site is blocked where i work. However i do know they have good instructions on how to install and run Oblivion in linux.

---

### Post by Zenithex on 2013-07-04
Thanks for the help,
That was the guide I followed, couldn't see anything about the error...
I will look again but thanks for the help anyways!

---

### Post by mastablasta on 2013-07-05
another option is to try to install it using playon linux. they could have some settings in there to install it. the version of the game probably matters.

if you check the wine appdb you will see various version and you can also see that sometimes with newer verison of wine certain game version with gold rating on old wine got a silver rating on new wine. so play on linux might solve this.

best just google "oblivion (add your exact version) wine appdb"
there are plenty of tips , tricks and worarrounds there. though i am guessing install should still work ok.

---

### Post by Zenithex on 2013-07-05
Thanks, will try that later when I get home.
Thanks for the help

---

### Post by Handssolow on 2013-09-09
I had problems trying to install Oblivion under Wine on my son's PC, I nearly gave up. Instead I used PlayOnLinux which makes things simple. It automatically downloads and installs the appropriate version of Wine, Wine Geeko and some other essential which I didn't note down. If you want to patch Oblivion, which you will no doubt, look for the file in the .wine folder of PlayonLinux rather than in .wine in Home.
enjoy.

---

### Post by DarkAmbient on 2013-09-09
You probably need to install some frameworks and libraries first. If you don't wanna use PoL, winetricks is sufficient.

```
winetricks oblivion
```

---

### Post by howefield on 2013-09-10
Thread moved to the "*Wine*" forum.

---

