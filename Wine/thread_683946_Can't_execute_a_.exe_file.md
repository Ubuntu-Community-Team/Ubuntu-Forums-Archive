---
title: "Can't execute a .exe file"
date: 2008-01-31
forum: Wine
---

### Post by samba on 2008-01-31
Hi all,

I've just installed Wine because I needed to execute a file.exe . So I apt-get installed the wine package today, but when i go to the folder where file.exe is and run "wine file.exe", I receive the message

```

Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/wheremyfileis/', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\file.exe": Module not found

```

Is that normal? What am I doing wrong?

Thanks a lot! :-)
vincent

---

### Post by happyhamster on 2008-01-31
Are you using an older wine version perhaps? (current = wine 0.9.54) If so, try to configure wine first, using the command:

winecfg

Then check if there's a .wine folder in your home dir: open your home dir (Places-->Home Folder), toggle View Hidden Files by pressing ctrl-h. There should be a .wine folder containing two folders "dosdevices" and "drive-c".

---

