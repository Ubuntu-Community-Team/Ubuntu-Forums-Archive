---
title: "Uninstaller fails to uninstall -- my options?"
date: 2008-01-08
forum: Wine
---

### Post by cyberkost on 2008-01-08
Ok, I've installed a windows app using wine (ABBYY Lingvo 10).  Now I know that I should have checked AppDB first (Lingvo 10 runability is rated as "garbage") .. but, I guess, I'm going through this painful process called "learning".

When I run uninstaller and select Lingvo 10 to be removed, uninstaller launches Lingo's setup program, in which I select the "Remove" radio-button ...  but it crashes without completing the job.:

```

me@computer:~$ uninstaller
fixme:advapi:LookupAccountNameW (null) L"me" (nil) 0x34f38c (nil) 0x34f390 0x34f384 - stub
fixme:advapi:LookupAccountNameW (null) L"me" 0x12fcd8 0x34f38c 0x12a040 0x34f390 0x34f384 - stub
fixme:msi:msi_unimplemented_action_stub MigrateFeatureStates -> 11 ignored L"Upgrade" table values
err:msi:ITERATE_Actions Execution halted, action L"MaintenanceType_Net" returned 1602

```

 Yes, I can remove the Lingvo 10 files, but how do I remove its entries from system32.reg?  Does it crash because of msi installer (I read somewhere that these are PITA)?

Thanks!

---

