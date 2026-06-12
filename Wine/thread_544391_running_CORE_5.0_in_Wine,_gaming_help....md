---
title: "running CORE 5.0 in Wine, gaming help..."
date: 2007-09-06
forum: Wine
---

### Post by drapaki on 2007-09-06
here is the program i am trying to run in Wine for some school work:

[http://www.vitechcorp.com/products/downloads.html](http://www.vitechcorp.com/products/downloads.html)

it seems as if the install went smoothly but when i run it i get these errors (screenshots):

the company said that they don't support linux but that one of their developers mentioned that [I]"In speaking with our development team, I am told that CORE requires Windows generally and its registry specifically to operate properly.  We neither recommend using nor provide support for CORE outside of Windows. 

That being said, I am also told that there are programs available for Wine designed to assist it in running video games.  One of the developers said that he thinks this may help plug some of the holes in Wine."
[/I]

any hope/help/suggestions as to what he may  be inferring?  I don't know much at all about computer games...

---

### Post by drapaki on 2007-09-09
bump

---

### Post by jacob01 on 2007-09-09
call the manufacture up and see what the prob is but don't tell them u are running it in linux.

they might tell you what things may cause it to make an error like that (since it is an error found within the program not wine) and if it is minor you might be able to fix it and get it working

 worth a try

if you tell them you use linux they will say, "no it doesn't support linux and that it will never work"

:cool:

---

### Post by cogadh on 2007-09-09
Rather than provide the error messages from the program, it would be much more helpful to give us whatever messages are produced in the terminal by Wine. Whatever is causing the error would be much easier to diagnose with that info.

---

### Post by drapaki on 2007-09-10
how do i do that?

---

### Post by cogadh on 2007-09-10
Open a terminal window and run the program like this:
```
cd ~/.wine/drive_c/Program\ Files/Program/Directory
wine program.exe
```
Replace the "Program/Directory" and "program.exe" with the application's actual directory and executable name. Wine will the output any errors it encounters into the terminal window, which you can then copy and paste here. Please use the forum "[code]" tags when you post any output, it will make it easier to read.

---

### Post by drapaki on 2007-09-10
```
err:module:import_dll Library MFC40.DLL (which is needed by L"C:\\Program Files\\Common Files\\Vitech Corporation\\CORE 30\\TX4OLE.OCX") not found
err:ole:get_inproc_class_object couldn't load in-process dll L"c:\\Program Files\\Common Files\\Vitech Corporation\\CORE 30\\TX4OLE.OCX"
err:ole:create_server class {3d6d5d2f-b9f2-101c-aed5-00608cf525a5} not registered
err:ole:CoGetClassObject no class object {3d6d5d2f-b9f2-101c-aed5-00608cf525a5} could be created for context 0x7
err:module:import_dll Library MFC40.DLL (which is needed by L"C:\\Program Files\\Common Files\\Vitech Corporation\\CORE 30\\TX4OLE.OCX") not found
err:ole:get_inproc_class_object couldn't load in-process dll L"c:\\Program Files\\Common Files\\Vitech Corporation\\CORE 30\\TX4OLE.OCX"
err:ole:CoGetClassObject no class object {3d6d5d2f-b9f2-101c-aed5-00608cf525a5} could be created for context 0x1


```

:confused:

---

### Post by cogadh on 2007-09-10
If you have a Windows install, copy the MFC40.dll from its System32 directory and put it in the ~/.wine/drive_c/windows/system32 directory in Ubuntu. Then run winecfg, go to the Libraries tab and add MFC40.dll to the library overrides. You won't find MFC40.dll in the drop-down list, just type it in and click "Add". After adding it, select it from the list of overrides and click "Edit". Change it from the default to "Native (Windows)". Now try running the app the same way you did this last time and see if there are any new errors.

If you do not have a Windows install to copy the .dll from, do a Google search for it, you may be able to download it legally.

---

### Post by drapaki on 2007-09-11
no-go yet, but way better!  
```
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\WIN98\\SYSTEM\\olepro32.dll" failed with error 1813

```

maybe sometime you can explain what i just did?

---

### Post by cogadh on 2007-09-11
Some of the DLL files common to Windows or required by certain apps are not included in Wine for any number of reasons. Occasionally you will need to use a Windows native DLL file in place of the missing Wine DLL. What you just did was add a native DLL and told Wine to use it, which has obviously eliminated the initial error.

Now, the new error is a bit different. Wine does have an olepro32.dll already, but its development is only 5% complete, meaning it is not really functional, it is only there as a place holder for future development or in case any applications need to detect the presence of the DLL, but not actually use it. You can do the same thing that you did with MFC40.dll, except this time, olepro32.dll is available on the drop down list in the Libraries tab. When you copy over the new olepro32.dll, I recommend renaming the original one, but not deleting it, just in case.

---

### Post by drapaki on 2007-09-11
did that.. but now i get this error:
```
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\WIN98\\SYSTEM\\olepro32.dll" failed with error 3

```

somewhat different.. but...

---

### Post by cogadh on 2007-09-11
Hmmm, that file path kind of concerns me, there is no "WIN98" directory in Wine, so I am curious as to why it is looking for it. What Windows version do you have set in winecfg?

---

### Post by drapaki on 2007-09-11
Xp

---

### Post by cogadh on 2007-09-11
Try running it with different Windows versions, starting with Windows 98. If that doesn't work, I may be stumped on this one. I did find some anecdotal evidence that this may be a problem that cannot be solved. There are a few other applications that encounter this same or similar errors in Wine and no one has been able to work around it.

---

### Post by drapaki on 2007-09-11
window 98 renders a new error.. perhaps fixable?

```
err:thunk:_loadthunk (VTK1631W.DLL, stv_ThunkData16, VTK3231W.DLL): Unable to load 'VTK1631W.DLL', error 2

```

---

### Post by cogadh on 2007-09-11
Not sure, I'm not familiar with those particular DLL files. They don't appear to be standard Windows DLL files and a Google search didn't provide any useful info. I've hit a brick wall on this one, my friend. Looks like we'll have to hope someone else has a useful answer.

---

### Post by drapaki on 2007-09-13
anyone else have any enlightening suggestions on this topic?

---

### Post by drapaki on 2007-09-20
feeling low... saw this program run seamlessly on a mac today.. bummer...

:-({|=

---

### Post by Petrush on 2008-10-01
I'm thinking about the possibility to run core in wine, did you get it to work in the end? When you saw it on the mac, was it in some vmware/fusion/paralells windows environment?

Regards

---

### Post by quintessentialk on 2008-11-15
I remember having CORE running some time last year on my mac. I don't remember what version of wine I was using at the time, but since 'CORE" hasn't been revised in that time, there must be some magic configuration of wine that will work.

With the 1.0.1 build, though, I reproduce the same problems as discussed here, error message for error message.

---

