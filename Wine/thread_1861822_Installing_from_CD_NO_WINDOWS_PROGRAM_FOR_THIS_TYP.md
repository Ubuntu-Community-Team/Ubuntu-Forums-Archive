---
title: "Installing from CD NO WINDOWS PROGRAM FOR THIS TYPE OF FILE ERROR"
date: 2011-10-16
forum: Wine
---

### Post by Trior27 on 2011-10-16
Hello!
I'm trying to install my old Sim City 3000 from it's CD.

When I try to execute the SETUP.EXE in /media/cdrom0/setup/english via nautilus I get the following error message from wine:

"Error
There is no windows program configured to open this type of file"

I get the same error if I try to execute LAUNCHER.EXE program at /media/cdrom0/launcher

When I try to do it via terminal the following way:

```
#cd /media/cdrom0/setup/english
#wine SETUP.EXE
```
I get the following:
```
wine: Bad EXE format for D:\setup\english\SETUP.EXE

```

I'm using Ubuntu 10.10 and wine 1.2.2.

Thanks in advance

---

### Post by Trior27 on 2011-10-16
I was suspecting that the CD was broken, so I installed the game in WindowsXP using virtual box. It installs fine but when I launch it it crashes to desktop almost instantly, just black screen for a couple of secs and then crash without any error message. Still I would like to run it on wine instead.

---

