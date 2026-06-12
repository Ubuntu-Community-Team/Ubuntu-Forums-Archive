---
title: "Cannot install ODBC drivers for MS Access"
date: 2013-11-12
forum: Wine
---

### Post by shestero on 2013-11-12
Cannot install ODBC drivers for MS Access (mdb) under Wine 1.4 / Ubuntu 12.04 64bit.
I downloaded and installed MDAC_TYP.EXE and downloaded jet40sp8_9xnt.exe.
Trying run jet40sp8_9xnt.exe got the following error:
```
~/Downloads$ wine jet40sp8_9xnt.exe
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:setupapi:extract_cabinet_file awful hack: extracting cabinet "C:\\users\\shestero\\Temp\\IXP001.TMP\\Jetsetup.CAB"
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program files\\Common files\\Microsoft shared\\dao\\dao2535.tlb" failed with error 2
```
Also:
```
C:\Program Files\Common Files\Microsoft shared\dao>regsvr32 dao360.dll
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\Common Files\\Microsoft shared\\dao\\dao2535.tlb" failed with error 2
Successfully registered DLL dao360.dll
```
the mentioned file dao2535.tlb is indeed absent in the directory.
What shall I do?

PS When I install MDAC_TYP.EXE i switch the wine to W2k mode, after it I turn it back to XP. Am I right?

---

### Post by Mark Phelps on 2013-11-12
You can NOT install drivers using Wine. 

Wine is not a Windows emulator -- meaning -- you must continue to use Linux drivers, not Windows drivers.

---

### Post by oldfred on 2013-11-12
I tried setting it up several years ago to a db I had. Not sure how much may have changed. Is the Access a .mdb or one of the newer verions? Older one may work.

Note: Permission for /home/fred/database.mdb is 777
chmod 777 ~/file.mdb

Downloaded from synaptic:
unixodbc-bin
unixodbc
libmyodbc

then I followed the instructions here to configure a odbc connection:

sudo apt-get install mdbtools
sudo ODBCConfig
ODBCConfig

For a different database but shows ODBCConfig
[http://schoolsplay.wikidot.com/wiki:howtoopendatabaselinux](http://schoolsplay.wikidot.com/wiki:howtoopendatabaselinux)

---

### Post by shestero on 2013-11-14
Thank you for your replays.

1. As I know the Windows applications running in Wine can use both UnixODBC or Windows-native ODBC drivers. The latest is possible by overriding Wine-dlls to Windows-dlls.
More information may be found at: [http://wiki.winehq.org/NativeOdbc](http://wiki.winehq.org/NativeOdbc)
My original question was about the using Windows ODBC drivers.

2. libmyodbc is about MySQL that isn't my question about.

3. Big thank you for getting me know that mdbtools provide Unix ODBC driver (I wasn't aware about this). The software package actually called libmdbodbc1 in my Ubuntu 12.04.
Unfortunately I suspect it doesn't work with a new accdb files, does it?

4. I found ODBCConfig in one ancient Ubuntu (8 or 9) but I was unable to get it in Ubuntu 12.04. I used ODBCManageDataSourcesQ4 instead.

5. I was fail in trying to use Unix mdbodbc in my simple program, written in Qt4:
Error at Line : syntax error near 'test'
syntax error near 'test'
Got no result for 'select 'test'' commandSegmentation fault (core dumped)
It is very similar to the situation described here: [http://qt-project.org/forums/viewthread/34057](http://qt-project.org/forums/viewthread/34057)
The same error I've got using tora application from standard Ubuntu software packages when I tried to connect to the ODBC-source in order to test it.
That looks like a bug either in Qt4 or most probably in mdbodbc.

6. Could you advice me some simple standard application to check Unix ODBC connection in Ubuntu (just to see a peace of data of my table)?

---

