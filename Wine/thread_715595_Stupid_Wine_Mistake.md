---
title: "Stupid Wine Mistake"
date: 2008-03-05
forum: Wine
---

### Post by MetalManiacMat on 2008-03-05
I'll get straight to the point, I've deleted everything in the .wine folder in my home folder. I've tried removing wine completely from the Synaptic Package Manager and tried reinstalling.... even tried updating but nothing. but wine config seems to be still working. so now im here asking for help over a stupid mistake ive made

---

### Post by FrozenFox on 2008-03-05
By 'completely' do you mean you used purge?

Open the terminal/console and 

sudo apt-get purge wine
sudo apt-get update
sudo apt-get install wine

Then try opening a program in wine from the terminal and give us more useful output (the error in specific given in the terminal). Perhaps try:

wine wordpad.exe

I'm betting when you say nothing but winecfg will work, it's because the version in the repositories atm for you is probably broken, in which case i'll just point you to winehq or something to download the .deb from there.

---

### Post by MetalManiacMat on 2008-03-05
"wine wordpad.exe" seems to work, (after about 30 secs in terminal)
but ive tried other applications with no luck.
in .wine there is only 2 files "system.reg" and "user.reg"
anyway heres the code i got from wordpad since im to much of a n00b to know how to open a windows application using wine in the terminal from the desktop.
```
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/mat', starting in the Windows directory.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
err:wineboot:main Cannot set the dir to L"c:\\windows" (2)
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:richedit:RichEditWndProc_common EM_SETTARGETDEVICE: stub
fixme:richedit:RichEditWndProc_common EM_SETTARGETDEVICE: stub
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet

```

---

### Post by kostkon on 2008-03-05
Open a terminal and give
```
winecfg
```
This command should recreate your *.wine* folder.

---

### Post by MetalManiacMat on 2008-03-06
Sorry kostkon, but nothing happened, just the same errors messages as wordpad gave me. but Wine Config did open after idling in the terminal for about 30 seconds.

---

### Post by MetalManiacMat on 2008-03-10
so nobody has any ideas at all?? because i would like to be windows free

---

### Post by christhemonkey on 2008-03-10
Type this into the terminal:
```
rm -rf ~/.wine 
wineprefixcreate
```

And you should be ready to go.

---

### Post by buried on 2008-03-10
The code above should delete everything in directory .wine, if all fails=reinstallation

---

### Post by SnakeHips on 2008-03-11
> **christhemonkey said:**
> Type this into the terminal:
```
rm -rf ~/.wine 
wineprefixcreate
```

And you should be ready to go.

Yup ,that fixed it for me :-)

---

