---
title: "Does 3dstudio max 9 work on wine?"
date: 2011-08-31
forum: Wine
---

### Post by Scottty on 2011-08-31
Hello

I was wondering if 3d studio max 9 works on Wine?

I was also wondering if you can do as much with Blender as you

Can with 3dmax9.

I would appeciate any feedback

I would like to stick with Blender but if 3dmax 9 is much better maybe I should stick with it.

Thanks
Scott

---

### Post by thatguruguy on 2011-08-31
I've never used 3dstudio max, but blender is pretty full-featured.

EDIT: According to [this]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=8544"), people have had mixed results installing 3D Studio Max using Wine.

---

### Post by X-Seti on 2012-02-03
I've been watching Youtube videos, clips here and there about those who got 3dsmax to run on linux but none really tell you how this can be done or for the fact this can be replicated for others.

I have been researching the possibility of getting 3dsmax 9 working on Ubuntu 10.10 as this seems a good place to start.

Maybe 10.04 or 11.04 but I will not be testing stuff that has anything to do with unity.

The most important thing to remember is you have all the windows dlls registered with wine to make your version work.

Running 3dmax from the terminal this can tell you what is missing and in some cases can be installed using winetricks.

Dotnet2, some needed fonts and some other dlls. 

I will post my progress in a new topic once I have a version up and running.

Ok, lets get to work! - Edit Imageshack is a joke.
[[IMG=http://img854.imageshack.us/img854/1641/ubuntu1010.png][/IMG]](http://imageshack.us/photo/my-images/854/ubuntu1010.png/)


Keith (X-Seti)

---

### Post by X-Seti on 2012-02-03
Digging into this more I get some wine bugs - for those interested in the console output look here - [http://pastebin.com/qLmqcxbD](http://pastebin.com/qLmqcxbD)

On and upwards - :)

Other needed stuff like **msxml3** and **cc580**

I already have **dotnet20** installed with [B]d3dx9_26, d3dx9_39, devenum, dinput, dinput8, dsound, dxdiag, msscript, riched20
[/B]

I know some of this looks overkill but I also copied the Fonts from the Windows XP's folder into the wine's windows Fonts folder as I have noticed a lot of other apps depend on these being there.

....  

[email]k@devbox12:~/.wine[/email][/email]/drive_c/3dsmax9Trial$ winetricks msxml3 cc580

```

Executing w_do_call msxml3
Executing load_msxml3
Using native override for following DLLs: msxml3
Executing winetricks_early_wine regedit C:\windows\Temp\_msxml3\override-dll.reg
Executing wine msiexec /i msxml3.msi
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:msvcr90:__clean_type_info_names_internal (0x60613064) stub
err:richedit:ReadStyleSheet skipping optional destination
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msvcr90:__clean_type_info_names_internal (0x60613064) stub
fixme:msvcr90:__clean_type_info_names_internal (0xcad5c8) stub
Executing w_do_call comctl32
comctl32 already installed, skipping
You opted in, so reporting 'msxml3 ' to the winetricks maintainer so he knows which winetricks verbs get used and which don't.  Use --optout to disable future reports.

```

Ok now the main **Setup.exe** and **directx 9c** stuff next

Edit ---- 

```
err:richedit:ReadStyleSheet skipping optional destination

``` 

This will scroll continuously in the terminal when DirectX9c is being installed, My best guess was to wait this out - 7 mins later I get to the next window.

The Autodesk 32bit trial installer...

Read and Accept the agreement - Press Next and wait. 

Edit ---- 

Name and Standalone - Press Next and wait for the window to change as at it goes dark for 4 mins.

Next window untick the following.

Help files.
Additional Maps.
Architectural Materials

Then press Next, Next and Next again..

Installer looked like it was doing well but now I feel like a Muppet, I am looking into these 2 errors

```

err:msi:ITERATE_Actions Execution halted, action L"StartServices" returned 1627
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1627
fixme:msvcr90:__clean_type_info_names_internal (0x60613064) stub
err:rpc:I_RpcGetBuffer no binding
err:rpc:I_RpcGetBuffer no binding
fixme:msvcr90:__clean_type_info_names_internal (0x7a38d5c8) stub

``` Read more - Click [http://pastebin.com/z7ASJ2Sx]("http://pastebin.com/z7ASJ2Sx")

...

---

