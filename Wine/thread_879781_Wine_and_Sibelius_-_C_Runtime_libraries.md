---
title: "Wine and Sibelius - C Runtime libraries"
date: 2008-08-04
forum: Wine
---

### Post by RussianPhysicsGuy on 2008-08-04
Hi all,

I've been trying to install Sibelius 5 using wine. I've gotten the .NET environment and the Visual C++ Runtime Libraries installed using winetricks, and the program itself is installed now, but when I start up Sibelius it gives me a runtime error "R6034, An application has made an attempt to load the C Runtime Library incorrectly." 

Anyone have any ideas? Winetricks only has C++ runtime libraries, not C, but in my experience with Windows, C++ libraries are "backwards compatible" with C... 

I've got Wine 1.0 on Hardy Heron.

Help is greatly appreciated!
Thanks,
-George

EDIT

So I downloaded VC80.CRT and others from [http://www.sweetpotatosoftware.com/files/microsoft.vc80.crt.zip](http://www.sweetpotatosoftware.com/files/microsoft.vc80.crt.zip) , and copied those into the Sibelius folder, and ran it from the Terminal - this is what I get:

<code>
fixme:actctx:parse_assembly_elem wrong version for assembly manifest
fixme:actctx:parse_manifest_buffer failed to parse manifest L"C:\\Program Files\\Sibelius Software\\Sibelius 5\\Microsoft.VC80.CRT\\Microsoft.VC80.CRT.manifest"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Sibelius Software\\Sibelius 5\\Sibelius.exe" failed, status c0000142
</code>

---

### Post by liquidfire_24 on 2008-08-28
im having the same issue with geting Adobe CS3 master suit up and going i dont under stand why the manifest are being assembled

---

### Post by pietgrijs on 2009-01-20
I'm having the exact same problem with Sibelius on Ubuntu 8.10! I just started a topic on it. Have you guys found anything yet?

---

### Post by tnd on 2009-02-21
Answer is here! 
Let me know if it works for you.

[http://ubuntuforums.org/showthread.php?p=6776274#post6776274](http://ubuntuforums.org/showthread.php?p=6776274#post6776274)

---

