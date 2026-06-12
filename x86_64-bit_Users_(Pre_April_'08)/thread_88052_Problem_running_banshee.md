---
title: "Problem running banshee"
date: 2005-11-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by grsing on 2005-11-09
I had banshee running a while ago, and when I tried to use it again, it won't start.  When I run it from the terminal, this is what I get:

gregg@GRSBuild:~$ banshee

(<unknown>:842): GModule-CRITICAL **: g_module_close: assertion `module != NULL'  failed

Unhandled Exception: System.ApplicationException: Sqlite error
in <0x00320> Mono.Data.SqliteClient.SqliteCommand:ExecuteReader (CommandBehavior  behavior, Boolean want_results, System.Int32 rows_affected)
in <0x00037> Mono.Data.SqliteClient.SqliteCommand:ExecuteNonQuery ()
in [0x00019] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src /Database.cs:115) Banshee.Database:Execute (System.Object query)
in [0x000c0] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src /Database.cs:197) Banshee.Database:ExecuteSqlStatements (System.Collections.Arra yList statements)
in [0x00015] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src /Database.cs:136) Banshee.Database:InitializeTables ()
in [0x00039] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src /Database.cs:76) Banshee.Database:.ctor (System.String dbname, System.String dbp ath)
in [0x0002a] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src /Library.cs:68) Banshee.Library:ReloadDatabase ()
in [0x00028] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src /Library.cs:57) Banshee.Library:.ctor ()
in [0x0005c] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src /Core.cs:144) Banshee.Core:.ctor ()
in [0x0000b] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src /Core.cs:73) Banshee.Core:get_Instance ()
in [0x000ef] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src /Main.cs:78) Banshee.BansheeEntry:Main (System.String[] args)


Any suggestions?  Thanks.

---

### Post by pitr on 2005-11-10
Seems to be related to sqlite. If I remember correctly banshee creates a file endig with .db in your music library. Try to move it out of the way and see if that help.

---

### Post by grsing on 2005-11-10
Not a problem anymore; I made a stupid mistake and had to reinstall (unrelated).  Oh well, works now.

---

### Post by sbassett on 2006-01-12
[QUOTE=grsing]Not a problem anymore; I made a stupid mistake and had to reinstall (unrelated).  Oh well, works now.[/QUOTE]

Anyone else have this issue, and a possible solution? I have rmoved the banshee.db file, and this is still issue.

---

