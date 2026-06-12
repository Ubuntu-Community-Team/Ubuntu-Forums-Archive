---
title: "Running a .bat file in Wine"
date: 2014-08-28
forum: Wine
---

### Post by jj.wauters on 2014-08-28
I have a very big third party .bat file along with the necessary files in one folder.

Running this .bat file in Windows is working fine
Running this .bat file in Wine stopped early due to the fact it's not finding the files used in the same folder.
As I don't like to change the bat file, i'am looking for a manner to force retrieving the current folder.

I wrote this .bat to reproduce the problem:

[TABLE="class: outer_border, width: 800"]
[TR]
[TD]echo OFF

if exist *.txt  goto :FOUND

if not exist *.txt  goto :NOTFOUND

:FOUND
dir *.txt
goto :END

:NOTFOUND
@echo I did not found any txt files

:END
pause
[/TD]
[/TR]
[/TABLE]


When running in Windows, it shows me the txt files.
When running in Wine it says the txt files are not found.

---

### Post by sudodus on 2014-08-28
It seems that the ***if*** statement cannot identify files via the wild card (*) in the wine version of cmd, and it causes your bat file to fail.

```
$ wine cmd
CMD Version 1.4

Z:\media\multimed-2\test\test0>if exist *.txt echo yes it exists

Z:\media\multimed-2\test\test0>if exist hello.txt echo yes it exists
yes it exists

Z:\media\multimed-2\test\test0>[COLOR=#0000cd]dir *.txt
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
Volume in drive Z has no label.
Diskvolymens serienummer är 0000-0000

Directory of Z:\media\multimed-2\test\test0

2013-03-09     17:39           141  1-50.txt
2012-03-31     16:24            12  hello.txt
2013-02-10     20:03           516  result1.txt
       5 files                   10,415 bytes
       0 directories     24,164,999,168 bytes free


Z:\media\multimed-2\test\test0>[/COLOR]

```

If you are prepared to use some other command and rewrite the bat file, it might help to know that ***dir*** can identify files via the wild card (*)

---

### Post by jj.wauters on 2014-08-28
As the batch file is so long, complex and referencing more than 125 times with different wild card combinations to the files to be treated,
I prefer not to change it. 

It is unfortunate that it does not work in Wine, so I will run the batch in Windows and copy the result into Ubuntu.

Anyway thanks for the clear response.

---

