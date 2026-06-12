---
title: "Americas Army 2.8 with Wine"
date: 2007-04-06
forum: Wine
---

### Post by Ted_Smith on 2007-04-06
Trying to launch Americas Army 2.8 using wine (as support for Linux stopped at 2.5). Install went OK, and the patch was applied ok bringing it to 2.8.1. However, at sratup I get : 

```

 Build AmericasArmy[BuildDate:03-15-07_BuildVersion:2.8.1]

OS: Windows 2000 5.0 (Build: 2195)
CPU: AuthenticAMD PentiumPro-class processor @ 1660 MHz with 1517MB RAM
Video: Direct3D HAL (9746)

unrecoverable error - bombing out

History: UObject::StaticAllocateObject <- (Class AGP_Pawn) <- UObject::StaticConstructObject <- ULinkerLoad::CreateExport <- (AGP_Pawn 2339484) <- ULinkerLoad::CreateImport <- IndexToObject <- ULinkerLoad<<UObject <- (LinkerLoad Package.LinkerLoad 364345)) <- SerializeExpr <- (31) <- SerializeExpr <- (0E) <- UStruct::Serialize <- (Function AGP_Gameplay.AGP_InventoryModifier.Run) <- UFunction::Serialize <- LoadObject <- (Function AGP_Gameplay.AGP_InventoryModifier.Run 364345==364345/525020 364238 542) <- ULinkerLoad::Preload <- LinkProperties <- UStruct::Link <- UState::Link <- UClass::Link <- UStruct::Serialize <- (Class AGP_Gameplay.AGP_InventoryModifier) <- UState::Serialize <- UClass::Serialize <- (Class AGP_Gameplay.AGP_InventoryModifier) <- LoadObject <- (Class AGP_Gameplay.AGP_InventoryModifier 364345==364345/525020 199879 211) <- ULinkerLoad::Preload <- ULinkerLoad::Preload <- ULinkerLoad::CreateExport <- (AGP_InventoryModifier0 346697) <- IndexToObject <- ULinkerLoad<<UObject <- (LinkerLoad Package.LinkerLoad 346697)) <- ULevelBase::Serialize <- ULevel::Serialize <- LoadObject <- (Level Entry.myLevel 346697==346697/347806 346679 91) <- ULinkerLoad::Preload <- PreLoadObjects <- UObject::EndLoad <- UObject::StaticLoadObject <- (Engine.Level None.MyLevel Entry) <- LoadLevel <- UGameEngine::LoadMap <- UGameEngine::Init <- InitEngine


```

Any thoughts?

---

### Post by Punker on 2007-04-06
isent their is AA for Linux??????????? you can call them they know more

---

### Post by hikaricore on 2007-04-06
AA stops at 2.5 for linux punker.

OP is trying to play 2.8 under wine

[http://appdb.winehq.org/appview.php?iAppId=908](http://appdb.winehq.org/appview.php?iAppId=908)

Here's the wine application database section for AA, it looks like there are some issues
with running 2.7 and 2.8, but very little other information.

I'm not familiar with the game in any useful way, but you should search to see if there's
an opengl mode (i believe there is) the game should be run in this mode when attempting
to play under wine.

---

### Post by Eviltechie on 2008-10-28
I can't seem to get it to work right. I got it installed ok, but none of the buttons on the main menu work right, so I can't play. Anyone know how to fix this?

---

