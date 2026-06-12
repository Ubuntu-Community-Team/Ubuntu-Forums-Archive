---
title: "Everquest with Wine"
date: 2007-06-20
forum: Wine
---

### Post by Jaxilian on 2007-06-20
Anyone got Everquest working on Wine?

I tried with no special configuration ,but at character selection everything is upside down and text is unreadable.

Wine version : 0.9.39

---

### Post by hikaricore on 2007-06-20
I know very little of everquest, but here's the wine application database page:

[http://appdb.winehq.org/appview.php?iAppId=229](http://appdb.winehq.org/appview.php?iAppId=229)

Maybe it will help you.  ^_^

---

### Post by Jaxilian on 2007-07-02
bump

---

### Post by Jaxilian on 2007-07-04
This is what I get when trying to run it:

```

$ wine EverQuest.exe fixme:advapi:SetSecurityInfo stub
flodis@zelos-laptop:~/.wine/drive_c/Program Files/Everquest$ fixme:d3d:IWineD3DDeviceImpl_SetMultithreaded No thread safety in wined3d yet
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x182188) : stub, simulating 64MB for now, returning 64MB left
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
[ERROR]   - Mouse Wheel supported = TRUE

fixme:d3d:IWineD3DDeviceImpl_ResourceReleased Vertex buffer released while bound to a state block, stream 0
[DEBUG]   - LoginViewManager::HandleAction() - the client is exiting for some reason...
fixme:d3d:IWineD3DDeviceImpl_ResourceReleased Vertex buffer released while bound to a state block, stream 0
err:d3d:IWineD3DDeviceImpl_Reset Cannot change the back buffer format yet
err:d3d:IWineD3DDeviceImpl_Reset What do do about a changed auto depth stencil parameter?
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock

```

---

### Post by Jaxilian on 2007-07-10
bump

---

### Post by Jaxilian on 2007-07-20
bump

---

### Post by Jaxilian on 2007-07-30
Confirmed that with latest Wine 0.9.42, EverQuest does not work. Everything is upside down and mirrored.

status: **unplayable**

but I am not an expert at Wine so someone might have done better than me. If so please respond here.

---

### Post by fktt on 2007-08-02
1 or 2? thats the first thing i would like to know(ps. 2 is a total NO)  (1 is"runnable" afaik(well.. so to say), so im guessing you mean that one..)

though i guess its right to say that everQ is a sad no :( its directx game afterall.. :(

---

### Post by Jaxilian on 2007-08-02
> **fktt said:**
> 1 or 2? thats the first thing i would like to know(ps. 2 is a total NO)  (1 is"runnable" afaik(well.. so to say), so im guessing you mean that one..)

though i guess its right to say that everQ is a sad no :( its directx game afterall.. :(

I mean EverQuest 1

---

### Post by Jaxilian on 2007-08-06
> **fktt said:**
> 1 or 2? thats the first thing i would like to know(ps. 2 is a total NO)  (1 is"runnable" afaik(well.. so to say), so im guessing you mean that one..)

though i guess its right to say that everQ is a sad no :( its directx game afterall.. :(


EverQuest 1 works well under Cedega though so the problem is Wine

---

### Post by hikaricore on 2007-08-06
> **flodis said:**
> EverQuest 1 works well under Cedega though so the problem is Wine


If it worked before and no longer does this is called a regression.

Check to see if there is an existing report on the WINE Application DataBase page, if not, consider adding one to inform other users and the WINE devs.  ^_^

---

### Post by Jaxilian on 2008-02-29
Any success now with latest wine?

---

### Post by tpb211 on 2008-08-22
Everquest 1 runs excellent with the latest version of wine.

---

### Post by tekno62 on 2008-09-05
I cant get EQ to do anything in ubuntu I have wine 1.1.3 but not sure how to set up wine.

I have it set to default setting, Windows XP - not sure about the rest. 

I have read the mine site and downloaded the D3DX9_30.dll and installed it in my windows /system32 dir with not much luck. Im not sure how to install it but copied it from my real windows drive

---

### Post by tekno62 on 2008-10-03
Sigh - Everquest is the only reason I have windows.

---

