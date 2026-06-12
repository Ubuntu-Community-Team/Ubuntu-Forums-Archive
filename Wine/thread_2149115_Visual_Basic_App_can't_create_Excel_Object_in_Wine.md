---
title: "Visual Basic App can't create Excel Object in Wine"
date: 2013-05-27
forum: Wine
---

### Post by Marcelo Ruiz on 2013-05-27
Hi all!
I am running wine in Ubuntu 12.10 amd64.
I have a program in Visual Basic 6 (lets call it Report) that reads some databases and then creates by sending all the information to Excel. In windows, when I click the export button it will open Excel and show the report.
Unfortunately I cannot make it work in wine. Even though I managed to install Excel 2003 and Report in the same wine win32 prefix, I get an error '91': Object variable or with block variable not set.
I used winetricks to install the following DDLs:

```
comctl32
comctl32ocx
comdlg32ocx
jet40
mdac27
mdac28
mfc42
mmmask
msvcirt
msxml3
riched20
riched30
richtx32
vcrun6
vcrun6sp6
wsh56vb
wsh57
```

The ddls overriden (native, buildin) for Reporter are:

```
comctl32
jscript
odbc32
odbccp32
oleaut32
oledb32
riched20
scrrun
vbscript
```

Excel has no overriden DLLs.

When I run Report, the console output is:

```
wine .wine/drive_c/Program\ Files/Report.exe
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
fixme:storage:create_storagefile Storage share mode not implemented.
err:ole:CoGetClassObject class {ecabb0c0-7f19-11d2-978e-0000f8757e2a} not registered
err:ole:CoGetClassObject no class object {ecabb0c0-7f19-11d2-978e-0000f8757e2a} could be created for context 0x1
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 0/00/0000, dlt (d/m/y): 0/00/0000
fixme:heap:RtlCompactHeap (0x110000, 0x0) stub
```


Even though I am not a Visual Basic programmer, I read in the Internet that usually you make this call to create the Excel object to pass it data later:

Code:
CreateObject("Excel.Application")


Maybe that part is the one failing... I am totally lost, and any help will be really appreciated!
Thanks!

---

### Post by Rebelli0us on 2013-05-27
Is the vb6 app using DDE to send data to Excel?  If the app is important to you why not run real Windows OS in a virtual machine?

---

### Post by QIII on 2013-05-27
*Moved to **Wine***

---

### Post by Marcelo Ruiz on 2013-05-27
Hi, thanks for your answer.
What is DDE? 
I tried running the app in a virtual machine with shared folders between ubuntu an virtualbox but it's awfully slow, that's why I want to run it in wine.

---

